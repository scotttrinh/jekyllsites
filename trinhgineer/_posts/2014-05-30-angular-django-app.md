---
layout: post
title: "Peek at our Django/AngularJS application"
---

All of the work that I do is hidden behind layers of firewalls and
authentication, so when I talk to people about what I do, I rarely get a
chance to show them! Well, here ya go!

# The Business Problem

We switched from a [closed point-of-sale
system](http://www.posim.com/products/legacy-systems/) to a [new
cloud-based point-of-sale system](http://lightspeedretail.com/cloud) last
year. For the most part, it has been a great boon to our business, and
having an open system with an... accessible API has been useful.
However, there are are a few business processes that grew up around the
way POSIM did things, and in LightSpeed Cloud, there were no analogs.
One of those issues was "Receiving Logs".

## The Order Process

When we place an order with a vendor, more than half of the time, the
order comes in on separate shipments. In POSIM, there was a record of
each shipment called a Receiving Log that would track who checked in the
order, what items were received, the invoice ID issued by the vendor and
other shipment specific details. In LightSpeed, each shipment is
received against the order itself, and there is no way to track the
individual shipments. Obviously, there are great benefits to be gained
by continuing to track the shipments.

## The Solution
<figure>
  <a href="/images/lscextend1-screenshot.png"><img src="/images/lscextend1-screenshot.png" width="80%"></a>
  <figcaption>Receiving Log Main Page</figcaption>
</figure>

In the above figure, you can see the 
