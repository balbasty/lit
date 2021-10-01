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

### Optical flows

- **DeepFlow: Large displacement optical flow with deep matching** <br />
  Philippe Weinzaepfel, Jérôme Revaud, Zaid Harchaoui, Cordelia Schmid <br />
  ICCV (2013) <br />
  https://hal.inria.fr/hal-00873592/document

- **FlowNet: Learning Optical Flow with Convolutional Networks** <br />
  Philipp Fischer, Alexey Dosovitskiy, Eddy Ilg, Philip Häusser, Caner Hazırbaş, 
  Vladimir Golkov, Patrick van der Smagt, Daniel Cremers, Thomas Brox <br />
  ICCV (2015) <br />
  https://arxiv.org/abs/1504.06852

### Registration networks

- **A CNN Regression Approach for Real-Time 2D/3D Registration** <br />
  Shun Miao, Z Jane Wang, Rui Liao <br />
  IEEE TMI (2016) <br />
  https://arxiv.org/abs/1507.07505

- **Fast Predictive Image Registration** <br />
  Xiao Yang, Roland Kwitt, Marc Niethammer <br />
  DLMIA/LABELS (2016) <br />
  https://arxiv.org/abs/1607.02504

- **Robust non-rigid registration through agentbased action learning** <br />
  Julian Krebs, Tommaso Mansi, Hervé Delingette, Li Zhang, Florin Ghesu, 
  Shun Miao, Andreas Maier, Nicholas Ayache, Rui Liao, Ali Kamen <br />
  MICCAI (2017) <br />
  https://hal.inria.fr/hal-01569447/document

- **SVF-Net: Learning Deformable Image Registration Using Shape Matching** <br />
  Marc-Michel Rohé, Manasi Datar, Tobias Heimann, Maxime Sermesant, Xavier Pennec <br />
  MICCAI (2017) <br />
  https://hal.inria.fr/hal-01557417/document

- **Nonrigid Image Registration Using Multi-scale 3D Convolutional Neural Networks** <br />
  Hessam Sokooti, Bob de Vos, Floris Berendsen, Boudewijn P.F. Lelieveldt, Ivana Isgum, Marius Staring <br />
  MICCAI (2017) <br />
  https://elastix.lumc.nl/marius/downloads/2017_c_MICCAIa.pdf

- **End-to-End Unsupervised Deformable Image Registration with a Convolutional Neural Network** <br />
  Bob D. de Vos, Floris F. Berendsen, Max A. Viergever, Marius Staring, Ivana Išgum <br/>
  DLMIA/ML-CDS @ MICCAI (2017) <br />
  https://arxiv.org/abs/1704.06065
 
- **Quicksilver: Fast Predictive Image Registration - a Deep Learning Approach** <br />
  Xiao Yang, Roland Kwitt, Martin Styner, Marc Niethammer <br />
  NeuroImage (2017) <br />
  https://arxiv.org/abs/1703.10908

- **Non-rigid image registration using fully convolutional networks with deep self-supervision** <br />
  Hongming Li, Yong Fan <br />
  ISBI (2018) / Preprint (2017) <br />
  https://arxiv.org/abs/1709.00799
  
- **Unsupervised Probabilistic Deformation Modeling for Robust Diffeomorphic Registration** <br />
  Julian Krebs, Tommaso Mansi, Boris Mailhé, Nicholas Ayache, Hervé Delingette <br />
  DLMIA/ML-CDS @ MICCAI (2018) <br />
  https://arxiv.org/abs/1804.07172
  
- **An Unsupervised Learning Model for Deformable Medical Image Registration** <br />
  Guha Balakrishnan, Amy Zhao, Mert R. Sabuncu, John Guttag, Adrian V. Dalca <br />
  CVPR (2018) <br />
  https://arxiv.org/abs/1802.02604

- **Unsupervised Learning for Fast Probabilistic Diffeomorphic Registration** <br />
  Adrian V. Dalca, Guha Balakrishnan, John Guttag, Mert R. Sabuncu <br />
  MICCAI (2018) <br />
  https://arxiv.org/abs/1805.04605

- **Weakly-Supervised Convolutional Neural Networks for Multimodal Image Registration** <br />
  Yipeng Hu, Marc Modat, Eli Gibson, Wenqi Li, Nooshin Ghavami, Ester Bonmati, Guotai Wang, 
  Steven Bandula, Caroline M. Moore, Mark Emberton, Sébastien Ourselin, J. Alison Noble, Dean C. Barratt, Tom Vercauteren <br />
  Medical Image Analysis (2018) <br />
  https://arxiv.org/abs/1807.03361

- **BIRNet: Brain Image Registration Using Dual-Supervised Fully Convolutional Networks** <br />
  Jingfan Fan, Xiaohuan Cao, Pew-Thian Yap, Dinggang Shen <br />
  Medical Image Analysis (2019) <br />
  https://arxiv.org/abs/1802.04692

- **VoxelMorph: A Learning Framework for Deformable Medical Image Registration** <br />
  Guha Balakrishnan, Amy Zhao, Mert R. Sabuncu, John Guttag, Adrian V. Dalca <br />
  IEEE TMI (2019) <br />
  https://arxiv.org/abs/1809.05231

- **Unsupervised Learning of Probabilistic Diffeomorphic Registration for Images and Surfaces** <br />
  Adrian V. Dalca, Guha Balakrishnan, John Guttag, Mert R. Sabuncu <br />
  Medical Image Analysis (2019) <br />
  https://arxiv.org/abs/1903.03545

- **Learning a Probabilistic Model for Diffeomorphic Registration** <br />
  Julian Krebs, Herve Delingette, Boris Mailhe, Nicholas Ayache, Tommaso Mansi <br />
  IEEE TMI (2019) <br/>
  https://arxiv.org/abs/1812.07460

- **3D Convolutional Neural Networks Image Registration Based on Efficient Supervised Learning from Artificial Deformations**
  Hessam Sokooti, Bob de Vos, Floris Berendsen, Mohsen Ghafoorian, Sahar Yousefi, 
  Boudewijn P.F. Lelieveldt, Ivana Isgum, Marius Staring <br />
  Preprint (2019) <br />
  https://arxiv.org/abs/1908.10235
  
- **Learning image registration without images** <br />
  Malte Hoffmann, Benjamin Billot, Juan Eugenio Iglesias, Bruce Fischl, Adrian V. Dalca <br />
  ISBI (2021) <br />
  https://arxiv.org/abs/2004.10282

- **HyperMorph: Amortized Hyperparameter Learning for Image Registration** <br />
  Andrew Hoopes, Malte Hoffmann, Bruce Fischl, John Guttag, Adrian V. Dalca <br />
  IPMI (2021) <br />
  https://arxiv.org/abs/2101.01035

- **Modeling the Probabilistic Distribution of Unlabeled Data forOne-shot Medical Image Segmentation**<br />
  Yuhang Ding, Xin Yu, Yi Yang <br />
  AAAI (2021) <br />
  https://arxiv.org/abs/2102.02033


### Joint Segmentation and Registration networks

- **DeepAtlas: Joint Semi-Supervised Learning of Image Registration and Segmentation** <br />
  Zhenlin Xu, Marc Niethammer <br />
  MICCAI (2019) <br />
  https://arxiv.org/abs/1904.08465v2

- **U-ReSNet: Ultimate Coupling of Registration and Segmentation with Deep Nets** <br />
  Théo Estienne, Maria Vakalopoulou, Stergios Christodoulidis, Enzo Battistella, Marvin Lerousseau, Alexandre Carré, 
  Guillaume Klausner, Roger Sun, Charlotte Robert, Stavroula Mougiakakou, Nikos Paragios, Eric Deutsch <br />
  MICCAI (2019) <br />
  https://hal.archives-ouvertes.fr/hal-02365899v2

- **Conditional Segmentation in Lieu of Image Registration**<br />
  Yipeng Hu, Eli Gibson, Dean C. Barratt, Mark Emberton, J. Alison Noble, Tom Vercauteren <br />
  MICCAI (2019) <br />
  https://arxiv.org/abs/1907.00438

- **Joint Vessel Segmentation and Deformable Registration on Multi-Modal Retinal Images Based on Style Transfer**<br />
  Junkang Zhang, Cheolhong An, Ji Dai, Manuel Amador, Dirk-Uwe Bartsch, Shyamanga Borooah, William R. Freeman, Truong Q. Nguyen <br />
  ICIP (2019) <br />
  http://cwc.ucsd.edu/sites/cwc.ucsd.edu/files/01-08802932.pdf

- **JSSR: A Joint Synthesis, Segmentation, and Registration System for 3D Multi-Modal Image Alignment of Large-scale Pathological CT Scans** <br />
  Fengze Liu, Jinzheng Cai, Yuankai Huo, Chi-Tung Cheng, Ashwin Raju, Dakai Jin, Jing Xiao, Alan Yuille, Le Lu, ChienHung Liao, Adam P Harrison <br />
  ECCV (2020) <br />
  https://arxiv.org/abs/2005.12209

- **A Cross-Stitch Architecture for Joint Registration and Segmentation in Adaptive Radiotherapy** <br />
  Laurens Beljaards, Mohamed S. Elmahdy, Fons Verbeek, Marius Staring <br />
  PMLR (2020) <br />
  http://proceedings.mlr.press/v121/beljaards20a.html

- **ASRNet: Adversarial Segmentation and Registration Networks for Multispectral Fundus Images** <br />
  Yanyun Jiang, Yuanjie Zheng, Xiaodan Sui, Wanzhen Jiao, Yunlong He, Weikuan Jia <br />
  Computer Systems Science & Engineering (2020) <br />
  https://www.techscience.com/csse/v36n3/41265
  
- **Atlas-ISTN: Joint Segmentation, Registration and Atlas Construction with Image-and-Spatial Transformer Networks** <br />
  Matthew Sinclair, Andreas Schuh, Karl Hahn, Kersten Petersen, Ying Bai, James Batten, Michiel Schaap, Ben Glocker <br />
  Preprint (2020) <br />
  https://arxiv.org/abs/2012.10533
  
- **Deep Learning-Based Concurrent Brain Registration and Tumor Segmentation** <br />
  Théo Estienne, Marvin Lerousseau, Maria Vakalopoulou, Emilie Alvarez Andres, Enzo Battistella, Alexandre Carré, 
  Siddhartha Chandra, Stergios Christodoulidis, Mihir Sahasrabudhe, Roger Sun, Charlotte Robert, Hugues Talbot, Nikos Paragios and Eric Deutsch <br />
  Front. Comput. Neurosci. (2020) <br />
  https://www.frontiersin.org/articles/10.3389/fncom.2020.00017/full
  
- **Learning unbiased group-wise registration (LUGR) and joint segmentation: evaluation on longitudinal diffusion MRI** <br />
  Bo Li, Wiro J. Niessen, Stefan Klein, M. Arfan Ikram, Meike W. Vernooij, Esther E. Bron <br />
  SPIE Medical Imaging (2021) <br />
  https://www.spiedigitallibrary.org/conference-proceedings-of-spie/11596/115960L/Learning-unbiased-group-wise-registration-LUGR-and-joint-segmentation/10.1117/12.2580928.short?SSO=1
  
- **Joint deep learning framework for image registration and segmentation of late gadolinium enhanced MRI and cine cardiac MRI** <br />
  Roshan Reddy Upendra, Richard Simon, Cristian A. Linte <br />
  SPIE Medical Imaging (2021) <br />
  https://www.spiedigitallibrary.org/conference-proceedings-of-spie/11598/115980F/Joint-deep-learning-framework-for-image-registration-and-segmentation-of/10.1117/12.2581386.short
