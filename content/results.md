## Results
{:#results}

<figure id="all_errors">
  <div>
    <div style="width:47%; vertical-align:top; display:inline-block; text-align: left;">
      <img src="img/overestimation_3.svg" alt="approximation error">    
      <strong>2a: </strong> Linear regression plot comparing the actual distances to the approximations. The relative approximation error decreases as the distance increases. Note that the approximations are strictly overestimations due to the triangle inequality.
    </div>
    <div style="width:47%; vertical-align:top; display:inline-block; text-align: left; float:right;">
      <img src="img/overestimation_2.svg" alt="approximation error">
      <strong>2b: </strong> The same linear regression plot but with 8 bins. The mean and standard deviation is shown for each bin, along with the 95% CI in the grey shaded area. The approximation error does not exceed 25% in 95% of cases. 
    </div>
    
  </div>

  <div style="margin: 1em 0 .5em; text-align: left;">
      <strong>Fig. 2: </strong> The relative difference between the actual and the approximated distance has a higher variance for shorter paths. Every data point in these plots is a path in between railway stations where the distance is approximated using a graph of bus stops and the footpaths between bus stops and railway stations. 
  </div>

</figure>

We aim to verify two claims about our method: (i) the graph we construct is almost as good as the complete graph for route planning and (ii) footpath graphs can be merged with minimal effort. To verify the first claim we have used a graph of paths between bus stops to approximate the distances between railway stations. Edges between train stations and bus stops have also been added to make the railway stations reachable. Fig 2 shows that the approximation overestimates the actual distance by about 20% on average. This seems reasonable for route planners – it is better to underestimate the time needed to catch a connection than to recommend an impossible route.

<table>
  <caption>
  	<strong>Table 1: </strong> The number of paths that need to be computed to connect two operators.
  </caption>
  <thead>
    <tr>
      <th>Case</th>
      <th>Paths of first operator</th>
      <th>Paths of second operator</th>
      <th>Additional required paths</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Flanders + Brussels</td>
      <td style="text-align:right">107,171</td>
      <td style="text-align:right">7,969</td>
      <td style="text-align:right">2,508</td>
    </tr>
    <tr>
      <td>Flanders + Wallonia</td>
      <td style="text-align:right">107,171</td>
      <td style="text-align:right">94,730</td>
      <td style="text-align:right">4,020</td>
    </tr>
  </tbody>
</table>

To verify that combining the graphs from two operators does not require excessive work, we consider both the usual and the worst case scenario, respectively being mostly disjoint service areas and entirely overlapping service areas. We have taken the public transit operators from the Belgian regions of Flanders and Wallonia for the usual case and we revisit the case from Fig. 1 for the worst case, where the Brussels public transit network is added to the one from Flanders. The results in Table 1 show that in the usual scenario merging two operators is relatively straight-forward as most work has already been done. The worst case scenario shows that it is possible that merging two operators can still require a significant amount of work, although the vast majority has already been done. Our implementation contains some additional experiments and is available on [https://github.com/hdelva/planner.js/tree/footpaths](https://github.com/hdelva/planner.js/tree/footpaths) as a frozen branch of an experimental serverless route planner.
