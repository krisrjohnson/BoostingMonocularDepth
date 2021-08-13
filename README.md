
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

---
## Goals
For this assignment, we found a very cool paper and github repository which trains a model to blend low and high resolution depth maps and depth map patches to create scene consistent, higher quality depth maps. With that, we wanted to understand the paper and explain what the repository was actually doing, as well as experiment with model hyperparameters to see if we could get better results.

1. Better explain existing repo
1. Experiments on Patch Size

---
## Methods Attempted
1. Understanding the Paper

For this assignment, we found a very cool paper that created impressive higher resolution depth maps than the existing state of the art, aka s.o.t.a., solutions. Exisitng solutions like pretrained, fully convolutional, s.o.t.a [MiDaS-v2][1], will generate demonstrably different outputs for the same image at different input resolutions, which the authors claim is due to receptive field size of CNNs.


<figure class="image">
  <img src="./figures/ReceptiveFieldEffects.png" alt="Receptive Field Effects on Different Input Resolutions" width=30%>
  <figcaption>Receptive Field Effects on Different Input Resolutions</figcaption>
</figure>


The paper performs a "double estimation method". The authors take MidaS inferences on the same image at both low and high resolutions and merge them. The low resolution outputs usefully capture scene consistency, so depth is consistent across the entire image, while the high resolution inputs capture high frequency details. 

Further, the authors splice out patches of the image to radically improve 

In doing their so-called "double estimation method" the authors 

In so merging low resolution and high resolution images the authors achieve much sharper object boundaries, 

### Experimenting with different patch size configs on pretrained model

### Recreate Repo Results


---
## Issues
We were very excited that there was a github repo so we could experiment with such a cool technique. However we ran into many issues when trying to actually replicate and then expand upon the authors' work.

### Matlab everywhere
First and foremost among the issues we encountered was the use of matlab scripts. 

1. Seemingly easy repo instructions, actually tons of complexity
1. No environment with GPU and Matlab together

---
## Outcomes


### Visual Reults
Here are three results from our experiments that show the differences in t-thresholds. They follow the general trend that at higher thresholds more details are visible while some of the scene consistency visually decreases. At lower resolutions the scene consistency, which you can think of as color smoothness on a given surface, is very strong but small details are often missing.

__Bike__

<p float="left" width=100%>
<figure class="image">
  <img src="./figures/bike1_im0.png" alt="Bike" width=49%>
  <img src="./figures/bike_exp.gif" alt="Bike Output" width=49%>
</figure>
</p>

At lower thresholds the rear tire blends in with the back wall, while higher thresholds it's visibly separate. At higher thresholds the details on the backpack become more visible.

__Pipes__
<p float="left" width=100%>
<figure class="image">
  <img src="./figures/pipes_im0.png" alt="Bike" width=49%>
  <img src="./figures/pipes_exp.gif" alt="Receptive Field Effects on Different Input Resolutions" width=49%>
</figure>
</p>

Starting at t15 the smaller pipes in the background appear. 

__Adirondack__
<p float="left" width=100%>
<figure class="image">
  <img src="./figures/Adirondack_im0.png" alt="Bike" width=49%>
  <img src="./figures/Adirondack_exp.gif" alt="Receptive Field Effects on Different Input Resolutions" width=49%>
</figure>
</p>

Higher thresholds bring out details for the scarf and the books.


### Repo Partial Cleanup
We created a [notebook](./Create_Training_Data.ipynb) we felt better showed how to create the training data, which consists of 

---
## Next Steps

1. Port Matlab code to Python
1. Experiment retraining Mergenet with different patch sizes
1. Video results



[1]: https://github.com/intel-isl/MiDaS/tree/v2