+++
title = "GOPHER-GENERA - OCC 2026 "
date = "2026-07-06T11:55:00.000-07:00"
+++
# Trying to implement a spec-compliant gopher server on the Lisp Machine

## Day 1

This was unfortunately quite boring. I was running Errands most of this Sunday, and didn't have any time to sit down with my computer. However, through the power of *generative AI* I was able to at least learn a bit more about how Symbolics managed its software, and how Lisp works. Remember, I've never written anything in Lisp before, so this is a war on two fronts. The devil is in the details, and I'm sure most of the heartache is yet to come. 

## Day 0

I came across the [Old Computer Challenge](http://occ.sdf.org/#2026) while browsing [HackerNews](https://news.ycombinator.com/item?id=48702320) (as I do far too frequently) and it really piqued my interest. I unfortunately tend to be a very plan-heavy, implementation-light kind of person, and while it means my mind is constantly churning through new ideas, my keyboard stays cold, and my gits stay uncommitted. I decided that this would be my chance to finally get something out of my head and into the world by hijacking the power of social pressure.

### Getting into Lisp
On the top of my stack of machinations was Lisp, and learning the language. I had the pleasure of reading Mark Tarver's excellent essay [The bipolar Lisp programmer](https://marktarver.com/bipolar.html). I really connected with it, and Lisp seemed to have a lot of things I had missed in other languages. Homoiconicity was especially alluring (I studied theoretical linguistics at the UofA for my BA, so parsers, ASTs, and the like are my first love.) 

During my forays into the Lisp mythos I couldn't help but come across the [Lisp machines](https://en.wikipedia.org/wiki/Lisp_machine). From the [MIT CADR](https://mitmuseum.mit.edu/collections/object/1991.003.002) to the [Symbolics machines](https://en.wikipedia.org/wiki/Symbolics#The_3600_series), the  idea of a single-process, single address-space system running Lisp was exactly the kind of turtles-all-the-way-down idealism that I find irresistible. I already had a faint recollection of Symbolics' work in the field from an excellent [Aisanometry video](https://www.youtube.com/watch?v=sV7C6Ezl35A) and now I had the context to understand its appeal. 

Thankfully Brad Parker and some other amazingly talented folks have put a ton of effort into making Open Genera (the OS for Symbolics' Lisp machines) [runnable on modern x86_64 machines](https://www.unlambda.com/index.php). Since Open Genera was already designed by Symbolics to emulate a proper lisp environment on a 64 bit UNIX machine (DEC Alphas, I believe), running it on my Linux laptop is actually shockingly close to the original architecture. 

### What to make?

Since the topic of this year's OCC is to 'build something', and since I am light on cash and materials, I decided I would try to bring some new functionality to the Open Genera ecosystem. Additionally, I wanted the thing I built to be accessible to the general public. Finally, I wanted something that would give me a good idea of what software development on a Lisp machine looked like, and that was fairly well-defined. For me, that really only left implementing a Gopher server. 

Because [CL-HTTP](https://en.wikipedia.org/wiki/CL-HTTP) was such a success, and I assume just by timing and happenstance, Open Genera doesn't have built-in Gopher support. Open Genera 2.0 (the version I'm running) stands in the goldilocks-zone for a novel implementation. Unlike earlier Lisp machines, I have a system TCP package, so no messing about with Chaosnet. Since Gopher is pretty much just raw TCP over port 70, with a tiny bit of logic added on, most of the work is already done. I'm probably speaking with the naivete of inexperience, but the folly of fools is what gets projects started. 
