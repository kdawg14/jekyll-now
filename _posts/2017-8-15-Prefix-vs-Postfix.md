---
layout: post
title: Prefix vs Postfix Operators (Or, Expressing Your Intent)
comments: true
---

Most relatively experienced programmers have come across the idea that typically `++i`, using the prefix `++` operator, is more efficient than `i++`, the postfix operator, and this is usually the case.  Particularly for user-defined types, you should always use the prefix operator unless you know you need the postfix, because it avoids the unnecessary and potentially costly copying of the object into a temporary variable before increment takes place.

You might, however, come across people who say that that doesn't really matter, especially for primitives, because it's such a small performance gain, or because the compiler could (and very well may) optimize it away anyway.  These are not untrue points, and some will use that to argue why they shouldn't have to adhere to good programming standards, but please, please, please: **don't let yourself be persuaded by this argument.**  

Aside from the fact that it's silly and lazy to purposely program inefficiently, particularly when it's something as simple as putting a `++` before a variable rather than after, you will also (excepting times when you actually want the postfix operator behavior) _express your intent_ better with the prefix operator.  Personally, I feel that this is the more useful and real benefit of using the prefix operator, to make it absolutely clear that all you're doing is just incrementing and you don't care about the value prior to incrementing.

Reading code is a tricky business, and it's tough to do easily, efficiently, or correctly most of the time.  **Almost anything** you can do to make it easier for the people reading your code who aren't you right at the moment that you wrote it (which includes your future self!) to understand what you meant when you wrote your code is time and effort well spent.

So, while it is true that `i++` is usually not much different than `++i`, by only using the prefix operator you help the reader of your code to know that all you want is to just increment your variable.  On at least two separate occasions in the past, I had to spend extra time trying to read code where it wasn't obvious whether or not the postfix operator really was supposed to be used, or whether it was a bug from the previous author.  If I recall correctly, one of those was actually a bug and the postfix operator was used incorrectly; but both times I could have saved a good 5-10 minutes by not having to have wondered at all. 

Ideally, you should always only have as much code as you need, doing only what you need it to do.  If you don't need the temporary copy done by the postfix operator, **don't use it**.