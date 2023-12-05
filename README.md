## ***Backdoor-Detector for BadNets***

Dataset: 
- Youtube Face
- Source: Readme of https://github.com/csaw-hackml/CSAW-HackML-2020/tree/master/lab3

Input:
- B, a backdoored neural network classifier with N classes
- validation dataset of clean, labelled images.

Output:
- Goodnet a “repaired” BadNet
  - Output the correct class if the test input is clean. The correct class will be in [1,N]
  - Output class N+1 if the input is backdoored

Approach:
- Pruning Defense
  -  Prune the last pooling layer of BadNet B by removing one channel at a time from that layer
  -  Channels should be removed in decreasing order of average activation values over the entire validation set
  -  Save the model when the accuracy drops by at least {2%, 4%, 10%}
 
Challenges:
- Since pooling layer doesn't have any weights, we make use of convolution layer (conv_3, in our case)
- Didn't have resources to run pruning of all 60 channels

How to run the code:
- Run all the cells of the [ipynb notebook](https://github.com/shreya1313/backdoor-detector/blob/main/backdoor_detector.ipynb) attached.

Results:
- The results are as follows
    - The pruned model as a function of the fraction of channels pruned
      ![Plot](https://github.com/shreya1313/backdoor-detector/blob/main/screenshots/pruned_model_plot.png)
    - Final comparison of Pruned and Good model
      ![Plot](https://github.com/shreya1313/backdoor-detector/blob/main/screenshots/final_comparison.png)

_Thanks!_
