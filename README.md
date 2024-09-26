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

# LICENSE
MIT License

Copyright (c) 2024 An Liang

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
