# Lecture 2
## Assignment 1
- K-Nearest neighbor
- Linear Classifiers:  SVM, Softmax
- 2- layer Neural network
---
## Other
- Python numpy tutorial
- Google cloud tutorial on github
## Part 1: Image classification
- Receive input image --> assign category label
- Computer see image as large grid of numbers
- Assigns a semantic label to image based on pixel values
- All pixels changes when the camera moves
- Positions, occlusion, background, variation within class (e.g. different colored cats) are potential challenges to algorithms
- What algo takes image as input and outputs label? Find edges, corners?
- Steps: 1. Collect lg dataset, 2. use ML to train classifier, evaluate classifier on new image
- Train --> Predict
## Part 2: Nearest neighbor
- Nearest neighbor ("dumb") memorize all, then predict nearest to evaluated image
- CIFAR10 dataset, 10 classes, 50,000 training images, 10,000 testing images
- What is the L1 distance? pixel-wise absolute value differences, sum pixel differences and use as metric
- Training completes in O(1) time, predict completes in O(N) time (quite slow)
- By contrast, CNN uses more at training time than prediction time
- Nearest neighbor classifier carves up space based on points and their neighbors
- Noise or spurrious points may cause issues at setting boundaries
- K-Nearest neighbors - majority vote from K closest points
    - Computation time with respect to K?
    - Should always use some value of K to smooth out boundaries and get better results
    - Manhattan vs Euclidean distance (L1 vs L1)
    - L1 depends on coordinates chosen, L2 is generic, agnostic
    - Try nearest neighbor algo
    - What is the best value of K to use?
    - What is the best distance to use?
    - How to determine whether to use L1 distance or L2 distance?
    - How to properly set hyperparameters?
    - Note that K=1 always works perfectly on training data --> Bad!
    - NEVER split data into train & test (no idea how it will perform on new data)
    - Split data into three different sets: train (most), validation, test --> Much better!
    - Cross-validation for smaller data sets - split data into folds, try each fold as validation and average the results
    - k-Nearest neighbor seldom used on images - slow at test time, distance metrix on pixels not very informative
## Linear classificaiton
- Linear classifier is a building block of the more complex CNNs
- Parametric model: Take in image, then weights as "W" in function f(x,W) --> 10 numbers, higher score in CIFAR10 is higher probability
- Training data no longer needed at test time - more efficient, parameters stored in W
- Coming up with the right structure for the function f is the most critical thing
- Linear classifier:  f(x,W) = Wx
- 10 numbers equal scores for each category in CIFAR10
- f(x,W) = Wx + b  --> b equals bias coefficient
- Linear classifier constrained by learning only a single template per category
- Linear classifier struggles to separate odd from even, multimodal (islands of different things in pixel space that can't be split cleanly
## Next time
- Loss functions and optimization
