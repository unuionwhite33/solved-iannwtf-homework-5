Download Link: https://assignmentchef.com/product/solved-iannwtf-homework-5
<br>
<h1>1      Data set</h1>

We will work with the Tensorflow Cifar10 dataset. <a href="https://www.cs.toronto.edu/%7Ekriz/cifar.html">https://www.cs.toronto.edu/ </a><a href="https://www.cs.toronto.edu/%7Ekriz/cifar.html">%7Ekriz/cifar.html</a><a href="https://www.cs.toronto.edu/%7Ekriz/cifar.html">.</a> It contains 60.000 coloured images of cells with equal sizes. Each images corresponds to one of 10 categories. The dataset is already implemented as a keras.dataset module and very convenient to load! Maybe try to find an load it yourself before referring to the hints. <sup>2</sup>

Print out some of the images together with their labels. The names of the label classes are: ”airplane”, ”automobile”, ”bird”, ”cat”, ”deer”, ”dog”, ”frog”, ”horse”,

”ship”, ”truck”. <sup>3</sup>

Perform other necessary or beneficial preprocessing steps.<sup>4</sup>

<h1>2      Model</h1>

Implement a Convolutional Neural Network to classify the pictures. This time, try to work in some of the optimization techniques you learned about (Data Augmentation is very optional here though).

5 6 7 8 9

<h1>3      Training</h1>

Then train your network. We would like you to just get started and try it yourself. In the hints we put some training hyperparameters for your orientation in case you’re stuck. <sup>10</sup>

For this task, you should reach a test accuracy of around 60% to pass. In the outstanding homeworks, we would like to see at least 85% accuracy, but be aware that training will take some time.

<h1>4      Visualization</h1>

Visualize accuracy and loss for training and test data using matplotlib.

It might be useful to work in the visualization into your training loop, so you can check on your networks progress while training. It will save you time as you can see how your changes affect the training earlier during the process.

<h1>5      Outstanding Requirements</h1>

To receive an outstanding your solution should include the following things:

<ul>

 <li><em>&gt;</em>= 85% accuracy</li>

 <li>a proper Data Pipeline</li>

 <li>use multiple regularization techniques</li>

 <li>nice visualizations</li>

 <li>useful comments</li>

</ul>

Data Augmentation is a nice add-on, but optional.

<h1>Notes</h1>

1 Remember, you learned about optimizers, weight penalties, dropout, batch normalization and data augmentation. 2

You can load this dataset directly from keras <a href="https://www.tensorflow.org/api_docs/python/tf/keras/datasets/cifar10">https://www.tensorflow.org/api_docs/python/tf/ </a><a href="https://www.tensorflow.org/api_docs/python/tf/keras/datasets/cifar10">keras/datasets/cifar10</a> with the method load data(). Remember, this way you directly get a tainand a testdataset.

3

You can put the label names in a list (in the correct order) and match the label classes to the list index when printing.

4 Relevant preprocessing steps:

<ul>

 <li>Shuffling</li>

 <li>Batching, an orientation would be minibatches of size 64. Feel free to also try other batchsizes and see what happens.</li>

 <li>Normalize the images so your network can work with them better. Check Courseware/Image</li>

</ul>

Representation for inspiration.

<ul>

 <li>One-hot-encode the labels. What should be the depth of the resulting labels?</li>

 <li>Feel free to apply Data Augmentation (rotation, zooming…). Check out Courseware/Regularization/Data augemantation for that. But be aware, it will slow down your training a lot!</li>

</ul>

5

You can always start with the convolutional network you used to solve last week’s homework and make some additions to it. Think about how the readout layer for this dataset should differ from the Malaria one! <a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>

6

If you want to use Dropout / Batch Normalization, remember to pass on the training flag in the call function. Also think about the order of these layers! <a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a>

7

If you are using Batch Normalization layers, remember your previous layer should not have any activation function, but you have to apply an activation function manually after the Batch Normalization layer.

8

Use a readout layer. You can decide to reshape your inputs before this read out layer (check out tf.keras.layers.Flatten()) or use global average pooling: tf.keras.layers.GlobalAveragePooling2D()

<ul>

 <li>6 convolutional layers should be enough to reach around 80% accuracy (if trained long enough). Feel free to build deeper networks but they need longer to train and are more prone to overfitting.</li>

 <li>Training Hyperparameters for orientation:</li>

 <li>epochs: around 30, depending on your architecture you can train even longer as long as the model is not overfitting</li>

 <li>learning rate: should be very small! Try something between 0.00001 and 0.0001.</li>

 <li>optimizer: Adam</li>

 <li>loss: BinaryCrossEntropy. Check keras.losses.BinaryCrossentropy()</li>

 <li>accuracy: how many items in prediction and target are the same (in the batched vectors)? → take the mean of it</li>

</ul>

<a href="#_ftnref1" name="_ftn1">[1]</a> Number of classes.

<a href="#_ftnref2" name="_ftn2">[2]</a> First apply Batch Normalization, then the activation function and then Dropout.