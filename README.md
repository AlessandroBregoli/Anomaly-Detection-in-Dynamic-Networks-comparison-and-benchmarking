

# Anomaly Detection in Dynamic Networks: comparison and benchmarking
## Introduction
This repo provides a set of pickles used in our comparison. Each pickle represents an experiment performed via Monte Carlo method (see section 3.4 of the paper for more info). 
## Dataset 
- [Enron](http://www.ahschulz.de/enron-email-data/): concerns email messages, and consists of about 90K nodes, more
  than a million directed arcs. The daily structure of the graph is made avail-
  able for more than 5 years.
- [Email-Eu-core](https://snap.stanford.edu/data/email-Eu-core.html): a graph of email messages between members of a European                 
  research center. About 1K nodes, and more than 300K directed arcs are used to describe the day-by-day evolution of the graph
  structure for more than 800 days.
- [Nodobo](http://nodobo.com/release.html): it concerns the cellular phone call behaviour of 27 students, and
  consists of more than 700 nodes, more than 13K directed and weighted arcs.
  The day-by-day phone calls graph is made available for about 200 days

## Exploration Analysis
Qui inserite l'analisi esplorativa

## Experimental settings
we have chosen 10 iterations for any experiments performed by using Monte Carlo method. The table here below shows more details on algorithms' parameters. On any iteration of Monte Carlo method the grid search uses all parameters' combination for any algorithm (as shown in paper's Section 3.4). For what concerns the parameter _p_ in monte carlo method we used the value 0.8 in order to create the set of anomalous snapshots __A__.  


|       Algorithm         |              Parameters          | 
|-----------------------: | :--------------------------------: | 
| Scan-Statistics         | __k__:{0,1,2} __tau__:{3,4,5,6} __tau__ = __l__ |
| Deltacon                |               __--__             |
| Edmcg                   | __W__:{3,5,7} __W1__:{3, 5,7}    |
| Icleod                  |     __k__:{1,2,3,7,10,15,20}     |



## Pickle
The pickle module implements binary protocols for serializing and de-serializing a Python object structure. 

#### How to import a Pickle file in Python 3
These two line of codes shows how to import a pickle file in Python3
```python3
pickle_in = open("dict.pickle","rb")
example_dict = pickle.load(pickle_in)
```
## Pickle file's contents
Each file contains:
An array containing ten objects, representing Monte Carlo's iterations, where any object provides a groundtruth (boolean array that shows where the anomalies are injected) and an array containing adjacency matrices already injected. 
Each pickel file represent an experiment using a type of anomaly.

File's structure:
  - pickle file
    - 0th Montecarlo iteration
      - groundtruth: <img src="http://latex.codecogs.com/svg.latex?\[0,1, 0, \ldots ,0\]" border="0"/>
      - adj_matrix:
          <img src="http://latex.codecogs.com/svg.latex? \[adj_{0},\ldots ,adj_{n}\]" border="0"/>

