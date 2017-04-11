## Intro to Graphs

### Objectives

* Learn what characterizes a graph
* Learn about how graphs exist in the real world
* Learn about how to represent graphs in code

### Introduction to Graphs

Here's a definition of graphs: 

* Pairwise connections between items

By that we mean that a graph is where one item is connected to another item.  From here, you may think this is vague.  You are right.  You may also think that we have already seen graphs.  You are again right.  After all, a linked list connects one item to another.  As does a tree.  

Here are some other graphs: 

| Application   | Connection    | Item  |
| ------------- |:-------------:| -----:|
| linked list   | pointer 		  | node |
| tree   		   | pointer       | node |
| subway map    | subway line   | subway stop |
| college graduation requirements    | pre-requisite to course    | course |
| social network    | friendship    | person |

We can see graphs everywhere that we see a connection.  And connections are everywhere.  This makes graphs a very powerful concept in computer science.  This is because if we develop a common language for talking about graphs, we can then solve common problems seen throughout different types of graphs.  

### Graph Nomenclature: Points and Lines

This is a map of a portion of the New York City subway.  

![](https://s3-us-west-2.amazonaws.com/curriculum-content/algorithms/nyc-subway.png) 

It is also a representation of a graph.  Graphs are a collection of points, as well as the lines connecting the points.  But computer scientists like to call the points **vertices** and the lines **edges** so instead we say: 

* A graph G is a set V of vertices and a set E of edges.

Let's turn this map into a graph by representing just the vertices and the edges.  Vertices directly connected by an edge are described as **adjacent** to one another, or as **adjacent neighbors**.

![](	https://s3-us-west-2.amazonaws.com/curriculum-content/algorithms/nyc-subway.png) 

The graph above has nine vertices and has nine edges.  To identify each vertex, we have labeled it with its cross street, or the name of the vertex.  Below is the set of vertices in the graph: 

```javascript
let vertices = ['34th&6th', '23rd&6th', 
'14th&6th', '28th&Bwy', '23rd&Bwy',
 '33rd&Lex', '28th&Lex', '23rd&Lex', '14th&Lex']
```

Now how do you think we represent each edge?  For example, how would we represent the edge between 14th&6th and 14th&Lex.  Well, we could just describe it as it's pair of vertices that are the edge's endpoints, `['14th&Lex', '14th&6th']`.  

And how would we represent the set of edges?  Well probably just as an array of arrays, where each inner array represents an edge.  Let's represent the edges of the graph along the left side (6th Avenue).  

```javascript
let edges = [
	['14th&6th', '23rd&6th'],
	['23rd&6th', '34th&6th']
]
```


The edges of the graph above would look like the following: 

```javascript
let edges = [
	['14th&6th', '23rd&6th'],
	['23rd&6th', '34th&6th'],
	['34th&6th', '28th&Bwy'],
	['28th&Bwy', '23rd&Bwy'],
	['23rd&Bwy', '14th&Lex'],
	['14th&Lex', '23rd&Lex'],
	['23rd&Lex', '28th&Lex'],
	['28th&Lex', '33rd&Lex']
]

let vertices = ['34th&6th', '23rd&6th', '14th&6th', 
'28th&Bwy', '23rd&Bwy',
 '33rd&Lex', '28th&Lex', '23rd&Lex', '14th&Lex']
```

That is a complete representation of the graph above: all of the edges and all of the vertices.  

### Types of Graphs 

So far we have characteristics common to all graphs, edges and vertices.  Now, it's time to discuss a couple of ways to distinguish graphs.  Let's compare our graph of the subway system below, to a different graph which shows the courses available to a computer science major at a college.

Here is a graph of our subway:

![](https://s3-us-west-2.amazonaws.com/curriculum-content/algorithms/subway-map-33rd.png) 



And here is a graph of our computer science courses:

![](	https://s3-us-west-2.amazonaws.com/curriculum-content/algorithms/directed-comp-sci.png) 

The graph of our subway is described as **undirected** as the relationship between a pair of nodes point in two directions: one can travel from 34th & 6th down to 23rd and 6th and then back to 34th and 6th.  

The graph of the computer science courses by contrast is **directed**, as the relationship has a direction.  Intro to Algorithms points to Algorithms II.  This is because one must take the intro course before Algorithms II.  Algorithms II does not point to Intro to Algorithms.  There is no way to go from Algorithms II back to Intro to Algorithms.  Just as one cannot go from Design Patterns to Object Orientation.

Let's look at one more type of graph.  This time, it is a graph of roads making up a New York City block.  Like our graph of computer science curriculum, the connections between the streets have a direction, used to represent the flow of traffic.  So the graph is directed.  However, this graph has **cycles**.  A cycle is when a path goes from a particular vertex back to itself. 

![](	https://s3-us-west-2.amazonaws.com/curriculum-content/algorithms/nyc-streets.png)

Now compare this with our graph of computer science courses.  This graph has no cycles. 
 
![](https://s3-us-west-2.amazonaws.com/curriculum-content/algorithms/directed-comp-sci.png) 

Upon visiting a node like Algorithms II, there is no path back to Algorithms II.  Such a graph is called **directed acyclic graph**, because the graph has a direction but does not have any cycles.  

### Summary

In the section above we learned that a graph is a collection of edges and vertices.  Vertices are the points of the graph, that we name so that we can identify each point.  We can represent the collection of vertices as an array of vertices.  The edges are the connections between each point in a graph.  We can represent an edge as an array where each element is a vertix that is an endpoint of the edge.  We can represent the collection of edges an array of arrays.  The array of vertices and array of edges is an accurate representation of our graph.   