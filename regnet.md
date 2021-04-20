Registration Nets
=================

Spatial Transformers
--------------------

Instead of focusing first on optimization-based image registration and then on how 
this problem ended-up being tackled with deep learning, I will directly start 
with the concept of spatial transformers in machine learning. Spatial transformers 
do not necessarily aim to register to image -- that is spatially transform one so 
that it lookds like another -- but merely to build network that are **invariant** 
to spatial transformations. For example, a number should be correctly classified 
enven if it is rotated by 45 degrees. 

One of the first such papers was by Hinton ([1981a](#hinton1981parallel), [1981b](#hinton1981shape)) (of course).
It is a pretty theoretical paper that assumes that a first layer of features are extracted,
and that these features are similar to that of the primary visual cortex: oriented lines.
A transformer unit (that can perform rotations, translations and zooms) is then applied 
to all features of the same object simulateneously. This maps the extracted "primary 
features" to another set of "primary features". This transformation is optimised until 
the object is optimally recognised. This representation assumes that primary features 
are "hardware". The transformer unit acts as a secondary layer.

Later, a lot of effort has been placed into building networks that extract features 
that are invariant to some transformations, which sounded like an easier task than learning
to transform features. The success of convolutional neural networks (partly) stems from 
the translation invariance of convolutional features, and building feature extractors 
that have other types of invariance is an active line of research 
([Sohn & Lee (2012)](#sohn2012learning), [Bruna & Mallat (2013)](#bruna2013invariant), 
[Gens & Domingos (2014)](#gens2014deep), [Kanazawa et _al._ (2014)](#kanazawa2014locally)).
Some of these methods design filters with built-in invariance properties while others
average the loss, or its gradients, across transformed inputs to force the networks 
to _learn_ invariant representations. Augmentation can be seen as a natural descendant of 
the latter, where stochasticity is applied to the samples _and_ transforms (whereas 
the original invariant networks used stochastic samples but applied all possible 
transformations at each optimization step).

References
----------

### Invariant features & Spatial transformers

- <b id="hinton1981parallel"></b>
  **A parallel computation that assigns canonical object-based frames of reference** <br/>
  Geoffrey E. Hinton <br/>
  IJCAI (1981) <br/>
  https://www.cs.toronto.edu/~hinton/absps/object-based81.pdf
 
- <b id="hinton1981shape"></b>
  **Shape representation in parallel systems** <br/>
  Geoffrey E. Hinton <br/>
  IJCAI (1981) <br/>
  http://www.cs.toronto.edu/~hinton/absps/shape81.pdf
  
- <b id="zemel1989traffic"></b>
  **TRAFFIC: Recognizing Objects Using Hierarchical Reference Frame Transformations** <br />
  Richard S. Zemel, Michael C. Mozer, Geoffrey E. Hinton <br />
  NeurIPS (1989) <br />
  https://papers.nips.cc/paper/1989/hash/f340f1b1f65b6df5b5e3f94d95b11daf-Abstract.html

- <b id="simard1992efficient"></b> 
  **An efficient algorithm for learning invariance in adaptive classifiers** <br />
  P. Simard, Y. Le Cun, J. Denker, B. Victorri <br />
  ICPR (1992) <br />
  https://www.computer.org/csdl/pds/api/csdl/proceedings/download-article/12OmNzwHvcI/pdf

- <b id="ranzato2007unsupervised"></b>
  **Unsupervised Learning of Invariant Feature Hierarchies with Applications to Object Recognition** <br />
  Marc'Aurelio Ranzato, Fu Jie Huang, Y. Lan Boureau, Yann LeCun <br />
  CVPR (2007) <br />
  https://www.cs.toronto.edu/~ranzato/publications/ranzato-cvpr07.pdf

- <b id="memisevic2007unsupervised"></b>
  **Unsupervised Learning of Image Transformations** <br />
  Roland Memisevic, Geoffrey Hinton <br />
  CVPR (2007) <br />
  https://www.cs.toronto.edu/~hinton/absps/cvpr07.pdf

- <b id="memisevic2010learning"></b>
  **Learning to Represent Spatial Transformations with Factored Higher-Order Boltzmann Machines** <br />
  Roland Memisevic, Geoffrey Hinton <br />
  Neural Computation (2010) <br />
  http://www.cs.toronto.edu/~hinton/absps/rolandNC.pdf

- <b id="hinton2011transforming"></b>
  **Transforming Auto-encoders** <br />
  G. E. Hinton, A. Krizhevsky, S. D. Wang <br />
  ICANN (2011) <br />
  http://www.cs.toronto.edu/~bonner/courses/2020s/csc2547/papers/capsules/transforming-autoencoders,-hinton,-icann-2011.pdf

- <b id="sohn2012learning"></b>
  **Learning Invariant Representations with Local Transformations** <br/>
  Kihyuk Sohn, Honglak Lee <br />
  ICML (2012) <br />
  https://arxiv.org/abs/1206.6418

- <b id="bruna2013invariant"></b>
  **Invariant Scattering Convolution Networks** <br/>
  Joan Bruna, Stephane Mallat  <br/>
  IEEE PAMI (2013) <br/>
  https://arxiv.org/abs/1203.1513

- <b id="gens2014deep"></b>
  **Deep Symmetry Networks** <br/>
  Robert Gens, Pedro Domingos <br/>
  NeurIPS (2014) <br/>
  https://papers.nips.cc/paper/2014/hash/f9be311e65d81a9ad8150a60844bb94c-Abstract.html

- <b id="kanazawa2014locally"></b>
  **Locally Scale-Invariant Convolutional Neural Networks** <br/>
  Angjoo Kanazawa, Abhishek Sharma, David Jacobs <br/>
  NeurIPS: Deep Learning and Representation Learning Workshop (2014) <br/>
  https://arxiv.org/abs/1412.5104

- <b id="jaderberg2015spatial"></b>
  **Spatial Transformer Networks** <br />
  Max Jaderberg, Karen Simonyan, Andrew Zisserman, Koray Kavukcuoglu
  NeurIPS (2015) <br />
  https://arxiv.org/abs/1506.02025

### Registration networks
