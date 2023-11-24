# <metaTP>
   
# metaTP

metaTP: a pipeline for analyzing meta-transcriptome.

metaTP is a pipeline that integrated bioinformatics tools for analyzing metatranscriptomic data comprehensively.

It includes quality control, non-coding RNA removal, transcript expression quantification, differential gene expression analysis, functional annotation, co-expression network analysis. 

Before running Effector-GAN, users should make sure all the following packages are installed in their Python environment. 


## **Prerequisites**
### **Install conda software**
### **Downloaded the conda environment** 
      sftp -oPort=60000 ftpuser@47.109.24.44:6000
      ftpuser@47.109.24.44's password: ftpuser
      cd ftp_soft
      get -r metaTP.tar.tgz
      tar zxvf  metaTP.tar.tgz -C ./   
      conda create -n metaTP
      tar -xzvf metaTP.tar.gz -C /home/xxx/anaconda3/envs/metaTP
      conda activate metaTP
   
### **The codes can be downloaded from our FTP**
      
      get -r metaTP_pipeline.tar.tgz
      tar -xzvf metaTP_pipeline.tar.tgz
      cd metaTP_pipeline

**1. Download the sra sequence according to the ACC number**

     python 1.prefetch_sra2fastq.py -i SRR_Acc_List.txt -o test_sra_data 

     ` # -i (SRR_Acc_List.txt)`  
     ` # -o (output_dir)`  
     ` # output_dir：test_sra_data； test_sra_data/fastq`  

   
   `source ~/.bashrc`
 
## **Installation**

  **Create an Python3.7 environment using conda:**
    
  `conda create -n Effector-GAN python=3.7`
    
  **Activate conda environment:**
    
  `conda activate Effector-GAN`
  
 **For python3.7 **
 
   **pytorch: https://pytorch.org/get-started/previous-versions/**
   
  **conda install**
   
    **# CUDA 10.0**
    
    conda install pytorch==1.3.1 torchvision==0.4.2 cudatoolkit=10.0 -c pytorch
    
    **# CPU Only**
    
    conda install pytorch==1.3.1 torchvision==0.4.2 cpuonly -c pytorch
    
  **pip install**
  
    **If you have GPU  # CUDA 10.0**
  
    pip install torch==1.3.1 torchvision==0.4.2
  
    **CPU Only python3.7**
    
    pip install torch==1.3.1+cpu torchvision==0.4.2+cpu -f https://download.pytorch.org/whl/torch_stable.html
  
 **other packages** 
   
    pip3 install joblib==1.0.1  
    pip3 install tape_proteins==0.5 
    pip3 install numpy==1.19.2 
    pip3 install pandas==1.2.0 
    pip3 install Bio==1.0.2
    pip3 install sklearn


## **Effector-GAN**

    git clone http://47.109.24.44:4747/wangys_biolab/effector-gan.git
  
    cd effector-gan

## Input parameters

    python Effector_GAN.py -h  
    $ -i  inputfile in FASTA format  
    $ -o  output csv file
 
## Usage

    conda activate Effector-GAN
    
  `python Effector_GAN.py -i independent_test_pos.fasta -o test_result.csv` 
  
### The model will run faster in GPU than CPU  
   
    For the test data (independent_test_pos.fasta), UniRep Embedding will take about 11 minutes in CPU and 0.239 mins in GPU
     `
## WGAN.py

     Synthetic protein feature samples based on generative adversarial networks

## CTST2.py
   
     Effector-GAN uses the leave-one-out cross-validation (LOOCV) method based on K nearest neighbor algorithm (KNN; K=1) classifier to evaluate the optimal synthetic protein feature samples, which are used to augment the original positive training samples

## figure_tsne.py
  
    t-SNE-transformed 2D visualization of real and synthetic protein feature samples obtained from different training iterations

## other tools

    http://lab.malab.cn/~wys/

## **If you use Effector-GAN, please cite:** 
    (1) Wang Y, .Effector-GAN: prediction of fungal effector proteins based on pre-trained deep representation learning methods and generative adversarial networks
    (2) Yansu Wang, Murong Zhou, Quan Zou, Lei Xu. Machine learning for phytopathology: from the molecular scale towards the network scale. Briefings in Bioinformatics. 2021, Doi: 10.1093/bib/bbab037
    (3) Yansu Wang, Lei Xu, Quan Zou, Chen Lin. prPred-DRLF: plant R protein predictor using deep representation learning features. Proteomics. 2021. DOI: 10.1002/pmic.202100161
