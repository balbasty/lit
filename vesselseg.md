# Vasculature segmentation (and/or other tree-like objects)

## TOC
- [**Segmentation**](#Segmentation)
- [**Topology**](#Topology)
- [**Constrained Constructive Optimization**](#Constrained-Constructive-Optimization)
- [**Flow**](#Flow)
- [**Axons**](#Axons)

## Segmentation

- **TriSAM: Tri-Plane SAM for zero-shot cortical blood vessel segmentation in VEM images** <br />
  ![micro](https://img.shields.io/badge/micro-green)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  J Wan, ..., D Wei <br />
  _ArXiv_ (2024) <br />
  https://arxiv.org/abs/2401.13961

- **Synthetic optical coherence tomography angiographs for detailed retinal vessel segmentation without human annotations** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![synth](https://img.shields.io/badge/synth-yellow)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  L Kreitner, ..., D Rueckert, MJ Menten <br />
  _IEEE TMI_ (2024) <br />
  https://doi.org/10.1109/TMI.2024.3354408 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{kreitner2024synthetic,
      title={Synthetic optical coherence tomography angiographs for detailed retinal vessel segmentation without human annotations},
      author={Kreitner, Linus and Paetzold, Johannes C and Rauch, Nikolaus and Chen, Chen and Hagag, Ahmed M and Fayed, Alaa E and Sivaprasad, Sobha and Rausch, Sebastian and Weichsel, Julian and Menze, Bjoern H and others},
      journal={IEEE Transactions on Medical Imaging},
      year={2024},
      publisher={IEEE}
    }
    ```
  </details>
  
- **Benchmarking the CoW with the TopCoW Challenge: Topology-Aware Anatomical Segmentation of the Circle of Willis for CTA and MRA** <br />
  ![angio](https://img.shields.io/badge/angio-cyan)
  ![topo](https://img.shields.io/badge/topo-pink)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  K Yang, ..., BH Menze <br />
  _ArXiv_ (2023) <br />
  https://doi.org/10.48550/arXiv.2312.17670 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{yang2023benchmarking,
      title={Benchmarking the CoW with the TopCoW Challenge: Topology-Aware Anatomical Segmentation of the Circle of Willis for CTA and MRA},
      author={Yang, Kaiyuan and Musio, Fabio and Ma, Yihui and Juchler, Norman and Paetzold, Johannes C and Al-Maskari, Rami and H{\"o}her, Luciano and Li, Hongwei Bran and Hamamci, Ibrahim Ethem and Sekuboyina, Anjany and others},
      journal={arXiv preprint arXiv:2312.17670},
      year={2023}
    }
    ```
  </details>
  
- **Rapid and fully automated blood vasculature analysis in 3D light-sheet image volumes of different organs** <br />
  ![micro](https://img.shields.io/badge/micro-green)
  ![frangi](https://img.shields.io/badge/frangi-red) <br />
  P Spangenberg, ..., A Mosig <br />
  _Cell Rep Met_ (2023) <br />
  https://doi.org/10.1016/j.crmeth.2023.100436

- **tUbe net: a generalisable deep learning tool for 3D vessel segmentation** <br />
  ![deep](https://img.shields.io/badge/deep-black) <br />
  _bioRxiv_ (2023) <br />
  N Holroyd, ..., S Walker-Samuel <br />
  https://doi.org/10.1101/2023.07.24.550334
  
- **Blood Vessel Segmentation from Low-Contrast and Wide-Field Optical Microscopic Images of Cranial Window by Attention-Gate-Based Network** <br />
  ![micro](https://img.shields.io/badge/micro-green)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  Y Wu, ..., K Mori <br />
  _CVPR_ (2022) <br />
  https://doi.org/10.1109/CVPRW56347.2022.00203

- **Volumetric characterization of microvasculature in ex vivo human brain samples by serial sectioning optical coherence tomography** <br />
  J Yang, ..., H Wang <br />
  ![micro](https://img.shields.io/badge/micro-green)
  ![frangi](https://img.shields.io/badge/frangi-red) <br />
  _IEEE TBE__ (2022) <br />
  https://doi.org/10.1109/TBME.2022.3175072 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{yang2022volumetric,
      title={Volumetric characterization of microvasculature in ex vivo human brain samples by serial sectioning optical coherence tomography},
      author={Yang, Jiarui and Chang, Shuaibin and Chen, Ichun Anderson and Kura, Sreekanth and Rosen, Grace A and Saltiel, Nicole A and Huber, Bertrand R and Varadarajan, Divya and Balbastre, Yael and Magnain, Caroline and others},
      journal={IEEE Transactions on Biomedical Engineering},
      volume={69},
      number={12},
      pages={3645--3656},
      year={2022},
      publisher={IEEE}
    }
    ```
  </details>

- **Physiology-based simulation of the retinal vasculature enables annotation-free segmentation of OCT angiographs** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![synth](https://img.shields.io/badge/synth-yellow)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  MJ Menten, ..., D Rueckert <br />
  _MICCAI_ (2022) <br />
  https://doi.org/10.1007/978-3-031-16452-1_32 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{menten2022physiology,
      title={Physiology-based simulation of the retinal vasculature enables annotation-free segmentation of oct angiographs},
      author={Menten, Martin J and Paetzold, Johannes C and Dima, Alina and Menze, Bjoern H and Knier, Benjamin and Rueckert, Daniel},
      booktitle={International Conference on Medical Image Computing and Computer-Assisted Intervention},
      pages={330--340},
      year={2022},
      organization={Springer}
    }
    ```
  </details>

- **Cross-Domain Depth Estimation Network for 3D Vessel Reconstruction in OCT Angiography** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  S Yu, ..., Y Zhao <br />
  _MICCAI_ (2021) <br />
  https://doi.org/10.1007/978-3-030-87237-3_2
  
- **Hierarchical imaging and computational analysis of three-dimensional vascular network architecture in the entire postnatal and adult mouse brain** <br />
  ![micro](https://img.shields.io/badge/micro-green)
  ![morpho](https://img.shields.io/badge/morpho-purple) <br />
  T Wälchli, ..., M Stampanoni  <br />
  _Nature Protocols_ (2021) <br />
  https://doi.org/10.1038/s41596-021-00587-1 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{walchli2021hierarchical,
      title={Hierarchical imaging and computational analysis of three-dimensional vascular network architecture in the entire postnatal and adult mouse brain},
      author={W{\"a}lchli, Thomas and Bisschop, Jeroen and Miettinen, Arttu and Ulmann-Schuler, Alexandra and Hinterm{\"u}ller, Christoph and Meyer, Eric P and Krucker, Thomas and W{\"a}lchli, Regula and Monnier, Philippe P and Carmeliet, Peter and others},
      journal={Nature protocols},
      volume={16},
      number={10},
      pages={4564--4610},
      year={2021},
      publisher={Nature Publishing Group UK London}
    }
    ```
  </details>

- **Segmentation-Less, Automated, Vascular Vectorization** <br />
  ![micro](https://img.shields.io/badge/micro-green)
  ![filter](https://img.shields.io/badge/filter-red) <br />
  SA Mihelic, ..., AK Dunn <br />
  _PLoS Comp Bio_ (2021) <br />
  https://doi.org/10.1371/journal.pcbi.1009451 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{mihelic2021segmentation,
      title={Segmentation-less, automated, vascular vectorization},
      author={Mihelic, Samuel A and Sikora, William A and Hassan, Ahmed M and Williamson, Michael R and Jones, Theresa A and Dunn, Andrew K},
      journal={PLoS computational biology},
      volume={17},
      number={10},
      pages={e1009451},
      year={2021},
      publisher={Public Library of Science San Francisco, CA USA}
    }
    ```
  </details>
  
- **Machine learning analysis of whole mouse brain vasculature** <br />
  ![micro](https://img.shields.io/badge/micro-green)
  ![synth](https://img.shields.io/badge/synth-yellow)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  MI Todorov, ..., BH Menze, A Ertürk  <br />
  _Nature Methods_ (2020) <br />
  https://doi.org/10.1038/s41592-020-0792-1 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{todorov2020machine,
      title={Machine learning analysis of whole mouse brain vasculature},
      author={Todorov, Mihail Ivilinov and Paetzold, Johannes Christian and Schoppe, Oliver and Tetteh, Giles and Shit, Suprosanna and Efremov, Velizar and Todorov-V{\"o}lgyi, Katalin and D{\"u}ring, Marco and Dichgans, Martin and Piraud, Marie and others},
      journal={Nature methods},
      volume={17},
      number={4},
      pages={442--449},
      year={2020},
      publisher={Nature Publishing Group US New York}
    }
    ```
  </details>

- **DeepVesselNet: Vessel Segmentation, Centerline Prediction, and Bifurcation Detection in 3-D Angiographic Volumes** <br />
  ![angio](https://img.shields.io/badge/angio-cyan)
  ![synth](https://img.shields.io/badge/synth-yellow)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  Tetteh G, ..., BH Menze <br />
  _Front. Neuroisci._ (2020) <br />
  https://doi.org/10.3389/fnins.2020.592352 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{tetteh2020deepvesselnet,
      title={Deepvesselnet: Vessel segmentation, centerline prediction, and bifurcation detection in 3-d angiographic volumes},
      author={Tetteh, Giles and Efremov, Velizar and Forkert, Nils D and Schneider, Matthias and Kirschke, Jan and Weber, Bruno and Zimmer, Claus and Piraud, Marie and Menze, Bj{\"o}rn H},
      journal={Frontiers in Neuroscience},
      volume={14},
      pages={1285},
      year={2020},
      publisher={Frontiers}
    }
    ```
  </details>
  
- **Anatomical Modeling of Brain Vasculature in Two-Photon Microscopy by Generalizable Deep Learning** <br />
  ![micro](https://img.shields.io/badge/micro-green)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  W Tahir, ..., L Tian <br />
  _BMEF_ (2020) <br />
  https://doi.org/10.34133/2020/8620932

- **A Distance-Based Loss for Smooth and Continuous Skin Layer Segmentation in Optoacoustic Images**  <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  S Gerl, ..., BH Menze <br />
  _MICCAI_ (2020) <br />
  https://doi.org/10.1007/978-3-030-59725-2_30

- **Image Projection Network: 3D to 2D Image Segmentation in OCTA Images** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  M Li, ..., S, Li <br />
  _IEEE TMI_ (2020) <br />
  https://doi.org/10.1109/TMI.2020.2992244

- **Variational intensity cross channel encoder for unsupervised vessel segmentation on OCT angiography** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  Y Liu, ..., JL Prince <br />
  _SPIE Medical Imaging: Image Processing_ (2020) <br />
  https://doi.org/10.1117/12.2549967

- **CS-Net: Channel and Spatial Attention Network for Curvilinear Structure Segmentation** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  L Mou, ..., J Liu <br />
  _MICCAI_ (2019) <br />
  https://doi.org/10.1007/978-3-030-32239-7_80
  
- **Transfer learning from synthetic data reduces need for labels to segment brain vasculature and neural pathways in 3d** <br />
  ![micro](https://img.shields.io/badge/micro-green)
  ![synth](https://img.shields.io/badge/synth-yellow)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  JC Paetzold, ..., BH Menze <br />
  _MIDL_ (2019) <br />
  https://openreview.net/forum?id=BJe02gRiY4
  
- **Learning to Segment 3D Linear Structures Using Only 2D Annotations** <br />
  ![angio](https://img.shields.io/badge/angio-cyan)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  M Koziński, ..., P Fua  <br />
  _MICCAI_ (2018) <br />
  https://doi.org/10.1007/978-3-030-00934-2_32 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{kozinski2018learning,
      title={Learning to segment 3D linear structures using only 2D annotations},
      author={Kozi{\'n}ski, Mateusz and Mosinska, Agata and Salzmann, Mathieu and Fua, Pascal},
      booktitle={Medical Image Computing and Computer Assisted Intervention--MICCAI 2018: 21st International Conference, Granada, Spain, September 16-20, 2018, Proceedings, Part II 11},
      pages={283--291},
      year={2018},
      organization={Springer}
    }
    ```
  </details>

- **Blood vessel segmentation algorithms—review of methods, datasets and evaluation metrics** <br />
  ![review](https://img.shields.io/badge/review-blue) <br />
  S Moccia, ..., LS Mattos <br />
  _CMPM_ (2018) <br />
  https://doi.org/10.1016/j.cmpb.2018.02.001

- **Retinal blood vessels semantic segmentation method based on modified U-Net** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  L Luo, D Chen, D Xue <br />
  _CCDC_ (2018) <br />
  https://doi.org/10.1109/CCDC.2018.8407435

- **Automatic Location of Blood Vessel Bifurcations in Digital Eye Fundus Images** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  T Chaichana, ..., A Nagar <br />
  _AISC_ (2017) <br />
  https://doi.org/10.1007/978-981-10-3325-4_33 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{chaichana2017automatic,
      title={Automatic location of blood vessel bifurcations in digital eye fundus images},
      author={Chaichana, Thanapong and Sun, Zhonghua and Barrett-Baxendale, Mark and Nagar, Atulya},
      booktitle={Proceedings of Sixth International Conference on Soft Computing for Problem Solving: SocProS 2016, Volume 2},
      pages={332--342},
      year={2017},
      organization={Springer}
    }
    ```
  </details>

- **Deep-FExt: Deep Feature Extraction for Vessel Segmentation and Centerline Prediction** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  G Tetteh, ..., BH Menze <br />
  _MLMI_ (2017) <br />
  https://doi.org/10.1007/978-3-319-67389-9_40 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{tetteh2017deep,
      title={Deep-FExt: Deep feature extraction for vessel segmentation and centerline prediction},
      author={Tetteh, Giles and Rempfler, Markus and Zimmer, Claus and Menze, Bjoern H},
      booktitle={Machine Learning in Medical Imaging: 8th International Workshop, MLMI 2017, Held in Conjunction with MICCAI 2017, Quebec City, QC, Canada, September 10, 2017, Proceedings 8},
      pages={344--352},
      year={2017},
      organization={Springer}
    }
    ```
  </details>
  
- **Cerebral vessels segmentation for light-sheet microscopy image using convolutional neural networks** <br />
  ![micro](https://img.shields.io/badge/micro-green)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  C Hu, ..., J Tian <br />
  _SPIE Medical Imaging_ (2017) <br />
  https://doi.org/10.1117/12.2254714

- **Blood vessel characterization using virtual 3d models and convolutional neural networks in fluorescence microscopy** <br />
  ![micro](https://img.shields.io/badge/micro-green)
  ![synth](https://img.shields.io/badge/synth-yellow)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  A Chowdhury, ..., A Santamaria-Pang <br />
  _IEEE ISBI_ (2017) <br />
  https://doi.org/10.1109/ISBI.2017.7950599

- **Vascular Segmentation in TOF MRA Images of the Brain Using a Deep Convolutional Neural Network** <br />
  ![micro](https://img.shields.io/badge/angio-cyan)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  R Phellan, ..., ND Forkert <br />
  _LABELS_ (2017) <br />
  https://doi.org/10.1007/978-3-319-67534-3_5 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{phellan2017vascular,
      title={Vascular segmentation in TOF MRA images of the brain using a deep convolutional neural network},
      author={Phellan, Renzo and Peixinho, Alan and Falc{\~a}o, Alexandre and Forkert, Nils D},
      booktitle={Intravascular Imaging and Computer Assisted Stenting, and Large-Scale Annotation of Biomedical Data and Expert Label Synthesis: 6th Joint International Workshops, CVII-STENT 2017 and Second International Workshop, LABELS 2017, Held in Conjunction with MICCAI 2017, Qu{\'e}bec City, QC, Canada, September 10--14, 2017, Proceedings 2},
      pages={39--46},
      year={2017},
      organization={Springer}
    }
    ```
  </details>
  
- **Comparison of vessel enhancement algorithms applied to time-of-flight MRA images for cerebrovascular segmentation** <br />
  ![micro](https://img.shields.io/badge/angio-cyan)
  ![frangi](https://img.shields.io/badge/frangi-red) <br />
  R Phellan, ND Forkert <br />
  _Med Phys_ (2017) <br />
  https://doi.org/10.1002/mp.12560 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{phellan2017comparison,
      title={Comparison of vessel enhancement algorithms applied to time-of-flight MRA images for cerebrovascular segmentation},
      author={Phellan, Renzo and Forkert, Nils D},
      journal={Medical physics},
      volume={44},
      number={11},
      pages={5901--5915},
      year={2017},
      publisher={Wiley Online Library}
    }
    ```
  </details>
  
- **Deep Retinal Image Understanding** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  KK Maninis, ..., L Van Gool <br />
  _MICCAI_ (2016) <br />
  https://doi.org/10.1007/978-3-319-46723-8_17 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{maninis2016deep,
      title={Deep retinal image understanding},
      author={Maninis, Kevis-Kokitsi and Pont-Tuset, Jordi and Arbel{\'a}ez, Pablo and Van Gool, Luc},
      booktitle={Medical Image Computing and Computer-Assisted Intervention--MICCAI 2016: 19th International Conference, Athens, Greece, October 17-21, 2016, Proceedings, Part II 19},
      pages={140--148},
      year={2016},
      organization={Springer}
    }
    ```
  </details>

- **Segmenting retinal blood vessels with deep neural networks** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  P Liskowski, K Krawiec <br />
  _IEEE TMI_ (2016) <br />
  https://doi.org/10.1109/TMI.2016.2546227
  
- **Retinal vessel segmentation via deep learning network and fully-connected conditional random fields** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  H Fu, ..., J Liu <br />
  _IEEE ISBI_ (2016) <br />
  https://doi.org/10.1109/ISBI.2016.7493362 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{fu2016retinal,
      title={Retinal vessel segmentation via deep learning network and fully-connected conditional random fields},
      author={Fu, Huazhu and Xu, Yanwu and Wong, Damon Wing Kee and Liu, Jiang},
      booktitle={2016 IEEE 13th international symposium on biomedical imaging (ISBI)},
      pages={698--701},
      year={2016},
      organization={IEEE}
    }
    ```
  </details>

- **Deep vessel tracking: A generalized probabilistic approach via deep learning** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  A Wu, ..., DJ Mollura <br />
  _IEEE ISBI_ (2016) <br />
  https://doi.org/10.1109/ISBI.2016.7493520 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{wu2016deep,
      title={Deep vessel tracking: A generalized probabilistic approach via deep learning},
      author={Wu, Aaron and Xu, Ziyue and Gao, Mingchen and Buty, Mario and Mollura, Daniel J},
      booktitle={2016 IEEE 13th International Symposium on Biomedical Imaging (ISBI)},
      pages={1363--1367},
      year={2016},
      organization={IEEE}
    }
    ```
  </details>

- **Piecewise Geodesics for Vessel Centerline Extraction and Boundary Delineation with Application to Retina Segmentation** <br />
  ![retina](https://img.shields.io/badge/retina-orange)  <br />
  D Chen, LD Cohen <br />
  _SSVM_ (2015) <br />
  https://doi.org/10.1007/978-3-319-18461-6_22 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{chen2015piecewise,
      title={Piecewise geodesics for vessel centerline extraction and boundary delineation with application to retina segmentation},
      author={Chen, Da and Cohen, Laurent D},
      booktitle={Scale Space and Variational Methods in Computer Vision: 5th International Conference, SSVM 2015, L{\`e}ge-Cap Ferret, France, May 31-June 4, 2015, Proceedings 5},
      pages={270--281},
      year={2015},
      organization={Springer}
    }
    ```
  </details>
  
- **Joint 3-D vessel segmentation and centerline extraction using oblique Hough forests with steerable filters** <br />
  ![micro](https://img.shields.io/badge/micro-green)
  ![filter](https://img.shields.io/badge/filter-red) <br />
  M Schneider, ..., BH Menze <br />
  _MedIA_ (2015) <br />
  https://doi.org/10.1016/j.media.2014.09.007 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{schneider2015joint,
      title={Joint 3-D vessel segmentation and centerline extraction using oblique Hough forests with steerable filters},
      author={Schneider, Matthias and Hirsch, Sven and Weber, Bruno and Sz{\'e}kely, G{\'a}bor and Menze, Bjoern H},
      journal={Medical image analysis},
      volume={19},
      number={1},
      pages={220--249},
      year={2015},
      publisher={Elsevier}
    }
    ```
  </details>
  
- **Globally Optimal Curvature-Regularized Fast Marching for Vessel Segmentation** <br />
  ![retina](https://img.shields.io/badge/retina-orange) <br />
  W Liao, K Rohr, S Wörz <br />
  _MICCAI_ (2013) <br />
  https://doi.org/10.1007/978-3-642-40811-3_69 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{liao2013globally,
      title={Globally optimal curvature-regularized fast marching for vessel segmentation},
      author={Liao, Wei and Rohr, Karl and W{\"o}rz, Stefan},
      booktitle={Medical Image Computing and Computer-Assisted Intervention--MICCAI 2013: 16th International Conference, Nagoya, Japan, September 22-26, 2013, Proceedings, Part I 16},
      pages={550--557},
      year={2013},
      organization={Springer}
    }
    ```
  </details>
  
- **3D cerebrovascular segmentation combining fuzzy vessel enhancement and level-sets with anisotropic energy weights** <br />
  ![angio](https://img.shields.io/badge/angio-cyan) <br />
  ND Forket, ..., J Ehrhardt <br />
  _MRI_ (2013) <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{forkert20133d,
      title={3D cerebrovascular segmentation combining fuzzy vessel enhancement and level-sets with anisotropic energy weights},
      author={Forkert, Nils Daniel and Schmidt-Richberg, Alexander and Fiehler, Jens and Illies, Till and M{\"o}ller, Dietmar and S{\"a}ring, Dennis and Handels, Heinz and Ehrhardt, Jan},
      journal={Magnetic resonance imaging},
      volume={31},
      number={2},
      pages={262--271},
      year={2013},
      publisher={Elsevier}
    }
    ```
  </details>
  
- **Vessel Wall Segmentation Using Implicit Models and Total Curvature Penalizers** <br />
  ![angio](https://img.shields.io/badge/angio-cyan) <br />
  R Moreno, C Wang, O Smedby <br />
  _SCIA_ (2013) <br />
  https://doi.org/10.1007/978-3-642-38886-6_29 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{moreno2013vessel,
      title={Vessel wall segmentation using implicit models and total curvature penalizers},
      author={Moreno, Rodrigo and Wang, Chunliang and Smedby, {\"O}rjan},
      booktitle={Image Analysis: 18th Scandinavian Conference, SCIA 2013, Espoo, Finland, June 17-20, 2013. Proceedings 18},
      pages={299--308},
      year={2013},
      organization={Springer}
    }
    ```
  </details>
  
- **Robust and accurate coronary artery centerline extraction in CTA by combining model-driven and data-driven approaches** <br />
  ![angio](https://img.shields.io/badge/angio-cyan) <br />
  Y Zheng, H Tek, G Funka-Lea <br />
  _MICCAI_ (2013) <br />
  https://doi.org/10.1007/978-3-642-40760-4_10 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{zheng2013robust,
      title={Robust and accurate coronary artery centerline extraction in CTA by combining model-driven and data-driven approaches},
      author={Zheng, Yefeng and Tek, Huseyin and Funka-Lea, Gareth},
      booktitle={Medical Image Computing and Computer-Assisted Intervention--MICCAI 2013: 16th International Conference, Nagoya, Japan, September 22-26, 2013, Proceedings, Part III 16},
      pages={74--81},
      year={2013},
      organization={Springer}
    }
    ```
  </details>
  
- **Blood vessel segmentation methodologies in retinal images – A survey** <br />
  ![review](https://img.shields.io/badge/review-blue)
  ![retina](https://img.shields.io/badge/retina-orange)<br />
  MM Fraz, ..., SA Barman <br />
  _CMPM_ (2012) <br />
  https://doi.org/10.1016/j.cmpb.2012.03.009

- **Fuzzy-based vascular structure enhancement in Time-of-Flight MRA images for improved segmentation** <br />
  ![angio](https://img.shields.io/badge/angio-cyan) <br />
  ND Forket, ..., D Säring <br />
  _MIM_ (2011) <br />
  https://doi.org/10.3414/me10-02-0003 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{forkert2011fuzzy,
      title={Fuzzy-based vascular structure enhancement in time-of-flight MRA images for improved segmentation},
      author={Forkert, Nils Daniel and Schmidt-Richberg, A and Fiehler, J and Illies, T and M{\"o}ller, D and Handels, H and S{\"a}ring, D},
      journal={Methods of information in medicine},
      volume={50},
      number={01},
      pages={74--83},
      year={2011},
      publisher={Schattauer GmbH}
    }
    ```
  </details>
  
- **Vessel centerline tracking in CTA and MRA images using hough transform** <br />
  ![angio](https://img.shields.io/badge/angio-cyan)
  ![filter](https://img.shields.io/badge/filter-red) <br />
  MMG Macedo, C Mekkaoui, MP Jackowski <br />
  _CIARP_ (2010) <br />
  https://doi.org/10.1007/978-3-642-16687-7_41 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{macedo2010vessel,
      title={Vessel centerline tracking in CTA and MRA images using hough transform},
      author={Macedo, Maysa MG and Mekkaoui, Choukri and Jackowski, Marcel P},
      booktitle={Progress in Pattern Recognition, Image Analysis, Computer Vision, and Applications: 15th Iberoamerican Congress on Pattern Recognition, CIARP 2010, Sao Paulo, Brazil, November 8-11, 2010. Proceedings 15},
      pages={295--302},
      year={2010},
      organization={Springer}
    }
    ```
  </details>
  
- **A review of 3D vessel lumen segmentation techniques: models, features and extraction schemes** <br />
  ![review](https://img.shields.io/badge/review-blue) <br />
  D Lesage, ..., G Funka-Lea <br />
  _MedIA_ (2009) <br />
  https://doi.org/10.1016/j.media.2009.07.011 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{lesage2009review,
      title={A review of 3D vessel lumen segmentation techniques: Models, features and extraction schemes},
      author={Lesage, David and Angelini, Elsa D and Bloch, Isabelle and Funka-Lea, Gareth},
      journal={Medical image analysis},
      volume={13},
      number={6},
      pages={819--845},
      year={2009},
      publisher={Elsevier}
    }
    ```
  </details>

- **A Novel Three-Dimensional Computer-Assisted Method for a Quantitative Study of Microvascular Networks of the Human Cerebral Cortex** <br />
  ![micro](https://img.shields.io/badge/micro-green)
  ![classic](https://img.shields.io/badge/classic-purple) <br />
  F Cassot F, ...S, V Lauwers-Cances <br />
  _Microcirculation_ (2006) <br />
  https://doi.org/10.1080/10739680500383407 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{cassot2006novel,
      title={A novel three-dimensional computer-assisted method for a quantitative study of microvascular networks of the human cerebral cortex},
      author={Cassot, Francis and Lauwers, Frederic and Fouard, C{\'e}line and Prohaska, Steffen and Lauwers-Cances, Valerie},
      journal={Microcirculation},
      volume={13},
      number={1},
      pages={1--18},
      year={2006},
      publisher={Taylor \& Francis}
    }
    ```
  </details>
  
- **Globally Optimal Active Contours, Sequential Monte Carlo and On-Line Learning for Vessel Segmentation** <br />
  ![angio](https://img.shields.io/badge/angio-cyan) <br />
  C Florin, N Paragios, J Williams <br />
  _ECCV_ (2006) <br />
  https://doi.org/10.1007/11744078_37 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{florin2006globally,
      title={Globally optimal active contours, sequential Monte Carlo and on-line learning for vessel segmentation},
      author={Florin, Charles and Paragios, Nikos and Williams, Jim},
      booktitle={Computer Vision--ECCV 2006: 9th European Conference on Computer Vision, Graz, Austria, May 7-13, 2006, Proceedings, Part III 9},
      pages={476--489},
      year={2006},
      organization={Springer}
    }
    ```
  </details>
  
- **A review of vessel extraction techniques and algorithms** <br />
  ![review](https://img.shields.io/badge/review-blue) <br />
  C Kirbas, F Quek <br />
  _ACM Computing Surveys_ (2004) <br />
  https://doi.org/10.1145/1031120.1031121 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{kirbas2004review,
      title={A review of vessel extraction techniques and algorithms},
      author={Kirbas, Cemil and Quek, Francis},
      journal={ACM Computing Surveys (CSUR)},
      volume={36},
      number={2},
      pages={81--121},
      year={2004},
      publisher={ACM New York, NY, USA}
    }
    ```
  </details>

- **Vessel Segmentation Using a Shape Driven Flow** <br />
  ![angio](https://img.shields.io/badge/angio-cyan) <br />
  D Nain, A Yezzi, G Turk <br />
  _MICCAI_ (2004) <br />
  https://doi.org/10.1007/978-3-540-30135-6_7 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{nain2004vessel,
      title={Vessel segmentation using a shape driven flow},
      author={Nain, Delphine and Yezzi, Anthony and Turk, Greg},
      booktitle={Medical Image Computing and Computer-Assisted Intervention--MICCAI 2004: 7th International Conference, Saint-Malo, France, September 26-29, 2004. Proceedings, Part I 7},
      pages={51--59},
      year={2004},
      organization={Springer}
    }
    ```
  </details>
  
- **Snake modeling and distance transform approach to vascular centerline extraction and quantification** <br />
  ![micro](https://img.shields.io/badge/micro-green)
  ![classic](https://img.shields.io/badge/classic-purple) <br />
  M Maddah, H Soltanian-Zadeh, A Afzali-Kusha <br />
  _CMIG_ (2003) <br />
  https://doi.org/10.1016/s0895-6111(03)00040-5 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{maddah2003snake,
      title={Snake modeling and distance transform approach to vascular centerline extraction and quantification},
      author={Maddah, Mahnaz and Soltanian-Zadeh, Hamid and Afzali-Kusha, Ali},
      journal={Computerized Medical Imaging and Graphics},
      volume={27},
      number={6},
      pages={503--512},
      year={2003},
      publisher={Elsevier}
    }
    ```
  </details>

- **Segmentation of vessel-like patterns using mathematical morphology and curvature evaluation** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![morpho](https://img.shields.io/badge/morpho-purple) <br />
  F Zana, JC Klein <br />
  _IEEE TIP_ (2001) <br />
  https://doi.org/10.1109/83.931095 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{zana2001segmentation,
      title={Segmentation of vessel-like patterns using mathematical morphology and curvature evaluation},
      author={Zana, Frederic and Klein, J-C},
      journal={IEEE transactions on image processing},
      volume={10},
      number={7},
      pages={1010--1019},
      year={2001},
      publisher={IEEE}
    }
    ```
  </details>

- **Vessel Segmentation for Visualization of MRA with Blood Pool Contrast Agent** <br />
  ![angio](https://img.shields.io/badge/angio-cyan) <br />
  S Young, V Pekar, J Weese  <br />
  _MICCAI_ (2001) <br />
  https://doi.org/10.1007/3-540-45468-3_59 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{young2001vessel,
      title={Vessel segmentation for visualization of MRA with blood pool contrast agent},
      author={Young, Stewart and Pekar, Vladimir and Weese, J{\"u}rgen},
      booktitle={International Conference on Medical Image Computing and Computer-Assisted Intervention},
      pages={491--498},
      year={2001},
      organization={Springer}
    }
    ```
  </details>
  
- **Retinal Blood Vessel Segmentation by Means of Scale-Space Analysis and Region Growing** <br />
  ![retina](https://img.shields.io/badge/retina-orange)
  ![morpho](https://img.shields.io/badge/morpho-purple) <br />
  ME Martínez-Pérez, ..., KH Parker <br />
  _MICCAI_ (1999) <br />
  https://doi.org/10.1007/10704282_10 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{martinez1999retinal,
      title={Retinal blood vessel segmentation by means of scale-space analysis and region growing},
      author={Mart{\'\i}nez-P{\'e}rez, M Elena and Hughes, Alun D and Stanton, Alice V and Thom, Simon A and Bharath, Anil A and Parker, Kim H},
      booktitle={Medical Image Computing and Computer-Assisted Intervention--MICCAI’99: Second International Conference, Cambridge, UK, September 19-22, 1999. Proceedings 2},
      pages={90--97},
      year={1999},
      organization={Springer}
    }
    ```
  </details>
  
- **Statistical 3D Vessel Segmentation Using a Rician Distribution** <br />
  ![angio](https://img.shields.io/badge/angio-cyan) <br />
  ACS Chung, JA Noble  <br />
  _MICCAI_ (1999) <br />
  https://doi.org/10.1007/10704282_9 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{chung1999statistical,
      title={Statistical 3D vessel segmentation using a Rician distribution},
      author={Chung, Albert CS and Noble, J Alison},
      booktitle={Medical Image Computing and Computer-Assisted Intervention--MICCAI’99: Second International Conference, Cambridge, UK, September 19-22, 1999. Proceedings 2},
      pages={82--89},
      year={1999},
      organization={Springer}
    }
    ```
  </details>
  
- **Multiscale vessel enhancement filtering** <br />
  ![angio](https://img.shields.io/badge/angio-cyan)
  ![frangi](https://img.shields.io/badge/frangi-red) <br />
  AF Frangi, ..., MA  Viergever  <br />
  _MICCAI_ (1998) <br />
  https://doi.org/10.1007/BFb0056195 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{frangi1998multiscale,
      title={Multiscale vessel enhancement filtering},
      author={Frangi, Alejandro F and Niessen, Wiro J and Vincken, Koen L and Viergever, Max A},
      booktitle={Medical Image Computing and Computer-Assisted Intervention—MICCAI’98: First International Conference Cambridge, MA, USA, October 11--13, 1998 Proceedings 1},
      pages={130--137},
      year={1998},
      organization={Springer}
    }
    ```
  </details>

- **3D multi-scale line filter for segmentation and visualization of curvilinear structures in medical images** <br />
  ![angio](https://img.shields.io/badge/angio-cyan)
  ![frangi](https://img.shields.io/badge/frangi-red) <br />
  Y Sato, ..., R Kikinis <br />
  _CVRMed-MRCAS_ (1997) <br />
  https://doi.org/10.1007/BFb0029240 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{sato19973d,
      title={3D multi-scale line filter for segmentation and visualization of curvilinear structures in medical images},
      author={Sato, Yoshinobu and Nakajima, Shin and Atsumi, Hideki and Koller, Thomas and Gerig, Guido and Yoshida, Shigeyuki and Kikinis, Ron},
      booktitle={International Conference on Computer Vision, Virtual Reality, and Robotics in Medicine},
      pages={213--222},
      year={1997},
      organization={Springer}
    }
    ```
  </details>
  
## Topology / Correction

- **Topologically faithful image segmentation via induced matching of persistence barcodes** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  N Stucki, ..., BH Menze, U Bauer <br />
  _ICML_ (2023) <br />
  https://proceedings.mlr.press/v202/stucki23a.html <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{stucki2023topologically,
      title={Topologically faithful image segmentation via induced matching of persistence barcodes},
      author={Stucki, Nico and Paetzold, Johannes C and Shit, Suprosanna and Menze, Bjoern and Bauer, Ulrich},
      booktitle={International Conference on Machine Learning},
      pages={32698--32727},
      year={2023},
      organization={PMLR}
    }
    ```
  </details>

- **Structure-Aware Image Segmentation with Homotopy Warping** <br />
  ![topo](https://img.shields.io/badge/topo-pink)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  X Hu <br />
  _NeurIPS_ (2022) <br />
  https://openreview.net/forum?id=CMcptt6nFaQ

- **Topology-Preserving Segmentation Network: A Deep Learning Segmentation Framework for Connected Component** <br />
  ![topo](https://img.shields.io/badge/topo-pink)
  ![deep](https://img.shields.io/badge/deep-black) <br />
  H Zhang, LM Lui <br />
  _ArXiv_ (2022) <br />
  https://arxiv.org/abs/2202.13331

- **Capturing Shape Information with Multi-scale Topological Loss Terms for 3D Reconstruction** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  DJE Waibel, ..., B Rieck <br />
  _MICCAI_ (2022) <br />
  https://doi.org/10.1007/978-3-031-16440-8_15

- **Topology-Aware Segmentation Using Discrete Morse Theory** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  X Hu, ..., C Chen <br />
  _ICLR_ (2021) <br />
  https://arxiv.org/abs/2103.09992

- **Whole Brain Vessel Graphs: A Dataset and Benchmark for Graph Learning and Neuroscience (VesselGraph)** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  JC Paetzold, ..., BH Menze <br />
  NeurIPS Datasets and Benchmarks (2021) <br />
  https://doi.org/10.48550/arXiv.2108.13233 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{paetzold2021whole,
      title={Whole brain vessel graphs: A dataset and benchmark for graph learning and neuroscience},
      author={Paetzold, Johannes C and McGinnis, Julian and Shit, Suprosanna and Ezhov, Ivan and B{\"u}schl, Paul and Prabhakar, Chinmay and Sekuboyina, Anjany and Todorov, Mihail and Kaissis, Georgios and Ert{\"u}rk, Ali and others},
      booktitle={Thirty-Fifth Conference on Neural Information Processing Systems Datasets and Benchmarks Track (Round 2)},
      year={2021}
    }
    ```
  </details>

- **clDice - A Novel Topology-Preserving Loss Function for Tubular Structure Segmentation** <br />
  ![micro](https://img.shields.io/badge/micro-green) 
  ![topo](https://img.shields.io/badge/topo-pink)  
  ![deep](https://img.shields.io/badge/deep-black) <br />
  S Shit, ..., BH Menze <br />
  _CVPR_ (2021) <br />
  https://openaccess.thecvf.com/content/CVPR2021/html/Shit_clDice_-_A_Novel_Topology-Preserving_Loss_Function_for_Tubular_Structure_CVPR_2021_paper.html <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{shit2021cldice,
      title={clDice-a novel topology-preserving loss function for tubular structure segmentation},
      author={Shit, Suprosanna and Paetzold, Johannes C and Sekuboyina, Anjany and Ezhov, Ivan and Unger, Alexander and Zhylka, Andrey and Pluim, Josien PW and Bauer, Ulrich and Menze, Bjoern H},
      booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
      pages={16560--16569},
      year={2021}
    }
    ```
  </details>

- **Joint Topology-preserving and Feature-refinement Network for Curvilinear Structure Segmentation** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  M Cheng, ..., J Guo <br />
  _ICCV_ (2021) <br />
  https://doi.org/10.1109/ICCV48922.2021.00706

- **3D Graph-Connectivity Constrained Network for Hepatic Vessel Segmentation** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  R Li, ..., L Wang <br />
  _JBHI_ (2021) <br />
  https://doi.org/10.1109/JBHI.2021.3118104

- **A Topological Loss Function for Deep-Learning Based Image Segmentation Using Persistent Homology** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  JR Clough, ..., AP King <br />
  _IEEE TPAMI_ (2020) <br />
  https://doi.org/10.1109/TPAMI.2020.3013679

- **Learning tree-structured representation for 3D coronary artery segmentation** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  B Kong, ..., Y Yin <br />
  _CMIG_ (2020) <br />
  https://doi.org/10.1016/j.compmedimag.2019.101688

- **TopoAL: An Adversarial Learning Approach for Topology-Aware Road Segmentation** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  S Vasu, ..., P Fua <br />
  _ECCV_ (2020) <br />
  https://doi.org/10.1007/978-3-030-58583-9_14

- **Topology-Preserving Deep Image Segmentation** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  X Hu, ..., C Chen <br />
  _NeurIPS_ (2019) <br />
  https://arxiv.org/abs/1906.05404

- **Unsupervised Microvascular Image Segmentation Using an Active Contours Mimicking Neural Network** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  S Gur, ..., P Blinder <br />
  _ICCV_ (2019) <br />
  https://arxiv.org/abs/1908.01373

- **A Deep Learning Design for Improving Topology Coherence in Blood Vessel Segmentation** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  RJ Araújo, JS Cardoso, HP Oliveira <br />
  _MICCAI_ (2019) <br />
  https://doi.org/10.1007/978-3-030-32239-7_11

- **Explicit topological priors for deep-learning based image segmentation using persistent homology** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  JR Clough, I Oksuz, N Byrne, JA Schnabel, AP King <br />
  _IPMI_ (2019) <br />
  https://doi.org/10.1007/978-3-030-20351-1_2

- **Large Scale Image Segmentation with Structured Loss Based Deep Learning for Connectome Reconstruction** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  J Funke, ..., SC Turaga <br />
  _IEEE TPAMI_ (2018) <br />
  https://doi.org/10.1109/TPAMI.2018.2835450

- **Beyond the Pixel-Wise Loss for Topology-Aware Delineation** <br />
  ![topo](https://img.shields.io/badge/topo-pink) 
  ![deep](https://img.shields.io/badge/deep-black) <br />
  A Mosinska, ..., P Fua <br />
  _CVPR_ (2018) <br />
  https://doi.org/10.1109/CVPR.2018.00331

- **Segmentation of Skeleton and Organs in Whole-Body CT Images via Iterative Trilateration** <br />
  M Bieth, ..., BH Menze <br />
  _IEEE TMI_ (2017) <br />
  https://doi.org/10.1109/TMI.2017.2720261 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{bieth2017segmentation,
      title={Segmentation of skeleton and organs in whole-body CT images via iterative trilateration},
      author={Bieth, Marie and Peter, Loic and Nekolla, Stephan G and Eiber, Matthias and Langs, Georg and Schwaiger, Markus and Menze, Bjoern},
      journal={IEEE transactions on medical imaging},
      volume={36},
      number={11},
      pages={2276--2286},
      year={2017},
      publisher={IEEE}
    }
    ```
  </details>

- **Uncertainty Estimation in Vascular Networks** <br />
  M Rempfler, B Andres, BH Menze <br />
  GRAIL (2017) <br />
  https://doi.org/10.1007/978-3-319-67675-3_5 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{rempfler2017uncertainty,
      title={Uncertainty estimation in vascular networks},
      author={Rempfler, Markus and Andres, Bjoern and Menze, Bjoern H},
      booktitle={Graphs in Biomedical Image Analysis, Computational Anatomy and Imaging Genetics: First International Workshop, GRAIL 2017, 6th International Workshop, MFCA 2017, and Third International Workshop, MICGen 2017, Held in Conjunction with MICCAI 2017, Qu{\'e}bec City, QC, Canada, September 10--14, 2017, Proceedings 1},
      pages={42--52},
      year={2017},
      organization={Springer}
    }
    ```
  </details>

- **Reconstructing cerebrovascular networks under local physiological constraints by integer programming** <br />
  M Rempfler, ..., BH Menze <br />
  _MedIA_ (2015) <br />
  https://doi.org/10.1016/j.media.2015.03.008 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{rempfler2015reconstructing,
      title={Reconstructing cerebrovascular networks under local physiological constraints by integer programming},
      author={Rempfler, Markus and Schneider, Matthias and Ielacqua, Giovanna D and Xiao, Xianghui and Stock, Stuart R and Klohs, Jan and Sz{\'e}kely, G{\'a}bor and Andres, Bjoern and Menze, Bjoern H},
      journal={Medical Image Analysis},
      volume={25},
      number={1},
      pages={86--94},
      year={2015},
      publisher={Elsevier}
    }
    ```
  </details>

- **TGIF: Topological Gap In-Fill for Vascular Networks** <br />
  M Schneider, ..., BH Menze <br />
  _MICCAI_ (2014) <br />
  https://doi.org/10.1007/978-3-319-10470-6_12 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{schneider2014tgif,
      title={TGIF: Topological Gap In-Fill for Vascular Networks: A Generative PhysiologicalModeling Approach},
      author={Schneider, Matthias and Hirsch, Sven and Weber, Bruno and Sz{\'e}kely, G{\'a}bor and Menze, Bjoern H},
      booktitle={Medical Image Computing and Computer-Assisted Intervention--MICCAI 2014: 17th International Conference, Boston, MA, USA, September 14-18, 2014, Proceedings, Part II 17},
      pages={89--96},
      year={2014},
      organization={Springer}
    }
    ```
  </details>

- **Extracting vascular networks under physiological constraints via integer programming** <br />
  M Rempfler, ..., BH Menze <br />
  _MICCAI_ (2014) <br />
  https://doi.org/10.1007/978-3-319-10470-6_63 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{rempfler2014extracting,
      title={Extracting vascular networks under physiological constraints via integer programming},
      author={Rempfler, Markus and Schneider, Matthias and Ielacqua, Giovanna D and Xiao, Xianghui and Stock, Stuart R and Klohs, Jan and Sz{\'e}kely, G{\'a}bor and Andres, Bjoern and Menze, Bjoern H},
      booktitle={Medical Image Computing and Computer-Assisted Intervention--MICCAI 2014: 17th International Conference, Boston, MA, USA, September 14-18, 2014, Proceedings, Part II 17},
      pages={505--512},
      year={2014},
      organization={Springer}
    }
    ```
  </details>

- **Enforcing topological constraints in random field image segmentation** <br />
  C Chen, D Freedman, CH Lampert <br />
  _CVPR_ (2011) <br />
  https://doi.org/10.1109/CVPR.2011.5995503

- **Three Dimensional Curvilinear Structure Detection Using Optimally Oriented Flux** <br />
  MWK Law, ACS Chung <br />
  _ECCV_ (2008) <br />
  https://doi.org/10.1007/978-3-540-88693-8_27 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{law2008three,
      title={Three dimensional curvilinear structure detection using optimally oriented flux},
      author={Law, Max WK and Chung, Albert CS},
      booktitle={Computer Vision--ECCV 2008: 10th European Conference on Computer Vision, Marseille, France, October 12-18, 2008, Proceedings, Part IV 10},
      pages={368--382},
      year={2008},
      organization={Springer}
    }
    ```
  </details>

- **Gap filling of 3-D microvascular networks by tensor voting** <br />
  L Risser, F Plouraboué, X Descombes <br />
  _IEEE TMI_ (2008) <br />
  https://doi.org/10.1109/TMI.2007.913248 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{risser2008gap,
      title={Gap filling of 3-D microvascular networks by tensor voting},
      author={Risser, Laurent and Plourabou{\'e}, Franck and Descombes, Xavier},
      journal={IEEE transactions on medical imaging},
      volume={27},
      number={5},
      pages={674--687},
      year={2008},
      publisher={IEEE}
    }
    ```
  </details>

- **Liver blood vessels extraction by a 3-D topological approach** <br />
  P Dokládal, ..., G Bertrand <br />
  _MICCAI_ (1999) <br />
  https://doi.org/10.1007/10704282_11 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{dokladal1999liver,
      title={Liver blood vessels extraction by a 3-D topological approach},
      author={Dokl{\'a}dal, Petr and Lohou, Christophe and Perroton, Laurent and Bertrand, Gilles},
      booktitle={Medical Image Computing and Computer-Assisted Intervention--MICCAI’99: Second International Conference, Cambridge, UK, September 19-22, 1999. Proceedings 2},
      pages={98--105},
      year={1999},
      organization={Springer}
    }
    ```
  </details>

## Constrained Constructive Optimization

- **Tissue metabolism driven arterial tree generation** <br />
  M Schneider, ..., S Hirsch <br />
  _MedIA_ (2012) <br />
  https://doi.org/10.1016/j.media.2012.04.009 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{schneider2012tissue,
      title={Tissue metabolism driven arterial tree generation},
      author={Schneider, Matthias and Reichold, Johannes and Weber, Bruno and Sz{\'e}kely, G{\'a}bor and Hirsch, Sven},
      journal={Medical image analysis},
      volume={16},
      number={7},
      pages={1397--1414},
      year={2012},
      publisher={Elsevier}
    }
    ```
  </details>

- **Simulating vascular systems in arbitrary anatomies** <br />
  D Szczerba, G Székely <br />
  _MICCAI_ (2005) <br />
  https://doi.org/10.1007/11566489_79 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{szczerba2005simulating,
      title={Simulating vascular systems in arbitrary anatomies},
      author={Szczerba, Dominik and Sz{\'e}kely, G{\'a}bor},
      booktitle={Medical Image Computing and Computer-Assisted Intervention--MICCAI 2005: 8th International Conference, Palm Springs, CA, USA, October 26-29, 2005, Proceedings, Part II 8},
      pages={641--648},
      year={2005},
      organization={Springer}
    }
    ```
  </details>
  

## Flow

- **Velocity-To-Pressure (V2P) - Net: Inferring Relative Pressures from Time-Varying 3D Fluid Flow Velocities** <br />
  S Shit, ..., BH Menze <br />
  _IPMI_ (2021) <br />
  https://doi.org/10.1007/978-3-030-78191-0_42 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{shit2021velocity,
      title={Velocity-to-pressure (V2P)-net: inferring relative pressures from time-varying 3D fluid flow velocities},
      author={Shit, Suprosanna and Das, Dhritiman and Ezhov, Ivan and Paetzold, Johannes C and Sanches, Augusto F and Thuerey, Nils and Menze, Bjoern H},
      booktitle={Information Processing in Medical Imaging: 27th International Conference, IPMI 2021, Virtual Event, June 28--June 30, 2021, Proceedings 27},
      pages={545--558},
      year={2021},
      organization={Springer}
    }
    ```
  </details>

- **Vascular graph model to simulate the cerebral blood flow in realistic vascular networks** <br />
  J Reichold, ..., B Weber <br />
  _JCBFM_ (2009) <br />
  https://doi.org/10.1038/jcbfm.2009.58 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @article{reichold2009vascular,
      title={Vascular graph model to simulate the cerebral blood flow in realistic vascular networks},
      author={Reichold, Johannes and Stampanoni, Marco and Keller, Anna Lena and Buck, Alfred and Jenny, Patrick and Weber, Bruno},
      journal={Journal of Cerebral Blood Flow \& Metabolism},
      volume={29},
      number={8},
      pages={1429--1443},
      year={2009},
      publisher={SAGE Publications Sage UK: London, England}
    }
    ```
  </details>
  

## Axons

- **Triple-Crossing 2.5D Convolutional Neural Network for Detecting Neuronal Arbours in 3D Microscopic Images** <br />
  S Liu, ..., W Cai  <br />
  _MLMI_ (2017) <br />
  https://doi.org/10.1007/978-3-319-67389-9_22 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{liu2017triple,
      title={Triple-crossing 2.5 D convolutional neural network for detecting neuronal arbours in 3D microscopic images},
      author={Liu, Siqi and Zhang, Donghao and Song, Yang and Peng, Hanchuan and Cai, Weidong},
      booktitle={Machine Learning in Medical Imaging: 8th International Workshop, MLMI 2017, Held in Conjunction with MICCAI 2017, Quebec City, QC, Canada, September 10, 2017, Proceedings 8},
      pages={185--193},
      year={2017},
      organization={Springer}
    }
    ```
  </details>

- **Automatic centerline extraction of irregular tubular structures using probability volumes from multiphoton imaging** <br />
  A Santamaría-Pang, ..., IA Kakadiaris <br />
  _MICCAI_ (2017) <br />
  https://doi.org/10.1007/978-3-540-75759-7_59 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{santamaria2007automatic,
      title={Automatic centerline extraction of irregular tubular structures using probability volumes from multiphoton imaging},
      author={Santamar{\'\i}a-Pang, Alberto and Colbert, Costa M and Saggau, Peter and Kakadiaris, Ioannis A},
      booktitle={Medical Image Computing and Computer-Assisted Intervention--MICCAI 2007: 10th International Conference, Brisbane, Australia, October 29-November 2, 2007, Proceedings, Part II 10},
      pages={486--494},
      year={2007},
      organization={Springer}
    }
    ```
  </details>
  

# Synth-based segmentation

- **Synthetic OCT-A blood vessel maps using fundus images and generative adversarial networks** <br />
  I Coronado, ..., L Giancardo <br />
  _Sci Rep_ (2023) <br />
  https://doi.org/10.1038/s41598-023-42062-9

- **Segmentation of 3D blood vessel networks using unsupervised deep learning** <br />
  P Sweeney, ..., SE Bohndiek <br />
  _bioRxiv_ (2023) <br />
  https://doi.org/10.1101/2023.04.30.538453

- **Deep learning based generation of synthetic blood vessel surfaces** <br />
  M Danu, ..., LM Itu <br />
  _ICSTCC_ (2019) <br />
  https://doi.org/10.1109/ICSTCC.2019.8885576

- **Endotracheal Tube Detection and Segmentation in Chest Radiographs Using Synthetic Data** <br />
  M Frid-Adar, R Amer, H Greenspan <br />
  _MICCAI_ (2019) <br />
  https://doi.org/10.1007/978-3-030-32226-7_87 <br />
  <details>
    <summary>bibtex</summary>
    
    ```bibtex
    @inproceedings{frid2019endotracheal,
      title={Endotracheal tube detection and segmentation in chest radiographs using synthetic data},
      author={Frid-Adar, Maayan and Amer, Rula and Greenspan, Hayit},
      booktitle={International Conference on Medical Image Computing and Computer-Assisted Intervention},
      pages={784--792},
      year={2019},
      organization={Springer}
    }
    ```
  </details>

- **Using synthetic training data for deep learning-based GBM segmentation** <br />
  L Lindner, ..., J Egger <br />
  _IEEE EMBC_ (2019) <br />
  https://doi.org/10.1109/EMBC.2019.8856297

- **The effects of physics-based data augmentation on the generalizability of deep neural networks: Demonstration on nodule false-positive reduction** <br />
  AO Omigbodun, ..., SS Hsieh <br />
  _Med Phys_ (2019) <br />
  https://doi.org/10.1002/mp.13755

- **Transfer learning from synthetic data reduces need for labels to segment brain vasculature and neural pathways in 3d** <br />
  JC Paetzold, ..., BH Menze <br />
  _MIDL_ (2019) <br />
  https://openreview.net/forum?id=BJe02gRiY4
