# covid19-sounds-NeurIPS2021
This repo is for our submission *COVID-19 Sounds: A Large-Scale Audio Dataset for Digital COVID-19 Detection.*

## Dataset

As introduced in the paper, for full data access, a DTA should be signed. Subsets of two evaluated tasks are also available on request.

Contact: covid-19-sounds@cl.cam.ac.uk

## Codes

Our model is implemented by Python3 with Tensorflow. To reproduce the results, codes are provided. 

Requirements: setup.py

### Automatic audio quality check

[Yamnet](https://www.tensorflow.org/hub/tutorials/yamnet) is deployed to detect whether a sample is qualified: it should contain breathing, cough, or speech.  Silent and noising samples will be labelled and excluded from experiments.  We have already prepared the check list for all samples, but the codes are provided if researchers need to conduct their own data selection. 

`python ./YAMNet/Inference_save.py`
`python ./YAMNet/prediction_via_inference.py`

Examples of the output as follows,

![quality](./quality.png)



### Benchmark implementation

Transfer learning  is applied for our task based on a pre-trained CNN model named  [VGGish](https://modelzoo.co/model/audioset). For both tasks, we implemented three baselines: OpenSMILE+SVM, Pre-trained VGGish, Fine-tuned VGGish. A simple illustration of the methods is as follows,

![model](./model.png)

### Task1: Respiratory symptom prediction.
- OpenSMILE+SVM: 
  -   Go to the path `cd ./Respiratory_prediction/Opensmile`
  -   Extract feature `python 1_extract_opensmile.py`
  -   Classification `python 2_classifcation.py`
- Pre-trained VGGish: 
- Go to the model path `cd ./Respiratory_prediction/model`
- Train the model `sh run_train_frozen.sh` 
- Test the model `sh run_test_frozen.sh` 
- Fine-tuned VGGish: 
  - Go to the model path `cd ./Respiratory_prediction/model`
  - Train the model `sh run_train.sh` 
  - Test the model `sh run_test.sh` 
Results are summarisd in Table2,
![model](./table2.png)
### Task2: COVID-19 prediction.
- OpenSMILE+SVM: 
  -   Go to the path `cd ./COVID19_prediction/Opensmile`
  -   Extract feature `python 1_extract_opensmile.py`
  -   Classification `python 2_classifcation.py`
- Pre-trained VGGish: 
- Go to the model path `cd ./COVID19_prediction/COVID_model`
- Train the model `sh run_train_frozen.sh` 
- Test the model `sh run_test_frozen.sh` 
- Fine-tuned VGGish: 
  - Go to the model path `cd ./COVID19_prediction/COVID_model`
  - Train the model `sh run_train.sh` 
  - Test the model `sh run_test.sh` 
 
Results are summarisd in Table3,
  ![model](./table3.png)


### Issues

This code project is developed by Tong Xia. Any problem, please contact me by tx229@cam.ac.uk.