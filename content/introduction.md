## Introduction
{:#introduction}

Fueled by the need for more sustainable transportation, users can pick between more forms of transport than ever before – and they expect that route planners can combine these to find the ideal journey. Those route planners integrate various kinds of data 
<span class="placeholder printonly">
<span style="display: block; height: 0em;"></span>
<!-- This is a dummy placeholder for the LNCS first page footnote -->
</span>
such as road networks and schedule-based public transit.
In this article, we focus on the link between the two, specifically on how to walk between stops. The walking time from one stop to another is commonly referred to as a [footpath](cite:citesAsEvidence delling2014round, dibbelt2018connection).

Computing these paths dynamically is often [too slow in practice](cite:cites delling2013computing, wagner2017public), yet computing them beforehand quickly becomes [prohibitively expensive in practice](cite:citesAsEvidence transfer-patterns, delling2014round, dibbelt2018connection). A small country such as Belgium already contains 100,000 public transit stops, yielding 10 billion pairs of stops. These scaling issues are often avoided by only evaluating algorithms on small unconnected footpath graphs. However, this restricts the amount of walking in a journey and has a [significant impact on travel times](cite:citesAsEvidence wagner2017public). On top of that, determining which stops belong to the same graph ultimately relies on a closed-world assumption; which makes it impractical to add additional public transit services.

Our goal is to find a method to compute and publish these footpaths in a scalable and decentralized manner. This implies that we need not publish all the paths, but ideally the ones that are published should allow for unrestricted walking. In practice this means that every stop in the footpath graph must be reachable from every other stop if there is a path between those stops in the real world. Various actors should be able to add information to this footpath graph, and adding a new service should not require changes in existing information. These actors would need a common frame of reference to combine their efforts, which can be provided by Semantic Web technologies.
