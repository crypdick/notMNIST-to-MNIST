The
[notMNIST dataset](http://yaroslavvb.blogspot.com/2011/09/notmnist-dataset.html)
is a image recognition dataset of font glypyhs for the letters A
through J useful with simple neural networks. It is quite similar to
the classic [MNIST dataset](http://yann.lecun.com/exdb/mnist/) of
handwritten digits 0 through 9.

Unfortunately, the notMNIST data is not provided in the same format as
the MNIST data, so you can't just swap in the notMNIST data files and
run your neural network on it unaltered. This repo solves that problem:
the four *.gz files here have the same number of entries, in the same
data format as the same-named file from the MNIST dataset. But instead
of handwritten digits, the images are letters from A to J (the labels
are still 0 through 9). (These files are posted here with permission
of the original author of the notMNIST data set.)

If you have a neural network that uses MNIST, you should be able to
substitute the data files from this repo and run the program without
making any changes. Note that the notMNIST dataset is harder and less clean than
MNIST. A simple 2 hidden layer net that gets 98% accuracy on MNIST gets
about 93 or 94% accuracy with these notMNIST files.

The notMNIST dataset is much larger than the MNIST set, so the data files here
are a random sample of the notMNIST data. If you want to take a different sample
or a larger sample, you can use the python script in this directory to
process notMNIST yourself.

Instructions:

1) if you already have a MNIST data/ directory, rename it and create a
new one with code like this:

```sh
mv data data.original_mnist
mkdir data
```

2) Download and unpack the notMNIST data. The files are not
particularly large, but unpacking them can take a long time
because there are well over 500,000 individual image files.

```sh
curl -o notMNIST_small.tar.gz http://yaroslavvb.com/upload/notMNIST/notMNIST_small.tar.gz
tar xzf notMNIST_small.tar.gz
```

3) Finally, run this script to convert the data to MNIST files in your
data/ directory and compress them:

```sh
python convert_to_mnist_format.py notMNIST_small 
```

This will create a few .npy archives
