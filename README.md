# Hybrid-IK

## 1. Introduction

This project is hosted on `Colab`, google's machine learning platform on the cloud. Please follow the [link](https://drive.google.com/drive/folders/1D1EdqgHQQv_skPSmAtS0Sztoe9zqJTh6?usp=sharing) to check out the full details of this project.

Please refer to my [colab page](https://colab.research.google.com/drive/1YVSZy-Lj4H49chmWO5FQyWEHP063vvdx?usp=sharing) to see how to setup the project, run the code, and reproduce the results.

Here is my [presentation](/demo/Hybrid_Analytical_and_Neural_IK_for_Human_Pose.pdf) and [technical report](/demo/CMPT_766_Final_Report.pdf) of this project.

**Topics:** _Inverse Kinematics_, _Pose Estimation_

**Skills:** _Pytorch_, _Deep Neural Networks_, _Colab_

### 1.1 Background

Recovering 3D human poses and shapes from one monocular RGB image is challenging because it is a fundamentally ill-posed problem. It is difficult for the `model-based methods` to learn the regression function for estimation of body parameters from the images. While researchers resort to `3D keypoint estimation-based methods` and achieved impressive performance, such approach might predict unrealistic body structures due to the lack of explicit modelling of human bodies.

`To bridge the gap between 3D keypoint estimation and body mesh estimation`, the [paper](https://openaccess.thecvf.com/content/CVPR2021/papers/Li_HybrIK_A_Hybrid_Analytical-Neural_Inverse_Kinematics_Solution_for_3D_Human_CVPR_2021_paper.pdf), _HybrIK: A Hybrid Analytical-Neural Inverse Kinematics Solution for 3D Human Pose and Shape Estimation_, proposed to jointly learn coarse estimations of body shape and pose parameters first, and then use `HybrIK` to refine pose estimation and generate more realistic and accurate body meshes and poses. In `HybrIK`, relative rotations are decomposed into `twist` and `swing`. While `swing` rotation is predicted by neural networks, `twist` rotation is calculated analytically.

Below is the learning framework of `HybrIK`:

<div align=center>![Learning Framework of HybrIK](/demo/framework.png)

### 1.2 Project Motivation and Tasks

In the paper of `HybrIK`, the authors proposed 2 methods: `naive HybrIK` and `adaptive HybrIK`. It is believed that `adaptive HybrIK` can generate better results, because by `adaptive HybrIK`, the reconstruction error won't accumulate from the ancestral nodes to the current joint. However, `adaptive HybrIK` is heuristic, and it is unclear if it is the best option for minimizing the reconstruction error.

In this project, our aims are:

- Propose $\lambda$-HybrIK, adding a tuning parameter to provide an _interpolation_ between `naive HybrIK` and `adaptive HybrIK`;

- Evaluate `HybrIK` with different $\lambda$ values and report the reconstruction errors.

Below is the $\lambda$-HybrIK algorithm that we proposed:

<div align=center>![Lambda HybrIK Algorithm](/demo/algorithm.png)

## 2. Demo and Conclusion

The results can be found at [here](https://drive.google.com/drive/folders/1K6U3LFzHFFvpT908A8deQIGXEGuqQJVV?usp=sharing).

## 3. Acknowledgement
