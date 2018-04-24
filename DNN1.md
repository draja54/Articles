# Feature Engineering

Feature engineering and feature extraction are key components as well as time consuming parts of the machine learning. It is about transforming training data, augmenting it with additional features, in order to make machine learning algorithms more effective.

It involves domain knowledge in carefully crafting the features. 

Each property or the column in the data is a feature. Some times a group of columns can be clubbed together to form a feature. Each feature carries some weightage in improving the model performance. Some fearures may not effect the model at all.

Carefully sellecting appropriate features and applying to the model results is better better performance of the predictive models. It is an expensive operation.

# Feature Map

Feature Map is the output obtained after applying filter to the input.
The output layer shares same weight and bias if any.
The number of filters (kernel) we use on the input will result in same amount of feature maps.

![](https://qph.ec.quoracdn.net/main-qimg-134024e4e35d7c7cbc4ccbe3a62dc8b2.webp)
In the above Image we have one filter and the result id one feature map

![](https://cdn-images-1.medium.com/max/1000/1*45GSvnTvpHV0oiRr78dBiw@2x.png)

In the above Image we have two filters. Hence the output has two feature maps.

The number of feature maps obtained will be equilant to number of filters used.

Lets see an example.

![](https://cdn-images-1.medium.com/max/1000/1*cTEp-IvCCUYPTT0QpE3Gjg@2x.png)
We have input and Filter available.<br>
Input dimension is **5x5** 
Filter dimension is **3x3** 
we are applying 3x3 filter on 5x5 Input to obtain **3x3** Feature Map.
<br>
The calculation as follows.
![](https://cdn-images-1.medium.com/max/1000/1*ghaknijNGolaA3DpjvDxfQ@2x.png)
<br>
The simulation is as follows
![](https://cdn-images-1.medium.com/max/1000/1*VVvdh-BUKFh2pwDD0kPeRA@2x.gif)

From the above scenario we have the following.
Input = 5x5 matrix(Blue colour)
Filter = 3x3 matrix(Green  Color)
Feature Map(Output) = 3x3 matrix(Pink Color)

<br>

# Activation Function

 Imagine you work for a company that has a job opening and you got large number of resumes.Dont worry. You can segregate them to be relevent and non relevent based on some factors. This is what an **Activation Function** does.

Activation functions help the network do this segregation. They help the network use the useful information and suppress the irrelevant data points.

Activation Functions decide whether a neuron should be activated or not. Whether the information that the neuron is receiving is relevant for the given information or should it be ignored.

![](https://harishnarayanan.org/images/writing/artistic-style-transfer/neuron.gif)

![](https://s3-ap-south-1.amazonaws.com/av-blog-media/wp-content/uploads/2017/10/17123344/act.png)

The activation function is the non linear transformation that we do over the input signal. This transformed output is then sen to the next layer of neurons as input.

 #### Why use it?

If activation function is not present then it is just a normal linear regression model. Linear equation is simple to solve but it is limited in its capacity. 

![](https://cdn-images-1.medium.com/max/2000/1*GIPiAdQyOa8wUOkHaL-MJg.gif)


![](https://analyticsindiamag.com/wp-content/uploads/2018/01/nural-network_3.gif)

## Popular types of activation functions

* Sigmoid
* ReLU
* SoftMax

### Sigmoid

Sigmoid is an activation function. It is of the form-

                                  f(x)=1/(1+e^-x)
    

Sigmoid is a smooth function and is continuously differentiable The advantage of sigmoid is that it is non linear. This means when we have multiple neurons having sigmoid function as activation function the output is always non-linear. The function ranges from 0 - 1 having an S shape.
    
Ploting the above equation look like this

![](https://s3-ap-south-1.amazonaws.com/av-blog-media/wp-content/uploads/2017/10/17154935/sigmoid-300x300.png)

The gradient is very high between the values of -3 and 3 but gets much flatter in other regions. This means that in this range small changes in x would also bring about large changes in the value of Y. So the function essentially tries to push the Y values towards the extremes. 

Gradient of the sigmoid function

![](https://s3-ap-south-1.amazonaws.com/av-blog-media/wp-content/uploads/2017/10/17155643/sigmoid-derivative-300x300.png)


It’s smooth and is dependent on x. This means that during backpropagation we can easily use this function. The error can be backpropagated and the weights can be accordingly updated


### ReLU
The ReLU function is the Rectified linear unit. It is defined as-

                                f(x)=max(0,x)

ReLU function is non linear, which can easily backpropagated the errors and have multiple layers of neurons being activated by the ReLU function.The main advantage of using the ReLU function is that it does not activate all the neurons at the same time.

Graphical representation of ReLU

![](https://s3-ap-south-1.amazonaws.com/av-blog-media/wp-content/uploads/2017/10/17160725/relu-300x300.png)



If the input is negative it will convert it to zero and the neuron does not get activated. This means that at a time only a few neurons are activated making the network sparse making it efficient and easy for computation.

Gradient of the ReLU function

![](https://s3-ap-south-1.amazonaws.com/av-blog-media/wp-content/uploads/2017/10/17160955/relu-derivative-300x300.png)

But ReLU also falls a prey to the gradients moving towards zero. If you look at the negative side of the graph, the gradient is zero, which means for activations in that region, the gradient is zero and the weights are not updated during back propagation. This can create dead neurons which never get activated. 

Always keep in mind that ReLU function should only be used in the hidden layers

### SoftMax

SoftMax is a type of Sigmoid that helps in solving classification problems. As we saw earlier sigmoid functions are able to handle two classes. While handling multiple classes having yes or no doesnt help much.Thats when SoftMax comes to the rescue. It would squeeze the output of each class between 0 and 1 and also divides the sum of the outputs. This gives the probability of each class.

Formula for SoftMax is 
                            ![](https://s3-ap-south-1.amazonaws.com/av-blog-media/wp-content/uploads/2017/10/17014509/softmax.png)

 softmax function is generally used in the output layer of the classifier where we are actually trying to attain the probabilities to define the class of each input

### When to use?

Sigmoid functions and SoftMax generally work better in the case of classifiers

ReLU function is a general activation function and is used in most cases these days

### Note : 
We can begin with using ReLU function and then move over to other activation functions in case ReLU doesn’t give optimum results


# Receptive Field 
When we are dealing with high dimensional inputs such as Images, it is not a good idea to connect neurons to all neurons in the previous volume. In order to overcome this issue we connect each neuron to only a local region of the input volume. The special extent of this connectivity is called receptive field of the neuron or the filter size.

![](https://i.stack.imgur.com/I7DBr.gif)

In the above Image
the input size is **5x5** (All green area including yellow)
the receptive field/ area is **3x3**.(All yellow area)
the outpur size is **3x3** (All pink area)

If the same filter is applied to the inpur size of **28X28** the results will be as follows.

the input size is **28x28** 
the receptive field/ area is **3x3**.
the outpur size is **26x26**
Here receptive field, kernel and filter are used interchangenably.