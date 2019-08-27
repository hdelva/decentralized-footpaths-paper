## Method
{:#methodology}

<figure id="triangulation">
  <img style="width:49%" src="img/base_tris.svg" alt="base triangulation">
  <img style="width:49%" src="img/mivb_tris.svg" alt="new triangulation">
  <img style="width:49%" src="img/missing_tris.svg" alt="missing edges">
  <img style="width:49%" src="img/combined_tris.svg" alt="combined triangulation">

  <figcaption>
  	Illustration of how two footpath graphs are merged. 
  	The subfigures from top to bottom, left to right:
    (i) an existing triangulation of a larger network; 
    (ii) the triangulation of an additional regional operator;
    (iii) the edges that are needed to attach the new triangulation to the existing one and 
    (iv) the end result.
  </figcaption>
</figure>

<span class="placeholder printonly">
<span style="display: block; height: 4em;"></span>
<!-- This is a dummy placeholder for the LNCS first page footnote -->
</span>

<!-- ### Point Set Triangulation -->

We use a Delaunay triangulation of the public transit stop locations to approximate the full footpath graph, based on the insights from the related work section.
The triangle edges represent which stops will be directly connected through a footpath. Our representation of a footpath differs slightly from the conventional one; we use walking distances instead of walking times to avoid making assumptions about walking speeds.
A road network route planner is used to compute the walking distances between the stops. 

Delaunay triangulations can be generalized to any metric space, but the walking distance is not a mathematical metric because it could, in theory, lack the required symmetry property. Even on foot, you cannot always retrace your steps – either due to legal restrictions or due to physical limitations. And, equally importantly, this would bring us back to the case where an impractical number of path lengths have to be precomputed. This is why we the triangulation uses the Euclidean distance between the stops' WGS84 coordinates instead. Other metrics such as the _great-circle distance_ can be used, but none of them have any relation to the walking distance so we opted for the most simple metric to implement. This also means that the theoretical guarantees of the Delaunay triangulation only hold for the Euclidean distance because that's the metric was used for its construction. 

<!-- ### Merging -->

The paths between stops of a single operator can be calculated independently from the rest. Combining the graphs of two operators is done by comparing their individual triangulations to the triangulation of their combined stops – and computing the missing footpaths. This process is illustrated in Fig. 1 where the graph of a city's public transit network is merged with the one from the region around it. The combined graph is the union of each operators' graph with the additional edges that connect the two graphs. Operators typically have their own service area, which means that the vast majority of paths will be between stops of the same operator, thus making it possible for anyone to combine several operators' graphs with minimal work. The results can be shared and reused, which stands in stark contrast to the conventional approaches. The paths can be published similar to the Routable Tiles dataset so that sharing them does not come at a significant extra cost.
