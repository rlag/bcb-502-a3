The dataset you use. It should be related to biology and included with the source code, or at least a portion of it so I can run the program. (Note: if you went the database route you will need to demo your project to me, but still submit the code.)  
For this project, I was inspired by the well-known, static, C. elegans connectivity map. I felt it could use a face-lift: user interactivity, filtering, and a quantitative comparison of neurons. I feel like I’ve successfully accomplished this with my node-link force directed diagram, adjacency matrix, and arc diagram.
 
I chose to use the NeuronConnect dataset from the Worm Atlas website, 2.1 Connectivity Data (excel file). This file contains the total number of neurons in the nematode C. elegans connectome, with over 6400 synaptic connections between each neuron. It is a large >6400 row and 4 column data matrix. Each row gives information between the interaction of two neurons, the type of neuron it is, and how many connections this pair has. 

Like C. elegans, humans also have neurons, except there are billions, and if not trillions of connections between each other. Exact numbers aren’t known, because the complete connectome of the human species is not complete. This is a major research area and could benefit greatly from elegant visualization techniques. In the meantime, we can practice with C. elegans as a simple model system in neuroscience. Understanding the connectome is one step in making sense of neurons, behavior, and disease.

http://wormatlas.org/neuronalwiring.html#NeuronalconnectivityII

The major transformations you make to the data before visualizing it.

I needed to transform the NeuronConnect.xls (.tsv) file into a node-link .json file. This allowed me to make a node-link force directed graph, an adjacency matrix, and an arc diagram in d3.

Whether your visualization can work with more than one dataset of the  same type (e.g. more rows, but same dimensions).

My visualizations could certainly work with more than one dataset of the same type; however, the animations and computations become slower as the file size increases. I unable to show the complete dataset for both the arc diagram and adjacency matrix, getting the following error on the localhost and when live on the web:

“Uncaught TypeError: Cannot read property 'z' of undefined”

I’m wondering if this is due to the large data size limit, or if the z range can be modified in a way that allows this range to be computed…

If you are using outside code for the core of your project: 
• Identify the source(s) of the code.
• Tell me how you modified it to make it your own work.
I referenced three sources of code to assist me with using d3 to display this large dataset:
http://bl.ocks.org/mbostock/4062045
http://bost.ocks.org/mike/miserables/
http://bl.ocks.org/sjengle/5431779

To make this code my own, I added features to the node-link force directed layout: (1) filter search, and (2) an interactive frequency bar plot. The search box allows you to find a neuron of interest within the ‘hairball’ of connections by dimming out other interactions for a period of time. The bar plot shows a sorted frequency plot of the number of connections between neurons. You can highlight over a bar and it will return the neuron name and the number of connections it has. This is one way for the user to filter search the network, as well as hovering over any node and it will give the neuron name.

I also added two other ways to visualize this data set using an adjacency matrix and arc diagram. The adjacency matrix shows a paired neuron comparison, resulting in a symmetric display of interactions. Boxes are filled with a shade of black depending on the number of connections between that pair of neurons (black being the most connections, white being none). This matrix can be sorted by name, cluster, and frequency. The frequency sort complements the results presented on the node-link diagram well, i.e. AVAL and AVAR seem to be the most connected pair of neurons. This is also complementary to the static C. elegans connectome image, which was exciting to discover! Hovering over each square will make the selected neuron pair text larger. The user can also zoom in and out of the screen for selected observation on each visualization, without effecting the page layout. The arc diagram is a display like the node-link diagram, except it is static and the nodes (neurons) are aligned horizontally. Hovering over each node will pop-up a text label of which neuron it is, but the computation speed is slow due to the large number of connections.

For the free-form (beyond the requirements) component: 
• Describe the biological significance of the additions you make. 

I used a unique dataset that I was unaware of— I only knew the connectome ‘image’ existed. I found and learned this dataset, then made useful graphic(s) for myself, and researchers within my field. I showed this to my colleagues and they love it and want to use it in their presentations. This idea could be expanded to the human connectome, of course with more filtering.

• Describe the technical significance of the additions you make.

I was able to make this connectome image interactive. The user can filter, search, and learn (quantified frequencies) about the connectome much more than just a static, overlaid, and confusing image. I’m proud of this accomplishment after this being only my first time using d3js. I also showed multiple views of the same dataset, allowing for novel discovery of neuron interactions and extrapolating new clustered patterns.

There are much more detailed searches and descriptions for the C. elegans connectome; however, my approach was to keep the interaction simple while providing an appealing visual display of these neuron connections. This visualization could be built upon to search for neuron types, integrate the bar plot with the connectivity map upon searching, etc.

Provide explicit instructions on running your program.

All instructions on running my program are printed on the website screen. 

After searching:

http://users.wpi.edu/~rosslagoy/connectome.html

The user should be able to see and use this visualization in any modern browser, linking to all of my visualizations.

Explicit instructions/features:

Connectome: Hover over a node once it stops moving to display that neuron name; hover over any bar to display that neuron name and frequency value (number of connections); search the neuron name to filter the view.

Adjacency matrix: Hover over a square to display that neuron pair interaction; sort the matrix with the dropdown menu.

Arc diagram: Hover over any node to display that neuron name.
