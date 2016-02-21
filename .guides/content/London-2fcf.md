Next weekend he tries out his algorithm in LondonHacks - as a computer scientist he decided to record his algorithm in Python! Yaaaay!!
Help him make the Python script for LondonHacks using the window at the side.

To start off with we need to let the computer know that we are working with a graph - the map made of points/nodes, and branches by setting up a basic structure in Python.

We have already written the following script for you:
"
>	from collections import defaultdict, deque

>	class Graph(object):
>	    def __init__(self):
>	        self.nodes = set()
>	        self.edges = defaultdict(list)
>	        self.distances = {}

>	    def add_node(self, value):
>	        self.nodes.add(value)

>	    def add_edge(self, from_node, to_node, distance):
>	        self.edges[from_node].append(to_node)
>	        self.edges[to_node].append(from_node)
>	        self.distances[(from_node, to_node)] = distance

#insert the algorithm here

>	if __name__ == '__main__':
>    graph = Graph()

>    for node in ['A', 'B', 'C', 'D', 'E', 'F', 'G']:
>        graph.add_node(node)

>    graph.add_edge('A', 'B', 15)
>    graph.add_edge('A', 'C', 5)
>    graph.add_edge('C', 'D', 10)
>    graph.add_edge('B', 'E', 5)
>    graph.add_edge('E', 'C', 20)
>    graph.add_edge('D', 'F', 20)
>    graph.add_edge('E', 'F', 5)

"

So firstly we need to define a function the do Dejkstra's algorithm of exploring the map/graph and recording the times, or the weights of the branches as they are more formally known. This function needs to take in the map and the initial setup and needs to ultimately return the places he has visited and the paths, or the times taken, to get to each one. We can do this as follows:

def dijkstra(graph, initial):
    visited = {initial: 0}
    path = {}

    nodes = set(graph.nodes)

#insert steps in here

    return visited, path


Next try writing the code in the middle to visit each node and record the weights for each - don't forget to throw your visited nodes out of your MLH Swag-Bag (aka your unvisited set) and to return to the first point each time to check on your team (really, so that you are always measuring the total time from the first node each time)!

Sorry we didn't have time to do this tutorial properly in Codeo!!! Not enough time!!


The next thing we need to do is in the middle of that is build a python version of Dijkstra's hand - something to write down the shortest total path time. We can define a function that takes in the graph, the start point and the end point that we are measuring the total time between. 

 def shortest_path(graph, origin, destination):
    visited, paths = dijkstra(graph, origin)
    full_path = deque()
    _destination = paths[destination]

    while _destination != origin:
        full_path.appendleft(_destination)
        _destination = paths[_destination]

    full_path.appendleft(origin)
    full_path.append(destination)

    return visited[destination], list(full_path)