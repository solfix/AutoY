# Yang

This repository contains the code and the data to train **AutoY and LSTMY** model.

​    Contact: 1974887272@qq.com
## Project Organization
      ├── AutoY                     
         │
         │
         │     
         ├── README.md                   <- The README for users using AutoY and LSTMY.
         │
         │
         ├── notebooks                   <- AutoY and LSTMY code for jupyter notebook. See README for their usages.
         │   ├── AutoY.ipynb             <- Trainingd and predictions AutoY models.
         │   ├── LSTMY.ipynb             <- Trainingd and predictions LSTMY models. 
         │   ├── Raw_data_processing.ipynb     <- Processing raw data for AutoY models.
         │
         ├── data                       <- Data for training and testing.See README for their usages.
         │   ├── RA
         │   ├── MS                   
         │   ├── TID                     
         │   ├── IAA                   
         │   ├── Health   
         │   ├── PCA15.txt  
         │   └── Example_raw_file.tsv        
         │
         ├── model
         │   ├── AutoY                <- Model for storing the optimal AutoY  
         │   ├── LSTMY                <- Model for storing the optimal LSTMY    
         ├── python_codes             <- Code for EarlyStopping    
         ├── LICENSE                  <- copyright statement  
       
             

## Usage

### Python and essential packages

```
python         3.10.9
numpy          1.23.5
pandas         1.5.3
torch      2.0.1+cu117
```

### Input file format

The input files are tsv files in the following format:

```
TCR	Abundance
CATSDNSGGQPQHF	0.21069978688318255
CASSETGTYGYTF	0.034178689598235334
CASSYSSFSGELFF	0.01868772093003411
CASRTGGYGYTF	0.009927318418711613
CASSVLNTGELFF	0.009917718562069473
CASSLSVGPYEQYF	0.007108160518136263
CASSQGERGGNEQYF	0.006789231947469584
CASSAIRGVNTEAFF	0.006762565679019193
......
```

The sequences in the `TCR` column are the top 100 most abundant TCRs.

You can use the following command to extract TCR and its frequency information from raw files:

```
 jupyter notebook Raw_data_processing.ipynb 
 -----isource_dir = "../data/ Example_raw_file.tsv"  #Original file path
 -----output =  "../The path to the file you want to save/"  #Save the path to the processed file
```

### Cancer index prediction with pre-trained models

Prediction of all TCR files in a directory

```
 jupyter notebook AutoY.ipynb 
 
 -----aa_file = "../data/PCA15.txt"  #Amino acid characterization file path
 -----disease_list = ["RA", "T1D", "MS", "IAA"]  #Documentation of processed autoimmune diseases
 -----data_dir = f'../data/{disease_name}' #Disease File Path
 ----- model_path = f'../model/AutoY/{disease_name}checkpoint{fold}.pt' #Save path of the model file
 
```
```
 jupyter notebook LSTMY.ipynb 
 
 -----aa_file = "../data/PCA15.txt"  #Amino acid characterization file path
 -----disease_list = ["RA", "T1D", "MS", "IAA"]  #Documentation of processed autoimmune diseases
 -----data_dir = f'../data/{disease_name}' #Disease File Path
 ----- model_path = f'../model/LSTMY/{disease_name}checkpoint{fold}.pt' #Save path of the model file
 
```
### Result

The metrics, accuracy, sensitivity, specificity, and area under the receiver operating characteristic (ROC) curve (AUC), are calculated and printed as:
``` 
 ----- T1D-----
Mean Accuracy (T1D): 0.9757
Mean Sensitivity (T1D): 0.9594
Mean Specificity (T1D): 0.9907
Mean AUC (T1D): 0.9970

```


