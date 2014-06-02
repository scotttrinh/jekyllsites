---
layout: post
title: "Considerations for the design of my next application"
---

This will be a thinking out-loud style post that will help me document
the thought process behind design considerations for a new application I
am developing for [work](http://earthshakingmusic.com). I will also use
it to record links to videos, blog posts, and other media that relates
to this stage in the application development process.

## The Business Process

I am constantly on the lookout for procedures at my job that make
us all groan when we have to do them. Those tasks are usually ripe for
tool-building and streamlining, and it gives me a great sense of pride
to know I've made something slightly more bearable for myself and my
co-workers.

One of the most common source of the groans is the process that
surrounds purchasing used items and consigning items for customers. Here
is the current process:

1. Customer brings the product to the store for evaluation.
2. We note the make, model and condition of the product.
3. We research used pricing using eBay's sold listings feature,
   Craigslist, and our own product history.
4. If we are paying cash or trade for the item, we average the price
   data we gathered in the previous step, and give the customer a quote
   on the cash or trade value based on a percentage of the average selling
   price of a comparable specimen.
5. If we are consigning an item, we discuss the pricing data found, and
   help the consignee determine the selling price they want to set, and
   inform them of the consignment fee that we would levy based on the
   selling price.
6. If everyone agrees to the terms, we create a new item in the system,
   associate the item with the customer, and print out a receiving log
   with the details.

## The Components

Given the business process outlined above, here are the individual
components that I have identified:

+ An item search component that has pluggable backends to handle eBay,
  Craigslist, and local item history searches. Can add more as more
  sources of data become available.
+ An item creation grid that streamlines the process of importing data
  from the item search component, and allows pricing to be set by margin
  percentage or explicitly.
+ Consignment vendor database that tracks information about the consignee,
  and ties to LightSpeed's customer database to keep contact information
  in sync.
+ An order generation script that takes the new items, and creates a
  purchase order, and fulfills the purchase order using the [Receiving
  Log](/2014/05/30/angular-django-app.html) API to increment the
  inventory and print a paper receipt for the customer.

## The Process Flow

<figure>
  <img src="/images/flowchart-useditem.png">
  <figcaption>Flow Chart of the Business Process</figcaption>
</figure>

Here is the basic flow from the user's perspective. You can see that
each process lends itself to a modular component we can build up. Some
of them can even be generic, reusable components, such as the item
editing grid, and obviously the data backends for pricing data.

## The Stack

As with the Receiving Log function, we will use the existing
Django/Python/PostgreSQL backend. On the client side, I will be using
Facebook's ReactJS for UI views and connecting to the backends via our
REST/Hypermedia API.
