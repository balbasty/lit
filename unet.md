U-Net
=====

The breakthrough
----------------

The U-Net ([Ronneberger _et al._, 2015](#ronneberger2015u)) has become the default architecture for 
feed forward neural networks in computer vision. It maps an image (or volume) to another image
of (roughly) the same dimensions and is characterized by the use of an _encoder_ (a series 
of convolutions with downsampling) followed by a _decoder_ (a series of convolutions with 
upsampling) and _skipped connections_ (the input to each encoding layer is concatenated 
with the output of each corresponding decoding layer). Multiple variations of the U-net have since
been designed, with different ways of performing the downsampling and upsampling steps 
(pooling or strided convolutions; linear upsampling, unpooling or transposed convolutions), as
well as an infinity of choices for the number of convolutions per layer and the number of features 
per convolution. Let us first describe the original architecture proposed by Ronneberger _et al._

![U-Net architecture](https://lmb.informatik.uni-freiburg.de/people/ronneber/u-net/u-net-architecture.png
"Architecture of the original U-Net.")

This network uses four downsampling and upsampling operations (and therefore works at five 
different resolutions), with two convolutions per resolution. Downsampling is performed 
using 2x2 max-pooling and upsampling is performed using 2x2 _up-convolutions_ which 
is simply a strided transposed convolution ([Long _et al._, 2015](#long2015fully)). The number of 
features (_i.e._, output channels after each convolution) is doubled afer each downsampling
step and halved after each upsampling step. All convolutions use a 3x3 kernel and are followed by 
a ReLU activation function ([Nair & Hinton, 2010](#nair2010rectified)). Since the application 
of this paper is semantic segmentation (_i.e._, classifying each pixel into _K_ classes), the 
final activation function is a softmax ([Bridle, 1989](#bridle1989training), [1990](#bridle1990probabilistic)).

Ronneberger's U-Net builds on the _fully convolutional network for segmentation_ 
([Long _et al._, 2015](#long2015fully)), which already had most of the elements that made the 
success of U-Nets. This paper is interesting because it reveals the intuition behind the 
success of this architecture. Long _et al._ were inspired by the success of convolutional 
neural networks (CNNs) for image classification, after the AlexNet breakthrough 
([Krizhevsky _et al._, 2012](#krizhevsky2012imagenet)), which made use of convolutions, 
ReLU and max pooling. Long's idea was to train a similar architecture on patches centered about 
each voxel to classify them; semantic segmentation would then be obtained by generating one 
classification per patch. Refinement of the solution was performed using upsampling and 
skipped connections (just like the U-Net). The intuition is that the decoder generates, 
at each resolution, a different prediction, which is more accurate but less resolved at the 
lowest resolution. Prediction is then propagated back to the highest resolution 
by fusing an upsampled version of the low-resolution accurate segmentation and the higher
resolution but less-accurate prediction from the encoder. Up-sampling is performed using 
strided transposed convolutions, which had been introduced in the context of object recognition
the year before ([Sermanet _et al._, 2014](sermanet2014overfeat)). Like many of the early
U-Nets, Long's uses the VGG16 network ([Simonyan & Zisserman, 2015](#simonyan2015very)) 
as a basis for its encoder architecture.

The use of classification network for pixel-wise segmentation had been proposed before
([Ciresan _et al._, 2012](ciresan2012deep)), but it was lacking the decoding aspect of 
modern U-Nets.

Table
-----

| Reference | Levels | Conv/level | Encoder | Decoder | Post | Down | Up | Kernel | Act. | Loss | Augment. | Batch Norm | Dropout | 
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| [Long _et al._, 2015](#long2015fully) | 6 | ? | ? | ? | no | maxpool | transposed | ? | ReLU | CE | no | no | no |
| [Ronneberger _et al._, 2015](#ronneberger2015u) | 5 | 2 | [64, 128, 256, 512, 1024] | sym | no | maxpool | transposed | 3 | ReLU | weighted CE | no | no | no |
| [Badrinarayanan _et al._, 2017](#badrinarayanan2017segnet) | 5 | [2, 2, 3] | [64, 128, 256, 512, 512] | sym | no | maxpool | maxunpool | [3, 3, 1] | ReLU | weighted CE | no | no | no |
| [Kendall _et al._, 2017](#kendall2017bayesian) | 5 | [2, 2, 3] | [64, 128, 256, 512, 512] | sym | no | maxpool | maxunpool | [3, 3, 1] | ReLU | weighted CE | no | no | yes |

References
----------

- <b id="bridle1989training"></b>
  **Training Stochastic Model Recognition Algorithms as Networks can Lead to 
    Maximum Mutual Information Estimation of Parameters** <br />
  John S. Bridle <br />
  NIPS (1989) <br />
  https://proceedings.neurips.cc/paper/1989/hash/0336dcbab05b9d5ad24f4333c7658a0e-Abstract.html

- <b id="bridle1990probabilistic"></b>
  **Probabilistic Interpretation of Feedforward Classification Network Outputs, 
    with Relationships to Statistical Pattern Recognition** <br />
  John S. Bridle <br />
  Neurocomputing (1990) <br />
  https://link.springer.com/chapter/10.1007%2F978-3-642-76153-9_28

- <b id="nair2010rectified"></b>
  **Rectified Linear Units Improve Restricted Boltzmann Machines** <br />
  Vinod Nair, Geoffrey E. Hinton <br />
  ICML (2010) <br />
  https://icml.cc/Conferences/2010/papers/432.pdf

- <b id="krizhevsky2012imagenet"></b>
  **ImageNet Classification with Deep Convolutional Neural Networks** <br />
  Alex Krizhevsky, Ilya Sutskever, Geoffrey E. Hinton <br />
  NIPS (2012) <br />
  https://papers.nips.cc/paper/2012/hash/c399862d3b9d6b76c8436e924a68c45b-Abstract.html

- <b id="ciresan2012deep"></b>
  **Deep Neural Networks Segment Neuronal Membranes in Electron Microscopy Images** <br />
  Dan Ciresan, Alessandro Giusti, Luca Gambardella, Jürgen Schmidhuber <br />
  NIPS (2012) <br />
  https://proceedings.neurips.cc/paper/2012/hash/459a4ddcb586f24efd9395aa7662bc7c-Abstract.html

- <b id="sermanet2014overfeat"></b>
  **OverFeat: Integrated Recognition, Localization and Detection using Convolutional Networks** <br />
  Pierre Sermanet, David Eigen, Xiang Zhang, Michael Mathieu, Rob Fergus, Yann LeCun <br />
  ICLR (2014) <br />
  https://arxiv.org/abs/1312.6229

- <b id="simonyan2015very"></b>
  **Very Deep Convolutional Networks for Large-Scale Image Recognition** <br />
  Karen Simonyan, Andrew Zisserman
  ICLR (2015) / Preprint (2014)
  https://arxiv.org/abs/1409.1556

- <b id="long2015fully"></b>
  **Fully Convolutional Networks for Semantic Segmentation** <br />
  Jonathan Long, Evan Shelhamer, Trevor Darrell <br/>
  CVPR (2015) <br/>
  https://arxiv.org/abs/1411.4038

- <b id="ronneberger2015u"></b>
  **U-Net: Convolutional Networks for Biomedical Image Segmentation** <br />
  Olaf Ronneberger, Philipp Fischer, Thomas Brox <br/>
  MICCAI (2015) <br/>
  https://arxiv.org/abs/1505.04597

- <b id="badrinarayanan2017segnet"></b>
  **SegNet: A Deep Convolutional Encoder-Decoder Architecture for Image Segmentation** <br />
  Vijay Badrinarayanan, Alex Kendall, Roberto Cipolla <br/>
  PAMI (2017) / Preprint (2015) <br/>
  https://arxiv.org/abs/1511.00561
  
- <b id="kendall2017bayesian"></b>
  **Bayesian SegNet: Model Uncertainty in Deep Convolutional Encoder-Decoder Architectures for Scene Understanding** <br />
  Alex Kendall, Vijay Badrinarayanan and Roberto Cipolla <br />
  BMVC (2017) / Preprint (2015)
  https://arxiv.org/abs/1511.02680
