# Installation Instructions

## 1) System Requirements  

- To install **QSM-Cereb** at least 40 GB of free space is required in your hard disk.    

- This software has been tested on Ubuntu 20.04, Ubuntu 20.10 and Ubuntu 22.04.

- The **QSM-Cereb** fundamentally runs its application on top of other tools, so it's necessary for the user to install of the following applications:
  
  **I)** Python 3.11.5 - [Installation](https://www.python.org/downloads/)
  
  **II)** Docker Engine - [Installation](https://docs.docker.com/engine/install/ubuntu/)  
   **OR**  
  Singularity - [Installation](https://github.com/apptainer/singularity/blob/master/INSTALL.md)  
   **OR**  
  Apptainer - [Installation](https://apptainer.org/docs/user/latest/quick_start.html#quick-installation)  

- We strongly reccomend the GPU integration for optimizing the prediction time of the pipeline. However, inference times are typically still manageable on CPU and MPS (Apple M1/M2). If using a GPU, it should have at least 4 GB of available (unused) VRAM.    
  
  CUDA-toolkit - [Installation](https://developer.nvidia.com/cuda-toolkit-archive)  
  CUDA container-toolkit - [Installation](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)

## 2) Download and Install QSM-Cereb 

### Installing QSM-Cereb

To download and install QSM-Cereb, open a terminal and type:  
  
```bash
git clone https://github.com/art2mri/QSM-Cereb.git  
chmod -R 777 QSM-Cereb/QSM-Cereb.py
```   
 
 It will clone all the QSM-Cereb repository files to an QSM-Cereb folder that will be created in your computer. **NOTE: Please don't rename the QSM-Cereb folder, because this will cause issues while running the pipeline later. You can move the entire folder to any other locations, but never changing its name**.

 ### Installing virtual environment to run QSM-Cereb GUI 

 Inside of the **QSM-Cereb** folder, open a terminal and type the following commands:  

 ```bash
pip install virtualenv
```
 ```bash
apt install python3-venv
```
 ```bash
python3.11 -m venv venv
```
 ```bash
source venv/bin/activate
```
 ```bash
pip install Pillow
```
 ```bash
pip3 install tkfilebrowser
```
 ```bash
apt-get install python3-tk
```
 ```bash
deactivate
```

**If you couldn't install the packages above due to permission problems, you can run the pipeline via command line, please check the section 4) Running QSM-Cereb** and no packages need to be installed.  

[command line tutorial](/command%20line%20TUTORIAL.md)  

## 3) Docker and Singularity Containers  

- You don't necessarily need to install both of these applications; you can choose to install one of them to run the spinal cord vertebral labeling. The containers will be automatically initialized from an existing Docker image that is already available on [DockerHub](https://hub.docker.com/repository/docker/art2mri/vertebral_labeling/general).

  ### Docker
  
  If you have already correctly installed the Docker Engine, run the following command on Linux Terminal:
   - ```bash
     docker pull art2mri/qsm_cereb:3.0
     ```
     
  ### Singularity

  If you have correctly installed Singularity, open the Linux terminal **inside of the QSM-Cereb** and run the following command:
  - ```bash
    singularity build --sandbox qsm_cereb.simg docker://art2mri/qsm_cereb:3.0
    ```
  - ```bash
    chmod -R 777 qsm_cereb.simg
    ```

  ### Apptainer

  If you have correctly installed Apptainer, open the Linux terminal **inside of the QSM-Cereb folder** and run the following command:
  - ```bash
    apptainer build --sandbox qsm_cereb.simg docker://art2mri/qsm_cereb:3.0
    ```
  - ```bash
    chmod -R 777 qsm_cereb.simg
    ```  
  - After that, a folder named ***vertebral_labeling.simg*** will appear on the **QSM-Cereb** folder. Please don't rename it.  
  

## 4) Running QSM-Cereb  

To run the **QSM-Cereb** software and open the interface, open a terminal **inside of the QSM-Cereb folder** and type:  

 ```bash
source venv/bin/activate  
python3 QSM-cereb.py
```
If you are running **QSM-Cereb** in a server, or if you couldn`t install all the packages listed on the section **2) Download and Install QSM-Cereb**, you can run the pipeline without opening the GUI, via command line, by opening a terminal **inside of the QSM-Cereb folder** and typing:  

 ```bash 
python3 command.py  
```  
[command line tutorial](/command%20line%20TUTORIAL.md)  
 
## 5) Uninstalling QSM-Cereb     
 
