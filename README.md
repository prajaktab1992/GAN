# GAN (Generative adversarial networks)

Generative adversarial networks (GANs) are an exciting recent innovation in machine learning. GANs are generative models: they create new data instances that resemble your training data.Discriminative models discriminate between different kinds of data instances.
### Generator and discriminator
![image](https://user-images.githubusercontent.com/52082561/110197018-99657e80-7e6e-11eb-84a4-fcd8450c8de7.png)


### Architecture
![image](https://user-images.githubusercontent.com/52082561/110197033-bef28800-7e6e-11eb-941c-e26966393c91.png)



Models that predict the next word in a sequence are typically generative models (usually much simpler than GANs) because they can assign a probability to a sequence of words.

More formally, given a set of data instances X and a set of labels Y:
  Generative models capture the joint probability p(X, Y), or just p(X) if there are no labels.
  Discriminative models capture the conditional probability p(Y | X).


The discriminator loss penalizes the discriminator for misclassifying a real instance as fake or a fake instance as real.
The generator part of a GAN learns to create fake data by incorporating feedback from the discriminator. It learns to make the discriminator classify its output as real.

Many machine learning systems look at some kind of complicated input (say, an image) and produce a simple output (a label like, "cat"). By contrast, the goal of a generative model is something like the opposite: take a small piece of input—perhaps a few random numbers—and produce a complex output, like an image of a realistic-looking face.

The big insights that defines a GAN is to set up this modeling problem as a kind of contest. This is where the "adversarial" part of the name comes from. The key idea is to build not one, but two competing networks: a generator and a discriminator. The generator tries to create random synthetic outputs (for instance, images of faces), while the discriminator tries to tell these apart from real outputs (say, a database of celebrities). The hope is that as the two networks face off, they'll both get better and better—with the end result being a generator network that produces realistic outputs.

### In short
A perfect GAN will create fake samples whose distribution is indistinguishable from that of the real samples!
The generator's loss value decreases when the discriminator classifies fake samples as real (bad for discriminator, but good for generator).



#### References:
https://poloclub.github.io/ganlab/

### Random input/noise:
In its most basic form, a GAN takes random noise as its input. The generator then transforms this noise into a meaningful output. By introducing noise, we can get the GAN to produce a wide variety of data, sampling from different places in the target distribution.
Experiments suggest that the distribution of the noise doesn't matter much, so we can choose something that's easy to sample from, like a uniform distribution. 
For convenience the space from which the noise is sampled is usually of smaller dimension than the dimensionality of the output space.

We keep the generator constant during the discriminator training phase. As discriminator training tries to figure out how to distinguish real data from fake, it has to learn how to recognize the generator's flaws. That's a different problem for a thoroughly trained generator than it is for an untrained generator that produces random output.
Similarly, we keep the discriminator constant during the generator training phase. Otherwise the generator would be trying to hit a moving target and might never converge.

### Convergence :
As the generator improves with training, the discriminator performance gets worse because the discriminator can't easily tell the difference between real and fake. If the generator succeeds perfectly, then the discriminator has a 50% accuracy. In effect, the discriminator flips a coin to make its prediction.

This progression poses a problem for convergence of the GAN as a whole: the discriminator feedback gets less meaningful over time. If the GAN continues training past the point when the discriminator is giving completely random feedback, then the generator starts to train on junk feedback, and its own quality may collapse.

### Loss :
GANs try to replicate a probability distribution. They should therefore use loss functions that reflect the distance between the distribution of the data generated by the GAN and the distribution of the real data.

#### minimax loss: The loss function used in the paper that introduced GANs.
#### Wasserstein loss: The default loss function for TF-GAN Estimators. First described in a 2017 paper.

![image](https://user-images.githubusercontent.com/52082561/110196889-9322d280-7e6d-11eb-85e6-7b8369328e42.png)

###### Wasserstein GANs are less vulnerable to getting stuck than minimax-based GANs, and avoid problems with vanishing gradients. The earth mover distance also has the advantage of being a true metric: a measure of distance in a space of probability distributions. Cross-entropy is not a metric in this sense.





















