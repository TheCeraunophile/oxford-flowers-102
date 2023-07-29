# oxford-flowers-102
The Oxford Flowers 102 is a Category Flower Dataset containing 102 types of flowers chosen to be flower commonly occuring in the United Kingdom.
Each class consists of between 40 and 258 images <a href=https://www.robots.ox.ac.uk/~vgg/data/flowers/102/>refrence,</a> <a href=https://www.robots.ox.ac.uk/~vgg/data/flowers/102/categories.html>overview</a>

In this repo I tried to create a model based on neural network to classify new flowers. you can download the dataset from <a href=https://www.robots.ox.ac.uk/~vgg/data/flowers/102/>here</a>.


Any image converted to an array with shape of (100, 100, 3) (As regard that the color is a main factor for flower, we kept the color and didn't convert the main images into grayscale).

In the first attempt, I used PCA for dimensional reduction with 95% of accuracy, the dimensions of every image from 30000 goes to 1529 so the first model was created by 7 fully connected layers with input shape of (1529,) at the first layer. After 75 epochs, overfit occoured and Early stoping, stop the training process. Final accuracy after all these 75 epoch on the training data was 55% while accuracy on the validation was 13%.

In the second attempt, I used CNN with input shape of (100, 100, 3) for first convolutional layer. Early stoping, stop the training process But. Final accuracy after all these 189 epoch on the training data was 43% while accuracy on the validation was 33%. In fact, this model cannot reach a better validation loss after a large number of epochs, and finally Early stopping stops the training process.

In the third attempt, I used predefined function: ImageDataGenarator on `tensorflow.keras.preprocessing` to generate new images based on the current dataset (on the fly). In this time learning speed decreased because of augmented images. Final accuracy after just 50 epoch on the training data was 64%, while accuracy on the validation was 53% and 43% on the test data that the model never seen them. It's clear that with more epoch the model will get better accuracy.
