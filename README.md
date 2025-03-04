# SITP-QLEF dataset

> Guo L, Rao P, Gao C, et al. Adaptive Differential Event Detection for Space-Based Infrared Aerial Targets[J]. Remote Sensing, 2025, 17(5): 845.

The SITP-QLEF dataset is the first IR event dataset for space-based dim small target detection, including event frames and corresponding ground truth labels.

## Abstract

We have designed and released the first IR event datasets for space-based dim small target detection, including event frames and corresponding ground truth (GT) labels. The dataset simulates real satellite platform jitter, with the camera operating in staring mode for aerial target detection scenarios. The backgrounds are derived from images captured by the Qilu Satellite-2 (QLSAT-2) long-wave infrared (LWIR) camera. The aerial targets are modeled using two-dimensional Gaussian fitting, reflecting real motion information and grayscale variations. To advance research on IR event detection, the proposed dataset addresses the current lack of publicly available datasets.

------

## Dataset Download

The dataset can be downloaded here (**Baidu Netdisk**): https://pan.baidu.com/s/1hTN44fWdwyBv9WuCdt53_Q?pwd=sgk7 

code：sgk7 

PDF Version: https://www.mdpi.com/2072-4292/17/5/845/pdf

------

## Data Structure

```
SITP_QLEF_single_event_frame
	-images
		--train
		--val
		--test
	-labels
		--train
		--val
		--test
SITP_QLEF_accumulated_event_frame
	-images
		--train
		--val
		--test
	-labels
		--train
		--val
		--test
```

For training and testing the network model, we format this dataset into YOLO's TXT format, where images and labels are stored in separate folders and split into training and validation sets according to a certain ratio. Each TXT file contains the target class and bounding box coordinates in the following format:

```
[class x_center y_center w h]
```

- class: Target category ID.
- x_center, y_center, w, h: Bounding box center coordinates, width, and height. These values are normalized relative to the entire image, with values less than 1.

The dataset is divided into training, validation, and test sets. 

|       | single event frame | accumulated event frame |
| ----- | ------------------ | ----------------------- |
| train | 8669               | 8706                    |
| val   | 1266               | 1271                    |
| test  | 1161               | 1165                    |

------

## Details

In this dataset, the background data are derived from the QLSAT-2 high-resolution optical camera, the core payload of QLSAT-2 developed by the Shanghai Institute of Technical Physics (SITP). The QLSAT-2 LWIR camera has a ground resolution of 14 m at an altitude of 500 km. The dataset uses real remote sensing LWIR images as backgrounds, including scenes such as cities, land, and clouds. In real scenarios, a satellite platforming jitter follows a distribution with a standard deviation of approximately $0.004^{\circ}$, resulting in platform speeds set between zero and three pixels per frame. The original imaging size of the targets is $5\times5$ pixels, with a mean SNR of 4.

The parameters of the dataset are as follows:

|                               | Parameters     |
| ----------------------------- | -------------- |
| Target Size                   | $5\times5$     |
| Target Number                 | 1–3            |
| SNR                           | 4              |
| Target Speed (Pixel/Frame)    | 1–1.4          |
| Platform  Speed (Pixel/Frame) | 0–3            |
| Sequences $\times$ Frame      | $67\times200$  |
| Resolution                    | $256\times256$ |
| Band                          | LWIR           |

------

## Citation

If you found our work useful, please cite
```
@article{guo2025adaptive,
title={Adaptive Differential Event Detection for Space-Based Infrared Aerial Targets},
author={Guo, Lan and Rao, Peng and Gao, Cong and Su, Yueqi and Li, Fenghong and Chen, Xin},
journal={Remote Sensing},
volume={17},
number={5},
pages={845},
year={2025},
publisher={Multidisciplinary Digital Publishing Institute}
}
```
