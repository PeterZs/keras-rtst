Real-Time Style Transfer with Keras
===================================
This is an attempt at implementing something like [Real-Time Style Transfer](http://arxiv.org/pdf/1603.08155v1.pdf)
with the [Keras](http://keras.io/) framework.

Install
-------
 * `pip install keras-rtst`
 * Download [pre-trained VGG16 weights](https://github.com/awentzonline/keras-vgg-buddy/releases/download/0.0.1/vgg16_weights.h5) You'll need to pass its path as a parameter to the scripts.
 * Training currently only supported on Theano backend, but texturing can be done
 with either.

Usage
-----
After installation you'll find `train-rtst.sh`, `render-rtst.sh` and `rtst.py` on your path.
The shell scripts are just wrappers around `rtst.py` to demonstrate usage and maybe be a little convenient. There's also a script `rtst-download-training-images.sh` that
will download a small batch of images randomly selected from a subset of ImageNet 2012.

Examples
--------
There's an examples folder. Example of an example:

Make a brick texturizer: `./make-example-texturizer.sh bricks0 <path/to/training/images> <path/to/vgg16/weights.h5>`

Differences from the paper
--------------------------
 * This code doesn't use strided convolutions for upsampling as it doesn't seem to be implemented in Keras/Theano.
 * The learning rate starts at 0.1 and decays at a rate of 0.9 every 200 iterations until it reaches 0.001.
 * Also similarly to "Texture Networks" I'm using a really small training set.