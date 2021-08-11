
# Experiments in Improving Boosting Monocular Depth
Deep Learning 631 Project Recap

By Phil Navo and Kris Johnson, based on the paper:
> Boosting Monocular Depth Estimation Models to High-Resolution via Content-Adaptive Multi-Resolution Merging, by
> S. Mahdi H. Miangoleh\*, Sebastian Dille\*, Long Mai, Sylvain Paris, Yağız Aksoy.
> [Main pdf](http://yaksoy.github.io/papers/CVPR21-HighResDepth.pdf),
> [Supplementary pdf](http://yaksoy.github.io/papers/CVPR21-HighResDepth-Supp.pdf),
> [Project Page](http://yaksoy.github.io/highresdepth/).

## TL;DR
Try the model easily in Colab : [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/krisrjohnson/BoostingMonocularDepth/blob/main/Boostmonoculardepth.ipynb)

## Goals
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
- Repo partial cleanup


## Next Steps

1. Port Matlab code to Python
1. Experiment retraining Mergenet with different patch sizes
1. Video results