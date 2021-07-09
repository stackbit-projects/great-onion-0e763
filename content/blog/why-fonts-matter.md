---
title: How I Won The Women in TensorFlow Hackathon Sponsored By Google
excerpt: >-
  Amet nibh adipiscing adipiscing. Commodo ante vis placerat interdum massa
  massa primis. Tempus condimentum tempus non ac varius cubilia adipiscing
  placerat lorem.
date: '2019-03-27'
thumb_image: images/google.jpg
thumb_image_alt: A pile of books on the table
image: images/12.jpg
image_alt: A pile of books on the table
seo:
  title: Why Fonts Matter
  description: >-
    Amet nibh adipiscing adipiscing ante vis placerat interdum massa massa
    primis
  extra:
    - name: 'og:type'
      value: article
      keyName: property
    - name: 'og:title'
      value: Why Fonts Matter
      keyName: property
    - name: 'og:description'
      value: >-
        Amet nibh adipiscing adipiscing ante vis placerat interdum massa massa
        primis
      keyName: property
    - name: 'og:image'
      value: images/12.jpg
      keyName: property
      relativeUrl: true
    - name: 'twitter:card'
      value: summary_large_image
    - name: 'twitter:title'
      value: Why Fonts Matter
    - name: 'twitter:description'
      value: >-
        Amet nibh adipiscing adipiscing ante vis placerat interdum massa massa
        primis
    - name: 'twitter:image'
      value: images/12.jpg
      relativeUrl: true
layout: post
---
It all started when I came across a [Meetup event](https://www.meetup.com/Seattle-WiDS-Meetup/events/gglgkryznbcc/) organised by the [Seattle Women In Data Science (SeaWIDS)](https://www.meetup.com/Seattle-WiDS-Meetup/) community in collaboration with Google to encourage women in Data Science to adopt [TensorFlow](https://www.tensorflow.org/).

![](/\_static/app-assets/Meetup.jpg)

For someone who’s been studying data science by myself for about a year, this was a learning opportunity I couldn’t miss out on.

Taking place in the Google campus in Kirkland, WA, the event was set to go through the [TensorFlow in Practice specialization](https://www.coursera.org/specializations/tensorflow-in-practice) on Coursera in a span of 6 weeks, the courses were delivered to the participants by the course author himself **Laurence Moroney**.

![](/\_static/app-assets/laurence.jpg)

![](/\_static/app-assets/audience.jpg)

Upon completion of the four courses, all participants will be granted the Coursera certificate and will have the opportunity to participate in a hackathon sponsored by Google and get a chance to win a Google Pixel 3A smartphone and Coral Boards.

# ![](/\_static/app-assets/prizes.jpg)&#xA;![](/\_static/app-assets/trophies.jpg)

Deep Learning was a bit overwhelming for me to dive into, but after reading the [Hands-On Machine Learning with Scikit-Learn and TensorFlow](https://www.amazon.com/Hands-Machine-Learning-Scikit-Learn-TensorFlow/dp/1491962291) book by Aurélien Géron, I started to put things into perspective and discovered more about TensorFlow. But still, I knew that I was lacking practical experience using Tensorflow, and **this course was exactly what I needed.**

Having no prior experience with TensorFlow nor building Deep Neural Networks (DNN), the idea of participating in the Hackathon didn’t even cross my mind, little did I know that by the end of the course I would be able to build, test, and train a complete DNN.

Having gone through the course material provided, and thanks to the impressive teaching skills of our instructor Laurence Moroney, followed by a month of practice, building deep neural networks became easy. As the Hackathon day was approaching I started to feel confident enough in my abilities that I decided to **take part of it**!

Since the goal of the event was to **promote women in Data Science**, I knew I wanted to consider a project that’s also related to the cause, but at the same time a project that solves a problem and adds value.

While brainstorming project ideas, I took time to reflect on solving actual problems I have: I use cosmetics and personal care products as part of my daily routine. For someone who has sensitive skin as well as being allergic to chemical ingredients in cosmetic products, I was tired of memorizing and looking up the name of every ingredient each time I wanted to buy a product to know if it’s safe for use.

Diving deeper into this topic, I was surprised to know how unregulated the cosmetic industry is in the USA, the FDA does not require cosmetic products and ingredients to be approved to go on market, as stated in their [website](https://www.fda.gov/cosmetics/cosmetic-products-ingredients/cosmetic-ingredients):

> The Federal Food, Drug, and Cosmetic Act does not require cosmetic products and ingredients to be approved by FDA before they go on the market, except for color additives that are not intended for use as coal tar hair dyes…

Also, according to the California Department and Public Health [California Safe Cosmetics Program](https://www.cdph.ca.gov/Programs/CCDPHP/DEODC/OHB/CSCP/Pages/CSCP.aspx):

> 595 cosmetics manufacturers have reported using 88 chemicals that have been linked to cancer, birth defects or reproductive harm in more than 73,000 products.

Hence the idea of building a cosmetic classifier (NLP DNN) that would arrange products according to their hazard concern level based on the ingredients it contains:

1.  High hazard concern

2.  Moderate hazard concern

3.  Low hazard concern

![](/\_static/app-assets/idea.png)

To my luck, the labeled data was already available on the [EWG Skin Deep®](https://www.ewg.org/skindeep) Cosmetics Database (database for personal care and beauty products that indexes and scores products based on ingredients hazard), for data collection, I scraped around 5000 product items, for each product I collected:

*   Product name

*   List of ingredients from packaging

*   EWG defined hazard concern score 1-10

![](/\_static/app-assets/product.jpg)

Once I had the data ready, I started exploring it.

I plotted the [Word Cloud](https://en.wikipedia.org/wiki/Tag_cloud) for a product with a low hazard score and a product with high hazard score to compare their ingredients reason for such score, in the example below, the figure on the left represents a low hazard product containing mainly water, fruit, juice and vegetable extract. As for the figure on the right, it represents a high product containing mostly synthetic, silicones (dimethicone) and petroleum-based compounds (PEG, PPG).

![](/\_static/app-assets/wordcloud.png)

As for the data preprocessing step, I applied the [tokenizer](https://www.tensorflow.org/api_docs/python/tf/keras/preprocessing/text/Tokenizer) and [padding](https://www.tensorflow.org/api_docs/python/tf/keras/preprocessing/sequence/pad_sequences) to the ingredients dataset:

![](/\_static/app-assets/preprocessing.png)

Then I [binned](https://en.wikipedia.org/wiki/Data_binning) the concern score into the three levels/categories that I defined, which I [hot encoded](https://en.wikipedia.org/wiki/One-hot) into a binary class matrix afterwards

![](/\_static/app-assets/binning.png)

For the **model building**, after multiple trials with different layers and parameters I ended up with this DNN model:



After training the model, I tested it with input ingredients that it had never seen and the model had correctly classified the products into the three categories.

Instead of stopping here, I wanted to make this classifier convenient for everyday use and available for everyone. That’s why I went ahead and decided to build a web app anyone can use by pasting the list of ingredients of a product and the model will classify it and display the category it belongs to as a result.
