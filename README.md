# Introduction
This is the Beagle dog dataset used in the paper "Three-dimensional surface motion capture of multiple freely moving pigs using MAMMAL" (Nature Communications 2023). 
If you have any problem, contact Liang An (anliang at mail dot tsinghua dot edu dot cn). 

# Download Links 
You could access the dataset by two ways: 

Google Drive: https://drive.google.com/drive/folders/1bRYKzB1-ClJwHGsk1g6Opi04eijASp0U?usp=sharing. 

Baidu Pan: https://pan.baidu.com/s/1ZxPvXKjECu-HKLx3OSg9eg?pwd=13tw, extraction code: 13tw. 

The only difference is, `beagle_coco` is provided as `.zip` in Google Drive, while as unzipped folder in Baidu Pan.

# Data Description
Three folders of videos are provided, which all share the same calibration data. All sequences have 10 views. Note that all videos are recorded in `linear` type using GoPro BLACK 11 cameras. 

`synced_15m_bk`: 15-minute long, 120fps, 1920*1080p, `.mp4` format, h264 encoding. Two Beagle dogs. Note that, `6.mp4` was broken during recording, therefore it has only 2min36s long. 

`synced_15m_1fps`: Downsampled as 1fps of the above videos. The first 113 frames are labeled with 3D keypoints and per-view masks. The 0th to 89th frames are used for training 2D detection model, and 90th to 112th frames are used for evaluation. See `beagle_coco` for cleaned coco dataset. 

`synced_0.5m_single`: 30-second long, 120fps, 1920*1080p, `.mp4` format, h264 encoding. Single Beagle dog. 

`calib`: Videos used for calibration (a chessboard with 12*9 grids, grid edge length is 0.03m). 

`beagle_coco`: 2D detection dataset in COCO format. For each image, 2D keypoints and masks are manually labeled. There are 29 keypoints. Note that, image folder `images` and `images_unique` have the same images with different names. `unique` index images from different views in a unified order. In my paper, `images_unique` is used for training. `annotations_unique_train.json` is the train part and `annotations_unique_eval.json` is the evaluation part. In fact, during training 2D pose model, using `annotations_unique_eval.json` as evaluation may cause the final model test well on `90~112th` frames, resulting in a risk of dataset leaking (90th to 112th frames are used for final 3D evaluation). However, as it is only used for generalization demonstration on new species, and consider the limited size of dataset, we ignore such problem. `labeled` provides the 3D keypoint annotations. For keypoint names, please refer to the json files. 

`calibdata_beagle`: `camera_undist.json` is the final calibration result. `backgrounds` have the cleaned background images for all views. 

# Citation
If you find this data useful, please cite the paper 
```
@article{an2023three,
  title={Three-dimensional surface motion capture of multiple freely moving pigs using MAMMAL},
  author={An, Liang and Ren, Jilong and Yu, Tao and Hai, Tang and Jia, Yichang and Liu, Yebin},
  journal={Nature Communications},
  volume={14},
  number={1},
  pages={7727},
  year={2023},
  publisher={Nature Publishing Group UK London}
}
```
# Acknowledgements 
We thank Beijing Sinogenetic Biotechnology Co., Ltd for the help in the Beagle dog video recording. We also thank Yuxiang Zhang for his help in video recording. Beagle dogs are provided by Beijing Sinogenetic Biotechnology Co., Ltd, and are both treated gentally and carefully.  

# License 
Please read carefully the following terms and conditions and any accompanying documentation before you download and/or use DeepHuman Software/Data (the "Software"). By downloading and/or using the Software, you acknowledge that you have read these terms and conditions, understand them, and agree to be bound by them. If you do not agree with these terms and conditions, you must not download and/or use the Software.

**Ownership**

The Software has been developed at the Tsinghua University and is owned by and proprietary material of the Tsinghua University.

**License Grant**

Tsinghua University grants you a non-exclusive, non-transferable, free of charge right:

To download the Software and use it on computers owned, leased or otherwise controlled by you and/or your organisation;

To use the Software for the sole purpose of performing non-commercial scientific research, non-commercial education, or non-commercial artistic projects.

Any other use, in particular any use for commercial purposes, is prohibited. This includes, without limitation, incorporation in a commercial product, use in a commercial service, as training data for a commercial product, for commercial ergonomic analysis (e.g. product design, architectural design, etc.), or production of other artifacts for commercial purposes including, for example, web services, movies, television programs, mobile applications, or video games. The Software may not be used for pornographic purposes or to generate pornographic material whether commercial or not. This license also prohibits the use of the Software to train methods/algorithms/neural networks/etc. for commercial use of any kind. The Software may not be reproduced, modified and/or made available in any form to any third party without Tsinghua University’s prior written permission. By downloading the Software, you agree not to reverse engineer it.

**Disclaimer of Representations and Warranties**

You expressly acknowledge and agree that the Software results from basic research, is provided “AS IS”, may contain errors, and that any use of the Software is at your sole risk. TSINGHUA UNIVERSITY MAKES NO REPRESENTATIONS OR WARRANTIES OF ANY KIND CONCERNING THE SOFTWARE, NEITHER EXPRESS NOR IMPLIED, AND THE ABSENCE OF ANY LEGAL OR ACTUAL DEFECTS, WHETHER DISCOVERABLE OR NOT. Specifically, and not to limit the foregoing, Tsinghua University makes no representations or warranties (i) regarding the merchantability or fitness for a particular purpose of the Software, (ii) that the use of the Software will not infringe any patents, copyrights or other intellectual property rights of a third party, and (iii) that the use of the Software will not cause any damage of any kind to you or a third party.

**Limitation of Liability**

Under no circumstances shall Tsinghua University be liable for any incidental, special, indirect or consequential damages arising out of or relating to this license, including but not limited to, any lost profits, business interruption, loss of programs or other data, or all other commercial damages or losses, even if advised of the possibility thereof.

**No Maintenance Services**

You understand and agree that Tsinghua University is under no obligation to provide either maintenance services, update services, notices of latent defects, or corrections of defects with regard to the Software. Tsinghua University nevertheless reserves the right to update, modify, or discontinue the Software at any time.

**Publication with the Software**

You agree to cite the paper describing the software and algorithm as specified on the download website.

**Media Projects with the Software**

When using the Software in a media project please give credit to Tsinghua University. For example: the Software was used for performance capture courtesy of the Tsinghua University.

**Commercial Licensing Opportunities**

For commercial use and commercial license please contact: liuyebin@mail.tsinghua.edu.cn.