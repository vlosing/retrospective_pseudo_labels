# Retrospective Self-Training
This repository contains supplementary information and data to the article Viktor Losing, Martina Hasenjäger "Leveraging Retrospective Self-Training for Online Time-Series Classification".

## Driver Intersection Prediction ([Access](https://github.com/vlosing/retrospective_pseudo_labels/blob/main/driver_intention_prediction.csv))
The goal of here is to predict the driver's intent at intersections consisting of stopping, driving straight without stopping, or turning. It is based on the daily commute of fourteen subjects represented by a few ego-vehicle features such as the velocity, acceleration, distance to the intersection asf. This data set is described in detail in: Losing et al. "Personalized Maneuver Prediction at Intersections", ICRA 2017(). This data set was used in the experiments of the article. 


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
