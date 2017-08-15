---
layout: post
title: JetBrains Rider .NET IDE First Impression
comments: true
---

One of my co-workers told me today about the new Rider IDE from JetBrains, and I was intrigued.  He's been a big fan of ReSharper (productivity tools for Visual Studio, mostly for the .NET world, but I also noticed that they have a C++ version), and so he was excited at the prospect of a full IDE with the ReSharper tools included natively.  I was excited about the prospect of a relatively lightweight IDE (Visual Studio always feels kind of sluggish, even on fast hardware) and native cross-platform development with full profiling tools at an attractive price-point. 

I'd never used any JetBrains products, but I've looked at their offerings before and they always seemed to have an impressive suite of tools, along with pretty fair pricing, so I thought I'd check Rider out and see if it's worth it for me to look into further.  To be fair, I should mention that most of my experience with Visual Studio has been on Visual Studio 2013 and below, but I have used Visual Studio 2015 and 2017 on some small personal projects.

# Download and Install

 I downloaded the [evaluation version](https://www.jetbrains.com/rider/download/download-thanks.html) (free for 30 days) and started to play around with it.  I've only spent around 30 minutes with it so far, but I'm pretty impressed.  The download was about 250 MiB, and the installation probably took less than a minute.  This compares favorably to my experience downloading and installing Visual Studio 2017 Community Edition, which (if I recall correctly) was several GiB large, and probably took on the order of 10-20 minutes to get fully downloaded and installed.  I chose the default options for the install (which I think probably installed every feature they offer), and there were a few more configuration windows than I expected, but it was pretty painless and (most importantly) over in just a couple minutes.

# First Impressions

After firing up the IDE for the first time, my first impression was that it looks a lot like Visual Studio, but much snappier.  I loaded up a little test project that I had created with Visual Studio 2017, with a few files and a handful of NUnit tests, and it all behaved very predictably.  It didn't ask me to do anything to change the `.sln` or `.csproj` files, which was nicer than what I'm used to.  Visual Studio has always seemed to require upgrading those files, with varying degrees of success (usually works properly, but not always automatically), and trying to open newer projects with older Visual Studio versions sometimes just fails until you manually go in and edit the version to match what it expects.

I can't really go in depth with the features and functionality yet, but just in the little bit of time that I've used it, it feels well laid out, and it's clear that they've given a lot of thought to the UI and UX.  Here are just a few items that I think are interesting in how they're handled in Rider. 

## Tasks

Rider has the concept of `Tasks`, which is intriguing to me for a couple reasons:

1. Apparently Visual Studio used to have this feature but it was removed in Visual Studio 2015.  Even though I use a version of Visual Studio that has task support, I was never aware of the functionality.  In contrast, `Tasks & Contexts` is the first option in the `Tools` menu in Rider, and as such caught my eye quickly, and I wonder if maybe the reason that I've never used it in Visual Studio 2013 is because it was kind of hidden out of the way.  

2. The feature itself allows you to create named tasks (go figure!), that each have their own associated context, including files open, cursor position, etc.  For someone like myself, who tends to jump between a variety of different and sometimes unrelated tasks (sometimes by choice, often out of necessity), I think that this could really help me to keep track of what I'm doing and help me use my time more efficiently by being able to context switch more quickly.

You can quickly create and switch between tasks using the menu in the upper-right-hand corner.

![Rider Task menu]({{site.url}}/images/rider-post/TaskRider.png)

I did notice a little bit of a quirk in that if you mouse over the task for more than a second or so before clicking, you'll have to click again before you can actually change your task.  This happens because hovering opens sub-menu and the first click will just close that menu out (unless you click the `Switch` option), and the second click will open your task.  If you quickly select your task without mousing over for very long, it just takes one click.  I guess that makes sense, but it did feel a bit non-intuitive to me.

## NuGet

I've had many bad experiences with the NuGet Package Manager UI provided in Visual Studio, so much so that I've pretty well abandoned it in favor of the NuGet Package Manager Console because I could often not quite get the UI to do what I needed it to, particularly when working with multiple sources, and it was often kind of slow.  I like the way that Rider displays all the packages in a compact area (Visual Studio takes up at least twice as much space to show the same information as contained in this window):

![Rider NuGet window]({{site.url}}/images/rider-post/NuGetRider.png)

It's also nice that searching for a package brings up results in both your `Installed`, and `Available` packages.  The default view in Visual Studio's package manager is the `Installed` packages, and if you try to search for something there, it will only show the ones you have installed.  This makes sense, of course, but the UX isn't as nice as it could be, as most of the time that I'm trying to search for a package, what I really want to see are the ones that I _don't_ have installed yet.  Combining the two makes a lot of sense and makes it easier to quickly do what I need to do.

Of course, it's not really a big deal to have to click over to a different tab, but I think that this is a good example of the type of polish that Rider exhibits.  It's something that's really irked me in other products that I've used (Visual Studio, Jenkins, etc.) to have to switch to different pages to move between my installed and available packages, so I'm happy to see that Rider gets it right.

## Other Language Support

As far as I can tell, Rider is just for .NET projects (though my co-worker did mention that he opened up a C++ project with it and was able to do some things with it), and so can't be used with C++ or other project types that normal Visual Studio can be configured to work with.  I'm not necessarily convinced that this is a bad thing, as C++ support in Visual Studio always seems to be lagging behind its .NET counterparts, and Intellisense, value introspection, and various other features never seem to work quite as well in C++ in Visual Studio as they do in .NET.  JetBrains does include, among other things, similar IDEs for C++, Python, Java, Ruby, PHP, and other web languages.  I haven't used any of them, but I believe that they're all built on the same IDE platform, so they should all feel similar, and having a separate product dedicated to each  language might help them to be more of first-class citizens rather than the ".NET first, then everything else" approach of Visual Studio.

## ReSharper

I haven't really used ReSharper, so can't really comment on it much, but I have seen others use it to good effect to simplify refactoring and profile applications.  At only $40 additional over the cost of the base product, getting the full ReSharper Ultimate suite to go with the IDE seems like a no-brainer if you're going to invest in the IDE at all.

## It Just Works

My apologies to Apple, but applying the "It Just Works" moniker to Rider seems to fit.  Starting up a solution completed quickly (in at least a couple seconds less time than it took Visual Studio to start up), built successfully, and ran all the NUnit tests (and displayed them more nicely than Visual Studio's Test Explorer).  It feels polished and designed to help developers be productive quickly.  That said, however...

## It Just Works... Unless you use MSTest

One notable feature lacking from Rider is MSTest support.  I expect that this will likely be a deal-breaker for many companies/individuals that have significant MSTest-based automated test suites.  However, according to their [blog post](https://blog.jetbrains.com/dotnet/2017/08/03/rider-2017-1-jetbrains-net-ide-hits-rtm/), that functionality will be coming soon: 

> We want to roll out at least two more releases this year: an inevitable bugfix release in a few weeks, and another major release (2017.2) in the Fall. Things that we expect to be addressing include support for MSTest and .NET Core 2.0, as well as releasing an SDK.

I'm glad to see that they're going to be addressing this fairly quickly, though it really seems kind of surprising to me that they didn't launch with this functionality already in place.  Given that MSTest is fairly decent and the default test option for .NET projects, it seems like it would have been higher priority to make their IDE work with that.

# Final Initial Thoughts

As Visual Studio 2017 has a free community version that probably most invidual developers (including myself) can legally use without paying anything for, I'm not totally convinced that Rider will make great inroads, at least initially, against Visual Studio.  However, I do find the pricing very fair, and probably not at all out of reach for the average developer.  An [individual subscription](https://www.jetbrains.com/rider/buy/#edition=personal) costs $139, the version with ReSharper Ultimate (including profiling tools) costs $179, and their full product package costs $249.  Business subscriptions are significantly more expensive, at $349, $449, and $649, respectively, which still seem fairly reasonable.  All of those subscriptions are for the first year, and subsequent re-subscriptions offer a substantial discount.  The cheapest professional version of Visual Studio ($499 at the [Microsoft Store](https://www.microsoft.com/en-us/store/d/visual-studio-professional-2017/dg7gmgf0dst5)) costs significantly more than the individual subscriptions and more than even all but the most expensive business subscription option, and I don't believe even in the latest versions that the profiling tools would match up well with what's provided in ReShareper Ultimate.  

All in all, I'm really pretty excited about this new IDE.  It might not displace Visual Studio 2017 Community Edition for me personally (though I am seriously considering purhcasing it), but I think a real, full-fledged Visual Studio competitor, backed by a large commercial company, that can interoperate with Visual Studio well, that offers cross-platform development (it runs on Linux, Windows, and Mac), and that's priced reasonably, can only be a good thing.  In general, Visual Studio is a good product, but its features sometimes feel dated, unpolished, or overly bulky and not intuitive.  I think Microsoft will need to up their game significantly to keep people from deserting Visual Studio, particularly if JetBrains should come out with a Community edition of Rider.  And the need for Rider to prove it can really compete with Microsoft's 800-pound gorilla should cause both companies to engage in some good healthy competition, which will ultimately benefit consumers of both products.

Hopefully this first-impressions article was useful to you.  I hope to continue using it and plan on posting a follow-up article in a month or so.  If you're using Rider, especially if it's replaced Visual Studio for you, please comment below. :)