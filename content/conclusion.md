## Conclusion and future work
{:#conclusion}

This paper introduced a decentralized publishing method for transit footpaths based on Delaunay triangulations. We have shown that different actors can add information to the footpath graph, splitting the work between them. The amount of paths scales linearly with the amount of public transit stops, and every stop is reachable from every other. This last property could prove useful in its own right, as it allows for unrestricted walking unlike conventional methods. However, this comes at the cost of precision; the walking distance between any pair of stops is overestimated by 20% on average. 
<span class="comment" data-author="RV">That's a summary; quite unneeded in such a short article, and I just read the 20% in the previous section. I suggest to remove.</span>
<span class="comment" data-author="RV">Can you add actual conclusions? What can the readers do based on this information? It is a viable direction or not? What is the external validity? What are the limitations of your approach?</span>

It still remains to be seen whether or not overestimation poses a problem in practice.
<span class="comment" data-author="RV">Suggestion on what to try next, how can we find out?</span>
Different kinds of point set triangulations may be tried instead of the Delaunay triangulation to improve the approximation, or several triangulations may even be combined to create a more complete graph. Alternatively, combining the haversine distance and the currently approximated distance seems promising as well – although this could lead to underestimations. Another question is how scalable this approach is when more modes of transportation are required; is it desirable to create separate graphs for bicycles, electric bikes, wheel chairs, etc. or can they share information?
<span class="comment" data-author="RV">Would not end on a (non-rhetorical) question; phrase as a statement.</span>
