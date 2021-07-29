# Visual Saliency Transformer (VST)

source code for our ICCV 2021 paper “Visual Saliency Transformer” by Nian Liu, Ni Zhang, Kaiyuan Wan, Junwei Han, and Ling Shao.

created by Ni Zhang, email: nnizhang.1995@gmail.com

![avatar](https://github.com/nnizhang/VST/blob/main/Network.png)

## Requirement
1. Pytorch 1.6.0
2. Torchvison 0.7.0

## RGB VST for RGB Salient Object Detection
### Data Preparation
#### Train Set
We use the training set of [DUTS](http://saliencydetection.net/duts/) to train our VST for RGB SOD. Besides, we follow [Egnet](https://github.com/JXingZhao/EGNet) to generate contour maps of DUTS trainset for training. You can directly download the generated contour maps (DUTS-TR-Contour) from [[baidu pan](https://pan.baidu.com/s/17OnUi09YuOOq23xNrdYCLQ) fetch code: ow76 | [Google drive](https://drive.google.com/file/d/1NizY8WZSz-5i5KV7bATODi76fovrLuVf/view?usp=sharing)] and put it into `RGB_VST/Data` folder.

#### Test Set
We use the testing set of [DUTS](http://saliencydetection.net/duts/), [ECSSD](http://www.cse.cuhk.edu.hk/leojia/projects/hsaliency/dataset.html), [HKU-IS](https://i.cs.hku.hk/~gbli/deep_saliency.html), [PASCAL-S](http://cbi.gatech.edu/salobj/), [DUT-O](http://saliencydetection.net/dut-omron/), and [SOD](http://elderlab.yorku.ca/SOD.) to test our VST. After Downloading, put them into `RGB_VST/Data` folder.

Your `RGB_VST/Data` folder should look like this:

````
-- Data
   |-- DUTS
   |   |-- DUTS-TR
   |   |-- | DUTS-TR-Image
   |   |-- | DUTS-TR-Mask
   |   |-- | DUTS-TR-Contour
   |   |-- DUTS-TE
   |   |-- | DUTS-TE-Image
   |   |-- | DUTS-TE-Mask
   |-- ECSSD
   |   |--images
   |   |--GT
   ...
````

### Training, Testing, and Evaluation
1. `cd RGB_VST`
2. Download the pretrained T2T-ViT_t-14 model [[baidu pan](https://pan.baidu.com/s/1adESOUSpErZEceyLIoNOxQ) fetch code: 2u34 | [Google drive](https://drive.google.com/file/d/1R63FUPy0xSybULqpQK6_CTn3QgNog32h/view?usp=sharing)] and put it into `pretrained_model` folder.
3. Run `python train_test_eval.py --Training True --Testing True --Evaluation True` for training, testing, and evaluation. The predictions will be in `preds/` folder and the evaluation results will be in `result.txt` file.

### Testing on Our Pretrained RGB VST Model
1. `cd RGB_VST`
2. Download our pretrained `RGB_VST.pth`[[baidu pan](https://pan.baidu.com/s/1oVeMDmffc8M1RgRUbZEdpQ) fetch code: pe54 | [Google drive](https://drive.google.com/file/d/1tZ3tQkQ7jlDDfF-_ZROnEZg44MaNQFMc/view?usp=sharing)] and then put it in `checkpoint/` folder.
3. Run `python train_test_eval.py --Training False --Testing True --Evaluation True` for testing and evaluation. The predictions will be in `preds/` folder and the evaluation results will be in `result.txt` file.

Our saliency maps can be download from [[baidu pan](https://pan.baidu.com/s/1CDkCjq9fRvOHLou9S9oGiA) fetch code: 92t0 | [Google drive](https://drive.google.com/file/d/1T4zDvBobQdT7L7i0HijOZSMfTS5hK-Ec/view?usp=sharing)].

### SOTA Saliency Maps for Comparison
Coming soon...


## RGB-D VST for RGB-D Salient Object Detection
### Data Preparation
#### Train Set
We use 1,485 images from NJUD, 700 images from NLPR, and 800 images from DUTLF-Depth to train our VST for RGB-D SOD. Besides, we follow [Egnet](https://github.com/JXingZhao/EGNet) to generate corresponding contour maps for training. You can directly download the whole training set from here [[baidu pan](https://pan.baidu.com/s/13mvL8pl6AacDdPd4jK44fg) fetch code: 7vsw | [Google drive](https://drive.google.com/file/d/1vK_PLtB4o-LMrVtQlnVysmQpB8MpSlRA/view?usp=sharing)] and put it into `RGBD_VST/Data` folder.

#### Test Set
We use the testing set of NJUD [[baidu pan](https://pan.baidu.com/s/1ywIJV_C0lG1KZNFow87bQQ) fetch code: 7mrn | [Google drive]()], NLPR [[baidu pan](https://pan.baidu.com/s/1G3ec34XV7oQboY8R9FPVDw) fetch code: tqqm | [Google drive]()], and DUTLF-Depth [[baidu pan](https://pan.baidu.com/s/1BZepaCfo2BsuvBczJKhN4Q) fetch code: 9jac | [Google drive]()] and STERE [[baidu pan](https://pan.baidu.com/s/16ros8tHMxy9YwfqBZJf1zQ) fetch code: 93hl | [Google drive]()], LFSD [[baidu pan](https://pan.baidu.com/s/1sSjFX45DIcNyExsA_lpybQ) fetch code: l2g4 | [Google drive]()], RGBD135 [[baidu pan](https://pan.baidu.com/s/1NQiTSYIs23Cl4TCf7Edp0A) fetch code: apzb | [Google drive]()], SSD [[baidu pan](https://pan.baidu.com/s/1Ihx001o1MUYaUtbBQH4TnQ) fetch code: j3v0 | [Google drive]()], SIP [[baidu pan](https://pan.baidu.com/s/1qvpfXrPYT94M6mD0pv3-SQ) fetch code: q0j5 | [Google drive]()], and [ReDWeb-S](https://github.com/nnizhang/SMAC) to test our VST. 

Your `RGBD_VST/Data` folder should look like this:

````
-- Data
   |-- NJUD
   |   |-- trainset
   |   |-- | RGB
   |   |-- | depth
   |   |-- | GT
   |   |-- | contour
   |   |-- testset
   |   |-- | RGB
   |   |-- | depth
   |   |-- | GT
   |-- STERE
   |   |-- RGB
   |   |-- depth
   |   |-- GT
   ...
````

### Training, Testing, and Evaluation
1. Download the pretrained T2T-ViT_t-14 model [[baidu pan](https://pan.baidu.com/s/1adESOUSpErZEceyLIoNOxQ) fetch code: 2u34 | [Google drive](https://drive.google.com/file/d/1R63FUPy0xSybULqpQK6_CTn3QgNog32h/view?usp=sharing)].

Coming soon...

### Testing on Our Pretrained RGB-D VST Model

Our saliency maps can be download from [[baidu pan](https://pan.baidu.com/s/1yPo9C-WrBXiN8WXNEOP4Hg) fetch code: jovk | [Google drive](https://drive.google.com/file/d/1ccpQv6dnZbC-hx9pZjNTTI-_5qm8QLm9/view?usp=sharing)].

Coming soon...

### SOTA Saliency Maps for Comparison
Coming soon...

## Acknowledgement
We thank the authors of [Egnet](https://github.com/JXingZhao/EGNet) for providing codes of generating contour maps. We also thank [Zhao Zhang](https://github.com/zzhanghub/eval-co-sod) for providing the efficient evaluation tool.

## Citation
If you think our work is helpful, please cite 
```
@inproceedings{liu2021VST, 
  title={Visual Saliency Transformer}, 
  author={Liu, Nian and Zhang, Ni and Han, Junwei and Shao, Ling},
  booktitle={Proceedings of the IEEE/CVF International Conference on Computer Vision},
  year={2021}
}
```



