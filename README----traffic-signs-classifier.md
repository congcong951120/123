## Project: Build a Traffic Sign Recognition Program
The Project
---
The goals / steps of this project are the following:
* Load the data set
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report

### Dependencies
This lab requires:
## Analysis
The goal is to modify LeNet to identify German traffic signs in 43 categories. LeNet convolution of two layers, three layers fully connected, I added a layer of convolution, modify the kernel size. Further, the addition of the whole dropou connecting layer for preventing over-fitting. Under this process to build the network of record, summarize method TensorFlow to build and train a network of convolution.In this data set, there are 34799, 4410, and 12630 images in the training, verification, and test sets, all of which are (32, 32, 3), with a total of 43 categories.

### Step 0: Load The Data

The downloaded data set is serialized with pickl, so pickle is used to read it.

### Step 1: Dataset Summary & Exploration

The pickled data is a dictionary with 4 key/value pairs:

- `'features'` is a 4D array containing raw pixel data of the traffic sign images, (num examples, width, height, channels).
- `'labels'` is a 1D array containing the label/class id of the traffic sign. The file `signnames.csv` contains id -> name mappings for each id.
- `'sizes'` is a list containing tuples, (width, height) representing the original width and height the image.
- `'coords'` is a list containing tuples, (x1, y1, x2, y2) representing coordinates of a bounding box around the sign in the image. 
##THE TRAINING, VERIFICATION,AND TEST SETS EACH HAVE 34799,4410 AND 12630 PICTURES,ALL OF WHICH ARE (32,32,3),WITH A TOTAL OF 43 CATEGORIES.##

### Step 2: Data augment

I used two particularly simple methods to expand the data set: one is to turn the pictures to gray, that is, to take the pixels on the three channels as their average; the other is to add one to each picture An integer up to 100.
But not all the data was used. Considering that I used CPU training, I only used more than 50,000 pictures.Design and Test a Model Architecture

### Step 3: Build a network

                     Layer                                Description 
                     Input                             32x32x3 RGB image 
                     Convolution3x3           1x1 stride, same padding, outputs 32x32x16 
                     LEAKY_RELU 
                     Max pooling 2x2              2x2 stride, outputs 16x16x16 
                     Convolution 3x3        1x1 stride, same padding, outputs 16x16x32 
                     LEAKY_RELU 
                     Max pooling 2x2               2x2 stride, outputs 8x8x32 
                     Convolution 3x3         1x1 stride, same padding, outputs 8x8x64 
                     LEAKY_RELU 
                     Max pooling 3x3                2x2 stride, outputs 3x3x64 
                     Flatten                               output 576 
                     Fully connected                       output 120 
                     LEAKY_RELU 
                     Dropout 
                     Fully connected                        outout 84 
                     LEAKY_RELU 
                     Dropout 
                     Fully connected                        output 43 
                     Softmax 

### Step 4: Network forward propagation

Build a network structure:
The API used is:
tf.nn.conv2d()
tf.nn.leaky_relu()
tf.nn.max_pool()
tf.nn.dropout()
tf.contrib.layers.flatten()
tf.matmul()

### Step 5: Create input and output placeholders

API used:
tf.placeholder()
tf.one_hot()

### Step 6: cost and optimizer

The following is the setting of some parameters, the establishment of the cost function, and the establishment of the optimizer. Here a learning rate decay is used.
API used:
tf.contrib.layers.l2_regularizer()
tf.nn.softmax_cross_entropy_with_logits()
tf.reduce_mean()
tf.add_n()
tf.get_collection()
tf.Variable()
tf.train.exponential_decay()
tf.train.AdamOptimizer()

### Step 7: Evaluation function.

The idea is very simple. For the output of the network, find the index of the maximum value, that is, the category of the instance, and compare it with its own label, which means that the classification is correct. Then calculate the correct classification ratio, which is the accuracy rate. API used:
tf.argmax()
tf.equal()
tf.cast()
tf.reduce_mean()
tf.get_default_session()
tf.Session.run()
tf.train.Saver()

### Step 8: Train the Model

The training process is the process of constantly calling the optimizer to optimize the cost on the batch. API used:
tf.Session()
tf.global_variables_initializer()
tf.Session.run()
tf.train.Saver.save()


### Step 9: Evaluation test set

It is time to evaluate the performance of the model on the test set. API used:
tf.train.Saver.restore()
The accuracy of the model on the test set can reach 0.943.

## Conclusion

By running the above code, according to the accuracy results of the training and validation sets, starting from the tenth epoch, the accuracy rate on the validation set is stable at 96.x%, and both on the training set are 99.9x% .This shows that overfitting is still very serious. We should try more methods to reduce overfitting and improve accuracy.