# DerainNeRF: 3D Scene Estimation with Adhesive Waterdrop Removal
**[ICRA 2024] [Yunhao Li](https://yunhaoli2020.github.io/), Jing Wu, [Lingzhe Zhao](https://github.com/LingzheZhao) and [Peidong Liu](https://ethliup.github.io/).


This is a simplified implementation of the paper DerainNeRF: 3D Scene Estimation with Adhesive Waterdrop Removal (ICRA 2024). Authors:
DerainNeRF reconstruct the clear 3D scene implicitly from multi-view images degraded by adhesive waterdrops.

The codes and data will be available soon!

## ✨News
📺 **[2024.01]** Our paper has been accepted by IEEE ICRA 2024!


## Novel View Synthesis

## Image Waterdrop Removal Result



## Method overview


Our method exploits a pre-trained attention network to predict the location of waterdrops and then train a Neural Radiance Fields (NeRF) to recover the 3D scene implicitly.



## Acknowledgment

The overall framework, metrics computing and camera transformation are derived from [nerf-pytorch](https://github.com/yenchenlin/nerf-pytorch/) and [AttGAN](https://github.com/rui1996/DeRaindrop) respectively. We appreciate the effort of the contributors to these repositories.
