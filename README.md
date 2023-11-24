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

### **1. Download the sra sequence according to the ACC number**

     python 1.prefetch_sra2fastq.py -i SRR_Acc_List.txt -o test_sra_data 

       # -i (SRR_Acc_List.txt)
       # -o (output_dir) 
       # output_dir：test_sra_data； test_sra_data/fastq
 
### **2. Sequence quality control**
、
      python 2.QC_test.py -i ./test_sra_data/fastq -o ./test_sra_data/QC_before_result
      # -i (fastq files)
      # -o (output_dir)
      # output_dir: test_sra_data/QC_before_result
 
 

## **If you use Effector-GAN, please cite:** 
    (1) Wang Y, .Effector-GAN: prediction of fungal effector proteins based on pre-trained deep representation learning methods and generative adversarial networks
    (2) Yansu Wang, Murong Zhou, Quan Zou, Lei Xu. Machine learning for phytopathology: from the molecular scale towards the network scale. Briefings in Bioinformatics. 2021, Doi: 10.1093/bib/bbab037
    (3) Yansu Wang, Lei Xu, Quan Zou, Chen Lin. prPred-DRLF: plant R protein predictor using deep representation learning features. Proteomics. 2021. DOI: 10.1002/pmic.202100161
