Somebody asked me for advice on how to give feedback to someone possibly over-building some code, and I ended up writing a lot!

----

When I think about overengineering, I think about a few specific coding habits that everybody does to some degree. And recognizing these is largely driven by experience, both messing up yourself and seeing other peoples' mistakes. So it's really hard to convince somebody without that experience that's what's happening.

- You can ask questions that lead them to consider the future differently.
- You can demonstrate a better way to write the same code - maybe they'll understand the improvement of the simpler version.
- You can try to compromise between a little and a lot of overengineering.

But ultimately people gotta make certain mistakes themselves to really learn. Because overengineering isn't about technical knowledge as much as humility. Believing that you can predict the future, even several months out, with a high degree of clarity, before that's possible. Sometimes senior engineers _can_ do that effectively, but they believe they can predict even farther out, and fall into the same trap.

# Classes of mistakes

We all do these, even people who have been doing it for 20 years. Hopefully when we're experienced we recognize that we're making the mistake sooner. Not always though!

1. **Write it all at once.** "Fully" implementing some class or module, where you're adding a bunch of code that isn't used yet. "Someday we'll need this," you think, not realizing how many times people will be looking at that code in the months and years to come not realizing it's completely unused. Those people will be mad at you! And those people might include you in the future!
2. **Premature generalization.** Adding abstractions that aren't needed yet. For example, a function call stack like "A calls B calls C calls D" and B or C are unused anywhere else. What are B and C doing besides hiding some of the logic from A and D? If you read a call stack that was 5 deep when it could be 1 or 2, how would you feel?
3. **Premature optimization**. Predicting the part of a program that needs to be fast, before you've run the whole thing and collected a lot of performance data. If this a brand new program, you're predicting a whole lot about the future, including how much latency or utilization is even going to matter.

# Questions I'd ask

- If you found a bunch of code that was X% unused, would you be glad the person wrote that code? Or would you be annoyed with them?
- What happens to our project if we don't have this {code, abstraction, optimized behavior} today?
- Is there anything you know now that you won't understand better in the future?

# Authoritative links

[C2Wiki - Do The Simplest Thing That Could Possibly Work](https://wiki.c2.com/?DoTheSimplestThingThatCouldPossiblyWork)

[C2Wiki - Make It Work, Make It Right, Make It Fast](https://wiki.c2.com/?MakeItWorkMakeItRightMakeItFast)

[C2Wiki - Premature Optimization](https://wiki.c2.com/?PrematureOptimization)

[C2Wiki - You Aren't Gonna Need It (YAGNI)](https://wiki.c2.com/?YouArentGonnaNeedIt)
