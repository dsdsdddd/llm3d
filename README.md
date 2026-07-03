# llm3d
<h1 align="center"><strong>A Geometry-Aware Vision-Language Model for 3D Scene
Understanding</strong></h1>
<h1 align="center">
  <strong></strong>
   <img src="figure1.jpg" align="center" width="100%">
</h1>



## 🌟 Overview

We propose a geometry-aware vision-language model for 3D scene understanding. Taking 3D point clouds and textual instructions as inputs, the proposed method adopts a two-stage training framework to achieve comprehensive modeling from scene-object perception to cross-modal semantic generation.

Environment Setup

Install Dependencies

Python 3.8.16 + CUDA 11.6

Core packages: h5py scipy cython 'trimesh<2.35.40' 'networkx<2.3' 'torch=1.13.1+cu116' 'transformers>=4.37.0'

Build extensions:

cd third_party/pointnet2 && python setup.py install

cd utils && python cython_compile.py build_ext --inplace


### 📂 Datasets
Our repo requires the 3D data from ScanNet, the natural language annotations, and the pre-trained LLM weights.

Step 1. Download and Prepare the ScanNet 3D Data.

1.Follow the instructions [here](https://github.com/ch3cook-fdu/Vote2Cap-DETR/tree/master/data/scannet) and download the ScanNetV2 dataset.

2.Change the SCANNET_DIR to the scans folder in [here](https://github.com/ch3cook-fdu/Vote2Cap-DETR/blob/master/data/scannet/batch_load_scannet_data.py))., and run the following commands.

cd data/scannet/

python batch_load_scannet_data.py

Step 2. Prepare Language Annotations

To train the model, you are required to prepare language annotations from ScanRefer, ScanQA.

ScanRefer. Follow the commands [here](https://github.com/daveredrum/ScanRefer)) to download the ScanRefer dataset.

ScanQA. Follow the commands [here](https://github.com/ATR-DBI/ScanQA/blob/main/docs/dataset.md)) to download the ScanQA dataset.

Step 3. Pre-trained LLM Weights (Optional)
Download opt-1.3b from HuggingFace to ./facebook/opt-1.3b (include config.json, pytorch_model.bin etc.)

## 🚀 Getting started

Training Commands

the first stage

bash scripts/train_stage1_detector.sh

the second stage

bash/scripts/opt-1.3b/tuning.scanqa.sh

Evaluation Commands

bash scripts/opt-1.3b/eval.scanqa.sh
