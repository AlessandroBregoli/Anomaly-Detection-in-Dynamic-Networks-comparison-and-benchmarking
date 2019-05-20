

# Anomaly Detection in Dynamic Networks: comparison and benchmarking
This repo provides a set of pickles used in our comparison. Each pickle represents an experiment performed via Monte Carlo method (see section 3.4 of the paper for more info). 
## Pickle
The pickle module implements binary protocols for serializing and de-serializing a Python object structure. 

#### How to import a Pickle file in Python 3
These two line of codes shows how to import a pickle file in Python3
```python3
pickle_in = open("dict.pickle","rb")
example_dict = pickle.load(pickle_in)
```
## Pickel file's contents
Each file contains:
An array containing ten objects, representing Monte Carlo's iterations, where any object provides a groundtruth (boolean array that shows where the anomalies are injected) and an array containing adjacency matrices. 
Each pickel file represent an experiment using a type of anomaly.

- pickle file
  - 0th Montecarlo iteration
    - groundtruth: <img src="http://latex.codecogs.com/svg.latex?\[0,1, 0, \ldots ,0\]" border="0"/>
    - adj_matrix:
        <img src="http://latex.codecogs.com/svg.latex? \[adj_{0},\ldots ,adj_{n}\]" border="0"/>
      
