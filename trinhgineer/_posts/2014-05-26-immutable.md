---
layout: post
title: "Immutability and Rich Hickey, or Why Metaphysics Matters, Even in
Computer Science"
---

Most of the time, it works out for us to be able to
think abstractly and to develop "rules of thumb". But, we should always
be open to thinking a bit more critically about the things we believe.

# Programming and Identity

Reading through even the documentation to Rich Hickey's Clojure language
gives one great insight into long standing philosophical
considerations. Topics such as identity through time and  what is a symbol
are deep, rich topics in philosophy, and they are treated by Clojure and
Functional Programming in general as important considerations to make.

For instance, take this excerpt from Clojure.org

> So, for this discussion, an identity is an entity that has a state,
> which is its value at a point in time. And <em><strong>a value is
> something that doesn't change.</strong></em> 42 doesn't change.
> June 29th 2008 doesn't change.
> Points don't move, dates don't change, no matter what some bad class
> libraries may cause you to believe. Even aggregates are values. The
> set of my favorite foods doesn't change, i.e. if I prefer different
> foods in the future, that will be a different set.
> <cite><a href="http://clojure.org/state">Clojure.org "Working Models
and Identity"</a></cite>

It is refreshing to see this level of metaphysical philosophy invade the
ultra-pragmatic world of computer science. I have no doubt that there
are other extremely astute students of philosophy in the world of
Computer Science, but it is exciting to see someone with the visibility of
Hickey pushing us to think a bit more deeply into how our abstractions
inform our programming.

# Immutablity to the rescue!

"Immutability?!" you might say, "But, I *need* to change things!" Quite
right. But, do you need to change the old thing, or simply save the
value of applying a function to the old thing? As noted in the above
quote from Clojure.org, "A value is something that doesn't change".

The thing that helped me over that hump was to think about how we do simple
math. When I buy pizza and a beer from the grocery store, I do not have
to mutate anything in order to derive the total of the receipt. The
pizza is $6, the beer is $8 and the tax is $1.12 (8% tax in Atlanta).
None of those values must change in order from me to capture the state
of $15.12 as my total grocery bill. At each point, I am taking the price
of the item as an immutable value and the total is simply a function of
the sum of those values plus the tax. When I go back to the grocery
store because I forgot the salad, I do not change the grocery bill value
to this new value, I simply have a new grocery bill that is the sum of
the salad, dressing, croutons and tax. It's not hard to reason that the
grocery bill is $15.12 for the first transaction and some other value
for the second transaction.

Follow the links below for some more food for thought on immutablity,
persistence and identity over time!

# Links

+ [Clojure Data Structures on Youtube, by Rich
  Hickey](https://www.youtube.com/watch?v=ketJlzX-254)
+ [Clojure, Rich Hickey's *FUN*ctional programming
  language](http://clojure.org)
+ [Mori, ClojureScript's persistent data structures for plain
  JavaScript](https://github.com/swannodette/mori)
+ [Persistent data structure on
  Wikipedia](http://en.wikipedia.org/wiki/Persistent_data_structure)
+ [Identity Over Time from the Standford Encyclopedia of
  Philosophy](http://plato.stanford.edu/entries/identity-time/)
