---
layout: post
title: AWS-Hosted NLP Book Recommendations
subtitle: Better Reads
gh-repo: better-reads/BR-Data-Science
gh-badge: [star, fork, follow]
tags: [data, natural language processing, AWS, books]
image: /img/br_mockup.png
comments: false
---


Better Reads, a book recommendation website based on a natural language processing model powered by spaCy and Elastic Beanstalk, was my first collaborative project with three other data scientists and six web developers.  Unfortunately, we pulled the plug on the AWS-hosted backend due to mounting costs, [but the website is still available on Netlify](https://better-reads-marketing.netlify.com/).

![picture](https://raw.githubusercontent.com/mmastin/mmastin.github.io/master/img/br_mockup.png)

First we web scraped 30,000 book details and descriptions from a popular online repository. After data cleaning and removal of non-English titles, our final database consister of ~18,000 books. Using AWS SageMaker Notebooks, we trained a spaCy convolutional neural network, vector-based model on the dataset.

In order to decrease the size of deployment, we built a cosine-similarity function to compare test descriptions against the database and generate recommendations. With the database stored in an AWS S3 bucket and model hosted on Elastic Beanstalk, we built a Flask app to interface with the Netlify website and return the model's top 10 recommendations as a JSON object. The resulting ISBN numbers were then sent to the Google Books API to retrieve corresponding covert art and book descriptions.

![pic2](https://raw.githubusercontent.com/mmastin/mmastin.github.io/master/img/br_model.png)
