# Handwritten Digit Recognition Using Neural Network

This project uses a simple artificial neural network to recognize handwritten digits from images. The model is trained to classify images into one of ten classes, from 0 to 9.

## How the Model Works

### 1. Image Representation

The model works with grayscale images of handwritten digits. In the MNIST dataset, each image has a size of 28 × 28 pixels.

Each pixel contains an intensity value between 0 and 255. Before training, these values are usually normalized to a range between 0 and 1. This makes the values easier for the neural network to process.

The input shape used by the model is:

```text
28 × 28 × 1
```

The `1` represents the grayscale channel.

### 2. Flatten Layer

The original image is two-dimensional, with 28 rows and 28 columns.

The `Flatten` layer converts it into a one-dimensional vector:

```text
28 × 28 = 784
```

Therefore, each image is represented by 784 input values.

### 3. Neural Network Layers

The model contains two hidden layers.

The first hidden layer has 128 neurons:

```text
Input: 784 values
Hidden Layer 1: 128 neurons
```

The second hidden layer has 64 neurons:

```text
Hidden Layer 1: 128 neurons
Hidden Layer 2: 64 neurons
```

The final layer has 10 neurons because there are ten possible digit classes:

```text
0, 1, 2, 3, 4, 5, 6, 7, 8, 9
```

Each neuron in a dense layer is connected to every neuron in the previous layer.

### 4. Weights and Bias

Each connection between neurons has a weight. The network also has biases associated with its neurons.

A neuron calculates a weighted combination of its inputs:

```text
z = w₁x₁ + w₂x₂ + ... + wₙxₙ + b
```

The weights and biases are the main parameters that the model learns during training.

Initially, these parameters do not produce useful predictions. The training process gradually adjusts them so that the model becomes better at recognizing digits.

### 5. ReLU Activation

The hidden layers use the ReLU activation function:

```text
ReLU(x) = max(0, x)
```

ReLU converts negative values to zero while keeping positive values.

It also introduces non-linearity into the network, which allows the model to learn more complicated patterns instead of only simple relationships between input and output.

For handwritten digits, the network can learn useful features such as lines, curves, edges, and combinations of these patterns.

### 6. Softmax Output

The final layer uses the softmax activation function.

There are 10 output values, one for each possible digit. Softmax converts these values into probabilities.

For example:

```text
0: 0.01
1: 0.02
2: 0.03
3: 0.01
4: 0.01
5: 0.04
6: 0.02
7: 0.03
8: 0.01
9: 0.82
```

In this example, the highest probability is associated with digit 9, so the model predicts 9.

### 7. Training

The model learns by using labeled training images.

For each image, the model makes a prediction and compares that prediction with the actual digit.

The basic training process is:

```text
Image
Prediction
Loss calculation
Backpropagation
Weight update
```

This process is repeated many times during training.

### 8. Loss Function

The model uses categorical cross-entropy as its loss function.

The loss represents how different the predicted probabilities are from the correct label.

A smaller loss generally means that the model's predictions are closer to the expected results.

For example, the digit 3 can be represented using one-hot encoding:

```text
[0, 0, 0, 1, 0, 0, 0, 0, 0, 0]
```

The fourth position represents digit 3.

### 9. Backpropagation

Backpropagation is used to determine how the model's weights contributed to the prediction error.

The calculated error is used to find gradients for the model parameters. These gradients indicate how the weights should be adjusted to reduce the loss.

This allows the network to improve its predictions during training.

### 10. Adam Optimizer

The model uses the Adam optimizer to update the weights.

Adam uses the gradients calculated during backpropagation and adjusts the model parameters accordingly.

The training process can be summarized as:

```text
Make prediction
Calculate loss
Calculate gradients
Update weights
Repeat
```

After many iterations, the model gradually learns parameters that are useful for distinguishing between different handwritten digits.

### 11. Model Evaluation

Accuracy is used to measure how many predictions the model gets correct.

For example, if the model correctly classifies 950 out of 1,000 images:

```text
Accuracy = 950 / 1000
Accuracy = 95%
```

The model can be evaluated on test data that was not used during training. This gives a better indication of how well the model performs on unseen handwritten digits.

## Overall Architecture

The neural network used in this project can be represented as:

```text
Input Image: 28 × 28 × 1

Flatten Layer: 784 values

Dense Layer: 128 neurons
Activation: ReLU

Dense Layer: 64 neurons
Activation: ReLU

Output Layer: 10 neurons
Activation: Softmax
```
<img width="708" height="568" alt="image" src="https://github.com/user-attachments/assets/a6806169-d884-425d-8b54-1c859d74feab" />

<img width="655" height="572" alt="image" src="https://github.com/user-attachments/assets/224a9e13-7466-4c92-b5d3-b344dbc0a86c" />



The model learns by adjusting its weights and biases based on the training data. Once trained, it uses the learned patterns to estimate which of the ten digits is present in a new handwritten image.
