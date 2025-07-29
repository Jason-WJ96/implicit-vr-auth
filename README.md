<!-- # Implicit VR User Authentication -->

# [*Accepted to the [RAID 2025](https://raid2025.github.io/index.html)*] When (Inter)actions Speak Louder Than (Pass)words: Task-Based Evaluation of Implicit Authentication in Virtual Reality

#### Woojin Jeon*, Chaejin Lim*, and Hyoungshick Kim*.
##### Sungkyunkwan University*

<div align="center">
<img src="https://github.com/Jason-WJ96/implicit-vr-auth/blob/main/figures/System_overview.jpg" width=100% height=100%>
</div>

## Abstract
We present a practical implicit authentication system for Virtual Reality (VR) that uses natural interaction tasks—grabbing, pointing, and typing—as behavioral biometrics. The system extracts 221 features from head-mounted and controller sensors and is trained as a lightweight SVM-based binary classifier using data from legitimate users and a small set of reference users to simulate attacker behavior. In a 24-participant study, our system achieved strong authentication performance, with median Equal Error Rates (EERs) of 0.4% for grabbing, 2.6% for pointing, and 0.3% for typing. Designed for on-device deployment, it requires no GPU support, completes inference within 1 second, and maintains a compact model size under 0.2 MB, enabling efficient, real-time authentication on standalone VR headsets. Security evaluations with attacker-in-the-loop experiments across no-knowledge, shoulder-surfing, and videoreplay conditions revealed clear trade-offs. Typing and pointing offered strong resistance to impersonation, while grabbing, despite high usability, was more vulnerable under video replay with a 23.8% attack success rate. These results demonstrate that secure, accurate, and real-time implicit authentication is feasible in VR, with task-specific characteristics enabling flexible deployment based on security and usability needs.

## Three Tasks for  Authentication

<table align="center">
  <tr>
    <td align="center"><b>Grabbing</b></td>
    <td align="center"><b>Pointing</b></td>
    <td align="center"><b>Typing</b></td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://github.com/Jason-WJ96/implicit-vr-auth/blob/main/figures/Task_grabbing.jpg" height="200">
    </td>
    <td align="center">
      <img src="https://github.com/Jason-WJ96/implicit-vr-auth/blob/main/figures/Task_pointing.jpg" height="200">
    </td>
    <td align="center">
      <img src="https://github.com/Jason-WJ96/implicit-vr-auth/blob/main/figures/Task_typing.jpg" height="200">
    </td>
  </tr>
</table>


## Citation
If you find it is helpful and used for publication, please kindly cite our work as:
```
    *It will be added after the conference presentation.*
```

<hr>

## Installation

### 1. Environment
This study has been run and tested in the following environment:
- *Windows 10 Pro 22H2*
- *Python==3.9.12*

### 2. Download Repository
Move to the directory you want to import our repository.
```bash
cd path/to/working/directory
```

To download the source code and dataset in the directory, clone by the following commands.
```bash
git clone https://github.com/Jason-WJ96/implicit-vr-auth.git
cd implicit-vr-auth
```

### 3. Python Virtual Environment
We recommend using venv to run our repository. The following commands will help you how to create a new python virtual environment, activate it, and install python package.
```bash
python -m venv imvrauth
source imvrauth/bin/activate
cd ../implicit-vr-auth
pip install -r requirements.txt
```

If the installation via `pip install -r requirements.txt` fails, please install the required pip libraries manually by running each command listed in `pip_install_list.txt` inside your python virtual environment.

## How To Run

To run Jupyter notebook, execute the following command.
```bash
jupyter notebook
```

In the **Parameter** cell of the `main-implicit_vr_auth.ipynb` file, you can configure the experimental settings by editing the predefined parameter lists. Adjusting these parameters allows you to evaluate the model under various conditions such as task types, training scenarios, classifiers, reference groups, data augmentation techniques, and feature categories. For detailed descriptions of each parameter, please refer to the [paper]().

Below is a description of each configurable parameter along with example values:

### 🔹Task List (`task_list`)
Add all the tasks you want to evaluate in your experiment to the list below.
```python
task_list = [
    'grabbing',
    'pointing', 
    'typing'
]
```

### 🔹Training Scenario (`scenario_list`)
Add all the training scenarios to the list below.
```python
scenario_list = [
    'Scen1', 
    'Scen2'
]
```

### 🔹Classifier Models  (`model_list`)
Add all the classifier models you want to use for training and evaluation to the list below.
```python
model_list = {
    'RF': RandomForestClassifier(random_state=42),
    'SVM': SVC(probability=True, random_state=42),
    'LR': LogisticRegression(random_state=42),
    'GradientBoost': GradientBoostingClassifier(random_state=42),
    'DecisionTree': DecisionTreeClassifier(random_state=42)
}
```

### 🔹Reference User Group (`ref_list`)
Add all the reference user groups you want to use for training and evaluation to the list below.
```python
ref_list = {
    'BaseGroup': basegroup_list,
    'SubGroup1': subgroup1_list,
    'SubGroup2': subgroup2_list,
    'SubGroup3': subgroup3_list,
    'SubGroup4': subgroup4_list,
}
```

### 🔹Data Augmentation (`data_aug_list`)
Add all the desired data augmentation techniques you want to evaluate in the experiment to the list below.
```python
data_aug_list = [
    'NoAug',
    'SMOTE', 
    'VAE'             
]
```

### 🔹Feature Category (`feature_category_list`)
Choose which categories of features to include in the input data.
```python
feature_category_list = [
    'movement',
    'spatial', 
    'orientation', 
    'interaction'
]
```

Configure the above parameters according to your experimental goals to test different combinations and analyze their impact on model performance. Each setting can be modified directly within the `main-implicit_vr_auth.ipynb` file.


Then, run the `main-implicit_vr_auth.ipynb`. 
This will create a folder named `Result-EER` inside the `./implicit-vr-auth` directory, where you can find the resulting CSV files.

<hr>

## Dataset
We opensource the dataset collected from 24 participants in our user study. Due to privacy concerns, we do not provide the raw sensor data of participants. Instead, we share feature data that was extracted through the feature extraction process described in our paper.

The dataset is organized into three CSV files, each corresponding to a specific task. These are available in `./dataset` directory.
```bash
grabbing_Dataframe_all.csv
pointing_Dataframe_all.csv
typing_Dataframe_all.csv
```
Each file contains the following columns: *Index*, *Name*, *Study*, and 224 extracted features.