---
title: "API"
date: 2023-05-29T18:45:17-04:00
draft: false
---

# Web API

Web APIs are a service accessed from client devices to a web server using the Hypertext Transfer Protocol (HTTP). Client devices send a request in the form of an HTTP request, and are met with a response message usually in JavaScript Object Notation (JSON) or Extensible Markup Language (XML) format. Developers typically use Web APIs to query a server for a specific set of data from that server.

An example might be a shipping company API that can be added to an eCommerce-focused website to facilitate ordering shipping services and automatically include current shipping rates, without the site developer having to enter the shipper's rate table into a web database. While "web API" historically has been virtually synonymous with web service, the recent trend (so-called Web 2.0) has been moving away from Simple Object Access Protocol (SOAP) based web services and service-oriented architecture (SOA) towards more direct representational state transfer (REST) style web resources and resource-oriented architecture (ROA). Part of this trend is related to the Semantic Web movement toward Resource Description Framework (RDF), a concept to promote web-based ontology engineering technologies. Web APIs allow the combination of multiple APIs into new applications known as mashups.

In the social media space, web APIs have allowed web communities to facilitate sharing content and data between communities and applications. In this way, content that is created in one place dynamically can be posted and updated to multiple locations on the web. For example, Twitter's REST API allows developers to access core Twitter data and the Search API provides methods for developers to interact with Twitter Search and trends data.

# Synchronous versus asynchronous

An application programming interface can be synchronous or asynchronous. A synchronous API call is a design pattern where the call site is blocked while waiting for the called code to finish. With a asynchronous API call, however, the call site is not blocked while waiting for the called code to finish, and instead the calling thread is notified when the reply arrives. 
