---
inFeed: true
description: >-
  Nearly everybody who does modeling and simulation work has heard (and
  probably, repeated) the aphorism, “All models are wrong, but some are useful,”
  usually attributed to George Box. Less popularly known, but as often observed
  are the, “Six (or so) things you can do with a bad model” that James Hodges
  wrote for Operations Research (and later, a RAND Note) [1].
dateModified: '2018-02-19T21:19:47.426Z'
datePublished: '2018-02-19T21:19:47.754Z'
title: Verification and Validation
author: []
publisher: {}
via: {}
sourcePath: _posts/2018-02-19-verification-and-validation.md
hasPage: true
starred: false
datePublishedOriginal: '2018-02-19T21:03:31.474Z'
url: verification-and-validation/index.html
_type: Article

---
# Verification and Validation

Nearly everybody who does modeling and simulation work has heard (and probably, repeated) the aphorism, "All models are wrong, but some are useful," usually attributed to George Box. Less popularly known, but as often observed are the, "Six (or so) things you can do with a bad model" that James Hodges wrote for Operations Research (and later, a RAND Note) \[1\].

---

Models do not need to be perfect recreations of the real world in order to be useful. In fact, it's better that they NOT be. After all, it was the real world that appeared to be so confounding that the modeler decided to build a model of it in the first place. So, models need to have a few links to the real world that give us the courage to believe that they represent the problems we want to understand.

My model of world order will necessarily be MUCH more simple than the real world. But, I do want to see that it can represent the features of world politics that generate the general shape of things. I've written previously about building a model that proves my initial ideas were wrong. To that end, I needed to compare my model to some data about the real world. It wasn't _that _hard but, it wasn't that easy. This chart shows the time I've spent coding on it the past few weeks.

<iframe src="https://the-grid.github.io/ed-userhtml/?g=eJwtzdEOgiAYhuFbaZ7jX4IjGjlvBX4-lSXZgPT2a62j9-x57RTnd8ZgkTzCqWS-N0utr3IjOtzD1ZjQ8paoLC6DRj5CXNftSdJ3WpnJiAvQC8VnJYyEFKbrXcCVtYZvyz43g6Wf_e3_9QH8byX6" height="480" style=""></iframe>

Even this isn't sufficient. I can explain what I'm up to, but it all leads up to [this][0]: a really long bit of cypher code to import data into a Neo4j graph data base. My plan is to import into this single data base, all of the data contributed to and related to the Correlates of War project. There are some drawbacks. For the most part, this data is exactly what I need to compare my model with. It just needs to be in the right shape to be useful for agent-based modeling. As it gets published, it's not. I still have some work to do.

\[1\] Hodges, J. S. 1991\. "Six (Or So) Things You Can Do with a Bad Model." _Operations Research_. doi:10.1287/opre.39.3.355\.

[0]: https://github.com/usuallycwdillon/vvna "usuallycwdillon"