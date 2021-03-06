# Modularity
### Updated March 19, 2017

modularity.cpp can be used to find the Newman Modularity of a partition of a network.

Modularity can be defined in a variety of ways, here I have used the 'community
based' definition found at 'The performance of modularity maximization in
practical contexts' at https://arxiv.org/pdf/0910.0165.pdf.

The program is resilient enough to handle graphs with arbitrarily numbered nodes,
making renumbering the edge list unnecessary. The user needs to ensure the validity
of the cover supplied, meaning that it should cover all the nodes of the graph.

Sample usage:
```
g++ modularity.cpp -o mod -std=c++11 -O5 -Wall
./mod <edgelist> <cover>
```

Flags:
1. Use ```-v``` to turn on verbose mode to see the time taken by the different phases
of the program.
Sample:
```
./mod <edgelist> <cover> -v
```

2. Use ```-a``` to feed in the cover in the alternate form which is described below.
Sample:
```
./mod <edgelist> <alt_cover> -a
```
**WARNING**: Using ```-a``` flag with normal covers will lead to wrong results.

Specifications:
1. **Edge list**:
Each line should have two numbers, ```u``` and ```v```, signifying an undirected
edge between ```u``` and ```v```. The edges must NOT appear twice, that is, there
must be ```|E|``` many lines in the edge list.

2. **Cover**:
- *Conventional form*: There should be exactly ```|V|``` lines, and each node
should appear exactly once. Each line should have two numbers, ```u``` and ```comm_u```
signifying the node label ```u``` and ```comm_u``` the corresponding community
label of ```u```. Community labels are also not required to be in order.
An example of this type of cover is at ```test_cover2``` for the network ```test_graph2```.

- *Alternate form*: For a cover with ```k``` communities, there must be exactly ```k```
lines, where each line represents a cluster, and has the labels of the members
of the cluster. The line MUST end with ```-1```.
An example of this type of cover is at ```test_cover2_a``` for the network ```test_graph2```.


Please contact ssikdar@nd.edu for any bug reports or suggestions.
