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

If you find it is helpful and used for publication, please kindly cite our work as:
```
```

<hr>

## Installation

### 1. Environment
This study has been run and tested in the following environment:
- *Windows 10 Pro 22H2*
- *Python==3.9.12*

### 2. Download Repository
1. Move to the directory you want to import our repository.
```bash
cd path/to/working/directory
```

2. To download the source code and dataset in the directory, clone by the following commands.
```bash
git clone https://github.com/Jason-WJ96/implicit-vr-auth.git
cd implicit-vr-auth
```

### 3. Python Venv
We recommend using venv to run our repository. The following commands will help you how to create a new python virtual environment, activate it, and install python package.
```bash
python -m venv imvrauth
source imvrauth/bin/activate
cd ../implicit-vr-auth
pip install -r requirements.txt
```

If the installation via `pip install -r requirements.txt` fails, please install the required pip libraries manually by running each command listed in `pip_install_list.txt` inside your python virtual environment.

## How To Run



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
