## Overview

This is the source code of paper "Multi-Head Transformer Architecture with Higher Dimensional Feature Representation for Massive MIMO CSI Feedback".
## Requirements

You need to satisfy the following requirements.

- Python >= 3.7
- [1.2 =< PyTorch <= 1.6](https://pytorch.org/get-started/locally/)
- [thop](https://github.com/Lyken17/pytorch-OpCounter)
- [tensorboardX](https://github.com/lanpa/tensorboardX)

## Project Preparation

#### A. Data Preparation

The CSI matrix is generated from [COST 2100](https://ieeexplore.ieee.org/document/6393523) channel model. Chao-Kai Wen and Shi Jin group provides a pre-processed version of COST 2100 dataset in [Google Drive](https://drive.google.com/drive/folders/1_lAMLk_5k1Z8zJQlTr5NRnSD6ACaNRtj?usp=sharing). You can also download it from [Baidu Netdisk](https://pan.baidu.com/s/1Ggr6gnsXNwzD4ULbwqCmjA).

#### B. Project Tree Arrangement

We recommend you to arrange the project tree as follows.

```
home
├── TransNet+ 
│   ├── dataset
│   ├── models
│   ├── utils
│   ├── main.py
├── COST2100  
│   ├── DATA_Htestin.mat
│   ├── ...
├── Results
│   ├── checkpoints
│   │     ├── 4_in.pth
│   │     ├── ...
│   ├── run.sh
...
```

## Train TransNet+ from Scratch

An example of run.sh is listed below. Simply use it with `sh run.sh`. It will start TransNet+ training from scratch.

``` bash
python /home/TransNet+/main.py \
  --data-dir '/home/COST2100' \
  --scenario 'in' \
  --epochs 1000 \
  --batch-size 200 \
  --workers 0 \
  --cr 4 \
  --scheduler const \
  --gpu 0 \
  2>&1 | tee log.out
```

## Results and Reproduction

The main results reported in our paper are presented as follows. All the listed results can be found in Table 1 and Table 3 of our paper. The epoch is set as 1000.

Scenario | Compression Rate | NMSE | Flops
:--: | :--: | :--: | :--: 
indoor | 1/4 | -33.12 | 35.65M 
indoor | 1/8 | -23.47 | 34.60M 
indoor | 1/16 | -15.70 | 34.08M 
indoor | 1/32 | -11.98 | 33.82M 
indoor | 1/64 | -7.99 | 33.69M 
outdoor | 1/4 | -15.80 | 35.65M 
outdoor | 1/8 | -9.86 | 34.60M 
outdoor | 1/16 | -7.88 | 34.08M 
outdoor | 1/32 | -4.87 | 33.82M 
outdoor | 1/64 | -3.07 | 33.69M 

## Acknowledgment

Thank Chao-Kai Wen and Shi Jin group again for providing the pre-processed COST2100 dataset, you can find their related work named CsiNet in [Github-Python_CsiNet](https://github.com/sydney222/Python_CsiNet) 
