# Diffusion Generative Adversial network

DiffMIC is a project to adapt [Diffusion Probabilistic Models](https://proceedings.neurips.cc/paper/2020/hash/4c5bcfec8584af0d967f1ab10179ca4b-Abstract.html) to general medical image classification by dual-granularity conditional guidance.
The method is elaborated in the paper [DiffMIC: Dual-Guidance Diffusion Network for Medical Image Classification](https://arxiv.org/abs/2303.10610).

## A Quick Overview 

<img width="800" height="400" src="https://github.com/KianAnbarestani/Diffusion-Gan-for-eye-disease-classifciation-/tree/main/figs/framework.png">

## Requirement

``conda env create -f environment.yml``
or you can simply create your own env and 
either use your own env if the libraries are added 

## Datasets

1. Download [HAM10000](https://challenge.isic-archive.com/data/#2018) or [APTOS2019](https://www.kaggle.com/competitions/aptos2019-blindness-detection/data) dataset or any dataset you want but you should create a pkl file and customize the database based on the infos .we added a custome loader dataset on the root for this situation. Your dataset folder under "your_data_path" should be like:

dataset/isic2018/

     images/...
     
     ISIC2018_Task3_Training_GroundTruth.csv
     
     isic2018_train.pkl

     isic2018_test.pkl

.pkl file contains the list of data whose element is a dictionary with the format as ``{'img_root':image_path,'label':label}``

## Run

2. For Training! run: ``bash training_scripts/run_isic.sh`` where the first command line is used ``python main.py --device ${DEVICE_ID} --thread ${N_THREADS} --loss ${LOSS} --config configs/${TASK}.yml --exp $EXP_DIR/${MODEL_VERSION_DIR} --doc ${TASK} --n_splits ${N_SPLITS}``

3. For Testing! run: ``bash training_scripts/run_isic.sh`` where the second command line is used ``python main.py --device ${DEVICE_ID} --thread ${N_THREADS} --loss ${LOSS} --config $EXP_DIR/${MODEL_VERSION_DIR}/logs/ --exp $EXP_DIR/${MODEL_VERSION_DIR} --doc ${TASK} --n_splits ${N_SPLITS} --test --eval_best``

The configuration for each of the above-listed tasks (including data file location, training log and evaluation result directory settings, neural network architecture, optimization hyperparameters, etc.) are provided in the corresponding files in the ``configs`` directory


## Thanks

Code is largely based on [XzwHan/CARD](https://github.com/XzwHan/CARD), [CompVis/stable-diffusion](https://github.com/CompVis/stable-diffusion), [MedSegDiff](https://github.com/WuJunde/MedSegDiff/tree/master), [nyukat/GMIC](https://github.com/nyukat/GMIC)




