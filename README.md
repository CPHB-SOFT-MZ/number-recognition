# number-recognition

## Prerequisites
- ```python3```
- ```tensorflow```
- ```matplotlib```
- ```numpy```

## Guide to run project
Clone this repository to your local machine.

To install the prerequisites, assuming Python 3 is already installed, you can run these commands:

- ```pip3 install --upgrade tensorflow```
- ```pip3 install --upgrade matplotlib```
- ```pip3 install --upgrade numpy```

Then you should be all set to run the project. 
Change the directory to the cloned folder and run the project by typing in the following:
-```python3 mnist.py```

This will produce the most optimized result we've come to in this project.


## Results
### First version: simple softmax

The first version of the project was simply a one neuron layer using the softmax function.

The training set produces the following results: 

![alt text](https://github.com/ziemerz/number-recognition/blob/master/images/accuracy-graph-softmax.png)

Which is OK for our first version. 

The results of the test data ended up like this: 

![alt text](https://github.com/ziemerz/number-recognition/blob/master/images/result-softmax.png)

This means we start off with an accuracy of approximately 92.2%. This is OK for a start, but it's the last 7.8% that are the toughest. 
Let's take a look at how to solve this. 

### Second version: Adding layers and relu
Next up, we'll add some more neuron layers to get a better accuracy. This way, the training data will be exercised better, since it will have more neurons to go through. 
We'll add 5 layers on top of the 1 we already have. 

We'll then get the following training results results:

![alt text]()

As we can see, the addition of layers and changing the sigmoid activation function with the relu function, we gave our training data a lot of noise, which means we're learning too fast. However, the graph seems somewhat the place where we want it to be regarding to accuracy.
Let's take a look at the result:

![alt text]()

We can see that we have achieved approximately 98.2% which is quite good, but not good enough. 

## Third version: Applying learning decay

We want to get rid of the noise. The way to do this will be to slow down our learning rate. By modifying our learning rate to something like 0.0001 will make it go too slow, so we will gradually slow down as we get more precise. 

This will look something like this:

![alt text](Link to accuracy on training data)
![alt text](https://github.com/ziemerz/number-recognition/blob/master/images/entropy-loss-relu-5layer-nodropout.png)

This looks good, as we have reduced noise. However, this resulted in somehting we didn't anticipate right away. The entropy loss is increasing the more training we does, which is not good. This means that the system is memorizing what it learns, and thus skipping on training. This can be OK in some cases. But if I were to write a new number which was not in the inital dataset, it would most likely fail to guess it. This is not what we want. This is usually caused by there being too many neurons.
However, our end result on the test data has increased by .5% which is good: 
![alt text](Link result of data)


And this will give us a result of approximately 98.7% which is quite an improvement! And this is just by slowing down a bit. However we will need to do something about the neurons "remembering".

## Fourth version: Dropout
The way to solve having too many neurons is by randomly dropping some of them in each layer. 
This is easy, we just randomly drop some neurons in each layer on each iteration and pass that layer to the next. 

This will give us the following result:
[!alt text](https://github.com/ziemerz/number-recognition/blob/master/images/accuracy-graph-relu-5layer-dropout.png)
As you can see, our cross entropy loss graph has flattened which is what we wanted. 

Let's check on the test result and ensure that it's just as good as befoe:
