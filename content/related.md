## Related work
{:#related-work}

### Routable Tiles

The [Routable Tiles](cite:cites colpaert_eswc_demo_2019) dataset was recently proposed as a scalable and cost-efficient way to republish the OpenStreetMap road network using [Linked Data Fragments](cite:cites verborgh_ldow_2014). The data is fragmented into a hierarchy of files, which are interconnected with hypermedia controls for automatic data discovery. This allows clients to find and download the data they need without having to ingest en entire data dump, while being significantly easier to provide reliably than a full-fledged querying API. 

### Point Set Triangulation
A triangulation of a set of points $$ P $$ can be defined as a maximal set of non-crossing edges between the points of $$ P $$. Any triangulation of $$ n $$ points has exactly $$2n - h - 2 $$ triangles and $$ 3n - h - 3 $$ edges where $$ h $$ is the number of points on the convex hull. Triangulations are not unique however, and certain triangulations are [NP-hard to compute](cite:cites mulzer2008minimum). 

One particularly interesting triangulation, which can be computed in just $$ \mathcal{O}(n\log{}n) $$ time, is the Delaunay triangulation. Intuitively this triangulation tries to maximize the minimum angle of all the triangles, effectively avoiding long and narrow triangles. The Delaunay graph, which is simply the graph representation of the triangulation, contains several other interesting graphs such as the [nearest neighbor graph and the minimal spanning tree of $$ P $$](cite:cites toussaint, matula1980properties). They are also known to be good approximations of complete graphs; the shortest path between two points along Delaunay edges is at most [$$ 4 \pi / (3 \sqrt{3}) \approx 2.418 $$ times the Euclidean distance between them](cite:cites keil1992classes).