---
inFeed: true
description: >-
  There are several ways to approach a research problem. One approach is to set
  up an experiment that can demonstrate a hypothesis true or false, execute it a
  few times until the outcome is consistent (collect data), and make a
  determination about the hypothesis from the experiment data. This is the
  scientific process we learn as children. I like the straight-forward nature of
  this approach, even if it isn’t much fun.
dateModified: '2017-12-22T01:19:05.081Z'
datePublished: '2017-12-22T01:19:13.368Z'
title: Demonstrating that I’m Wrong
author: []
publisher: {}
via: {}
starred: false
datePublishedOriginal: '2017-12-22T01:19:13.368Z'
sourcePath: _posts/2017-12-22-demonstrating-that-im-wrong.md
_type: Blurb

---
# Demonstrating that I'm Wrong

There are several ways to approach a research problem. One approach is to set up an experiment that can demonstrate a hypothesis true or false, execute it a few times until the outcome is consistent (collect data), and make a determination about the hypothesis from the experiment data. This is the scientific process we learn as children. I like the straight-forward nature of this approach, even if it isn't much fun.

I've been developing [my simple model of world order][0], primarily with the intent to demonstrate that it is far too simple to be useful or expanitory. I've been hard at work building a virtual research environment (more on that later) and I have some pretty solid results. In this case, "solid" means that I have clearly demonstrated that my simple model of world order is all but useless, except as a place to start working. This is the result I was expecting. 

I had written my initial model in NetLogo. I like NetLogo. It's got more capacity then many researchers ever utilize and it's an easy easy language, once you get used to the syntax. I don't like the way NetLogo's BehaviorSpace parameter sweeping tool presents the results, though. I developed an R script that converts the really, really wide BehaviorSpace results into a useable dataframe. Instead of using it, I decided to try [Jan Thiel's RNetLogo][1] package for R. This is a long-term project, so it makes sense to experiment with such tools. 

If I haven't written it down before, I'll write it now: I am a terrible programmer. Saying so is a prelude to the following remark: it took me a long time to figure out how to use RNetLogo the way I wanted. I'm pretty comfortable with it now. It took me a while to get comfortable though. To get started, I copy-pasted a few choice code snippets from the wilds of the internet. (Any experienced programmer reading this just cringed. Yah. I know.) It was months later that I started paying for this lazy approach to getting started. 

After a couple of sessions wrestling back and forth between R, NetLogo and RNetLogo I got my bearings and was able to generate some clean, usable data. Without knowing anybody else's experience with this setup, I'll make a blanket statement that using NetLogo's own BehaviorSpace is much faster than scripting up the same experiment in R and having R run the NetLogo experiments. That statement is ambiguous, so I'll clarify: it is much more complicated and it takes longer to write an R script to run NetLogo experiments via RNetLogo than it takes to set up the same experiments in BehaviorSpace AND it takes a lot longer to run the experiments through R than directly in NetLogo. It's worth it. The output data is ready to go the moments the experimentation script finishes running. I have a list of R dataframes that mean something and are useful without further manipulation. The output is glorious.

Once I'd gotten the particulars of RNetLogo figured out, I made my life more difficult by running it in parallel. It takes a lot less time---in my case, about 1/6th as long---to run the full parameter sweep. There is the added bonus of feeling like a mad scientist every time I kick off a script to run an experiment in parallel. I love it. I probably wasted as much time figuring out how to do it properly as it would have taken to run the experiments in series, but I don't care. I can re-run the experiment again tomorrow and save that time back again. This is important, because I had to re-run the experiment a few times, already. The full parameter sweep runs for about 9 hours in 6x parallel, so I can kick it off in the evening, spend some time with my kids, get a good night's sleep and analyze data the next morning. Without the parallel run, the same parameter sweep would cost me a week of evenings or four days (~54 hours) without touching my laptop for fear of crashing something and having to start over. A 6x speedup is significant.

I hadn't been reviewing the data long before I realized that it told me a lot about what was happening in my simulation, but nothing about how well my simulation mirrors anything in the real world. So, I set about finding some things to compare it against: real wars and real peace. So far, I've only implemented a comparison to real wars. Peace can wait, for now. 

I grabbed Kristian Gleditsch's [Expanded War Data][2], because he includes wars with as few as 2,500 military casualties (vs. the 10,000 required to be included in the more famous-er Correlates of War, _aka_ COW data). Gleditsch breaks his data out between interstate disputes and intra-state disputes (civil wars). I munged his diad-year data into two data files: interstate wars and all wars (civil and international). Because my simulation often runs for about 3,000 ticks and the Expanded War Data includes wars from 1816 to 2006, I decided that a tick in my simulation matches about a week of real-world time. My munged version of Gleditsch's data includes the unique wars (attributed to the first country in the diad) the number of weeks since 1 January 1816 on which the war started, when it ended, and the number of weeks in between. This allows me to randomly assign a real state identifier to each of the states in my simulation, create a "real war" in NetLogo for every war in the Expanded War Data that involved that state, then activate/delete the real war on the appropriate NetLogo tick. This method allows for historical inaccuracy through randomness, I realize. I expect that by running the simulation 30 times for each set of input data, I am correcting for the randomness. I do all that data munging in R but use NetLogo to randomly assign a real country's historical war data to each of the states (defined by the _num-states_ input variable).

The benefit of all this extra work is a little blue line inside the "Number of Wars" monitor. It seems like a small thing, but it represents the first level of verification and validation for the model. In the first image below, you can see that the experiment does not include civil war data. There are 70 states in my simulated system and each represents (nominally) a real state that existed in the period between 1816 and 2006\.
![A screenshot of a simulation that includes 70 states, but the real war data does not include civil wars.](https://the-grid-user-content.s3-us-west-2.amazonaws.com/feedbac3-c218-4c2d-81a2-52fe21672c27.png)

The pattern of war onset and duration without including civil wars does not look at all like the pattern produced by the simulation. The simulation creates many, many more wars. ![A screenshot of a simulation that includes 70 states and includes civil and international war data.](https://the-grid-user-content.s3-us-west-2.amazonaws.com/f4389ca9-7f4c-484b-8976-5075d3231525.png)

The pattern of real wars is even more different than the simulated wars if we include civil wars. 

Not that I won't do any further data analysis, but it's easy to see (without doing any further data analysis) that my simulation misses the mark. It's not even close. 

There's a lot of work to do before the simulation even gets interesting. 

[0]: http://www.studycomplexity.io/first-step
[1]: http://rnetlogo.r-forge.r-project.org/
[2]: http://privatewww.essex.ac.uk/~ksg/expwar.html