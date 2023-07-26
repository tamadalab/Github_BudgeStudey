

# Deep Image Analogy

The major contributors of this repository include [Jing Liao](https://liaojing.github.io/html/index.html), [Yuan Yao](http://yuanyao.info/), [Lu Yuan](http://www.lyuan.org/), [Gang Hua](http://www.ganghua.org/) and [Sing Bing Kang](http://www.singbingkang.com/publications/) at Microsoft Research.

## Introduction

**Deep Image Analogy** is a technique to find semantically-meaningful dense correspondences between two input images. It adapts the notion of image analogy with features extracted from a Deep Convolutional Neural Network.

**Deep Image Analogy** is initially described in a [SIGGRAPH 2017 paper](https://arxiv.org/abs/1705.01088)


![image](https://github.com/msracver/Deep-Image-Analogy/blob/master/windows/deep_image_analogy/example/readme/teaser.png)


## Disclaimer

This is an official C++ combined with CUDA implementation of [Deep Image Analogy](https://arxiv.org/abs/1705.01088). It is worth noticing that:
- Our codes are based on [Caffe](https://github.com/Microsoft/caffe).
- Our codes only have been tested on Windows 10 and Windows Server 2012 R2 with CUDA 8 or 7.5.
- Our codes only have been tested on several Nvidia GPU: Titan X, Titan Z, K40, GTX770.
- The size of input image is limited, mostly should not be large than 700x500 if you use 1.0 for parameter **ratio**.


## License

© Microsoft, 2017. Licensed under a MIT license.

## Citation
If you find **Deep Image Analogy** (include deep patchmatch) helpful for your research, please consider citing:

```
@article{Liao:2017:VAT:3072959.3073683,
 author = {Liao, Jing and Yao, Yuan and Yuan, Lu and Hua, Gang and Kang, Sing Bing},
 title = {Visual Attribute Transfer Through Deep Image Analogy},
 journal = {ACM Trans. Graph.},
 issue_date = {July 2017},
 volume = {36},
 number = {4},
 month = jul,
 year = {2017},
 issn = {0730-0301},
 pages = {120:1--120:15},
 articleno = {120},
 numpages = {15},
 url = {http://doi.acm.org/10.1145/3072959.3073683},
 doi = {10.1145/3072959.3073683},
 acmid = {3073683},
 publisher = {ACM},
 address = {New York, NY, USA},
 keywords = {deep matching, image analogy, transfer},
} 
```

## Application

### Photo to Style

One major application of our code is to transfer the style from a painting to a photo.
<div>
<img src="https://github.com/msracver/Deep-Image-Analogy/blob/master/windows/deep_image_analogy/example/readme/p2s1.png"/>
<img src="https://github.com/msracver/Deep-Image-Analogy/blob/master/windows/deep_image_analogy/example/readme/p2s2.png"/>
</div>

### Style to Style

It can also swap the styles between two artworks.

![image](https://github.com/msracver/Deep-Image-Analogy/blob/master/windows/deep_image_analogy/example/readme/s2s.png)

### Style to Photo

The most challenging application is converting a sketch or a painting to a photo.

<img src = "https://github.com/msracver/Deep-Image-Analogy/blob/master/windows/deep_image_analogy/example/readme/s2p3.png">

<img src = "https://github.com/msracver/Deep-Image-Analogy/blob/master/windows/deep_image_analogy/example/readme/s2p4.png">

### Photo to Photo

It can do color transfer between two photos, such as generating time lapse.

![image](https://github.com/msracver/Deep-Image-Analogy/blob/master/windows/deep_image_analogy/example/readme/p2p.png)

## Getting Started

### Prerequisite

- Windows 7/8/10 (for linux or mac os x user, please check branch [linux](https://github.com/msracver/Deep-Image-Analogy/tree/linux).)
- CUDA 8 or 7.5
- Visual Studio 2013

### Build

- Build [Caffe](http://caffe.berkeleyvision.org/) at first. Just follow the tutorial [here](https://github.com/Microsoft/caffe).
- Edit ```deep_image_analogy.vcxproj``` under ```windows/deep_image_analogy``` to make the CUDA version in it match yours .
- Open solution ```Caffe``` and add ```deep_image_analogy``` project.
- Build project ```deep_image_analogy```.

### Download models

You need to download models VGG-19 model before start to run a demo. Go to ```windows/deep_image_analogy/models/vgg19/``` folder and download:
- http://www.robots.ox.ac.uk/~vgg/software/very_deep/caffe/VGG_ILSVRC_19_layers.caffemodel

### Demo

Open ```main.cpp``` in ```windows/deep_image_analogy/source/``` to see how to run a demo. You need to set several parameters which have been mentioned in the paper. To be more specific, you need to set

- **path_model**, where the VGG-19 model is.
- **path_A**, the input image A.
- **path_BP**, the input image BP.
- **path_output**, the output path.
- **GPU Number**, GPU ID you want to run this experiment.
- **Ratio**, the ratio to resize the inputs before sending them into the network.
- **Blend Weight**, the level of weights in blending process.
- **Flag of WLS Filter**, if you are trying to do photo style transfer, we recommend to switch this on to keep the structure of original photo.

### Direct Run

We also provide a pre-built executable file in folder ```windows/deep_image_analogy/exe/```, don't hesitate to try it.

To run this ```deep_image_analogy.exe```, you need to write a command line as:

```
deep_image_analogy.exe ../models/ ../demo/content.png ../demo/style.png ../demo/output/ 0 0.5 2 0
```

which means
- **path_model**=```../models/```
- **path_A**=```../demo/content.png```
- **path_BP**=```../demo/style.png```
- **path_output**=```../demo/output/```
- **GPU Number**=```0```
- **Ratio**=```0.5```
- **Blend Weight**=```2```
- **Flag of WLS Filter**=```0```( ```0```: WLS filter disabled, ```1```: WLS filter enabled, only required for the case of photo to photo)

### Tips

- We often test images of size 600x400 and 448x448.
- We set ratio to 1.0 by default. Specifically, for face (portrait) cases, we find ratio = 0.5 often make the results better.
- Blend weight controls the result appearance. If you want the result to be more like original content photo, please increase it; if you want the result more faithful to the style, please reduce it.
- For the four applications, our settings are mostly (but not definitely):
  - Photo to Style: blend weight=3, ratio=0.5 for face and ratio=1 for other cases.
  - Style to Style: blend weight=3, ratio=1.
  - Style to Photo: blend weight=2, ratio=0.5.
  - Photo to Photo: blend weight=3, ratio=1.

## Acknowledgments

Our codes acknowledge [Eigen](http://eigen.tuxfamily.org/index.php?title=Main_Page), [PatchMatch](http://gfx.cs.princeton.edu/gfx/pubs/Barnes_2009_PAR/index.php), [CudaLBFGS](https://github.com/jwetzl/CudaLBFGS) and [Caffe](https://github.com/BVLC/caffe). We also acknowledge to the authors of our image and style examples but we do not own the copyrights of them.
