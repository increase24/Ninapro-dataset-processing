# Ninapro-dataset-processing
This repository provides the processing flow of Ninapro datasets and the pytorch dataloader of the processed Ninapro data.

## Ninapro Dataset Processing
The experiment are taken on the [Ninapro dataset](http://ninaweb.hevs.ch/). The first sub-dataset DB1 and second sub-dataset DB2 are ultilized. 
1. Firstly download the [Ninapro DB1](http://ninaweb.hevs.ch/data1) and [Ninapro DB2](http://ninaweb.hevs.ch/data2) datasets. And then extract the data files from the zip files. We provide two jupyter notebooks [extractFile_db1](https://github.com/increase24/Ninapro-dataset-processing/blob/master/processing/extractFile_db1.ipynb) / [extractFile_db2](https://github.com/increase24/Ninapro-dataset-processing/blob/master/processing/extractFile_db2.ipynb) under the directory **processing** for extracting DB1 / DB2 respectively.
After extraction, your directory tree should look like this: 

```
${ROOT}/data/ninapro
├── db1
|   |—— s1
|   |—— s2
|   |   ...
|   └── s27
|       |—— S27_A1_E1.mat
|       |—— S27_A1_E2.mat
|       └── S27_A1_E3.mat
└── db2
    |—— DB2_s1
    |—— DB2_s2
    |   ...
    └── DB2_s40
        |—— S40_E1_A1.mat
        |—— S40_E2_A1.mat
        └── S40_E3_A1.mat
```

2. Secondly run the jupyter notebook script [process_db1](https://github.com/increase24/Ninapro-dataset-processing/blob/master/processing/process_db1.ipynb) / [process_db2](https://github.com/increase24/Ninapro-dataset-processing/blob/master/processing/process_db2.ipynb), which convert the mat files to txt files.
After convertion, your directory tree should look like this: 
```
${ROOT}/data/ninapro
├── db1_processed
|   |—— s1
|   |—— s2
|   |   ...
|   └── s27
|       |—— emg.txt
|       |—— rerepetition.txt
|       └── restimulus.txt
└── db2_processed
    |—— DB2_s1
    |—— DB2_s2
    |   ...
    └── DB2_s40
        |—— emg.txt
        |—— rerepetition.txt
        └── restimulus.txt
```

## Ninapro Dataloader
We provide dataloaders of Ninapro DB1 and Ninapro DB2 for pytorch network training.
### Unit testing of Ninapro DB1/DB2 dataloader
```
# Ninapro DB1 dataloader
python ./dataloaders/db1.py 
# Ninapro DB2 dataloader
python ./dataloaders/db2.py
```
### Embeded into pytorch training code
utilizing dataloader of Ninapro DB1:
```
from dataloaders.db1 import get_dataloader_db1
train_loader, val_loader = get_dataloader_db1(DataConfig, path_subject)
```
utilizing dataloader of Ninapro DB1:
```
from dataloaders.db2 import get_dataloader_db2
train_loader, val_loader = get_dataloader_db2(DataConfig, path_subject)
```
the configuration of **DataConfig** and **path_subject** can be seen from the unit testing of [db1.py](https://github.com/increase24/Ninapro-dataset-processing/blob/master/dataloaders/db1.py) and [db2.py](https://github.com/increase24/Ninapro-dataset-processing/blob/master/dataloaders/db2.py)

## Contact
If you have any questions, feel free to contact me through jia.zeng@sjtu.edu.cn or Github issues.