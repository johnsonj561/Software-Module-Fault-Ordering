### Module Order Modelling

The Module Order Modelling (MOM) methodology is applied to fit and test data sets which describe software modules. The labelled data sets contain 9 attributes, where the 9th attribute (label) provides the total number of faults for the given module. The training data contains 188 instances and a total of 427 faults among all instances. The test data contains 94 instances and a total of 241 faults. The goal of MOM is to order a set of software modules based on their predicted number of faults. Development managers are then able to select a percentage of the most fault prone modules for additional review. This is more flexible than traditional classification of modules as fault prone vs non-fault prone, as the team can then focus on the most fault prone modules, and select a cutoff point based on their available resources.

The labelled data sets are used to evaluate the performance of MOM. First, software modules are ordered by their actual number of faults, creating a perfect ranking. Cutoff points are selected between 5% and 50%, where a cutoff of 5% selects the top 5% of software modules which have the greatest number of faults. For each cutoff point, the number of actual faults captured in the given range is compared to the total number of faults contained in the data set, resulting in a percentage of total faults captured.

Next, modules are ordered by their predicted rank, where each module's predicted number of faults is calculated using linear regression models that were learned during Assignment 1. The predicted number of faults are only used to order the modules and create the predicted ranking. The same cutoff points are then applied to the predicted ranking. For each cutoff point, the number of actual faults captured in the given range is compared to the total number of faults in the data set. 

The MOM model is evaluated by comparing the total faults captured with the predicted ranking to the total faults captured with the perfect ranking at various cutoff points. Tables and diagrams are provided to compare the perfect ranking results to the predicted ranking results.


The two linear regression models which will be used to predict module faults and determine predicted ranking are:

M5 Model: Linear Regression Model with M5 Method of Attribute Selection
FAULTS = - 0.0516 * NUMUORS + 0.0341 * NUMUANDS - 0.0027 * TOTOTORS - 0.0372 * VG + 0.2119 * NLOGIC + 0.0018 * LOC + 0.005 * ELOC - 0.3091

Greedy Model: Linear Regression Model with Greedy Method of Attribute Selection
FAULTS = - 0.0482 * NUMUORS + 0.0336 * NUMUANDS - 0.0021 * TOTOTORS - 0.0337 * VG + 0.2088 * NLOGIC + 0.0019 * LOC - 0.3255

### Results

See report for full result set, tables, and diagrams.

Both linear regression models led to module ordering with high accuracy near 90%, indicating that the underlying prediction models effectively predicted the number of faults for ordering purposes. This does not imply that the models accurately predicted the number of faults for each module, rather that they predicted the number of faults in such a way that allowed the predicted rank to closely match the perfect rank.

Compared to traditional classification of software modules, as fault prone vs non-fault prone, MOM is favorable for practical application. It is flexible in the sense that development teams can select a cutoff point that matches their available resources. If a team only has resources to apply software improvement to 10% of their modules, MOM can be applied to rank modules by predicted number of faults and then the top 10% can be selected for review. Since modules are effectively ordered from greatest predicted faults to least predicted faults, development teams can maximize productivity by focusing on the most fault prone modules first. This also eliminates the need to define a fault prone threshold (total number of faults which defines a module 'fault prone'). Another key takeaway is the presence of the Pareto Principle, where roughly 80% of the faults come from just 20% of the software modules.

