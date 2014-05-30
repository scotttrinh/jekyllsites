---
layout: post
title: "Peek at our Django/AngularJS Shipment Tracking Application"
---

All of the work that I do is hidden behind layers of firewalls and
authentication, so when I talk to people about what I do, I rarely get a
chance to show them! Well, here ya go!

# The Business Problem

We switched from a [closed point-of-sale
system](http://www.posim.com/products/legacy-systems/) to a [new
cloud-based point-of-sale system](http://lightspeedretail.com/cloud) last
year. For the most part, it has been a great boon to our business, and
having an open system with an accessible API has been useful.
However, there are are a few business processes that grew up around the
way POSIM did things, and in LightSpeed Cloud, there were no analogs.
One of those issues was "Receiving Logs".

## The Order Process

When we place an order with a vendor, more than half of the time, the
order comes in on separate shipments. In POSIM, there is a record of
each shipment called a Receiving Log that would track who checked in the
order, what items were received, the invoice ID issued by the vendor and
other shipment specific details. In LightSpeed, each shipment is
received against the order itself, and there is no way to track the
individual shipments. Obviously, there are great benefits to be gained
by continuing to track the shipments.

## The Design

I know a lot of developers work on a team with designers and managers
whom they must coordinate with in order to complete their project. In my
case, I am the be-all-end-all of this tool since I am the developer,
designer and one of the end users. So, I did not need to go through
design iterations, wireframes and complex model layouts. The
functionality I implemented is based on an existing, working system, so
most of the hard work modeling the tool was already done for me.

Since I think in HTML/CSS already, it was a no-brainer to do the initial
design and layout in HTML (actually Django Templates) and add features
directly to the view based on feedback and feature requests.

This shouldn't be taken as a condemnation of wireframing, UML or other
forms of design modeling. In fact, on my next work project, I am
using [gliffy](http://www.gliffy.com) to help visualize and direct
the build. I'll post a follow-up post about my efforts on that. Stay
tuned!

## The Solution
<figure>
  <a href="/images/lscextend1-screenshot.png"><img src="/images/lscextend1-screenshot.png" alt="Receiving Log Main Page"></a>
  <figcaption>Receiving Log Main Page</figcaption>
</figure>

In the above figure, you can see the initial screen that appears when
the user opens the Receiving Log bookmark. The screen contains 3 tabs:
Orders, Open Logs and Posted Logs. The orders come from LightSpeed's API
and we filter only orders that have items remaining to be received on
them. Open Logs are Receiving Logs that we are still working on, and
Posted Logs are completed. There is a filter box that makes finding
orders a bit easier and does a fuzzy search across all of the order
data, including items! The table of orders is an AngularJS directive
that is loaded asynchronously, which makes the [filtering trivial to
implement.](https://docs.angularjs.org/api/ng/filter/filter)

When the user selects an order, the following edit view greets them:

<figure>
  <a href="/images/lscextend2-screenshot.png"><img
src="/images/lscextend2-screenshot.png" alt="Receiving Log Edit View"></a>
  <figcaption>Receiving Log Edit View</figcaption>
</figure>

Most of this should be self-explanatory, but I will make a few comments
about the technologies. Most people who do any web design will notice
the obvious Bootstrap3/FontAwesome theme at play here. Natch. Bootstrap3
is pretty good about adding lots of whitespace around elements, but I
had to fit this whole view in the browser viewport of a 17" iMac, so
margins begone! 

Also note the editing grid. It is the [awesome
Handsontable](http://handsontable.com), a jQuery plugin for
spreadsheet-style data editing. Handsontable is a really brilliant piece
of kit, and allows for extremely flexible, programmatic manipulation of
data. I knew I wanted a spreadsheet edit view, since most of the time
you are moving down columns rather than tabbing through fields in a row.
Any edits made to the item details, such as SKU, Pricing, Description,
etc. are updating on the item in LightSpeed. There is a dirty-checker
that filters the items that were changed from the items that were not
changed to avoid updating unchanged items.

When the user completes the log, he/she is directed to the display view:

<figure>
  <a href="/images/lscextend3-screenshot.png"><img src="/images/lscextend3-screenshot.png" alt="Receiving Log Display View"></a>
  <figcaption>Receiving Log Display View</figcaption>
</figure>

This view is optimized for printing, although we rarely print them. The
accountant pays the vendors based on the Logs, so she is the primary
user of this view.

## Final Thoughts

This was a fun challenge. I had a clear picture of what kind of
affordances and functionality the user was expecting since I was
duplicating a feature from another program. I was also able to use this
as an opportunity to add some features that were missing from the old
implementation. 
