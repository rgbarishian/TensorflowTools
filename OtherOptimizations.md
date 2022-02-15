# Optimizations During Training
It is hard to optimize during the training process without affecting the training process too much.

## Quantization Aware Training
Use quantization.keras.quantize_model from tensorflow_model_optimization

Details ...

## Remove BatchNorm and/or Dropout in Valdiaton Pass
How to tf.GradientTape(): https://colab.research.google.com/github/keras-team/keras-io/blob/master/guides/ipynb/writing_a_training_loop_from_scratch.ipynb#scrollTo=W1QwN4lUroMz

If your network takes a significant time to train and validate, it may be advantageous to accelerate validation by removing Dropout and folding BatchNorm. To do it do the following outline:
1. Define initial network/graph
2. Define optimized architecture without Dense and/or BatchNorm
3. Create custom training loop with tf.GradientTape()
4. After training part of epoch is complete (including metric updates) copy weights by layer name from training model to optimized model
5. Pass validation data into optimized model and report results

# Post Training Optimizations
## Weight Pruning
Use Tensorflow Model Optimization to create a sparese model by pruning activations that are near zero.
While this can accelerate inference, be aware that low activations can make a difference.

## Weight Clustering
Compresses model by clustering shared weights to reduce number of unique weight values.


## Tensorflow Tensor-RT
Requires custom build of Tensorflow or an NVIDIA tensorflow container with both TensorRT and Tensorflow Tensor-RT

Features
* Reduce precision to either FP16 or INT8
* Layer and Tensor Fusion
* Reduce memory footprint and improve efficiency
* Optimizes RNNs with dynamic kernels

Guide in Future ...
