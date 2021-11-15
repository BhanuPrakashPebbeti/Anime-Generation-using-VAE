# Overview of VAE Structure 
A variational autoencoder (VAE) provides a probabilistic manner for describing an observation in latent space. Thus, rather than building an encoder which outputs a single value to describe each latent state attribute, we'll formulate our encoder to describe a probability distribution for each latent attribute.

Rather than directly training it for the latent space as in a standard autoencoder, the encoder model of a VAE will be trained to output parameters describing a distribution for each dimension in the latent space.

<img src="https://github.com/BhanuPrakashPebbeti/Anime-Generation-using-VAE/blob/main/VAE-architecture_images/vae.png">

## Reparameterization
When training the model, we need to be able to calculate the gradients which are required for backpropagation which cannot be done in this case because of random sampling process. We could use a method called "reparameterization trick" which suggests that we randomly sample ε from a unit Gaussian, and then shift the randomly sampled ε by the latent distribution's mean μ and scale it by the latent distribution's variance σ.

<img src="https://github.com/BhanuPrakashPebbeti/Anime-Generation-using-VAE/blob/main/VAE-architecture_images/reparameterization.png">

Using this reparameterization trick we are able to backpropagate through our network and optimize the parameters.

<img src="https://github.com/BhanuPrakashPebbeti/Anime-Generation-using-VAE/blob/main/VAE-architecture_images/gradient_flow.png">

## Image reconstruction during VAE training

<img src="https://github.com/BhanuPrakashPebbeti/Anime-Generation-using-VAE/blob/main/image_reconstructions/reconstructions-1.png">

## Variational autoencoders as a generative model
By sampling from the latent space which we assumed to follows a unit Gaussian distribution, we can use our trained decoder network to generate new data similar to the samples which were observed during training. 

<img src="https://github.com/BhanuPrakashPebbeti/Anime-Generation-using-VAE/blob/main/generations/__results___10_57.png">

## Model optimizing using training
The animation below visualizes the images generated by the decoder network of a variational autoencoder during training for a particular random sample sampled from unit Gaussian distribution.

![training_gif](https://github.com/BhanuPrakashPebbeti/Anime-Generation-using-VAE/blob/main/training_results/training.gif)
