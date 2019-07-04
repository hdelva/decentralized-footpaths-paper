## Results
{:#results}

<figure id="all_errors">
  <div>
    <span class="comment" data-author="RV">Remove the frames and top captions; plots have axes, not frames. (This is not about aesthetics but about ink minimization: the less noise, the more the graphs stand out.) Top captions can become unnecessary by more precise axis labeling.</span>
    <span class="comment" data-author="RV">Make plot text larger.</span>

    <div style="width:47%; vertical-align:top; display:inline-block; text-align: left;">
      <img src="img/overestimation_3.svg" alt="approximation error">    
      <span class="comment" data-author="RV">So it's not just overestimation, but also under? Adjust axis label.</span>
      <span class="comment" data-author="RV">Rescale the graph? Not all outliers have to be on there, I think. From 0 to 100?</span>
      <span class="comment" data-author="RV">Zeros should be zeros! Axes should originate bottom left.</span>
      <strong>2a: </strong> Linear regression plot comparing the actual distances to the approximations. Note that the approximations are strictly overestimations due to the triangle inequality.
      <span class="comment" data-author="RV">Don't say what we are seeing; that's what the graph is for. Say what we are supposed to conclude: <q>The approximation error is especially strong for short walks, but in 90% of cases, people will not be suggested to walk more than <var>x</var>m extra.</q></span>
    </div>
    <div style="width:47%; vertical-align:top; display:inline-block; text-align: left; float:right;">
      <img src="img/overestimation_2.svg" alt="approximation error">
      <strong>2b: </strong> Linear regression plot with 8 bins. The mean and standard deviation is shown for each bin, along with the 95% CI in the grey shaded area.
    </div>
    
  </div>

  <div style="margin: 1em 0 .5em; text-align: left;">
      <strong>Fig. 2: </strong> The relative difference between the actual and the approximated distance <span class="comment" data-author="RV"><ins>decreases with walking length</ins> / <ins>highly varies for short walks</ins> / whatever you want to say. <strong>Importantly</strong>, note how these are two different messages! Don't leave it up to the reader to conclude, tell the story that you want to draw their attention to.</span> Every data point is a path in between railway stations, the distance is approximated using a graph of bus stops and the footpaths between bus stops and railway stations.
      <span class="comment" data-author="RV">Idem; draw the conclusion for the reader.</span>
  </div>

  <span class="comment" data-author="RV"><code>&lt;figcaption&gt;</code>! Also, ScholarMarkdown will generate labels for you if you do things properly. Never hard-coded labels, not in the ref, not in the text.</span>

</figure>

We aim to verify two claims about our method: (i) the graph we construct is almost <span class="comment" data-author="RV">define? for what purpose?</span> as good as the complete graph and (ii) footpath graphs can be merged with minimal effort. To verify the first claim we have used a graph of paths between bus stops to approximate the distances between railway stations. Edges between train stations and bus stops have also been added to make the railway stations reachable. Fig 2 shows that the approximation overestimates the actual distance by about 20% on average. This seems reasonable for route planners – it is better to underestimate the time needed to catch a connection than to recommend an impossible route.

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
      <td>107171</td>
      <td>7969</td>
      <td>2508</td>
    </tr>
    <tr>
      <td>Flanders + Wallonia</td>
      <td>107171</td>
      <td>94730</td>
      <td>4020</td>
    </tr>
  </tbody>
</table>
<span class="comment" data-author="RV">Numbers are incomparable: should be right-aligned and have thousands separators. (Don't just right align, but have a class like <code>number</code> or <code>numeric</code> or so.)</span>

To verify that combining the graphs from two operators does not require excessive work, we consider both the usual and the worst case scenario, respectively being mostly disjoint service areas and entirely overlapping service areas. We have taken the public transit operators from the Belgian regions of Flanders and Wallonia for the usual case and we revisit the case from Fig. 1 for the worst case, where the Brussels public transit network is added to the one from Flanders. The results in Table 1 show that in the usual scenario merging two operators is relatively straight-forward as most work has already been done. The worst case scenario shows that it is possible that merging two operators can still require a significant amount of work, although the vast majority has already been done. Our implementation contains some additional experiments and is available on [https://github.com/hdelva/planner.js/tree/footpaths](https://github.com/hdelva/planner.js/tree/footpaths) as a frozen branch of an experimental serverless route planner.
