## Abstract

<!-- Context -->
Users expect multi-modal route planners that combine all modes of transportation to find the best journey to their destination. These route planners have to combine different kinds of data sources, such as road networks and schedule-based public transit. We focus on the link between the two, specifically the walking distances between stops.
<!-- Need -->
Research in this field so far has found that computing these paths dynamically is too slow, but that computing all of them results in a quadratic amount of edges which is prohibitive in practice. The common solution is to cluster the stops into small transitively closed graphs, but this restricts the amount of walking which has a significant impact on the travel times. On top of that, clustering operates on a closed-world assumption, which makes it impractical to add additional public transit services.
<!-- Task -->
A publishing strategy that fixes these issues should thus (i) scale gracefully with the number of stops; (ii) support unrestricted walking; (iii) make it easy to add new services and (iv) ideally the work can be split among several actors.
<!-- Object -->
We introduce a data publishing strategy that is based on a point set triangulation of public transit stops. The triangle edges determine the paths between stops that should be precomputed. This ensures that every stop is connected to at least two other stops, while the number of precomputed paths increases linearly with the number of stops. Each public transit service can be processed separately, as long as a separate data source provides the paths between stops from different providers. The work can be divided among several actors if they have a common frame of reference – such as IRIs. 
<!-- Findings -->
The amount of paths still makes the data hard to ingest though. This is alleviated by fragmenting the paths into geospatial clusters similar to the Routable Tiles dataset. In order to satisfy our second requirement we focus on the Delaunay triangulation because Delaunay graphs have been shown to good approximations of complete graphs. Empirical tests show that the paths along the triangle edges overestimate the actual distance by about 20% on average. This is not an unreasonable amount, and could even be beneficial to ensure transfers in case of delays. Finally, we investigate the amount of work that's required to incrementally add three providers with overlapping service regions.


<!-- Conclusion   -->
<!-- Perspectives -->
