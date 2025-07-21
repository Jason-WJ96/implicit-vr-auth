# Implicit VR User Authentication

Document for accepted paper *When (Inter)actions Speak Louder Than
(Pass)words: Task-Based Evaluation of Implicit
Authentication in Virtual Reality* at RAID 2025.

<hr>

# 1. Within Python Environment

## 1. Prerequisites
This study has been run and tested in *Python==3.9.12*, in the following environment:
- *Windows 10 Pro 22H2*

## 2. Download Repository

To access the full source code, please click the **"Download Repository"** button located at the top right corner of the following page: <a href="https://anonymous.4open.science/r/implicit-vr-auth-C4D9/README.md">https://anonymous.4open.science/r/implicit-vr-auth-C4D9/README.md</a>

## 3. Python Venv
To run the source codes in python virtual environment run the following code. 
```bash
mkdir implicit_vr_auth
cd implicit_vr_auth
python3 -m venv imvrauth
source imvrauth/bin/activate
cd ../implicit-vr-auth-C4D9
pip3 install -r requirements.txt
```

If the installation via `pip3 install -r requirements.txt` fails, please install the required pip libraries manually by running each command listed in `pip_install_list.txt` inside your python virtual environment.

## 3. Dataset
We opensource the dataset collected from 24 participants in our user study. Due to privacy concerns, we do not provide the raw sensor data of participants. Instead, we share feature data that was extracted through the feature extraction process described in our paper.

The dataset is organized into three CSV files, each corresponding to a specific task. These are available in `./dataset` directory.
```bash
grabbing_Dataframe_all.csv
pointing_Dataframe_all.csv
typing_Dataframe_all.csv
```
Each file contains the following columns: *Index*, *Name*, *Study*, and 224 extracted features.