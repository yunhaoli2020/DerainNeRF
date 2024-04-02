# DerainNeRF: 3D Scene Estimation with Adhesive Waterdrop Removal

**[Paper Link](https://arxiv.org/abs/2403.20013)**


<img src="https://github.com/yunhaoli2020/DerainNeRF/blob/main/doc/img0823_4_orig_spiral_200000_rgb-ezgif.com-video-to-gif-converter.gif" width="45%"> <img src="https://github.com/yunhaoli2020/DerainNeRF/blob/main/doc/img0823_4_mask_spiral_200000_rgb-ezgif.com-video-to-gif-converter.gif" width="45%">






**[Yunhao Li](https://yunhaoli2020.github.io/), Jing Wu, [Lingzhe Zhao](https://github.com/LingzheZhao) and [Peidong Liu](https://ethliup.github.io/) [ICRA 2024]**


This is a simplified implementation of the paper DerainNeRF: 3D Scene Estimation with Adhesive Waterdrop Removal (ICRA 2024). Authors:
DerainNeRF reconstruct the clear 3D scene implicitly from multi-view images degraded by adhesive waterdrops.

## ✨News
📺 **[2024.01]** Our paper has been accepted by IEEE ICRA 2024!


## Novel View Synthesis
<img src="https://github.com/yunhaoli2020/DerainNeRF/blob/main/doc/tanabata_mask_spiral_200000_rgb-ezgif.com-video-to-gif-converter.gif" width="32%"> <img src="https://github.com/yunhaoli2020/DerainNeRF/blob/main/doc/factory_mask_spiral_200000_rgb-ezgif.com-video-to-gif-converter.gif" width="32%"> <img src="https://github.com/yunhaoli2020/DerainNeRF/blob/main/doc/church_mask_spiral_200000_rgb-ezgif.com-video-to-gif-converter.gif" width="32%">


## Image Waterdrop Removal Result
<img src="https://github.com/yunhaoli2020/DerainNeRF/blob/main/doc/fig5_github.jpg" width="99%">


## Method overview
<img src="https://github.com/yunhaoli2020/DerainNeRF/blob/main/doc/method_github.jpg" width="99%">

Our method exploits a pre-trained attention network to predict the location of waterdrops and then train a Neural Radiance Fields (NeRF) to recover the 3D scene implicitly.

## Quickstart

### 1. Setup environment

```
git clone https://github.com/yunhaoli2020/DerainNeRF
cd DerainNeRF
pip install -r requirements.txt
```

### 2. Download datasets

You can download the data [here](https://drive.google.com/file/d/1BZ5s8MSm6cfz4n3asf4_640fSVIweUCE/view?usp=sharing).

For different scenes (*cozy2room*, *factory* etc.), the folder `images` includes images in original resolution and the folder `images_3` (or `images_4`) includes input images of DerainNeRF. The number indicates the scale factor. For example, `images_3` indicates the 3x downsample when loading the dataset. The file `poses_bounds.npy` contains poses derived from COLMAP. The file `rainMask.npy` contains binary masks which indicates the waterdrops in input images.

### 3. Configs

Change the data path and other parameters (if needed) in `configs/tanabata.txt`. We use *tanabata* scene as an example.

### 4. Training

```
python run_derainnerf.py --config configs/tanabata.txt
```

After training, you can get clear images, depth maps and novel-view images synthesized from NeRF.


### 5. Demo with our pre-trained model

You can test our code and render clear images with the provided weight files. To do this, you should first download the pre-trained models from [here](https://drive.google.com/file/d/1EavSnqkKptJxj-Z7cTq2jl5x9Je0Q5T3/view?usp=sharing), unzip it, then put the weight file under the corresponding logs folder `./logs`, finally run

```
python run_derainnerf.py --config configs/tanabata.txt
```


## Your own data

`images`: This folder is used to estimate initial camera poses from waterdrop images. Specifically, just put your own data in the folder `images`, and run `imgs2poses.py` script from the [LLFF code](https://github.com/fyusion/llff) to estimate camera poses and generate `poses_bounds.npy`.

`images_X`: This is the default training folder, which includes the downsampled waterdrop images in `images` folder. The number `X` indicates the downsample rate. If X it 1, then the images in the two folders would be the same. 

`rainMask.npy`: This file contains binary masks which indicates waterdrops in the input images.
```

images folder: (suppose 20 images)
000.png
001.png
...
019.png
#-----------------------------------------------------------------------------------------#
images_X folder: (training folder, suppose 20 images)
000.png
001.png
....
019.png
#-----------------------------------------------------------------------------------------#
poses_bounds.npy
rainMask.npy
```
## Citation

If you find this useful, please consider citing our paper:

```bibtex
@misc{li2024derainnerf,
      title={DerainNeRF: 3D Scene Estimation with Adhesive Waterdrop Removal}, 
      author={Yunhao Li and Jing Wu and Lingzhe Zhao and Peidong Liu},
      year={2024},
      eprint={2403.20013},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```

## Acknowledgment

The overall framework, metrics computing and camera transformation are derived from [nerf-pytorch](https://github.com/yenchenlin/nerf-pytorch/) and [AttGAN](https://github.com/rui1996/DeRaindrop) respectively. We appreciate the effort of the contributors to these repositories.
