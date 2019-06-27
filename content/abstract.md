## Abstract

<!-- Context -->
Users expect multi-modal route planners that combine all modes of transportation to find the best journey to their destination. These route planners have to combine different kinds of data sources, such as road networks and schedule-based public transit. We focus on the link between the two, specifically the walking distances between stops.
<!-- Need -->
Research in this field so far has found that computing these paths dynamically is too slow, but that computing all of them results in a quadratically scaling amount of edges which is prohibitive in practice. The common solution is to cluster the stops into small unconnected graphs, but this restricts the amount of walking and has a significant impact on the travel times. Moreover clustering operates on a closed-world assumption, which makes it impractical to add additional public transit services.
<!-- Task -->
A decentralized publishing strategy that fixes these issues should thus (i) scale gracefully with the number of stops; (ii) support unrestricted walking; (iii) make it easy to add new services and (iv) support splitting the work among several actors.
<!-- Object -->
We introduce a publishing strategy that is based on the Delaunay triangulation of public transit stops, where every triangle edge corresponds to a single footpath that is precomputed. 
<!-- Findings -->
This guarantees that all stops are reachable from one another, while the number of precomputed paths increases linearly with the number of stops. Each public transit service can be processed separately, and combining several operators' can be done with a minimal amount of work. Approximating the walking distance with a path along the triangle edges overestimates the actual distance by 20% on average. 
<!-- Conclusion -->
Our results show that our approach is a middle-ground between completeness and practicality. It consistently overestimates the walking distances, but this seems workable since underestimating the time needed to catch a connection is arguably better than recommending an impossible journey.
<!-- Perspectives -->
The estimates could still be improved by combining the haversine distance with our approximations. Alternatively, different triangulations could be combined to create a more complete graph.