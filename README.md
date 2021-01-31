# SCNet

## Introduction

[ALGORITHM]

We provide the code for reproducing experiment results of [SCNet](https://arxiv.org/abs/2012.10150).

## Highlight:
- SCNet addresses the limitation in training-inference sample distribution mismatch of existing cascade method for instance segmentation.
- SCNet strengen the relationship between subtasks: classification, detection and segmentation.
- **State-of-the-art**: without bell and whistle, SCNet achieves 44.7 box AP and 42.3 mask AP on ResNext-101. This can be further improved with well-known plugins and tricks, such as Group Norm, DCN, multi-scale training/testing.
- **Fast training and testing**: SCNet achieves better performancce while training/inference faster and requires less memory compared to [Cascade Mask R-CNN]() and [HTC]().

```
@inproceedings{vu2019cascade,
  title={SCNet: Training Inference Sample Consistency for Instance Segmentation},
  author={Vu, Thang and Haeyong, Kang and Yoo, Chang D},
  booktitle={AAAI},
  year={2021}
}
```

## Dataset

SCNet requires COCO and COCO-stuff dataset for training. You need to download and extract it in the COCO dataset path.
The directory should be like this.

```none
mmdetection
├── mmdet
├── tools
├── configs
├── data
│   ├── coco
│   │   ├── annotations
│   │   ├── train2017
│   │   ├── val2017
│   │   ├── test2017
|   |   ├── stuffthingmaps
```

##Results and Models

The results on COCO 2017val are shown in the below table. (results on test-dev are usually slightly higher than val)

|     Backbone    |  Style  | Lr schd | Mem (GB) | Inf speed (fps) | box AP | mask AP | TTA box AP | TTA mask AP | Config |   Download   |
|:---------------:|:-------:|:-------:|:--------:|:---------------:|:------:|:-------:|:----------:|:-----------:|:------:|:------------:|
|     R-50-FPN    | pytorch |    1x   |    7.0   |       6.2       |  43.5  |   39.2  |    44.8    |     40.9    | [config](https://github.com/open-mmlab/mmdetection/tree/master/configs/scnet/scnet_r50_fpn_1x_coco.py) | [model](htt      ps://drive.google.com/file/d/1K5_8-P0EC43WZFtoO3q9_JE-df8pEc7J/view?usp=sharing) \| [log](https://drive.google.com/file/d/1ZFS6QhFfxlOnDYPiGpSDP_Fzgb7iDGN3/view?usp=sharing) |
|     R-50-FPN    | pytorch |   20e   |    7.0   |       6.2       |  44.5  |   40.0  |    45.8    |     41.5    | [config](https://github.com/open-mmlab/mmdetection/tree/master/configs/scnet/scnet_r50_fpn_20e_coco.py) | [model](ht      tps://drive.google.com/file/d/15VGLCt5-IO5TbzB4Kw6ZyoF6QH0Q511A/view?usp=sharing) \| [log](https://drive.google.com/file/d/1-LnkOXN8n5ojQW34H0qZ625cgrnWpqSX/view?usp=sharing) |
|    R-101-FPN    | pytorch |   20e   |    8.9   |       5.8       |  45.8  |   40.9  |    47.3    |     42.7    | [config](https://github.com/open-mmlab/mmdetection/tree/master/configs/scnet/scnet_r101_fpn_20e_coco.py) | [model](h      ttps://drive.google.com/file/d/1aeCGHsOBdfIqVBnBPp0JUE_RSIau3583/view?usp=sharing) \| [log](https://drive.google.com/file/d/1iRx-9GRgTaIDsz-we3DGwFVH22nbvCLa/view?usp=sharing) |
| X-101-64x4d-FPN | pytorch |   20e   |   13.2   |       4.9       |  47.5  |   42.3  |    48.9    |     44.0    | [config](https://github.com/open-mmlab/mmdetection/tree/master/configs/scnet/scnet_x101_64x4d_fpn_20e_coco.py) | [mo      del](https://drive.google.com/file/d/1YjgutUKz4TTPpqSWGKUTkZJ8_X-kyCfY/view?usp=sharing) \| [log](https://drive.google.com/file/d/1OsfQJ8gwtqIQ61k358yxY21sCvbUcRjs/view?usp=sharing) |

### Notes

- Training hyper-parameters are identical to those of [HTC](https://github.com/open-mmlab/mmdetection/tree/master/configs/htc).
- TTA means Test Time Augmentation, which applies horizonal flip and multi-scale testing. Refer to [config](https://github.com/open-mmlab/mmdetection/tree/master/configs/scnet/scnet_r50_fpn_1x_coco.py).

