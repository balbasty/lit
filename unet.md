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

Challenge success
-----------------

U-Nets have quickly become the backbone to most leading methods in image (especially biomedial image)
segmentation challenges. In this section, I go through a selection of challenges and look at 
the architectures used by the leading methods (when they use a relatively vanilla U-Net as 
a backbone). The challenges studied here are:

- **BRATS** (Brain Tumor Segmentation Challenge): this challenge aims to segment tumours from 
  multimodal magnetic resonance images (MRI) into four classes (enhancing tumor, tumor core, 
  whole tumor and non-tumor). It has been held alongside the MICCAI conference every year 
  since 2012. <br/>
  * https://www.med.upenn.edu/cbica/brats2020/
  * https://www.cbica.upenn.edu/BraTS20/lboardValidation.html
  
- **MRBrainS** (MR Brain Segmentation Challenge): this challenge aims to segment relatively 
  normal multimodal MRIs (some have white matter hyper intensities) into either 4 or 11 
  anatomical classes. It has been held alongside the MICCAI conference in 2013 (in the 
  pre U-Net era) and 2018.
  * https://mrbrains18.isi.uu.nl

- **MSD** (Medical Segmentation Decathlon): this challenge aims to apply a single 
  architecture to 10 difference medical image segmentation tasks. It was held alongside the 
  MICCAI conference in 2018.
  * http://medicaldecathlon.com

- **RVC** (Robust Vision Challenge): this challenge contains multiple computer vision tasks,
  one of which is semantic segmentation. It was held alongside the CVPR conference in 2018.
  * http://www.robustvision.net

### BRATS

Since BRATS has been running continuously since 2012, the sudden rise of deep learning 
can be easily detected. Here are the number and proportion of entries that use 
deep learning (or convolutional networks, U-nets, etc) per year:

| Year.    | 2012 | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 |
| -------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | 
| N(DL)    |    0 |    0 |    4 |    5 |    9 |   41 |   55 |   56 | 
| N(total) |   10 |   10 |    8 |   12 |   18 |   53 |   58 |   58 | 
| %        |    0 |    0 |   50 |   42 |   50 |   77 |   95 |   97 | 

The post-AlexNet era starts to show up in 2014, with half the entries using 
CNNs (including one by Y Bengio), although they use patch-wise classifiers similar 
to those in [Ciresan _et al._ (2012)](ciresan2012deep), without a decoder. The first 
U-Net-like architectures appear in 2016, inspired by their success in computer 
vision. That year, [Long _et al._ (2015)](#long2015fully) (FCNN), 
[Ronneberger _et al._ (2015)](#ronneberger2015u) (U-Net),
[Kendall _et al._ (2017)](#kendall2017bayesian) (SegNet) and 
[Kamnitsas _et al._ (2017)](#kamnitsas2017efficient) (DeepMedic)
are widely cited. The impact of the ML field on the medical imaging field can also be 
felt by the use of preprints, as SegNet and DeepMedic had not been published yet but were 
already cited. Year 2017 saw a surge of entries, with all top 3 entries using some flavour of 
CNNs. The question is not "which class of methods wil win" anymore, but 
"how to best train your U-Net". After that, litteraly all entries use deep convolutional networks.
Interestingly, in 2018 [Isensee _et al._ (2018)](isensee2018no) got second place 
with their NoNewNet, which argues that finding new architectures is not necessary 
for segmentation tasks anymore, and that all that matters is to properly train 
U-Nets for each task. This strategy got them first place at the Medical Segmentation Decathlon
that same year ([Isensee _et al._, 2020](#isensee2020nnu)).

Here's a survey of parameters used by the leading entries:

| Reference | Levels | Conv/level | Encoder | Decoder | Post | Down | Up | Kernel | Act. | Loss | Augment. | Batch Norm | Dropout | Residual | Notes |
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| [Jiang _et al._, 2019](#jiang2019brats) | 4 | [2, 4, 4, 8, 2, 2, 2] | [16, 32, 64, 128] | sym | no | stride | transposed | 3 | ReLU | Dice | affine intensity transform, flip | group | yes | yes | cascade |
| [Myronenko _et al._, 2018](#myronenko2018brats) | 4 | [2, 4, 4, 8, 2, 2, 2] | [32, 64, 128, 256] | sym | no | stride | linear | 3 | ReLU | Dice | affine intensity transform, flip | group | yes | yes | dual-branch + vae |
| [Isensee _et al._, 2018](#isensee2018brats) | 5 | 2 | [30, 60, 120, 240, 480] | sym | no | maxpool | linear | 3 | Leaky ReLU | Dice | rotation, scaling, elastic, flip, gamma | instance | no | no | |
| [Kamnitsas _et al._, 2017](#kamnitsas2017brats) - UNet | 4 | 2 | [16, 32, 64, 128] | sym | no | stride/maxpool | nearest | 3 | ReLU | CE | yes | yes | no | yes/no | skip: add/cat |
| [Kamnitsas _et al._, 2017](#kamnitsas2017brats) - FCN | 5 | 2 | [16, 32, 64, 128, 128] | no | no | maxpool | nearest | 3 | ReLU | CE | yes | yes | no | no | |
| [Kamnitsas _et al._, 2017](#kamnitsas2017brats) - DeepMedic | 2 | 8 + 3 | [30, 40, 50, 150] | no | no | linear | linear | 3 | ReLU | CE | yes | yes | no | yes | patch-wise residual FCN |

The leading entry from 2019 ([Jiang _et al._, 2019](#jiang2019brats)) actually uses two U-Nets in cascade, this first of which is entered 
in the table. The second U-Net has a similar architecture but with two decoding branches. The output of the first
network predicts the whole tumor class while the outputs of the second network predict the two sub-components
(enhancing tumor and tumor core). 

This first U-Net has exactly the same architecture as the winning entry 
from the previous year ([Myronenko _et al._, 2018](#myronenko2018brats)), although this one predicted all
three classes from the same branch, and had an additional regularisation branch whose purpose 
was to reconstruct the input image through a variational auto-encoder.

- <b id="jiang2019brats"></b>
  **Two-Stage Cascaded U-Net: 1st Place Solution to BraTS Challenge 2019 Segmentation Task** <br />
  Zeyu Jiang, Changxing Ding, Minfeng Liu, Dacheng Tao <br />
  BRATS (2019) 1st place <br />
  https://link.springer.com/chapter/10.1007/978-3-030-46640-4_22

- <b id="myronenko2018brats"></b>
  **3D MRI brain tumor segmentation using autoencoder regularization** <br />
  Andriy Myronenko <br />
  BRATS (2018) 1st place <br />
  https://arxiv.org/abs/1810.11654

- <b id="isensee2018brats"></b>
  **No new-net** <br />
  Fabian Isensee, Philipp Kickingereder, Wolfgang Wick, Martin Bendszus, Klaus H. Maier-Hein <br />
  BRATS (2018) 2nd place <br />
  https://arxiv.org/abs/1809.10483

- <b id="kamnitsas2017brats"></b>
  **Ensembles of Multiple Models and Architectures for Robust Brain Tumour Segmentation** <br />
  Konstantinos Kamnitsas, Wenjia Bai, Enzo Ferrante, Steven McDonagh, Matthew Sinclair, Nick Pawlowski, Martin Rajchl, Matthew Lee, Bernhard Kainz, Daniel Rueckert, Ben Glocker <br />
  BRATS (2017) 1st place <br />
  https://arxiv.org/abs/1711.01468


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
  Karen Simonyan, Andrew Zisserman <br />
  ICLR (2015) / Preprint (2014) <br />
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
  BMVC (2017) / Preprint (2015) <br />
  https://arxiv.org/abs/1511.02680

- <b id="kamnitsas2017efficient"></b>
  **Efficient Multi-Scale 3D CNN with Fully Connected CRF for Accurate Brain Lesion Segmentation** <br />
  Konstantinos Kamnitsas, Christian Ledig, Virginia F.J. Newcombe, Joanna P. Simpson, Andrew D. Kane, David K. Menon, Daniel Rueckert, Ben Glocker <br />
  Medical Image Analysis (2017) / Preprint (2016) <br />
  https://arxiv.org/abs/1603.05959

- <b id="isensee2018no"></b>
  **No new-net** <br />
  Fabian Isensee, Philipp Kickingereder, Wolfgang Wick, Martin Bendszus, Klaus H. Maier-Hein <br />
  BrainLes (2018) <br />
  https://arxiv.org/abs/1809.10483
  
- <b id="isensee2020nnu"></b>
  **nnU-Net: Self-adapting Framework for U-Net-Based Medical Image Segmentation** <br />
  Fabian Isensee, Jens Petersen, Andre Klein, David Zimmerer, Paul F. Jaeger, Simon Kohl, Jakob Wasserthal, Gregor Koehler, Tobias Norajitra, Sebastian Wirkert, Klaus H. Maier-Hein <br />
  Nature Methods (2020) / Preprint (2018) <br />
  https://arxiv.org/abs/1809.10486
