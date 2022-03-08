# Height Democratization of Jump Height estimates exploiting Smartphone IMU measures 

## Description

This repository contains the main code used for the jump height democratization analysis performed for the paper "*A Countermovement Jump Height Estimate Democratization Approach through Smartphone Measures*" by Mascia and Camomilla. 

The code here shared is so divided:

1. Feature extraction (written in GNU Octave/MATLAB language);
2. Feature selection (written in R language)

## Feature Extraction
The code extracts all those features which were biomechanically related to the jump itself (Dowling and Vamos, 1993; Mascia and Camomilla, 2021). Moreover, they included the three *central frequencies* extrapolated through Variational Mode Decomposition (Dragomiretskiy and Zosso, 2014). 

It must be noticed that the anthropometric features, described by four skinfold lengths, were not automatically computed through the presented algorithm, since they were manually measured by an external operator.

All the features, along with their description are listed in the table below.

|     ID     |     Feature                                                     |     Measure unit    |     Description                                                                                     |
|------------|-----------------------------------------------------------------|---------------------|-----------------------------------------------------------------------------------------------------|
|     Bi     |     Biceps skinfold                                             |     mm              |     Self-explanatory                                                                                |
|     Tr     |     Triceps skinfold                                            |     mm              |     Self-explanatory                                                                                |
|     Sc     |     Subscapular skinfold                                        |     mm              |     Self-explanatory                                                                                |
|     Ic     |     Superior-Anterior Iliac Crest skinfold                      |     mm              |     Self-explanatory                                                                                |
|     h<sup>SP</sup>    |     Jump height                                                 |     m               |     Height computed via TOV from a<sup>SP<sup>                                                                |
|     A      |     Unweighting phase duration                                  |     s               |     [t<sub>0</sub>, t<sub>UB</sub>]                                                                                       |
|     b      |     Minimum acceleration                                        |     m / s<sup>2</sup>          |     a(<sub>a, min</sub>)                                                                                      |
|     C      |     Time from minimum to maximum acceleration time              |     s               |     [t<sub>a, min</sub>, t<sub>a, max</sub>]                                                                              |
|     D      |     Main positive impulse time                                  |     s               |     Positive acceleration from t<sub>UB</sub>   until the last positive sample prior t<sub>TO</sub>                       |
|     e      |     Maximum acceleration                                        |     m / s<sup>2</sup>          |     a(t<sub>a, max</sub>)                                                                                      |
|     F      |     Time from acceleration positive peak to   take-off          |     s               |     [t<sub>a,max</sub>, t<sub>TO</sub>]                                                                                   |
|     G      |     Ground duration                                             |     s               |     [t<sub>0</sub>, t<sub>TO</sub>]                                                                                       |
|     H      |     Time from minimum acceleration to the end of B              |     s               |     [t<sub>a, min</sub>, t<sub>BP</sub>]                                                                                   |
|            |                                                                 |                     |                                                                                                     |
|     k      |     Acceleration at the end of the braking phase                |     m / s<sup>2</sup>          |     a(t<sub>BP</sub>)                                                                                          |
|     J      |     Time from negative peak velocity to the end of B          |     s               |     [t<sub>v, min</sub>, t<sub>BP</sub>]                                                                                  |
|     l      |     Negative peak power                                         |     W / kg          |     P(t<sub>P, min</sub>)                                                                                      |
|     M      |     Positive power duration                                     |     s               |     Self-explanatory                                                                                |
|     n      |     Positive peak power                                         |     W / kg          |     P(t<sub>P, max</sub>)                                                                                      |
|     O      |     Time distance between positive peak power and   take-off    |     s               |     [t<sub>P, max</sub>, t<sub>TO</sub>]                                                                                  |
|     p      |     Mean slope between acceleration peaks                       |     au              |     p = (e - b) / C                                                                                 |
|     q      |     Shape factor                                                |     au              |     Ratio between the area under the curve along D   and the one of a rectangle of sides D and e    |
|     r      |     Impulse ratio                                               |     au              |     r = b / e                                                                                       |
|     s      |     Minimum negative velocity                                   |     m / s           |     v(t<sub>v, min</sub>)                                                                                      |
|     u      |     Mean Concentric Power                                       |     W / kg          |     Self-explanatory                                                                                |
|     W      |     Power peaks delta time                                      |     s               |     [t<sub>P, min</sub>, t<sub>P, max</sub>]                                                                              |
|     z      |     Mean Eccentric Power                                        |     W / kg          |     Self-explanatory                                                                                |
|     f<sub>1</sub>     |     High central frequency                                      |     Hz              |     Highest central frequency computed through   VMD, associated with wobbling tissues and noise    |
|     f<sub>2</sub>     |     Middle central frequency                                    |     Hz              |     Middle central frequency computed through VMD,   associated with wobbling tissues               |
|     f<sub>3</sub>     |     Low central frequency                                       |     Hz              |     Lowest central frequency computed through VMD,   associated with the jump proper                |

**Table 1**: Detailed explanation of each of the analyzed features. Capital letters are for timings, small letters for the other parameters. Legend: au = arbitrary units; t<sub>0</sub> = jump onset time; t<sub>UB</sub> = unbraking-braking phase transition time; t<sub>BP</sub> = braking-propulsion phase transition time; t<sub>TO</sub> = take-off time; t<sub>a, min</sub> = minimum acceleration time; t<sub>a, max</sub> = maximum acceleration time; t<sub>v, min</sub> = minimum velocity time; t<sub>P, min</sub> = minimum power time; t<sub>P, max</sub> = maximum power time.

<img src="./common/features.png" height=600>


## Feature Selection

## References
Mascia, G., & Camomilla, V. (2021). An automated Method for the Estimate of Vertical Jump Power through Inertial Measurement Units. ISBS Proceedings Archive, 39(1). https://commons.nmu.edu/isbs/vol39/iss1/74

Dowling, J. J., & Vamos, L. (1993). Identification of Kinetic and Temporal Factors Related to Vertical Jump Performance. Journal of Applied Biomechanics, 9(2), 95–110. https://doi.org/10.1123/jab.9.2.95

Dragomiretskiy, K., & Zosso, D. (2014). Variational Mode Decomposition. IEEE Transactions on Signal Processing, 62(3), 531–544. https://doi.org/10.1109/TSP.2013.2288675