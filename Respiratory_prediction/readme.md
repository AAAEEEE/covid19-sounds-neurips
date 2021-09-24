# Task1: Respiratory symptom prediction.

## Data:  

- Raw audio: ./data/0426_EN_used_task1
- Meta data and split: ./data/data_0426_en_task1.csv
- Pre-process: `python pickle_data.py``python pickle_user.py`

## Code

- OpenSMILE+SVM: 
  -   Go to the path `cd ./Opensmile`
  -   Extract feature `python 1_extract_opensmile.py`
  -   Classification `python 2_classifcation.py`
- Pre-trained VGGish: 
- Go to the model path `cd ./model`
- Train the model `sh run_train_frozen.sh` 
- Test the model `sh run_test_frozen.sh` 
- Fine-tuned VGGish: 
  - Go to the model path `cd ./model`
  - Train the model `sh run_train.sh` 
  - Test the model `sh run_test.sh` 