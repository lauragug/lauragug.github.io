---
layout: post
title: Scoring users with RadiumOne
published: true
---



[RadiumOne](https://radiumone.com) is an advertising platform that offers a full spectrum display advertising solution. They serve an agreed upon number of ad impressions at a given cost for the client and, in doing so, hit a pre arranged number of users to go on to purchase the product. RadiumOne proprietary data sources and intelligent targeting algorithms allow them to generate a high conversion rate.

For my [Insight Data Science](http://insightdatascience.com) Project I collaborated with RadiumOne to explore whether it is possible to gain additional value from unsupervised learning on the site space based on the users that visit each site and the shared users between sites. 

Slides are located [here](http://www.slideshare.net/LauraGuglielmini/laura-guglielmini-demo-53678095).

## The problem: predict users similarity to converters
Given a set of converters, people who actually bought, for a specific advertiser, we want to find the users that are more similar to converters by exploiting what we know about user behaviour. RadiumOne provided the converters population for a week traffic, about 4M events and 50000 siteids, and the users population for a day, 450M events and about 300M userids. These numbers give an approximate idea of the size of the users-site space, which is very sparse.

## The approach
For the whole dataset of user events, the individual user behaviour can be described by the vector of visited sites and eventually by the number of visits. At the same time from the dataset of user events we can evaluate the matrix of Jaccard similarities for the domains, where similarity between sites A and B is defined by the number of shared users, divided by the union of the users of A and B. These quantities can as well be interpreted as the weight on the edges of the network of sites.
This description of the space of sites can be employed to reduce the dimensionality of the vector of users via PCA or to produce a clustering of the sites, thus producing a new set of features to be employed in our predictive model. 
By training our model on a set of users and converters for a given campain, we can obtained scores, probability of conversion, for a new set of users.
