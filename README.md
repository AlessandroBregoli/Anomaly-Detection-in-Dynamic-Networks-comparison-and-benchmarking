

# Anomaly Detection in Dynamic Networks: comparison and benchmarking
_The 16th International Conference on Modeling Decisions for Artificial Intelligence_

Milan, Italy September 4 - 6, 2019 http://www.mdai.cat/mdai2019

## Introduction
This repo contains pickle files used to compare performance of different anomaly detection algorithms, each one represents an experiment performed via Monte Carlo method (see section 3.4 of the paper for more info). The Section __Datasets__ provides links to download datasets and gives information about their content. The section __Exploratory Analysis__ provides a brief explaination on how the exploratory analysis, cited in Section 3.4 of the paper, was performed. The section __Experimental settings__ gives more details about algorithms' parameters values used by grid search method and describes the timelaps chosen in order to split the datasets into snapshots. The last section describes the structure of the pickle files and how to import them into the Python3 environment.   
## Datasets 
- [Enron](http://www.ahschulz.de/enron-email-data/): concerns email messages, and consists of about 90K nodes, more
  than a million directed arcs. The dataset made available in this repository is a subset containing only the email which have enron dependants as both sender and reciver.  The day-by-day structure of the graph is made available for more than 3 years.
- [Email-Eu-core](https://snap.stanford.edu/data/email-Eu-core.html): a graph of email messages between members of a European                 
  research center. About 1K nodes, and more than 300K directed arcs are used to describe the daily evolution of the graph
  structure for more than 800 days.
- [Nodobo](http://nodobo.com/release.html): it concerns the cellular phone call behaviour of 27 students, and
  consists of more than 700 nodes, more than 13K directed and weighted arcs.
  The day-by-day phone calls graph is made available for about 200 days.

## Exploratory Analysis
For each dataset we carefully selected the candidate snapshots _C_ for anomaly injection by performing an exploratory analysis characterized by two main steps. The first step concerns splitting the datasets into snapshots using a timelaps (i.e. week, day, month). The other step concerns actual exploratory analysis performed by using two empirical method:
- __statistical analysis__ : related to analyzing each snapshots by using max degree and number of edges.
- __algorithms execution__ : related to exploiting the output of each algorithm run on the datasets in order to select the set of snapshots possibly containing no anomalies. 

## Experimental settings
Table 1 shows timelaps chosen to splitting each dataset.

|       Dataset      | Splitted by  |
|-------------------:| :-----: | 
| Nodobo             | Day |
| Email-Eu-core      | Week |
| Enron              | Week |

__Table 1__ : Datasets and their associated splitting parameters.

We set the number of iterations to 10 for each experiment performed using Monte Carlo method. __Table 1__ shows more details on algorithms parameters. It is worthwhile to mention that at each Monte Carlo iteration the grid search uses all parameters combination for each algorithm (as shown in paper's Section 3.4). For what concerns the parameter _p_ in Monte Carlo method we used the value 0.8 in order to create the set of anomalous snapshots __A__.  


|       Algorithm         |              Parameters          | 
|-----------------------: | :--------------------------------: | 
| Scan-Statistics         | __k__:{0,1,2} __tau__:{3,4,5,6}  |
| Deltacon                |               __--__             |
| Edmcg                   | __W__:{3,5,7} __W1__:{3, 5,7}    |
| Icleod                  |     __k__:{1,2,3,7,10,15,20}     |

__Table 1.1__ : Algorithms and their associated parameters as used by the grid search method.

## Pickle file structure and content

Each file contains:

An array composed by ten objects, representing Monte Carlo iterations, where each object provides a groundtruth (boolean array that shows where the anomalies are injected) and an array containing already injected adjacency matrices. 
Each pickle file is associated with an experiment when using a given type of anomaly.

File structure:
  
  - pickle file
    - 0th Montecarlo iteration
      - groundtruth: <img src="http://latex.codecogs.com/svg.latex?\[0,1, 0, \ldots ,0\]" border="0"/>
      - adj_matrix:
          <img src="http://latex.codecogs.com/svg.latex? \[adj_{0},\ldots ,adj_{n}\]" border="0"/>

