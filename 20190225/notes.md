## Review of literature on encrypted data, LDSJC Feb 2019

We focussed our review mainly on the paper by Dowlin et al (see references below).

# Introduction

A has trained model M. 

B has data D and wants ouput of M on D but does not want to share it with A.

Homomorphic encryption allows B to encrypt its data D and send it to A. A can then perform inference using model M on the encrypted data 
and sent the result back to B. B can decrypt the result.

A does not have access to the key so cannot decrypt D.



# What is homomorphic encryption?

A type of encryption that allows computation on encrypted data, generating an encrypted result which, when decrypted, matches 
the result of the operations as if they had been performed on the unencrypted data.
[Wikipedia link](https://en.wikipedia.org/wiki/Homomorphic_encryption)

In mathematics, a homomorphismus is a structure-preserving transformation.

Advances in fully homomorphic encryption allow us to perform a limited number of operations on the encrypted data. Furthermore, the
operations are usually limited to additions and multiplications. This means that the classifier, and in particular neural networks,
need to be adapted accordingly (in particular activation functions such as ReLU etc).

Dowlin et al achieve this by approximating the activation functions and pooling layers in terms of polynomial functions.

Another problem is the fact that the encryption operates on polynomial rings with (integer?) coefficients whereas the neural network
operates on floating point numbers. To circumvent this problem (details in the paper), Downlin et need to introduce scaling factors 
with very large absolute values. Using some mathematical trick (Chinese Remainder Theorem), they can still perform an efficient en- 
and decoding.

# Results

Dowlin et al train a CNN with two convolutional and two fully-connected layers and achieve 99% accuracy on MNIST. 
The drawback is that a single predicton takes 570 seconds to compute.


# Questions

How about training on encrypted data? There are some references that discuss this but we did not go into the detail. Most of the
papers I am aware focus on relatively simple ML algorithms such as Nearest Neighbours or Naive Bayes.


- CryptoNets: Applying Neural Networks to Encrypted Data with High Throughput and Accuracy, Dowlin et al - https://www.microsoft.com/en-us/research/publication/cryptonets-applying-neural-networks-to-encrypted-data-with-high-throughput-and-accuracy/
- CryptoDL: Deep Neural Networks over Encrypted Data, Ehsan Hesamifard, Hassan Takabi, Mehdi Ghasemi - https://arxiv.org/abs/1711.05189
- ML Confidential: Machine Learning on Encrypted Data, Graepel et al - https://www.microsoft.com/en-us/research/publication/ml-confidential-machine-learning-on-encrypted-data-2/


