
# Experiments in Improving Boosting Monocular Depth
Deep Learning 631 Project Recap

By Phil Navo and Kris Johnson, based on the paper:
> Boosting Monocular Depth Estimation Models to High-Resolution via Content-Adaptive Multi-Resolution Merging, by
> S. Mahdi H. Miangoleh\*, Sebastian Dille\*, Long Mai, Sylvain Paris, Yağız Aksoy.
> [Main pdf](http://yaksoy.github.io/papers/CVPR21-HighResDepth.pdf),
> [Supplementary pdf](http://yaksoy.github.io/papers/CVPR21-HighResDepth-Supp.pdf),
> [Project Page](http://yaksoy.github.io/highresdepth/),
> [Github Repo](https://github.com/compphoto/BoostingMonocularDepth).

## TL;DR
Try the model easily in Colab : [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/krisrjohnson/BoostingMonocularDepth/blob/main/Boostmonoculardepth.ipynb)

## Goals
For this assignment, we found a very cool paper that created impressive higher resolution depth maps than the existing state of the art, aka s.o.t.a., solutions. Exisitng solutions like pretrained, fully convolutional, s.o.t.a [MiDaS-v2][1], will generate demonstrably different outputs for the same image at different input resolutions, which the authors claim is due to receptive field size of CNNs.


<figure class="image">
  <img src="./figures/ReceptiveFieldEffects.png" alt="Receptive Field Effects on Different Input Resolutions" width=30%>
  <figcaption>Receptive Field Effects on Different Input Resolutions</figcaption>
</figure>


The paper performs a "double estimation method". The authors take MidaS inferences on the same image at both low and high resolutions and merge them. The low resolution outputs usefully capture scene consistency, so depth is consistent across the entire image, while the high resolution inputs capture high frequency details. 

Further, the authors splice out patches of the image to radically improve 

In doing their so-called "double estimation method" the authors 

In so merging low resolution and high resolution images the authors achieve much sharper object boundaries, 

1. Better explain existing repo
1. Experiments on Patch Size


## Methods Attempted
1. understanding the repo
1. experimenting with different patch size configs on pretrained model
1. recreate repo results
    1. dealing with matlab


## Issues
1. Matlab everywhere
1. Seemingly easy repo instructions, actually tons of complexity
1. No environment with GPU and Matlab together


## Outcomes
- Phil results

![Bike Experiments](./figures/bike_exp.gif)
![Pipes Experiments](./figures/pipes_exp.gif)


- Repo partial cleanup


## Next Steps

1. Port Matlab code to Python
1. Experiment retraining Mergenet with different patch sizes
1. Video results



[1]: https://github.com/intel-isl/MiDaS/tree/v2