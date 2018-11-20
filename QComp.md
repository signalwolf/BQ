# Qualcomm Deep learning competition

It is an internal competition with the assist of wandb. Max three people form a group and trying to solve 
some machine learning problems. We get training from wandb and then train our modules by spliting it to 
training and validation test set. Then upload our modules to the wandb. They will run the modules on their
test data and provide the scores.

Our project is to build an machine learning module to estimate the america sign language. So, it is an 
multi-classification problem. We got an CSV data (28*28) * 1 data to indicate the pixels, so first we
reshape the data to 28 * 28 then applied 3 layers of convolution layers, maxpooling layers and two full
connected layers after that with the softmax function in the end to output the class. 

It get 100% pass in the wandb's database. But we know it is not that great, because we tried another 
online america sign langeuage database CIFAR-10 and it only get 80% pass.

Obvious we tried different method, like in the beginning our module overfit the training set. So we add 
dropout into the module and final achieve the solution. 

### We have three people, each one is going to different route:
One of us is trying to implement the transfer learning because the training set is not too big. So, the
initial thought is using the transfer learning to get good result. 
The other guy is build the module on Keras with some easy verification because the transfer learning 
is not that fast. So, we build something easy first and see the performance. Keras is very easy to use
and can built up the CNN module very fast.

### Details:
1.  Input shape: 28 * 28 
2.  CNN: 3 * 3 * 32 conv layer with same padding and Relu activation
    output: 28 * 28 * 32
    parameters: (3 * 3 + 1) * 32 = 320
2.  CNN: 3 * 3 * 32 * 64 conv layer with same padding and Relu activation
    output: 28 * 28 * 64
    parameters: (32 * 3 * 3 + 1) * 64 = 18496
3.  MaxPooling: 
    output: 14 * 14 * 64
4.  Droput:
    output: 14 * 14 * 64
5.  CNN: 3 * 3 * 128 conv layer with same/relu
    output: 14 * 14 * 128
    parameters: (3 * 3 * 64 + 1) * 128 = 73856
6.  MaxPooling: 
    output: 7 * 7 * 128
7.  CNN: 2 * 2 * 128 conv layer with same/relu
    output: 7 * 7 * 128
    parameters: (2 * 2 * 128 + 1) * 128 = 65664
8.  MaxPooling:
    output: 3 * 3 * 128
9.  Flattern:
    output: 1152
10. Dense:
    output: 1500.
    parameters: 1152 * 1500 + 1500 = 1729500
11. Dense:
    output: 26 * 1500  + 26 = 39026
    