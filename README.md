# Retrospective Self-Training
This repository contains supplementary information and data to the article Viktor Losing, Martina Hasenjäger "Leveraging Retrospective Self-Training for Online Time-Series Classification".

## Data sets


### Activity ([Access](https://www.utwente.nl/en/eemcs/ps/dataset-folder/sensors-activity-recognition-dataset-shoaib.rar))([Paper](https://pubmed.ncbi.nlm.nih.gov/24919015/))
This publicly available data set contains body motions of ten different subjects and the task is to categorize them into daily activities such as walking, cycling, running etc. 
The recordings are based on five Inertial Measurement Units (IMUs) that are mainly covering the upper body.
### Factory (Proprietary)([Paper](https://ieeexplore.ieee.org/abstract/document/8794251))
Different body motions that are inspired by common tasks factory-worker tasks are performed by four subjects. There are twenty different motion classes encoded such as stand, crouch down, pick-up a box asf. We recorded the data using the XSens body suit that incorporates seventeen IMUs spread over the whole body. 
### Industry ([Access](https://zenodo.org/record/3254403#.YUyEtXuxWuc))([Paper](https://journals.sagepub.com/doi/abs/10.1177/0278364919882089))
Similar to the \emph{\factorymotion{}} data set, the goal is to assess the motions of humans performing manual labour that can typically be found in assembly lines. The main focus here though is to estimate the posture for an ergonomic analysis. The data is also based on the XSens body suit and includes recordings of thirteen subjects. Three different label sets are available for the same motion data each covering slightly different aspects. \industrycuact{} focuses on general activities such as standing, crouching, walking, whereas \industrygepos{} and \industrydepos{} encode the body posture in a varying degree of detail. It was originally published in \cite{doi:10.1177/0278364919882089}. We regularly sub-sampled the data from originally \SI{240}{\Hz} to \SI{60}{\Hz} which still amounts to around 1.5 million data points.
### Intersections ([Access](https://github.com/vlosing/retrospective_pseudo_labels/blob/main/driver_intention_prediction.csv))([Paper](https://ieeexplore.ieee.org/document/8317760))
The goal of here is to predict the driver's intent at intersections consisting of stopping, driving straight without stopping, or turning. It is based on the daily commute of fourteen subjects represented by a few ego-vehicle features such as the velocity, acceleration, distance to the intersection asf.


## Meta-Parameter Configuration
In the following, we give a list of all used meta-parameters for the corresponding experiments.
### LSTM
The LSTM model was a bidirectional network with 2 LSTM layers, 128 hidden neurons within each layer, learning rate of 0.001, batch size of 256, and dropout 0,5. We used PyTorch for the implementation.

| Data set      | Window size | Retro past window size| Retro future window size | 
| ------------- | ----------- | --------------------- | ------------------------ |
| Activities    | 25  |7|58  |
| Factory       | 12  |10|86  |
| Industry-cuact| 43  |34  |41  |
| Industry-depos| 3  |16  |96  |
| Industry-gepos| 20  |8  |65  |
| Intersections | 17  |15  |34  |

### GRU
The GRU model was a bidirectional network with 2 GRU layers, 128 hidden neurons within each layer, learning rate of 0.001, batch size of 256, and dropout 0,5. 
 We used PyTorch for the implementation.
| Data set      | Window size | Retro past window size| Retro future window size | 
| ------------- | ----------- | --------------------- | ------------------------ |
| Activities    | 20  |7  |48  |
| Factory       | 2  |5  |45  |
| Industry-cuact| 49  |58  |14  |
| Industry-depos| 90  |14  |66  |
| Industry-gepos| 46  |17  |51  |
| Intersections | 18  |20  |40  |

### Rocket
The rocket model was based on a projection on 10000 dimensions paired with a scikit-learn logistic regression model using the lbfgs solver. We used the sktime implementation to get the rocket projections.
| Data set      | Window size | Retro past window size| Retro future window size | 
| ------------- | ----------- | --------------------- | ------------------------ |
| Activities    | 60  |11  |14  |
| Factory       | 11  |16  |23  |
| Industry-cuact| 3  |33  |43  |
| Industry-depos| 12  |11  |17  |
| Industry-gepos| 3  |43  |40  |
| Intersections | 2  |3  |39  |

### Random Forest
We used the scikit-learn implementation with an ensemble size of 100 decision trees.
| Data set      | Window size | Retro past window size| Retro future window size | 
| ------------- | ----------- | --------------------- | ------------------------ |
| Activities    | 79  |49  |87  |
| Factory       | 11  |56  |67  |
| Industry-cuact| 36  |60  |47  |
| Industry-depos| 2  |53  |68  |
| Industry-gepos| 14  |87  |44  |
| Intersections | 13  |15  |35  |
