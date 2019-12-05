# pruningDNN
1, Justification of choices.
a, Used CNN because it gives better result for image dataset.
b, Tried different combinations for filters dimension, number of filters, pooling dimensions, and chose the best model based on experimental results.
c, For pruning, implemeted the l2 heuristic as defined in the paper.
d, Used more than 10 epochs for baseline training, it lead to over-fitting.


2, Baseline Classification and Accuracy.

Used CNN with following structure:
Input(28,28,1) --> Filter(28,3,3,1) --> Max_pooling(2,2) --> Filter(28,3,3,28) --> max_pooling(2,2) --> FC(1372, 32) --> softmax(32, 10)


Test Accuracy = 0.9904000163078308

3, Different strategies used.

For Baseline: 1,Tried with different activation fucntions in filters. 
2, Tried bigger filters than (3,3), also tried average pooling.

For Pruning: 1, Used more than 5 epochs (10 and 15) per training after pruning. 

4, Analysis of results.

I used l2 norm of a filter as pruning criteria.
Baseline Model: 28(3,3,1) filter, (2,2) max_pooling, 28(3,3,28) filter, (2,2) max pooling, 1 FC layer, 1 softmax layer. 
Pruned Model: 1(3,3,1) filter, (2,2) max_pooling, 2(3,3,1) filter, (2,2) max_pooling, 1 FC layer, 1 softmax layer. 

Baseline Model parameters count:51630
Pruned Model parameters count:3528

(Using 1core on 4 core machine, 4GB memory and on 10000 test cases.)
Baseline Model Inference rate: 9s 450us
Pruned Model Inference rate: 5s 345us

Baseline Model Test Accuracy:0.9904000163078308
Pruned Model Test Accuracy:0.9663000106811523


There is 93.16% decrease in model parameters, and ~44% decrease in inference time. 


5, Further Improvements.

a. Exploration step needs to be added.
b. DIfferent scoring criterias such as l1 norm, FS could be used.

