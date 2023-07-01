# variational-autoencoder

A <a href="https://pyro.ai/examples/vae.html">Pyro/Pytorch</a> implementation of probabilistic variational autoencoders for MNIST.

IN order to be able to use the decoder of an autoencoder for generative purpose, we have to be sure that the latent space is regular enough. One possible solution to obtain such regularity is to introduce explicit regularisation during the training process. Thus, a variational autoencoder can be defined as being an autoencoder whose training is regularised to avoid overfitting and ensure that the latent space has good properties that enable generative process.

Just as a standard autoencoder, a variational autoencoder is an architecture composed of both an encoder and a decoder and that is trained to minimise the reconstruction error between the encoded-decoded data and the initial data. However, in order to introduce some regularisation of the latent space, we proceed to a slight modification of the encoding-decoding process: instead of encoding an input as a single point, we encode it as a distribution over the latent space. The model is then trained as follows:

- first, the input is encoded as distribution over the latent space
- second, a point from the latent space is sampled from that distribution
- third, the sampled point is decoded and the reconstruction error can be computed
- finally, the reconstruction error is backpropagated through the network

<img src="vae-introductory-notebook/vae.png">

This repository represents a generative model which utilizes VAE impleneted with Pyro deep probabilistic language to regenrate the MNIST images samples pulled from a distribution over the latent space and then compare the extracted features and generated images with the grand truth.

<img src="results/pyro/reconstruction_9.png">
<img src="results/pyro/reconstruction_8.png">
<img src="results/pyro/reconstruction_7.png">
<img src="results/pyro/reconstruction_6.png">
<img src="results/pyro/reconstruction_5.png">
<img src="results/pyro/reconstruction_4.png">

<img src="vae_results/VAE_embedding.png">


# Usage and Requirements

This repository has been tested on the following environemt:

```
python == 3.10.11
pyro == 1.8.4
pytorch == 2.0.0
scikit-learn == 1.2.2
pandas == 2.0.1
numpy == 1.24.3
matplotlib == 3.7.1
seaborn == 0.12.2
graphviz == 0.20.1

```

- Clone the repository in your local machine

- If you seek to use a virtual environment and pip package manager, create and activate your virtual env, and install packages running the following:
```
python3.10.11 -m venv .pyroenv
source pyroenv/bin/activate
pip install -r requirements.txt
```

- If you seek to use conda environment and conda package manager, create  your conda env and install packages running the following in terminal:
```
conda env create -f environment.yml
```
