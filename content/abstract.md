## Abstract

<!-- Context -->
Users expect route planners that combine all modes of transportation to propose good journeys to their destination.
These route planners use data from several sources such as road networks and schedule-based public transit. We focus on the link between the two; specifically, the walking distances between stops.
<!-- Need -->
Research in this field so far has found that computing these paths dynamically is too slow, but that computing all of them results in a quadratically scaling number of edges which is prohibitively expensive in practice. The common solution is to cluster the stops into small unconnected graphs, but this restricts the amount of walking and has a significant impact on the travel times. Moreover, clustering operates on a closed-world assumption, which makes it impractical to add additional public transit services. A decentralized publishing strategy that fixes these issues should thus (i) scale gracefully with the number of stops; (ii) support unrestricted walking; (iii) make it easy to add new services and (iv) support splitting the work among several actors.
<!-- Task -->
We introduce a publishing strategy that is based on the Delaunay triangulation of public transit stops, where every triangle edge corresponds to a single footpath that is precomputed. 
This guarantees that all stops are reachable from one another, while the number of precomputed paths increases linearly with the number of stops. Each public transit service can be processed separately, and combining several operators' can be done with a minimal amount of work.
<!-- Object -->
<!-- Findings -->
Approximating the walking distance with a path along the triangle edges overestimates the actual distance by 20% on average. 
<!-- Conclusion -->
Our results show that our approach is a middle-ground between completeness and practicality. It consistently overestimates the walking distances, but this seems workable since overestimating the time needed to catch a connection is arguably better than recommending an impossible journey.
<!-- Perspectives -->
The estimates could still be improved by combining the great-circle distance with our approximations. Alternatively, different triangulations could be combined to create a more complete graph.

<span class="printonly firstpagefooter">
<span class="footnotecopyright">
Copyright © 2019 for this paper by its authors. Use permitted under Creative Commons License Attribution 4.0 International (CC BY 4.0).
</span>
</span>
