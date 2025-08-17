# Underwater Object Detection using YOLOv11

## 🐠 Introduction  

Underwater object detection plays a critical role in **marine research, aquaculture, environmental monitoring, and autonomous underwater vehicles (AUVs)**. Unlike object detection in natural scenes, underwater detection faces unique challenges due to the complexity of aquatic environments:  

- 🌊 **Light Distortion** – Absorption & scattering cause low visibility, poor contrast, and color shifts.  
- ⚪ **Water Turbidity** – Suspended particles blur images and add noise.  
- 🐟 **Occlusions & Shape Changes** – Objects overlap, deform, or hide each other.  
- 🌐 **Domain Variability** – Differences in depth, regions, and capture devices hinder generalization.  
- 🦀 **Small & Camouflaged Targets** – Many species are tiny or blend into their surroundings.

This project employ YOLOv11 - the latest version of yolo, and compare its performance with previous versions (YOLOv8 and YOLOv10) across multiple datasets. The goal is to evaluate how the modern YOLO architecture performs in challenging underwater environments.

🎬 **Demo**

<p align="center">
  <img src="demo/output_videos/out_1.gif" width="45%" />
  <img src="demo/output_videos/out_2.gif" width="45%" />
</p>

## 🚀 YOLOv11: Key Advancements
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
    <td align="center" width="400px" height=="400px">
      <img src="examples/urpc_type1.jpg" width="800"/><br/><sub><b style="font-size: 40px;">Type 1</b></sub>
    </td>
    <td align="center" width="400px" height=="400px">
      <img src="examples/urpc_type2.jpg" width="800"/><br/><sub><b style="font-size: 40px;">Type 2</b></sub>
    </td>
    <td align="center" width="400px" height=="400px">
      <img src="examples/urpc_type3.jpg" width="800"/><br/><sub><b style="font-size: 40px;">Type 3</b></sub>
    </td>
    <td align="center" width="400px" height=="400px">
      <img src="examples/urpc_type4.jpg" width="800"/><br/><sub><b style="font-size: 40px;">Type 4</b></sub>
    </td>
  </tr>
  <tr>
    <td align="center" width="400px" height=="400px">
      <img src="examples/urpc_type5.jpg" width="200"/><br/><sub><b style="font-size: 40px;">Type 5</b></sub>
    </td>
    <td align="center" width="400px" height=="400px">
      <img src="examples/urpc_type6.jpg" width="200"/><br/><sub><b style="font-size: 40px;">Type 6</b></sub>
    </td>
    <td align="center" width="400px" height=="400px">
      <img src="examples/urpc_type7.jpg" width="250"/><br/><sub><b style="font-size: 40px;">Type 7</b></sub>
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

## 📈 Evaluation Results
We evaluate the detection performance of **YOLOv11x**, **YOLOv10x**, and **YOLOv8x** across all datasets.

The metrics used for comparison are:
- **mAP@50**: Mean Average Precision at IoU threshold 0.5 (focuses on correct object localization).  
- **mAP@50-95**: Mean Average Precision averaged across IoU thresholds from 0.5 to 0.95 (stricter and more comprehensive).

### Results on benchmark datasets
<table>
  <tr>
    <th>Dataset</th>
    <th>Image Size</th>
    <th>Metric</th>
    <th>YOLOv8x</th>
    <th>YOLOv10x</th>
    <th>YOLOv11x</th>
  </tr>
  <tr>
    <td rowspan="2" align="center"><b>DUO</b></td>
    <td rowspan="2" align="center">640</td>
    <td align="center">mAP@0.5</td>
    <td align="center">0.513</td>
    <td align="center">0.849</td>
    <td align="center"><b>0.868</b></td>
  </tr>
  <tr>
    <td align="center">mAP@0.5:0.95</td>
    <td align="center">0.26</td>
    <td align="center">0.678</td>
    <td align="center"><b>0.72</b></td>
  </tr>
  <tr>
    <td rowspan="2" align="center"><b>URPC2019</b></td>
    <td rowspan="2" align="center">640</td>
    <td align="center">mAP@0.5</td>
    <td align="center"><b>0.877</b></td>
    <td align="center">0.855</td>
    <td align="center">0.874</td>
  </tr>
  <tr>
    <td align="center">mAP@0.5:0.95</td>
    <td align="center">0.544</td>
    <td align="center">0.508</td>
    <td align="center"><b>0.56</b></td>
  </tr>
  <tr>
    <td rowspan="2" align="center"><b>UDD</b></td>
    <td rowspan="2" align="center">640</td>
    <td align="center">mAP@0.5</td>
    <td align="center">0.685</td>
    <td align="center">0.551</td>
    <td align="center"><b>0.719</b></td>
  </tr>
  <tr>
    <td align="center">mAP@0.5:0.95</td>
    <td align="center">0.357</td>
    <td align="center">0.25</td>
    <td align="center"><b>0.389</b></td>
  </tr>
  <tr>
    <td rowspan="2" align="center"><b>Brackish</b></td>
    <td rowspan="2" align="center">640</td>
    <td align="center">mAP@0.5</td>
    <td align="center">0.988</td>
    <td align="center">0.987</td>
    <td align="center"><b>0.991</b></td>
  </tr>
  <tr>
    <td align="center">mAP@0.5:0.95</td>
    <td align="center">0.87</td>
    <td align="center">0.85</td>
    <td align="center"><b>0.886</b></td>
  </tr>
</table>

### Results across different environments
As mentioned above, we also conducted testing in 7 different environments of the URPC dataset to further assess model performance:
**Results for Standard Environments**
<table>
  <tr>
    <th>Environment</th>
    <th>Image Size</th>
    <th>Metric</th>
    <th>YOLOv8x</th>
    <th>YOLOv10x</th>
    <th>YOLOv11x</th>
  </tr>
  <tr>
    <td rowspan="2" align="center"><b>Type 1</b></td>
    <td rowspan="2" align="center">640</td>
    <td align="center">mAP@0.5</td>
    <td align="center">0.662</td>
    <td align="center">0.377</td>
    <td align="center"><b>0.678</b></td>
  </tr>
  <tr>
    <td align="center">mAP@0.5:0.95</td>
    <td align="center">0.359</td>
    <td align="center">0.178</td>
    <td align="center"><b>0.383</b></td>
  </tr>
  <tr>
    <td rowspan="2" align="center"><b>Type 2</b></td>
    <td rowspan="2" align="center">640</td>
    <td align="center">mAP@0.5</td>
    <td align="center">0.639</td>
    <td align="center">0.436</td>
    <td align="center"><b>0.654</b></td>
  </tr>
  <tr>
    <td align="center">mAP@0.5:0.95</td>
    <td align="center">0.339</td>
    <td align="center">0.203</td>
    <td align="center"><b>0.349</b></td>
  </tr>
  <tr>
    <td rowspan="2" align="center"><b>Type 3</b></td>
    <td rowspan="2" align="center">640</td>
    <td align="center">mAP@0.5</td>
    <td align="center">0.738</td>
    <td align="center">0.644</td>
    <td align="center"><b>0.762</b></td>
  </tr>
  <tr>
    <td align="center">mAP@0.5:0.95</td>
    <td align="center">0.414</td>
    <td align="center">0.332</td>
    <td align="center"><b>0.44</b></td>
  </tr>
  <tr>
    <td rowspan="2" align="center"><b>Type 4</b></td>
    <td rowspan="2" align="center">640</td>
    <td align="center">mAP@0.5</td>
    <td align="center">0.584</td>
    <td align="center">0.391</td>
    <td align="center"><b>0.632</b></td>
  </tr>
  <tr>
    <td align="center">mAP@0.5:0.95</td>
    <td align="center">0.317</td>
    <td align="center">0.18</td>
    <td align="center"><b>0.349</b></td>
  </tr>
  <tr>
    <td rowspan="2" align="center"><b>Type 5</b></td>
    <td rowspan="2" align="center">640</td>
    <td align="center">mAP@0.5</td>
    <td align="center">0.702</td>
    <td align="center">0.574</td>
    <td align="center"><b>0.715</b></td>
  </tr>
  <tr>
    <td align="center">mAP@0.5:0.95</td>
    <td align="center">0.4</td>
    <td align="center">0.278</td>
    <td align="center"><b>0.411</b></td>
  </tr>
  <tr>
    <td rowspan="2" align="center"><b>Type 6</b></td>
    <td rowspan="2" align="center">640</td>
    <td align="center">mAP@0.5</td>
    <td align="center">0.524</td>
    <td align="center">0.333</td>
    <td align="center"><b>0.553</b></td>
  </tr>
  <tr>
    <td align="center">mAP@0.5:0.95</td>
    <td align="center">0.292</td>
    <td align="center">0.154</td>
    <td align="center"><b>0.307</b></td>
  </tr>
  <tr>
    <td rowspan="2" align="center"><b>Type 7</b></td>
    <td rowspan="2" align="center">640</td>
    <td align="center">mAP@0.5</td>
    <td align="center">0.785</td>
    <td align="center">0.671</td>
    <td align="center"><b>0.801</b></td>
  </tr>
  <tr>
    <td align="center">mAP@0.5:0.95</td>
    <td align="center">0.441</td>
    <td align="center">0.345</td>
    <td align="center"><b>0.468</b></td>
  </tr>
</table>

## 📸 Model Prediction Examples

### Results for Standard Environment

<table>
  <tr>
    <th>Ground Truth</th>
    <th>YOLOv11x</th>
    <th>YOLOv10x</th>
    <th>YOLOv8x</th>
  </tr>
  <tr>
    <td align="center"><img src="examples/duo_1_gt.jpg" width="400"/></td>
    <td align="center"><img src="examples/duo_1_yolov11.jpg" width="400"/></td>
    <td align="center"><img src="examples/duo_1_yolov10.jpg" width="400"/></td>
    <td align="center"><img src="examples/duo_1_yolov8.jpg" width="400"/></td>
  </tr>
  <tr>
    <td align="center"><img src="examples/duo_2_gt.jpg" width="400"/></td>
    <td align="center"><img src="examples/duo_2_yolov11.jpg" width="400"/></td>
    <td align="center"><img src="examples/duo_2_yolov10.jpg" width="400"/></td>
    <td align="center"><img src="examples/duo_2_yolov8.jpg" width="400"/></td>
  </tr>
  <tr>
    <td align="center"><img src="examples/udd_1_gt.jpg" width="400"/></td>
    <td align="center"><img src="examples/udd_1_yolov11.jpg" width="400"/></td>
    <td align="center"><img src="examples/udd_1_yolov10.jpg" width="400"/></td>
    <td align="center"><img src="examples/udd_1_yolov8.jpg" width="400"/></td>
  </tr>
  <tr>
    <td align="center"><img src="examples/udd_2_gt.jpg" width="400"/></td>
    <td align="center"><img src="examples/udd_2_yolov11.jpg" width="400"/></td>
    <td align="center"><img src="examples/udd_2_yolov10.jpg" width="400"/></td>
    <td align="center"><img src="examples/udd_2_yolov8.jpg" width="400"/></td>
  </tr>
  <tr>
    <td align="center"><img src="examples/urpc_1_gt.jpg" width="400"/></td>
    <td align="center"><img src="examples/urpc_1_yolov11.jpg" width="400"/></td>
    <td align="center"><img src="examples/urpc_1_yolov10.jpg" width="400"/></td>
    <td align="center"><img src="examples/urpc_1_yolov8.jpg" width="400"/></td>
  </tr>
</table>

### Results for Diverse Environments of URPC Dataset

<table>
  <tr>
    <th>Ground Truth</th>
    <th>YOLOv11x</th>
    <th>YOLOv10x</th>
    <th>YOLOv8x</th>
  </tr>
  <tr>
    <td align="center"><img src="examples/type1_1_gt.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type1_1_yolov11.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type1_1_yolov10.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type1_1_yolov8.jpg" width="600" height="800"/></td>
  </tr>
  <tr>
    <td align="center"><img src="examples/type2_1_gt.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type2_1_yolov11.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type2_1_yolov10.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type2_1_yolov8.jpg" width="600" height="800"/></td>
  </tr>
  <tr>
    <td align="center"><img src="examples/type3_1_gt.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type3_1_yolov11.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type3_1_yolov10.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type3_1_yolov8.jpg" width="600" height="800"/></td>
  </tr>
  <tr>
    <td align="center"><img src="examples/type4_1_gt.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type4_1_yolov11.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type4_1_yolov10.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type4_1_yolov8.jpg" width="600" height="800"/></td>
  </tr>
  <tr>
    <td align="center"><img src="examples/type5_1_gt.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type5_1_yolov11.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type5_1_yolov10.jpg" width="600" height="800"/></td>
    <td align="center"><img src="examples/type5_1_yolov8.jpg" width="600" height="800"/></td>
  </tr>
</table>

## 🔮 Conclusion
The experimental results across four benchmark datasets and seven underwater environments show that **YOLOv11 consistently outperforms YOLOv8 and YOLOv10** in both **mAP@0.5** and **mAP@0.5-95**.

- On **benchmark datasets (DUO, URPC2019, UDD, Brackish)**, YOLOv11 achieved the **highest scores in most cases**, especially on the stricter **mAP@0.5-95** metric.  
- In **challenging URPC environments** with varying visibility and lighting, YOLOv11 also outperformed YOLOv8 and YOLOv10, achieving higher accuracy across all environment types, although performance varied slightly depending on the conditions.

The improvements are driven by architectural enhancements, enabling YOLOv11 to better capture fine-grained underwater object features.  

