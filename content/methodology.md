## Method
{:#methodology}

<figure id="triangulation">
  <img style="width:49%" src="img/base_tris.svg" alt="base triangulation">
  <img style="width:49%" src="img/mivb_tris.svg" alt="new triangulation">
  <img style="width:49%" src="img/missing_tris.svg" alt="missing edges">
  <img style="width:49%" src="img/combined_tris.svg" alt="combined triangulation">

  <figcaption>
  	Illustration of how two footpath graphs are merged. 
  	The subfigures in counter-clockwise order, starting at the top right: (i) the triangulation of an additional regional operator; (ii) an existing triangulation of a larger network; (iii) the edges that are needed to attach the new triangulation to the existing one and (iv) the end result.
  </figcaption>
</figure>

<!-- ### Point Set Triangulation -->

We use a Delaunay triangulation of the public transit stop locations. The triangle edges represent footpaths that need to be computed. A road network route planner is then used to compute the actual path lengths. The construction of the triangulation  uses the Euclidean distance between their WGS84 coordinates instead of the walking distance between them. Delaunay triangulations can be generalized to any metric space, but the walking distance is not a metric because it could, in theory, lack the symmetric property. Even on foot, you cannot always retrace your steps – either due to legal restrictions or due to physical limitations. And just as important, this would bring us back to the case where an unpractical amount of path lengths have to be precomputed. Other metrics such as the great-circle distance can be used, but none of them have any relation to the walking distance so we opted for the most simple metric to implement. This also means that the theoretical guarantees of the Delaunay triangulation only hold for the Euclidean distance. Empirical tests are required to verify that the end result is indeed useful. 

<!-- ### Merging -->

The paths between stops of a single operator can be calculated independently from the rest. Combining the graphs of two operators is done by comparing their individual triangulations to the triangulation of their combined stops – and computing the missing footpaths. This process is illustrated in Fig. 1 where the graph of a city's public transit network is merged with the one from the region around it. The combined graph is the union of each operators' graph with the additional edges that connect the two graphs. Operators typically have their own service area, which means that the vast majority of paths will be between stops of the same operator. Thus making it possible for anyone to combine several operators' graphs with minimal work. And just as important: the results can be shared and reused, which stands in stark contrast to the conventional approaches. The paths can be published similar to the Routable Tiles dataset so that sharing them does not come at a significant extra cost. The paths can be published similar to the Routable Tiles dataset so that sharing them doesn't come at a significant extra cost.


<!--
### Publishing on the web

<figure id="example snippet" class="listing">
````/code/example.ttl````
<figcaption markdown="block">
The definition of a single footpath
</figcaption>
</figure>

It is easy enough to share data on the web, but special care is needed to ensure that the data can actually be used and understood by anyone. 
Listing 1 contains a minimal description of a footpath between two Belgian railway stations. 
It describes the essential information: the stops that are connected by this path and the distance between them.
Data consumers should be able to verify this information though, so we must also describe who did the calculation, when they did it, and which datasets they used.
In this paper we do not go into more detail on how the footpath graphs themselves should be published. 
We propose an approach similar to the Routable Tiles dataset: fragmented geospatially and with hypermedia controls interconnecting the fragments. 
-->