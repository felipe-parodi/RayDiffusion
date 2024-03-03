# Cameras as Rays

[[`arXiv`](https://arxiv.org/abs/2402.14817)]
[[`Project Page`](https://jasonyzhang.com/RayDiffusion/)]
[[`Bibtex`](#citing-cameras-as-rays)]

This repository contains code for "Cameras as Rays: Pose Estimation via Ray Diffusion" (ICLR 2024).

## Setting up Environment

If you're installing on Windows, first install Visual Studio C++ Desktop Development. Then, ensure CUDA and conda are all on PATH.

Find a version of Pytorch compatible with your CUDA version from the [Pytorch website](https://pytorch.org/get-started/locally/). Note: if you pip install xformers, then use the latest Pytorch version.

```
conda create -n raydiffusion python=3.10
conda activate raydiffusion
conda install pytorch==2.2.0 torchvision==0.16.1 torchaudio==2.1.1 pytorch-cuda=11.8 -c pytorch -c nvidia
pip install --pre -U xformers
pip install -r requirements.txt
pip install timm
```

Then, follow the directions to install Pytorch3D on Windows [here](https://github.com/facebookresearch/pytorch3d/blob/main/INSTALL.md).
```
git clone pytorch3d
cd pytorch3d
python setup.py install
```

## Run Demo

Download the model weights from [Google Drive](https://drive.google.com/file/d/1anIKsm66zmDiFuo8Nmm1HupcitM6NY7e/view?usp=drive_link).

Run ray diffusion with known bounding boxes (provided as a json):
```
python demo.py  --model_dir models/co3d_diffusion --image_dir examples/robot/images \
    --bbox_path examples/robot/bboxes.json --output_path robot.html
```

Run ray diffusion with bounding boxes extracted automatically from masks:
```
python demo.py  --model_dir models/co3d_diffusion --image_dir examples/robot/images \
    --mask_dir examples/robot/masks --output_path robot.html
```

Run ray regression:
```
python demo.py  --model_dir models/co3d_regression --image_dir examples/robot/images \
    --bbox_path examples/robot/bboxes.json --output_path robot.html
```

## Code release status
- [x] Demo Code
- [ ] Evaluation Code
- [ ] Training Code

## Citing Cameras as Rays

If you find this code helpful, please cite:

```
@InProceedings{zhang2024raydiffusion,
    title={Cameras as Rays: Pose Estimation via Ray Diffusion},
    author={Zhang, Jason Y and Lin, Amy and Kumar, Moneish and Yang, Tzu-Hsuan and Ramanan, Deva and Tulsiani, Shubham},
    booktitle={International Conference on Learning Representations (ICLR)},
    year={2024}
}
```
