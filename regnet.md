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

- **Adversarial Deformation Regularization for Training Image Registration Neural Networks** <br />
  Yipeng Hu, Eli Gibson, Nooshin Ghavami, Ester Bonmati, Caroline M. Moore, Mark Emberton, Tom Vercauteren, J. Alison Noble, Dean C. Barratt <br />
  MICCAI (2018) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-00928-1_87

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

- **Dual-Stream Pyramid Registration Network** <br />
  Xiaojun Hu, Miao Kang, Weilin Huang, Matthew R. Scott, Roland Wiest, Mauricio Reyes <br />
  MICCAI (2019) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-32245-8_43 <br />
  https://arxiv.org/abs/1909.11966v1

- **Image-and-Spatial Transformer Networks for Structure-Guided Image Registration** <br />
  Matthew C. H. Lee, Ozan Oktay, Andreas Schuh, Michiel Schaap, Ben Glocker <br />
  MICCAI (2019) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-32245-8_38

- **Probabilistic Multilayer Regularization Network for Unsupervised 3D Brain Image Registration** <br />
  Lihao Liu, Xiaowei Hu, Lei Zhu, Pheng-Ann Heng <br />
  MICCAI (2019) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-32245-8_39

- **TopAwaRe: Topology-Aware Registration** <br />
  Rune Kok Nielsen, Sune Darkner, Aasa Feragen <br />
  MICCAI (2019) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-32245-8_41

- **Cooperative Autoencoder for Population-Based Regularization of CNN Image Registration** <br />
  Riddhish Bhalodia, Shireen Y. Elhabian, Ladislav Kavan, Ross T. Whitaker <br />
  MICCAI (2019) <br/>
  https://link.springer.com/chapter/10.1007/978-3-030-32245-8_44

- **Networks for Joint Affine and Non-Parametric Image Registration** <br />
  Zhengyang Shen, Xu Han, Zhenlin Xu, Marc Niethammer <br />
  CVPR (2019) <br />
  https://openaccess.thecvf.com/content_CVPR_2019/html/Shen_Networks_for_Joint_Affine_and_Non-Parametric_Image_Registration_CVPR_2019_paper.html

- **Metric Learning for Image Registration** <br />
  Marc Niethammer, Roland Kwitt, Francois-Xavier Vialard <br />
  CVPR (2019) <br />
  https://openaccess.thecvf.com/content_CVPR_2019/html/Niethammer_Metric_Learning_for_Image_Registration_CVPR_2019_paper.html

- **Arbicon-Net: Arbitrary Continuous Geometric Transformation Networks for Image Registration** <br />
  Jianchun Chen, Lingjing Wang, Xiang Li, Yi Fang <br />
  NeurIPS (2019) <br />
  https://proceedings.neurips.cc/paper_files/paper/2019/hash/56f9f88906aebf4ad985aaec7fa01313-Abstract.html
  
- **Recurrent Registration Neural Networks for Deformable Image Registration** <br />
  Robin Sandkühler, Simon Andermatt, Grzegorz Bauman, Sylvia Nyilas, Christoph Jud, Philippe C. Cattin <br />
  NeurIPS (2019) <br />
  https://proceedings.neurips.cc/paper_files/paper/2019/hash/dd03de08bfdff4d8ab01117276564cc7-Abstract.html

- **Region-specific Diffeomorphic Metric Mapping** <br />
  Zhengyang Shen, Francois-Xavier Vialard, Marc Niethammer <br />
  NeurIPS (2019) <br />
  https://proceedings.neurips.cc/paper_files/paper/2019/hash/291597a100aadd814d197af4f4bab3a7-Abstract.html
  
- **MvMM-RegNet: A New Image Registration Framework Based on Multivariate Mixture Model and Neural Network Estimation** <br />
  Xinzhe Luo, Xiahai Zhuang <br />
  MICCAI (2020) <br/>
  https://link.springer.com/chapter/10.1007/978-3-030-59716-0_15

- **Large Deformation Diffeomorphic Image Registration with Laplacian Pyramid Networks** <br />
  Tony C. W. Mok, Albert C. S. Chung <br />
  MICCAI (2020) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-59716-0_21

- **Adversarial Uni- and Multi-modal Stream Networks for Multimodal Image Registration** <br />
  Zhe Xu, Jie Luo, Jiangpeng Yan, Ritvik Pulya, Xiu Li, William Wells III, Jayender Jagadeesan <br />
  MICCAI (2020) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-59716-0_22

- **DeepFLASH: An Efficient Network for Learning-Based Medical Image Registration** <br />
  Jian Wang, Miaomiao Zhang <br />
  CVPR (2020) <br />
  https://openaccess.thecvf.com/content_CVPR_2020/html/Wang_DeepFLASH_An_Efficient_Network_for_Learning-Based_Medical_Image_Registration_CVPR_2020_paper.html

- **Unsupervised Multi-Modal Image Registration via Geometry Preserving Image-to-Image Translation** <br />
  Moab Arar, Yiftach Ginger, Dov Danon, Amit H. Bermano, Daniel Cohen-Or <br />
  CVPR (2020) <br />
  https://openaccess.thecvf.com/content_CVPR_2020/html/Arar_Unsupervised_Multi-Modal_Image_Registration_via_Geometry_Preserving_Image-to-Image_Translation_CVPR_2020_paper.html

- **Fast Symmetric Diffeomorphic Image Registration with Convolutional Neural Networks** <br />
  Tony C.W. Mok, Albert C.S. Chung <br />
  CVPR (2020) <br />
  https://openaccess.thecvf.com/content_CVPR_2020/html/Mok_Fast_Symmetric_Diffeomorphic_Image_Registration_with_Convolutional_Neural_Networks_CVPR_2020_paper.html

- **CoMIR: Contrastive Multimodal Image Representation for Registration** <br />
  Nicolas Pielawski, Elisabeth Wetzer, Johan Öfverstedt, Jiahao Lu, Carolina Wählby, Joakim Lindblad, Natasa Sladoje <br />
  NeurIPS (2020) <br />
  https://proceedings.neurips.cc/paper_files/paper/2020/hash/d6428eecbe0f7dff83fc607c5044b2b9-Abstract.html
  
- **Medical Image Registration Based on Uncoupled Learning and Accumulative Enhancement** <br/>
  Yucheng Shu, Hao Wang, Bin Xiao, Xiuli Bi, Weisheng Li <br />
  MICCAI (2021) <br/>
  https://link.springer.com/chapter/10.1007/978-3-030-87202-1_1

- **Learning Unsupervised Parameter-Specific Affine Transformation for Medical Images Registration** <br />
  Xu Chen, Yanda Meng, Yitian Zhao, Rachel Williams, Srinivasa R. Vallabhaneni, Yalin Zheng <br />
  MICCAI (2021) <br/>
  https://link.springer.com/chapter/10.1007/978-3-030-87202-1_3

- **Conditional Deformable Image Registration with Convolutional Neural Network** <br />
  Tony C. W. Mok, Albert C. S. Chung <br />
  MICCAI (2021) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-87202-1_4

- **A Deep Discontinuity-Preserving Image Registration Network** <br />
  Xiang Chen, Yan Xia, Nishant Ravikumar, Alejandro F. Frangi <br />
  MICCAI (2021) <br/>
  https://link.springer.com/chapter/10.1007/978-3-030-87202-1_5

- **SAME: Deformable Image Registration Based on Self-supervised Anatomical Embeddings** <br />
  Fengze Liu, Ke Yan, Adam P. Harrison, Dazhou Guo, Le Lu, Alan L. Yuille, Lingyun Huang, Guotong Xie, Jing Xiao, Xianghua Ye & Dakai Jin  <br />
  MICCAI (2021) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-87202-1_9

- **Learning Dual Transformer Network for Diffeomorphic Registration** <br />
  Yungeng Zhang, Yuru Pei, Hongbin Zha <br />
  MICCAI (2021) <br/>
  https://link.springer.com/chapter/10.1007/978-3-030-87202-1_13

- **Multi-scale Neural ODEs for 3D Medical Image Registration** <br />
  Junshen Xu, Eric Z. Chen, Xiao Chen, Terrence Chen, Shanhui Sun  <br />
  MICCAI (2021) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-87202-1_21

- **A review of deep learning-based three-dimensional medical image registration methods** <br />
  Haonan Xiao, Xinzhi Teng, Chenyang Liu, Tian Li, Ge Ren, Ruijie Yang, Dinggang Shen, Jing Cai <br />
  Quant Imaging Med Surg (2021) <br />
  https://qims.amegroups.com/article/view/75304/html

- **Learning image registration without images** <br />
  Malte Hoffmann, Benjamin Billot, Juan Eugenio Iglesias, Bruce Fischl, Adrian V. Dalca <br />
  ISBI (2021) <br />
  https://arxiv.org/abs/2004.10282

- **HyperMorph: Amortized Hyperparameter Learning for Image Registration** <br />
  Andrew Hoopes, Malte Hoffmann, Bruce Fischl, John Guttag, Adrian V. Dalca <br />
  IPMI (2021) <br />
  https://arxiv.org/abs/2101.01035

- **Learning-Based Image Registration With Meta-Regularization** <br />
  Ebrahim Al Safadi, Xubo Song <br />
  CVPR (2021) <br />
  https://openaccess.thecvf.com/content/CVPR2021/html/Safadi_Learning-Based_Image_Registration_With_Meta-Regularization_CVPR_2021_paper.html

- **Deep Learning Based Geometric Registration for Medical Images: How Accurate Can We Get Without Visual Features?** <br />
  Lasse Hansen, Mattias P. Heinrich <br />
  IPMI (2021) <br />
  https://link.springer.com/book/10.1007/978-3-030-78191-0

- **Modeling the Probabilistic Distribution of Unlabeled Data forOne-shot Medical Image Segmentation**<br />
  Yuhang Ding, Xin Yu, Yi Yang <br />
  AAAI (2021) <br />
  https://arxiv.org/abs/2102.02033

- **A review of deep learning-based deformable medical image registration** <br />
  Jing Zou, Bingchen Gao, Youyi Song, Jing Qin <br />
  Front Oncol (2022) <br />
  https://www.frontiersin.org/articles/10.3389/fonc.2022.1047215/full
  
- **Dual-stream pyramid registration network** <br />
  Miao Kang, Xiaojun Hu, Weilin Huang, Matthew R. Scott, Mauricio Reyes <br />
  Medical Image Analysis (2022) <br />
  https://www.sciencedirect.com/science/article/abs/pii/S1361841522000317 <br />
  https://arxiv.org/abs/1909.11966v2

- **SynthMorph: Learning Contrast-Invariant Registration Without Acquired Images** <br />
  Malte Hoffmann, Benjamin Billot, Douglas N. Greve, Juan Eugenio Iglesias, Bruce Fischl, Adrian V. Dalca <br />
  IEEE TMI (2022) <br />
  https://ieeexplore.ieee.org/document/9552865 <br />
  https://arxiv.org/abs/2004.10282

- **Dual-Branch Squeeze-Fusion-Excitation Module for Cross-Modality Registration of Cardiac SPECT and CT** <br />
  Xiongchao Chen, Bo Zhou, Huidong Xie, Xueqi Guo, Jiazhen Zhang, Albert J. Sinusas, John A. Onofrey, Chi Liu <br />
  MICCAI (2022) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_5

- **Embedding Gradient-Based Optimization in Image Registration Networks** <br />
  Huaqi Qiu, Kerstin Hammernik, Chen Qin, Chen Chen, Daniel Rueckert <br />
  MICCAI (2022) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_6

- **ContraReg: Contrastive Learning of Multi-modality Unsupervised Deformable Image Registration** <br />
  Neel Dey, Jo Schlemper, Seyed Sadegh Mohseni Salehi, Bo Zhou, Guido Gerig, Michal Sofka <br />
  MICCAI (2022) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_7

- **Swin-VoxelMorph: A Symmetric Unsupervised Learning Model for Deformable Medical Image Registration Using Swin Transformer** <br />
  Yongpei Zhu, Shi Lu <br />
  MICCAI (2022) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_8

- **Non-iterative Coarse-to-Fine Registration Based on Single-Pass Deep Cumulative Learning** <br />
  Mingyuan Meng, Lei Bi, Dagan Feng, Jinman Kim <br />
  MICCAI (2022) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_9

- **Deformer: Towards Displacement Field Learning for Unsupervised Medical Image Registration** <br/>
  Jiashun Chen, Donghuan Lu, Yu Zhang, Dong Wei, Munan Ning, Xinyu Shi, Zhe Xu, Yefeng Zheng <br />
  MICCAI (2022) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_14

- **Unsupervised Deep Non-rigid Alignment by Low-Rank Loss and Multi-input Attention** <br />
  Takanori Asanomi, Kazuya Nishimura, Heon Song, Junya Hayashida, Hiroyuki Sekiguchi, Takayuki Yagi, Imari Sato, Ryoma Bise <br />
  MICCAI (2022) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_18

- **XMorpher: Full Transformer for Deformable Medical Image Registration via Cross Attention** <br />
  Jiacheng Shi, Yuting He, Youyong Kong, Jean-Louis Coatrieux, Huazhong Shu, Guanyu Yang, Shuo Li <br />
  MICCAI (2022) <br/>
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_21

- **RFNet: Unsupervised Network for Mutually Reinforcing Multi-Modal Image Registration and Fusion** <br />
  Han Xu, Jiayi Ma, Jiteng Yuan, Zhuliang Le, Wei Liu <br />
  CVPR (2022) <br />
  https://openaccess.thecvf.com/content/CVPR2022/html/Xu_RFNet_Unsupervised_Network_for_Mutually_Reinforcing_Multi-Modal_Image_Registration_and_CVPR_2022_paper.html

- **NODEO: A Neural Ordinary Differential Equation Based Optimization Framework for Deformable Image Registration** <br />
  Yifan Wu, Tom Z. Jiahao, Jiancong Wang, Paul A. Yushkevich, M. Ani Hsieh, James C. Gee <br />
  CVPR (2022) <br />
  https://openaccess.thecvf.com/content/CVPR2022/html/Wu_NODEO_A_Neural_Ordinary_Differential_Equation_Based_Optimization_Framework_for_CVPR_2022_paper.html

- **Topology-Preserving Shape Reconstruction and Registration via Neural Diffeomorphic Flow** <br />
  Shanlin Sun, Kun Han, Deying Kong, Hao Tang, Xiangyi Yan, Xiaohui Xie <br />
  CVPR (2022) <br />
  https://openaccess.thecvf.com/content/CVPR2022/html/Sun_Topology-Preserving_Shape_Reconstruction_and_Registration_via_Neural_Diffeomorphic_Flow_CVPR_2022_paper.html

- **Geometric Deep Learning for Unsupervised Registration of Diffusion Magnetic Resonance Images** <br />
  Jose J. Bouza, Chun-Hao Yang, Baba C. Vemuri <br />
  IPMI (2023) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-34048-2_43

- **MetaMorph: Learning Metamorphic Image Transformation with Appearance Changes** <br />
  Jian Wang, Jiarui Xing, Jason Druzgal, William M. Wells III, Miaomiao Zhang <br />
  IPMI (2023) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-34048-2_44

- **NeurEPDiff: Neural Operators to Predict Geodesics in Deformation Spaces** <br />
  Nian Wu, Miaomiao Zhang <br />
  IPMI (2023) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-34048-2_45

- **POLAFFINI: Efficient Feature-Based Polyaffine Initialization for Improved Non-linear Image Registration** <br />
  Antoine Legouhy, Ross Callaghan, Hojjat Azadbakht, Hui Zhang <br />
  IPMI (2023) <br/>
  https://link.springer.com/chapter/10.1007/978-3-031-34048-2_47

### Affine 

- **Deep Global Registration** <br />
  Christopher Choy, Wei Dong, Vladlen Koltun <br />
  CVPR (2020) <br />
  https://openaccess.thecvf.com/content_CVPR_2020/html/Choy_Deep_Global_Registration_CVPR_2020_paper.html

- **Affine Medical Image Registration With Coarse-To-Fine Vision Transformer** <br />
  Tony C. W. Mok, Albert C. S. Chung <br />
  CVPR (2022) <br />
  https://openaccess.thecvf.com/content/CVPR2022/html/Mok_Affine_Medical_Image_Registration_With_Coarse-To-Fine_Vision_Transformer_CVPR_2022_paper.html

### Within subject

- **Highly Accurate and Memory Efficient Unsupervised Learning-Based Discrete CT Registration Using 2.5D Displacement Search** <br />
  Mattias P. Heinrich, Lasse Hansen <br />
  MICCAI (2020) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-59716-0_19

- **Longitudinal Image Registration with Temporal-Order and Subject-Specificity Discrimination** <br />
  Qianye Yang, Yunguan Fu, Francesco Giganti, Nooshin Ghavami, Qingchao Chen, J. Alison Noble, Tom Vercauteren, Dean Barratt, Yipeng Hu <br />
  MICCAI (2020) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-59716-0_24

- **Cross-Modal Attention for MRI and Ultrasound Volume Registration** <br />
  Xinrui Song, Hengtao Guo, Xuanang Xu, Hanqing Chao, Sheng Xu, Baris Turkbey, Bradford J. Wood, Ge Wang, Pingkun Yan <br />
  MICCAI (2021) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-87202-1_7

- **Unsupervised Deformable Image Registration with Absent Correspondences in Pre-operative and Post-recurrence Brain Tumor MRI Scans** <br />
  Tony C. W. Mok, Albert C. S. Chung (2022) <br />
  MICCAI (2022) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_3

- **Learning Iterative Optimisation for Deformable Image Registration of Lung CT with Recurrent Convolutional Networks** <br />
  Fenja Falta, Lasse Hansen, Mattias P. Heinrich <br />
  MICCAI (2022) <br/>
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_29

- **CASHformer: Cognition Aware SHape Transformer for Longitudinal Analysis** <br/>
  Ignacio Sarasua, Sebastian Pölsterl, Christian Wachinger <br />
  MICCAI (2022) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-16431-6_5

- **Non-rigid Medical Image Registration using Physics-informed Neural Networks** <br />
  Zhe Min, Zachary M. C. Baum, Shaheer U. Saeed, Mark Emberton, Dean C. Barratt, Zeike A. Taylor, Yipeng Hu <br />
  IPMI (2023) <br/>
  https://link.springer.com/chapter/10.1007/978-3-031-34048-2_46

### Slice to volume // 2D/3D

- **Multiview 2D/3D Rigid Registration via a Point-Of-Interest Network for Tracking and Triangulation** <br />
  Haofu Liao, Wei-An Lin, Jiarui Zhang, Jingdan Zhang, Jiebo Luo, S. Kevin Zhou <br />
  CVPR (2019) <br />
  https://openaccess.thecvf.com/content_CVPR_2019/html/Liao_Multiview_2D3D_Rigid_Registration_via_a_Point-Of-Interest_Network_for_Tracking_CVPR_2019_paper.html

- **Generalizing Spatial Transformers to Projective Geometry with Applications to 2D/3D Registration** <br />
  Cong Gao, Xingtong Liu, Wenhao Gu, Benjamin Killeen, Mehran Armand, Russell Taylor, Mathias Unberath <br />
  MICCAI (2020) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-59716-0_32

- **Fluid Registration Between Lung CT and Stationary Chest Tomosynthesis Images** <br/>
  Lin Tian, Connor Puett, Peirong Liu, Zhengyang Shen, Stephen R. Aylward, Yueh Z. Lee, Marc Niethammer  <br />
  MICCAI (2020) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-59716-0_30

- **End-to-end Ultrasound Frame to Volume Registration** <br />
  Hengtao Guo, Xuanang Xu, Sheng Xu, Bradford J. Wood, Pingkun Yan <br />
  MICCAI (2021) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-87202-1_6

- **Weakly Supervised Registration of Prostate MRI and Histopathology Images** <br />
  Wei Shao, Indrani Bhattacharya, Simon J. C. Soerensen, Christian A. Kunder, Jeffrey B. Wang, Richard E. Fan, Pejman Ghanouni, James D. Brooks, Geoffrey A. Sonn, Mirabela Rusu <br />
  MICCAI (2021) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-87202-1_10

- **SVoRT: Iterative Transformer for Slice-to-Volume Registration in Fetal Brain MRI** <br/>
  Junshen Xu, Daniel Moyer, P. Ellen Grant, Polina Golland, Juan Eugenio Iglesias, Elfar Adalsteinsson <br />
  MICCAI (2022) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_1

- **End-to-End Multi-Slice-to-Volume Concurrent Registration and Multimodal Generation** <br />
  Amaury Leroy, Marvin Lerousseau, Théophraste Henry, Alexandre Cafaro, Nikos Paragios, Vincent Grégoire, Eric Deutsch <br />
  MICCAI (2022) <br/>
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_15

- **LiftReg: Limited Angle 2D/3D Deformable Registration** <br />
  Lin Tian, Yueh Z. Lee, Raúl San José Estépar, Marc Niethammer <br />
  MICCAI (2022) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_20

- **Global Multi-modal 2D/3D Registration via Local Descriptors Learning** <br />
  Viktoria Markova, Matteo Ronchetti, Wolfgang Wein, Oliver Zettinig, Raphael Prevost <br />
  MICCAI (2022) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_26

### Groupwise

- **Pair-Wise and Group-Wise Deformation Consistency in Deep Registration Network** <br />
  Dongdong Gu, Xiaohuan Cao, Shanshan Ma, Lei Chen, Guocai Liu, Dinggang Shen & Zhong Xue  <br />
  MICCAI (2020) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-59716-0_17

- **DSR: Direct Simultaneous Registration for Multiple 3D Images** <br />
  Zhehua Mao, Liang Zhao, Shoudong Huang, Yiting Fan, Alex P. W. Lee <br />
  MICCAI (2022) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-16446-0_10

- **Aladdin: Joint Atlas Building and Diffeomorphic Registration Learning With Pairwise Alignment** <br />
  Zhipeng Ding, Marc Niethammer <br />
  CVPR (2022) <br />
  https://openaccess.thecvf.com/content/CVPR2022/html/Ding_Aladdin_Joint_Atlas_Building_and_Diffeomorphic_Registration_Learning_With_Pairwise_CVPR_2022_paper.html

- **BInGo: Bayesian Intrinsic Groupwise Registration via Explicit Hierarchical Disentanglement** <br />
  Xin Wang, Xinzhe Luo, Xiahai Zhuang <br />
  IPMI (2023) <br />
  https://link.springer.com/chapter/10.1007/978-3-031-34048-2_25

- **Learning Probabilistic Piecewise Rigid Atlases of Model Organisms via Generative Deep Networks** <br />
  Amin Nejatbakhsh, Neel Dey, Vivek Venkatachalam, Eviatar Yemini, Liam Paninski, Erdem Varol <br />
  IPMI (2023) <br/>
  https://link.springer.com/chapter/10.1007/978-3-031-34048-2_26

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


### Misc

- **On the Applicability of Registration Uncertainty** <br />
  Jie Luo, Alireza Sedghi, Karteek Popuri, Dana Cobzas, Miaomiao Zhang, Frank Preiswerk, Matthew Toews, Alexandra Golby, Masashi Sugiyama, William M. Wells III, Sarah Frisken <br />
  MICCAI (2019) <br />
  https://link.springer.com/chapter/10.1007/978-3-030-32245-8_46

- **Anatomical Data Augmentation via Fluid-Based Image Registration** <br />
  Zhengyang Shen, Zhenlin Xu, Sahin Olut, Marc Niethammer <br />
  MICCAI (2020) <br/>
  https://link.springer.com/chapter/10.1007/978-3-030-59716-0_31

- **A Variational Bayesian Method for Similarity Learning in Non-Rigid Image Registration** <br />
  Daniel Grzech, Mohammad Farid Azampour, Ben Glocker, Julia Schnabel, Nassir Navab, Bernhard Kainz, Loïc Le Folgoc <br />
  CVPR (2022) <br />
  https://openaccess.thecvf.com/content/CVPR2022/html/Grzech_A_Variational_Bayesian_Method_for_Similarity_Learning_in_Non-Rigid_Image_CVPR_2022_paper.html
