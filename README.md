# Retrospective Self-Training
Repository to the article Viktor Losing, Martina Hasenjäger "Leveraging Retrospective Self-Training for Online Time-Series Classification".

## Driver Intersection Prediction ([Access](https://github.com/vlosing/retrospective_pseudo_labels/blob/main/driver_intention_prediction.csv))
The goal of here is to predict the driver's intent at intersections consisting of stopping, driving straight without stopping, or turning. It is based on the daily commute of fourteen subjects represented by a few ego-vehicle features such as the velocity, acceleration, distance to the intersection asf. This data set is described in detail in: Losing et al. "Personalized Maneuver Prediction at Intersections", ICRA 2017(). This data set was used in the experiments of the article. 


## Meta-Parameter Configuration
### LSTM
The LSTM model was a bidirectional network with 2 LSTM layers, 128 hidden neurons within each layer, learning rate of 0.001, batch size of 256, and dropout 0,5. We used PyTorch for the implementation.

| Data set      | Window size | Retro past window size| Retro future window size | 
| ------------- | ----------- | --------------------- | ------------------------ |
| Activities    | 100  |100  |100  |
| Factory       | 100  |100  |100  |
| Industry-cuact| 100  |100  |100  |
| Industry-depos| 100  |100  |100  |
| Industry-gepos| 100  |100  |100  |
| Intersections | 100  |100  |100  |

### GRU
The GRU model was a bidirectional network with 2 GRU layers, 128 hidden neurons within each layer, learning rate of 0.001, batch size of 256, and dropout 0,5. 
 We used PyTorch for the implementation.
| Data set      | Window size | Retro past window size| Retro future window size | 
| ------------- | ----------- | --------------------- | ------------------------ |
| Activities    | 100  |100  |100  |
| Factory       | 100  |100  |100  |
| Industry-cuact| 100  |100  |100  |
| Industry-depos| 100  |100  |100  |
| Industry-gepos| 100  |100  |100  |
| Intersections | 100  |100  |100  |

### Rocket
The rocket model was based on a projection on 10000 dimensions paired with a scikit-learn logistic regression model using the lbfgs solver. We used the sktime implementation to get the rocket projections.
| Data set      | Window size | Retro past window size| Retro future window size | 
| ------------- | ----------- | --------------------- | ------------------------ |
| Activities    | 100  |100  |100  |
| Factory       | 100  |100  |100  |
| Industry-cuact| 100  |100  |100  |
| Industry-depos| 100  |100  |100  |
| Industry-gepos| 100  |100  |100  |
| Intersections | 100  |100  |100  |

### Random Forest
We used the scikit-learn implementation with an ensemble size of 100 decision trees.
| Data set      | Window size | Retro past window size| Retro future window size | 
| ------------- | ----------- | --------------------- | ------------------------ |
| Activities    | 100  |100  |100  |
| Factory       | 100  |100  |100  |
| Industry-cuact| 100  |100  |100  |
| Industry-depos| 100  |100  |100  |
| Industry-gepos| 100  |100  |100  |
| Intersections | 100  |100  |100  |
