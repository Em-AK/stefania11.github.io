---
layout: post-hover
title: Programing collective intelligence..
description: "..How to build the simplest recommendation engine in ruby"
category: articles
tags: [cosmos, api, cli, flatironschool]
image:
  feature: "knowledge_graph_banner.jpg"
---

> Some other eyes will look around, and find the things I've never found.
--Malvina Reynolds

For our final project at FlatironSchool we created a platform to help parents best respond their kids questions and discover stories/questions/answers via different concepts, characters. One of our ideas was to recommend stories to parents based on their previous activity with the goal of reproducing what in pedagogy is called “zone of proximal development”. The main motivation behind this feature is to enable users to learn new concepts by using references and concepts they already know.

<a data-flickr-embed="true"  href="https://www.flickr.com/photos/bferster/15156617496/in/photolist-ocp6Ds-fddyqQ-ovDKEK-owiUAg-otBETz-ehnmSk-obPETQ-nW2Sop-owytzH-9C31Sn-owD4wc-p6kCkj-xMN5NJ-wTeL42-xMLZ9j-xxAEpH-xPf8i1-xxAukp-ovRVRd-oezpXN-wLjZwS-sJEpUw-xuyvQ6-xA8Yxt-xbNusY-wKPAzD-xsnkiJ-xKCdgX-xsnjTW-xKCcQB-x3Xojz-w6N5SC-w73vPc-wS1P3C-xF7mAr-x3evQN-xiu16d-wL5rkX-t7gBVu-wKXDpE-xKAqGT-wKUvmm-8f3KNU-ovMMm2-je65xE-9z68a5-AUzg4-oac1ra-7P1AHV-6aS7FE" title="Figure 3.9: Vygotsky&#x27;s Zone of Proximal Development (ZPD)"><img src="https://farm4.staticflickr.com/3903/15156617496_4e933ea73c_b.jpg" width="600" height="600" alt="Figure 3.9: Vygotsky&#x27;s Zone of Proximal Development (ZPD)"></a><script async src="//embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>

There are multiple ways to implement this feature in our code but the main two directions are the following:

* __Option 1: Content-Based Similarity__. In this scenario we would analyze semantically our stories, concepts and characters and calculate the similarity between the different texts. This ruby gem could be used for this purpose. It calculates the similarity between texts using a bag-of-words Vector Space Model with Term Frequency-Inverse Document Frequency (tf*idf) weights. The problem with this approach is that our application would need to have a significant amount of content in order to get observable results.
* __Option 2 : Collaborative filtering__ where we enable our users to rate stories based on relevancy, difficulty, or likeability or any other criteria. Build a similarity matrix based on these ratings and use collaborative filtering to make future stories recommendations.
If we were to make an analogy with other recommendation engines build for music platforms the option 1 would be the Pandora model and the option 2 would be Last-Fm.
Based on the structure of our database, lack of initial content and desire to encourage and enable user choices I decided to look more into the second option.
There are a good number of different algorithms used in memory-based collaborative filtering to calculate the similarity between users. A few of the more widely used algorithms or formulae include Euclidean Distance, Pearson’s Correlation, Cosine-based vector similarity, and the k-Nearest Neighbor algorithm.

##How to build the most simple recommender in Ruby

Most of these collaborative-filtering algorithms use a rating range (1..x) but in order to build the most simple recommender engine in ruby only with likes and dislikes I turned to Recommendable gem.

###How does it work?

We find the number of stories that both Parent 1 and Parent 2 like, add it to the number of stories that both Parent 1 and Parent 2 dislike, and then divide that by the total number of different stories that Parent 1 and Parent 2 have rated.

```
$ ((@p1.likes + @p2.likes) + (@p1.dislikes + @p2.dislikes)) / (@p1.stories_rated + @p2.stories_rated)
```

##The Jaccard index

The Jaccard index can be described as the size of the intersection between two sample sets divided by the size of the union between the same sample sets.
In our case all we do is subtract the number of disagreements from the number of agreements, and divide by the total number of stories liked or disliked across the two parents.

###Pseudo-implementation in Ruby code:
<script src="https://gist.github.com/stefania11/b4d44c1078361277a1b7.js"></script>
[Source](http://davidcel.is/posts/collaborative-filtering-with-likes-and-dislikes/)

##Community based learning
<a data-flickr-embed="true"  href="https://www.flickr.com/photos/albertovo5/4113467727/in/photolist-7guADn-fQi9kb-95aKAn-j5iVxT-jj4mNb-i7Sk4z-feNTmi-7ndqJm-eJKuJm-aQgwca-pSnSW1-id4NKW-bW37Jb-h77Syf-iPpASY-79pRfj-jM9vFh-7HHDbg-4x3oAi-a8pWSS-g6YGtt-8jqFRH-exzvcz-nPFdZ5-fqNC7N-eeo47-n77LrV-haLQDC-hqHA2j-fETGyc-mN1iRR-8EMnHr-he54GG-4jNZ8d-mQZzKD-eUW7bd-fXsfDv-atGbxj-e5cZ8s-FA2hH-jA6xwo-9viFEH-9JMu7Z-q5rndx-jBz1MA-sqn5Ws-481nio-hxSHX8-7pJDFt-xZ2zch" title="Gimme a V"><img src="https://farm3.staticflickr.com/2639/4113467727_95a6b15d56_b.jpg" width="1024" height="683" alt="Gimme a V"></a><script async src="//embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>


If want to predict how you’ll feel about a specific story we need to get every user in our system that has rated that story and start calculating a hive-mind sum. If another user liked the story, we add your similarity value with them to the hive-mind sum. If they disliked it, we subtract it instead.
The main concept behind this formula is that if someone with tastes similar to yours likes this story, you’ll probably like it too but if a user with tastes dissimilar to yours likes the story, you’re less likely to like it. At the end we need to divide the hive-mind sum for this specific story and divide it by the total number of people that rated it.
From community similarity to collective intelligence programming
Paul Jaccard developed the coefficient de communauté (similarity coefficient) that we use in our code near the turn of the 20th century and today many major large companies like Amazon, Netflix, Facebook have integrated recommendations as one of their core features mainly focused on marketing outcomes.


>> Moving forward I am extremely interested how we could create more personalized learning environments that don’t rely only on large data-sets but more on the behavior of an evolving active community of learners.

@Stefania_druga 2015 
