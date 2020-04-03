# Learning-the-inverse-of-a-neural-network
Its easy to classify images of digits to various classes, Can we generate the images back from the classes?
Training the deep learning network to classify images is one of the frequently attempted problems. These images are classified
into various classes using softmax layer. 

Given the data X and learning to classify it to class C can be expressed as P(C|X). How about learning the inverse problem o
given the class (i.e. softmax output) can we generate back a data sample of the class? In other words can we learn P(X|C).

Generating the images (or in general the data) back has been solved by many models like GANs, Autoencoder-decoders and others.
The point to be noted is learning P(C|X) is a relatively easy problem, Can't we make use of P(C|X) in learning p(X|C)? 
The bayes theorem clearly states that P(C|X) and P(X|C) are related by P(X|C) = P(C|X)xP(C)/P(X). Making use of P(C|X) must 
definitely aid in learning of P(X|C). This work is the first attempt in exploring this line of thought. 

Here we work with the basic MNIST dataset. We train a neural network with three fully connected layers to classify the images 
of digits. Let A1, A2 and A3 be three fully connected layers.
Observe the basic representation of Network below: 

X -> A1 -> X1-> A2 -> X2 -> A3 -> X3

X1, X2 and X3 are outputs of the three layers A1, A2 and A3 respectively. We wish to make use of this trained network(P(C|X) 
to learn the inverse of this network.

We train three networks say I1, I2 and I3 with each network having single fully connected layers. We train I3 to input X3 
and output X2, I2 to input X2 and output X1 and I1 to input X1 and ouput X.

This is how we generate the images and learn P(X|C).

This idea is coded on Google Colab using pytorch framework. Any ideas and collaborations to take this idea ahead are welcomed.
