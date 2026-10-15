# Graph Algorithms for a Simplified Glycolysis Network

**UC Berkeley CHEM 274B | Algorithms & Data Structures in Scientific Computing**

**Team:** David Houshangi, Kirk Ehmsen, Christian Fernandez, and Yash Maheshwaran ([original repository](https://github.com/ktehmsen-berkeley/Graph_Algorithms_in_Biological_Pathway_Analysis) · [contributions](team_contributions.md)).

A collaborative course project applying network-flow concepts to a **simplified, capacity-weighted graph of glycolysis**. The example is intended to illustrate how directed graphs, augmenting paths, and cut sets can be used to reason about network bottlenecks. **It is not a validated biochemical flux model or a substitute for flux balance analysis.**

## What the project implements

- Represent a simplified glycolysis pathway as a directed graph with reaction capacities stored in a CSV.
- Find augmenting paths using **breadth-first search (BFS)**.
- Increase flow along available **forward edges** and calculate an illustrative source-to-sink flow.
- Identify a corresponding cut from the remaining reachable nodes.
- Visualize the network, edge capacities, and computed flows.

**Algorithmic limitation:** The current educational implementation checks forward residual capacities but does **not** add or traverse reverse residual edges. Therefore, it does **not** implement the fully general residual-graph version of Ford–Fulkerson/Edmonds–Karp; on some graphs it can miss opportunities to reroute flow and yield a suboptimal result. Reported bottlenecks should be interpreted within the simplified example, not as experimentally demonstrated rate-limiting reactions in living cells.

## Run the example

Requires Python 3 and the packages listed in [requirements.txt](requirements.txt).

```bash
git clone https://github.com/yashm4-4/graph-algorithms-metabolic-networks.git
cd graph-algorithms-metabolic-networks
python -m pip install -r requirements.txt
make run
```

Alternatively:

```bash
cd PythonCode
python glycolysis_graph_analysis.py
```

The script reads `PythonCode/glycolysis_network.csv`, prints flow and cut information, and writes PNG plots **to its working directory** (normally `PythonCode/` when launched using `make run`).

## Files

| Path | Contents |
| --- | --- |
| [PythonCode/glycolysis_graph_analysis.py](PythonCode/glycolysis_graph_analysis.py) | Graph construction, augmenting-path search, flow/cut routines, plotting |
| [PythonCode/glycolysis_network.csv](PythonCode/glycolysis_network.csv) | Toy biochemical network and assigned capacities |
| [Results/](Results/) | Illustrative project output figures |
| [presentation/](presentation/) | Collaborative course presentation and recording |
| [team_contributions.md](team_contributions.md) | Original statement of equal team contributions |
| [Makefile](Makefile) | Convenience target for running the analysis |

## Example output

The figures below were produced for the original course project. They illustrate the simplified graph and its computed flow rather than validated biochemical fluxes.

![Simplified glycolysis network](Results/glycolysis.png)

![Illustrative computed flow](Results/glycolysis_maxflow.png)

## Scientific scope

In real metabolic systems, fluxes reflect stoichiometric constraints, reaction reversibility, compartmentation, regulatory effects, and measured or inferred conditions. A generic graph's maximum flow does not by itself establish biological pathway flux or enzymatic rate limitation. This project is primarily an illustration of **graph algorithm concepts in a biological setting**.
