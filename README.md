# MSC_TransUNet
This repo holds code for MSC-TransUNet
## Usage
### 1. Download Google pre-trained ViT model
- Get model in this [link](https://console.cloud.google.com/storage/vit_models/) to get R50+ViT-B_16.npz
- Move pre-trained model into "./model/vit_checkpoint/imagemet21k/"
```
mv R50+ViT-B_16.npz ./model/vit_checkpoint/imagenet21k/R50+ViT-B_16.npz
```

### 2. Prepare Data
- We use "**ACDC**" and "**Synapse**" to evaluate our model. You can download datasets in this link [ACDC](https://www.creatis.insa-lyon.fr/Challenge/acdc/) and [Synapse](https://www.synapse.org/!Synapse:syn3193805/wiki/217789)
- After downloading datasets, we move them into the data directory, and the directory  structure as followed:
- 
```
.
├── MSU-TransUNet
│   ├──datasets
│   │       └── dataset_*.py
│   ├──train.py
│   ├──test.py
│   └──...
├── model
│   └── vit_checkpoint
│       └── imagenet21k
│           └── R50+ViT-B_16.npz
│           
└── data
    └──Synapse
    │    ├── test_vol_h5
    │    │   ├── case0001.npy.h5
    │    │   └── *.npy.h5
    │    └── train_npz
    │       ├── case0005_slice000.npz
    │       └── *.npz
    └ ─ACDC
         ├── test
         │   ├── case_0002_volume_ED.npy
         │   └── *.npy
         └── train
         │   ├── case_001_sliceED_0.npz
         │   └── *.npz
         └── valid
             ├── ccase_019_sliceED_0.npz
             └── *.npz
```
### 3. Environment
Please prepare environment with python >= 3.7 
### 4. Train
- Run the train script on Synapse dataset.

```
python train.py --dataset Synapse --vit_name R50-ViT-B_16 --batch_size 24 --max_epochs 1000
```

- Run the train script on ACDC dataset.
```
python train.py --dataset ACDC --vit_name R50-ViT-B_16 --batch_size 24 --max_epochs 1000
```
### 5. Test 
- Run the test script on Synapse dataset. 
```
python test.py --dataset Synapse --vit_name R50-ViT-B_16
```
- Run the test script on ACDC dataset. 
```
python test.py --dataset ACDC --vit_name R50-ViT-B_16
```
## Citations
```
@article{chen2021transunet,
  title={TransUNet: Transformers Make Strong Encoders for Medical Image Segmentation},
  author={Chen, Jieneng and Lu, Yongyi and Yu, Qihang and Luo, Xiangde and Adeli, Ehsan and Wang, Yan and Lu, Le and Yuille, Alan L., and Zhou, Yuyin},
  journal={arXiv preprint arXiv:2102.04306},
  year={2021}
}
```
