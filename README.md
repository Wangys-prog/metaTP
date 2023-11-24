# <metaTP>
   
# metaTP

metaTP: a pipeline for analyzing meta-transcriptome.metaTP is a pipeline that integrated bioinformatics tools for analyzing metatranscriptomic data comprehensively.It includes quality control, non-coding RNA removal, transcript expression quantification, differential gene expression analysis, functional annotation, co-expression network analysis. 

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
 
### **2. Sequence quality test**

      python 2.QC_test.py -i ./test_sra_data/fastq -o ./test_sra_data/QC_before_result  
      # -i (fastq files)  
      # -o (output_dir)  
      # output_dir: test_sra_data/QC_before_result  

### **2. Sequence quality control, rmrRNA contig cds**

       python 3.QC_rmrRNA_contigs_cds.py -i ./test_sra_data/fastq -o ./test_sra_data  
   
      #Required_dir: trimmomatic_adapters, rRNA_databases  fastq后缀文件  
      #output_dir：test_sra_data/QC_control;test_sra_data/rmrRNA;test_sra_data/magahit  
      # all_longest_orfs_cds_rmdup.fasta  
      #-i (input folder contain fastq )  
      #-threads (thread setting,default=24)  
      #-phred （you can choose "-phred33 or -phred64",default="-phred33"）  
      #-ILLUMINACLIP （paths for adapters,default="trimmomatic_adapters/TruSeq3"）  
      #-LEADING （Remove front-end low-quality sequences or N bases,",type =int,default=5）  
      #-SLIDINGWINDOW (SLIDINGWINDOW:4:15, scan sequences using a 4-base width sliding window and trim when the average mass per base is below 15",
                      default="4:15")  
      #-MINLEN (MINLEN:25, Remove the sequences that less than 25 bases",type =int,
                      default=25)  
      # -m minimum protein length (default: 100)  
   
      #-o (the output folder)  
   
      TransDecoder.LongOrfs #提取开放阅读框架  
      TransDecoder.LongOrfs -t ./target_transcripts.fasta  
	
	'报错  
	/xxxx/xxxx/bin/megahit_core: /xxx/metaTP/bin/../lib/libstdc++.so.6: version `CXXABI_1.3.11' not found (required by /xxx/anaconda3/envs/metaTP2.0/bin/megahit_core)  
    /xxxxx/xxxxx/anaconda3/envs/metaTP/bin/megahit_core: /xxxx/metaTP/bin/../lib/libstdc++.so.6: version `GLIBCXX_3.4.29' not found (required by /xxxx/anaconda3/envs/metaTP2.0/bin/megahit_core)  
    /xxxxx/xxxxx/anaconda3/envs/metaTP/bin/megahit_core: /xxx/envs/metaTP/bin/../lib/libstdc++.so.6: version `GLIBCXX_3.4.22' not found (required by /xxxx/anaconda3/envs/metaTP2.0/bin/megahit_core)  
    /xxxxx/xxxx/anaconda3/envs/metaTP/bin/megahit_core: /xxxx/anaconda3/envs/metaTP/bin/../lib/libstdc++.so.6: version `CXXABI_1.3.13' not found (required by /xxxxx/anaconda3/envs/metaTP2.0/bin/megahit_core)  

	conda install -c anaconda libstdcxx-ng  
	删除anaconda3/envs/metaTP/lib中的 rm -rf libstdc++.so， 保留一个版本的libstdc++.so.6.xxx.xxx'  

## **If you use Effector-GAN, please cite:** 
    (1) Wang Y, .Effector-GAN: prediction of fungal effector proteins based on pre-trained deep representation learning methods and generative adversarial networks
    (2) Yansu Wang, Murong Zhou, Quan Zou, Lei Xu. Machine learning for phytopathology: from the molecular scale towards the network scale. Briefings in Bioinformatics. 2021, Doi: 10.1093/bib/bbab037
    (3) Yansu Wang, Lei Xu, Quan Zou, Chen Lin. prPred-DRLF: plant R protein predictor using deep representation learning features. Proteomics. 2021. DOI: 10.1002/pmic.202100161
