## Abstract

<!-- Context -->
Users expect multi-modal route planners that combine all modes of transportation to find the best journey to their destination.
<span class="comment" data-author="RV">Bit of a tautology here: <q>multi-modal</q>/<q>all modes</q>. But also, the sentence has been condensed (as appropriate in an abstract) to the point where it is no longer fully correct: users do not expect multi-modal route planners, they do not really expect it to give the best journey. They know that they might get suboptimal results; in fact, they have come to expect (in my opinion) that the route is just a suggestion, not the best. What they would really want is the best, probably. TL;DR: ensure the sentence is truthful, even though condensed.</span>
These route planners have to combine different kinds of data sources,
<span class="comment" data-author="RV">Again, a condensed truth: they don't <q>have</q> to combine this (runtime, design time?). In practice, data originate from different sources though (which is probably what we should say).</span>
such as road networks and schedule-based public transit. We focus on the link between the two; specifically, the walking distances between stops.
<!-- Need -->
Research in this field so far has found that computing these paths dynamically is too slow, but that computing all of them results in a quadratically scaling number of edges which is prohibitively expensive in practice. The common solution is to cluster the stops into small unconnected graphs, but this restricts the amount of walking and has a significant impact on the travel times. Moreover, clustering operates on a closed-world assumption, which makes it impractical to add additional public transit services.
<span class="comment" data-author="RV">Excellent problem statement!</span>
A decentralized publishing strategy that fixes these issues should thus (i) scale gracefully with the number of stops; (ii) support unrestricted walking; (iii) make it easy to add new services and (iv) support splitting the work among several actors.
<!-- Task -->
We introduce a publishing strategy that is based on the Delaunay triangulation of public transit stops, where every triangle edge corresponds to a single footpath that is precomputed. 
This guarantees that all stops are reachable from one another, while the number of precomputed paths increases linearly with the number of stops. Each public transit service can be processed separately, and combining several operators' can be done with a minimal amount of work.
<!-- Object -->
<span class="comment" data-author="RV">Normally, you would introduce here what the current article covers; but I think your abstract flows fine, so we don't need to follow the suggested structure.</span>
<!-- Findings -->
Approximating the walking distance with a path along the triangle edges overestimates the actual distance by 20% on average. 
<!-- Conclusion -->
Our results show that our approach is a middle-ground between completeness and practicality. It consistently overestimates the walking distances, but this seems workable since underestimating <span class="comment" data-author="RV">overestimating??</span> the time needed to catch a connection is arguably better than recommending an impossible journey.
<!-- Perspectives -->
The estimates could still be improved by combining the haversine distance with our approximations. Alternatively, different triangulations could be combined to create a more complete graph.
<span class="comment" data-author="RV">haversine and triangulation come out of the blue here (but not a major problem if fixing involves too much text)</span>
