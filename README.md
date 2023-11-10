# Network graph for a Bitcoin Lightning Network routing node

To create a network graph based on relative transactional volume and related fees between channels.

Date: 11/02/2023

Fulmine Labs LLC

## Overview

The problem: It can be hard for Lightning Network node operators to determine which of their channels are performing well (and which may not be) from the raw transactional data provided by interfaces such as Ride the Lightning (RTL).

This Python code aggregates transactions and provides an at-a-glance vizualization of where traffic was heavy or light, which channels cluster together and how fees were set relative to other nodes.

The input to this is a transaction history CSV file, exported from the RTL routing interface
A sample file, Forwarding-history-sample.csv is provided. The sample data has been anonymized for privacy, but actual RTL data will display actual node names.

1. Node Creation: Each node represents a channel that has participated in some routing
2. Edge Creation: Each edge between two nodes represents the transactional volume between those two channels, where the thickness or color of the edge represents the normalized transactional volume
3. Node Size: The size of the node indicates the sum of the transactions for that channel
4. Node Color: The node color indicates the average fee for that node:
 *   Red no outbound transactions
 *   Orange lowest fees
 *   Yellow medium fees 
 *   Green highest fees

To achieve this, we used the networkx library, a tool for creating and analyzing networks and the ipycytoscape library to visualize and interact with the networkx graph.
cytoscape allows interactive zoom and the dragging of nodes for improved visualization

## Prerequisites

* A working Bitcoin Lighning Network routing node, with some active channels - see [RaspiBolt](https://raspibolt.org/) for detailed instructions on how to setup a node running on a Raspberry Pi
* The Ride The Lightning interface to your node
* Anaconda
* The Python libraries listed in requirements.txt

## Usage

1) Install Anaconda
2) Clone the LNRoutingVizualization repository to your local machine and navigate to the cloned directory in Anaconda Powershell Prompt: 'cd LNRoutingVizualization'
3) Install the dependencies listed in requirements.txt with 'pip install -r requirements.txt'
4) Open Jupyter Notebook or Jupyter Lab from Anaconda (see note below for large transaction volumes)
5) Open _LN Routing Node Visualization.ipynb_ from the cloned directory inside Jupyter
6) Modify the call to load_data(), as needed
7) In Jupyter 'Run All Cells'

## Screenshots

If successful the output should look something like this:



![alt text](sample_output.png "Title")

## Testing

This code was run in Jupyter Notebook and Jupyter Lab from Anaconda on Windows.
It was tested with over 10,000 transactions. The graph gets a little 'dense' (GPT-4V's description), but is definitely still helpful, particularly by taking advantage of cytoscape's interactive capabilties. 

## Known issues

1) To avoid 'datarate is exceeded' errors in Jupyter, for large numbers of transactions it is recommended to start Jupyter from Anaconda Powershell:
_jupyter notebook --NotebookApp.iopub_data_rate_limit=1.0e10_
or
_jupyter lab --NotebookApp.iopub_data_rate_limit=1.0e10_

2) If the first transaction happens to include a node who's name is a decimal number, node formatting information may be lost

## Acknowledgements

* This code was written collaboratively with GPT-4V. Thank you Assistant!
* A series of [excellent articles on ipycytoscape](https://joseberlines.medium.com/learning-and-visualising-graphs-with-ipycytoscape-1ca150f24933) by Jose Ferro inspired some styling issue workarounds
* [Ride the Lightning](https://github.com/Ride-The-Lightning/RTL)

## License

[MIT open source license](LICENSE.txt)

## Collaboration

We welcome contributions at all levels of experience, whether it's with code, documentation, tests, bug reports, feature requests, or other forms of feedback. If you're interested in helping improve this tool, here are some ways you can contribute:

- **Ideas for Improvements**: Have an idea that could make the LN Routing Vizualization tool better? Open an issue with the tag `enhancement` to start a discussion about your idea.
- **Bug Reports**: Notice something amiss? Submit a bug report under issues, and be sure to include as much detail as possible to help us understand the problem.
- **Feature Requests**: If you have a suggestion for a new feature, describe it in an issue with the tag `feature request`.
- **Documentation**: Good documentation is just as important as good code. Although this is currently a very simple tool, if you'd like to contribute documentation, we'd greatly appreciate it.
- **Code**: If you're looking to update or write new code, check out the open issues and look for ones tagged with `good first issue` or `help wanted`.

## Contact

Duncan Henderson, Fulmine Labs LLC
henderson.duncanj@gmail.com
