/*
    This program will receive an input file in the following format:
    1) The first line of input contains the number of vertices V and number of edges E in the graph.
    2) The next E lines list out the connections between vertices in the graph in the format of "u v",
    which indicates the existence of an edge between u and v.
    
    Calculates and prints out the number of connected components in the graph
*/


#include <stdio.h>
#include <vector>
#include <iostream>
#include <numeric>
using std::vector;
using std::cin;
using std::cout;
using std::endl;

class Graph {
    int V;
    int E;
	vector<int> reps;

public:
    // Graph constructor that initializes the graph and its member variables
    Graph(int V, int E) {
        this->V = V;
        this->E = E;
		reps.resize(V);
		std::iota(reps.begin(), reps.end(), 0);
    } // Graph()

    int find(int v) {
		if (reps[v] == v) {
			return v;
		}
		reps[v] = find(reps[v]);
		return reps[v];
    } // find()

    void set_union(int a, int b) {
		int a_rep = find(a);
		int b_rep = find(b);
		if (a_rep != b_rep) {
			reps[b_rep] = a_rep;
		}
    } // set_union()

    int count_components() {
		for (int i = 0; i < E; i++) {
			int x, y;
			cin >> x >> y;
			set_union(x, y);
		}

		int counter = 0;
		
		for (int i = 0; i < V; i++) {
			if (reps[i] == i) {
				++counter;
			}
		}

		return counter;
    } // count_components()

};

int main() {
    std::ios_base::sync_with_stdio(false);
    int vertex_count, edge_count = 0;
    cin >> vertex_count;
    cin >> edge_count;
    Graph g(vertex_count, edge_count);
    cout << g.count_components() << endl;
    return 0;
}
