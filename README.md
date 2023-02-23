This repo contains the data and code peform a social network analysis on the French novel - Les Miserables (Victor Hugo)

A summary of the novel can be found at https://www.sparknotes.com/lit/lesmis/summary/

The weighted network of this novel is avaiable in the form of lesmis.gml. It contains the weighted network of coappearances of characters from the novel where each node in this network is labeled by one character. 

We define coapperance as being seen in the same chapter of the novel. An edge between two nodes represents that those two characters will appear in the same chapter. The value of the eges represents the number of such coapperances.

The data is sourced from D.E. Knuth, The Stanford GraphBase (https://www-cs-faculty.stanford.edu/~knuth/sgb.html)

Code is in the form of a Jupyter Notebook under /notebooks/Social Network Analysis - Les Miserables

Below is the results from the analysis:

# Final Analysis

### Graph Overview:
The graph has 77 nodes indicating 77 characters in the novel.
There are 254 edges indicting that there are 254 relationships between people.

Even though the graph has smaller clusters, on a whole it is a single component. So, every character in the novel is somehow connected to the other. The relationship might be weak or strong depending on the weights of the edges and the distance between two nodes.

![image](https://user-images.githubusercontent.com/100599523/220806856-1737bcdb-f1f2-4897-baa0-f8ffc05d79b4.png)

### Centrality Analysis:

<img width="826" alt="Screen Shot 2023-02-22 at 6 14 42 PM" src="https://user-images.githubusercontent.com/100599523/220807044-01af31a8-a78e-4e14-97b4-0e7db7e66cd1.png">

The top 5 degrees of centrality are as follows:

    eigen vector centrality:
                ('Gavroche', 0.31783893977497674)
                ('Valjean', 0.2676181759885393)
                ('Enjolras', 0.26717863282356663)
                ('Marius', 0.25911114534178753)
                ('Bossuet', 0.24213078637474134)

    degree centrality:
                ('Valjean', 0.47368421052631576)
                ('Gavroche', 0.2894736842105263)
                ('Marius', 0.25)
                ('Javert', 0.22368421052631576)
                ('Thenardier', 0.21052631578947367)

    closeness centrality:
                ('Valjean', 0.6440677966101694)
                ('Marius', 0.5314685314685315)
                ('Thenardier', 0.5170068027210885)
                ('Javert', 0.5170068027210885)
                ('Gavroche', 0.5135135135135135)

    betweenness centrality:
                ('Valjean', 0.5699890527836184)
                ('Myriel', 0.17684210526315788)
                ('Gavroche', 0.16511250242584766)
                ('Marius', 0.132032488621946)
                ('Fantine', 0.12964454098819422)


By looking at the centrality values, we can easily say that 'Valjean' is the protagonist of the novel without even seeing the cover face of the book.
Valjean is related to 47% of the characters (about 36 out of 77) directly. The next best being 28% (about 21 out of 77). This clearly imdicates that he is the most popular character of the novel.

The most popular person may not be the most important person. This is the difference between degree centrality and betweenness centrality.

We consider the node with highest betweenness centrality to be the most important node of a social network graph because it is like a bridge which connects two entirely different components of the graph. That one character can change a lot in the plot. So, in this novel, the highest degree centrality is for 'Valjean' only. So we can conclude that he is the most important of all.

One more interesting point that we can take a look at is that, Myriel has the second highest betweennes centrality but his degree centrality is very high. So we can say that he is an introvert wo doesn't have many relationships but he is very important for the plot of the novel. So he has acted as a bridge between many characters and has been helpful to his acquaintances. 

There is one measure in this graph where we see a differnt result. 'Jean Valjean' is not the one whi has the higest measure in this. For eigen vector centrality, the highest value is attained by 'Gavroche'. So, we can say that he is the most influential person in the plot of the novel.

Coming to the correlation plot,
    i) We can see that most of the values of betweenness centrality are near to 0. So it is very less. This shows that there are        very few important people and can also mean that the no. of unconnected components is very less because the edges that          work as bridges are less in this case.
    ii) We can see that closeness centrality is spread out like a normal distribution. This says that the central nodes are of 
        average number.
    iii) We can see that both degree cetrality and eigen-vector centrality have more values near 0 and decrease further. So we can say that there are not so many characters which are popular.
    iv) Betweenness centrality is positively correlated to all other centralities but the correlation is very low. So it means that important charcaters may not be popular or central or inluential. 
    v) All other centralities are positively correlated to all other centralities because usually popular,influential and central go hand in had with each other. centralities. A central node can be popular, central and influential.

### Community Detection using Louvain Method:

<img width="446" alt="Screen Shot 2023-02-22 at 6 10 41 PM" src="https://user-images.githubusercontent.com/100599523/220806579-207053dd-d1f8-4ecb-b4bd-4adfea196d56.png">

Some of the communities detected here are:
  Community  1 :  ['Jondrette', 'MmeBurgon']
  Community  2 :  ['Myriel', 'Napoleon', 'MlleBaptistine', 'MmeMagloire', 'CountessDeLo', 'Geborand', 'Champtercier', 'Cravatte', 'Count', 'OldMan']
  Community  3 :  ['Labarre', 'Valjean', 'MmeDeR', 'Isabeau', 'Gervais', 'Fauchelevent', 'Bamatabois', 'Scaufflaire', 'Woman1', 'Judge', 'Champmathieu', 'Brevet', 'Chenildieu', 'Cochepaille', 'MotherInnocent', 'Gribier']
  Community  4 :  ['Marguerite', 'Tholomyes', 'Listolier', 'Fameuil', 'Blacheville', 'Favourite', 'Dahlia', 'Zephine', 'Fantine', 'Perpetue', 'Simplice']
  Community  5 :  ['MmeThenardier', 'Thenardier', 'Javert', 'Boulatruelle', 'Eponine', 'Anzelma', 'Gueulemer', 'Babet', 'Claquesous', 'Montparnasse', 'Brujon']
  Community  6 :  ['Gavroche', 'Marius', 'Mabeuf', 'Enjolras', 'Combeferre', 'Prouvaire', 'Feuilly', 'Courfeyrac', 'Bahorel', 'Bossuet', 'Joly', 'Grantaire', 'MotherPlutarch', 'Child1', 'Child2', 'MmeHucheloup']
  Community  7 :  ['Cosette', 'Pontmercy', 'Woman2', 'Gillenormand', 'Magnon', 'MlleGillenormand', 'MmePontmercy', 'MlleVaubois', 'LtGillenormand', 'BaronessT', 'Toussaint']

### Community Detection using Clique Percolation Method:

Some of the communities detected here are:
            
            community with K=3:  ['Tholomyes', 'Zephine', 'Listolier', 'Favourite', 'Blacheville', 'Fantine', 'Fameuil', 'Dahlia']

            community with K=3:  ['MotherInnocent', 'MmeThenardier', 'Cochepaille', 'Fantine', 'MlleGillenormand', 'Joly', 'Gueulemer', 'Marius', 'BaronessT', 'Bossuet', 'Javert', 'Brujon', 'MmeHucheloup', 'Enjolras', 'Bamatabois', 'Brevet', 'Toussaint', 'LtGillenormand', 'Grantaire', 'Simplice', 'Gavroche', 'Courfeyrac', 'Montparnasse', 'Pontmercy', 'Mabeuf', 'Claquesous', 'Tholomyes', 'Champmathieu', 'Woman2', 'Bahorel', 'Fauchelevent', 'Perpetue', 'Thenardier', 'Valjean', 'Babet', 'Anzelma', 'Chenildieu', 'Gillenormand', 'Eponine', 'Judge', 'Prouvaire', 'Feuilly', 'Combeferre', 'Cosette', 'Woman1', 'Marguerite']

            community with K=3:  ['MlleBaptistine', 'Myriel', 'MmeMagloire', 'Valjean']

            community with K=3:  ['Child1', 'Child2', 'Gavroche']

            community with K=4:  ['Tholomyes', 'Zephine', 'Listolier', 'Favourite', 'Blacheville', 'Fantine', 'Fameuil', 'Dahlia']

            community with K=4:  ['Gavroche', 'MmeThenardier', 'Courfeyrac', 'Montparnasse', 'Mabeuf', 'Claquesous', 'Woman2', 'Bahorel', 'Thenardier', 'Valjean', 'Babet', 'Fantine', 'MlleGillenormand', 'Anzelma', 'Joly', 'Gueulemer', 'Marius', 'Javert', 'Brujon', 'MmeHucheloup', 'Eponine', 'Gillenormand', 'Prouvaire', 'Enjolras', 'Bamatabois', 'Feuilly', 'Combeferre', 'Toussaint', 'LtGillenormand', 'Cosette', 'Grantaire', 'Simplice', 'Bossuet']

            community with K=4:  ['MlleBaptistine', 'Myriel', 'MmeMagloire', 'Valjean']

            community with K=4:  ['Judge', 'Bamatabois', 'Valjean', 'Brevet', 'Cochepaille', 'Champmathieu', 'Chenildieu']

We can see that the characters that occur in the same frame, or closeby in the novel are grouped into the same communities. For example, Jean Valjean was seen with Myriel most of the time. So, irrespective of K value, always these both are in the same component. 

### Analysis on the structural similarity:

The structural similarity is 1 for a lot of nodes whose degree is also 1. This is not a very good measure atleast when the degree is low because everyone who is connected to valjean alone will have the same structural similarity.
And with Jaccard similarity, as it is the length(intersection) by length(union). So if the similarity is 1, then it means that the intersection and union are of the same length. So it basically leads to both the nodes having almost the same degree centrality if the Jaccard coefficient is 1.


### Analysing the clusters, density and diameter:

The global clustering coefficient is based on the number of connected triplets. It gives an indication of the clustering in the whole network on a whole. The value we have got is 0.5731367499320134. This means that around 57% of the total number of triplets are closed triplets.

The diameter (longest path between any two characters) is 5. 
This means that from any one character the maximum that any other character would be away from that character would be through 5 other characters. The average distance between any two characters is 2.6. This shows that each distinct character is generally 2 to 3 characters away from any other character.

The network density of the graph is around 8.6% only. This shows that the graph is actually very sparse. 8% of 77-C-2 is around 77 out of the 2926 distinct edges possible. 


### Other interesting observations:

The novel is a single component. This means everyone in the novel knows everyone else atleast indirectly. One of the most interesting observation is Gavroche's eigen-vector centrality. This character is the most influential character because it has the most influencing connections in the novel. But his degree centrality is still low, that is he does not have the most connections. Jean
Valjean's clustering coefficient is comparatively, and it means that many of his acquaintances don’t know one another. And several other characters also have very high clustering coefficients, so their networks are comparatively smaller and denser than Valjean’s. Valjean beats everyone by a very high margin in betweenness centrality and the degree centrality. This is where he scores more than the rest and is concluded as the protagonist. 
