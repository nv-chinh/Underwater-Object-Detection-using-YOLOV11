# Underwater Object Detection using YOLOv11

## 🐠 Introduction  

Underwater object detection plays a critical role in **marine research, aquaculture, environmental monitoring, and autonomous underwater vehicles (AUVs)**. Unlike object detection in natural scenes, underwater detection faces unique challenges due to the complexity of aquatic environments:  

- 🌊 **Light Distortion** – Absorption & scattering cause low visibility, poor contrast, and color shifts.  
- ⚪ **Water Turbidity** – Suspended particles blur images and add noise.  
- 🐟 **Occlusions & Shape Changes** – Objects overlap, deform, or hide each other.  
- 🌐 **Domain Variability** – Differences in depth, regions, and capture devices hinder generalization.  
- 🦀 **Small & Camouflaged Targets** – Many species are tiny or blend into their surroundings.

This project employ YOLOv11 - the latest version of yolo, and compare its performance with previous versions (YOLOv8 and YOLOv10) across multiple datasets. The goal is to evaluate how the modern YOLO architecture performs in challenging underwater environments.

## YOLOv11: Key Advancements
YOLOv11 represents the latest evolution of the YOLO family, bringing improvements in both accuracy and efficiency. Comparing to its predecessors, YOLOv11 introduces:
- **Stronger architecture**: Incorporates novel components including **C3k2**, **SPPF**, and **C2PSA**, which significantly enhance feature extraction and spatial focus. These architectural upgrades allow the model to better capture fine-grained details, making it more robust in complex detection tasks.
- **Improved efficiency**: Optimized for faster inference without sacrificing accuracy, making it suitable for both research and real-time applications.
- **Enhanced training strategies**: Includes refined data augmentation, label assignment, and loss balancing techniques, which improve convergence and generalization across different datasets.

## 📊 Datasets
To evaluate the performance of our model, we conducted experiments on four diverse and challenging underwater datasets:
- **DUO Dataset**: A large-scale underwater object detection dataset containing diverse marine species. It includes **four classes**: *echinus, holothurian, scallop, starfish*.
  <p align="center">
  <img src="examples/Duo_1.jpg" width="22%" height="80%"/>
  <img src="examples/Duo_2.jpg" width="22%" height="80%"/>
  <img src="examples/Duo_3.jpg" width="22%" height="80%"/>
  <img src="examples/Duo_4.jpg" width="22%" height="80%"/>
</p> 

- **URPC2019 Dataset**: Released as part of the Underwater Robot Picking Contest 2019, featuring underwater objects under varying visibility and lighting conditions. Same as **DUO Dataset**, it also includes **four classes**: *echinus, holothurian, scallop, starfish*.  
<p align="center">
  <img src="examples/urpc_1.jpg" width="22%" height="80%"/>
  <img src="examples/urpc_2.jpg" width="22%" height="80%"/>
  <img src="examples/urpc_3.jpg" width="22%" height="80%"/>
  <img src="examples/urpc_4.jpg" width="22%" height="80%"/>
</p> 

Additionally, the URPC_2019 dataset provides test images from 7 different underwater environments (e.g., varying visibility, lighting, and background conditions). We use these additional test sets to further evaluate the robustness and generalization performance of the models.

<p align="center"><strong>📸 Example Samples for 7 Different Environments</strong></p>

<table align="center">
  <tr>
    <td align="center" width="200px">
      <img src="examples/urpc_type1.jpg" width="800"/><br/><sub><b style="font-size: 15px;">Type 1</b></sub>
    </td>
    <td align="center" width="200px">
      <img src="examples/urpc_type2.jpg" width="800"/><br/><sub><b style="font-size: 15px;">Type 2</b></sub>
    </td>
    <td align="center" width="200px">
      <img src="examples/urpc_type3.jpg" width="800"/><br/><sub><b style="font-size: 15px;">Type 3</b></sub>
    </td>
    <td align="center" width="200px">
      <img src="examples/urpc_type4.jpg" width="800"/><br/><sub><b style="font-size: 15px;">Type 4</b></sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="200px">
      <img src="examples/urpc_type5.jpg" width="200"/><br/><sub><b style="font-size: 15px;">Type 5</b></sub>
    </td>
    <td align="center" width="200px">
      <img src="examples/urpc_type6.jpg" width="200"/><br/><sub><b style="font-size: 15px;">Type 6</b></sub>
    </td>
    <td align="center" width="200px">
      <img src="examples/urpc_type7.jpg" width="250"/><br/><sub><b style="font-size: 15px;">Type 7</b></sub>
    </td>
  </tr>
</table>
- **UDD Dataset**: A comprehensive underwater detection dataset. It includes **three classes**: *scallop, seacucumber, seaurchin*.
<p align="center">
  <img src="examples/udd_1.jpg" width="22%" height="80%"/>
  <img src="examples/udd_2.jpg" width="22%" height="80%"/>
  <img src="examples/udd_3.jpg" width="22%" height="80%"/>
  <img src="examples/udd_4.jpg" width="22%" height="80%"/>
</p> 

- **Brackish Dataset**: Collected in brackish water environments, featuring species and objects that differ from open-sea datasets. It includes **six classes**: *crab, fish, jellyfish, shirmp, small fish, starfish*.
<p align="center">
  <img src="examples/brackish_1.jpg" width="22%" height="80%"/>
  <img src="examples/brackish_2.jpg" width="22%" height="80%"/>
  <img src="examples/brackish_3.jpg" width="22%" height="80%"/>
  <img src="examples/brackish_4.jpg" width="22%" height="80%"/>
</p> 

Below is the number of samples for training, validation, testing in each dataset used in this project:
| Dataset    |   Train   |   Valid   |   Test   |
|:----------:|:---------:|:---------:|:--------:|
| DUO        |   5296    |   1321    |   1100   |
| URPC2019   |   3767    |    695    |    245   |
| UDD        |   1892    |    223    |    111   |
| Brackish   |  11739    |   1467    |   1468   |
