# Paper Information

Repository of our following paper **Segmentation of Variants of Nuclei on Whole Slide Images by Using Radiomic Features** (Bioengineering): [Paper](https://)

1. ***Abstract***
	<p align="justify"> 	
	The histopathological segmentation of nuclear types is a challenging task because nuclei exhibit distinct morphologies, textures, and staining characteristics. Accurate segmentation is critical because it affects the diagnostic workflow for patient assessment. In this study, a framework was proposed for segmenting various types of nuclei from different body organs. The proposed framework improved the segmentation performance for each nuclear type using radiomics. First, we used distinct radiomic features to extract and analyze quantitative information about each type of nucleus and subsequently trained various classifiers based on the best input sub-features of each radiomic feature selected by a LASSO operator. Second, we inputted the outputs of the best classifier to various segmentation models to learn the variants of nuclei. Using the MoNuSAC2020 dataset, we achieved state-of-the-art segmentation performance for each category of nuclei type despite the complexity, overlapping, and obscure regions. The generalized adaptability of the proposed framework was verified by the consistent performance obtained in whole slide images of different body organs and radiomic features.
	 </p>
	<br />

	<img src="/Images/Idea_N.PNG" width="700"  align="justify">
	<br />

2. ***Dataset***

	We used the following public WSI dataset as reference standards for training and evaluating our models.

	Link: [MoNuSAC2020](https://monusac-2020.grand-challenge.org/)

	<img src="/Images/Dataset.PNG" width="300">
	<br />	<br />

3. ***Environment Setup***

	We used python with environment 3.7.x ++ and install necessary packages and dependencies using dockerfile:
	- Numpy
	- Tensorflow 
	- Keras
	- Scikit-learn
	- Pandas
	- OpenSlide
	- OpenCV
	- Scipy
	- Six
	<br />

4. ***Directory Structure:***

	- README.md
	- Images
	- DockerFiles (Docker.cpu, Docker.gpu)
	
	**(Stage-A): WSI Processing Module Scipts**

	1) WSI-XML-Read-Write
	2) Creating Patches With Masks 

	**(Stage-B): Patch Retrieval Module Scipts**
	
	1) Representation of Radiomics Features (Part-1)
	2) Representation of Radiomics Features (Part-2)
	3) Representation of Radiomics Features (Part-3)
	4) LASSO Operator, Training Different Classifiers, Selection of the Best Classifier

	**(Stage-C): Segmentation Module Scipts**

	1) With Radiomics (User-Defined Selection of Model, Training Different Models)
	2) Without Radiomics (User-Defined Selection of Model, Training Different Models)
	<br />

5. ***Basic Experimental Information:***

	We used four radiomics features to find different characteristics about each nuclei type from WSIs which help our model to learn and segment the input samples more accurately with substantial information.

	- GLCM
	- GLDM
	- GLRLM
	- GLSZM
	<br />
	<img src="/Images/Radiomics.png" width="800">

	**All Modules Information**

	Our framework comprises of three basic modules with following specifications.

	**(Stage-A): WSI Processing Module**

	1) SVS Files
	2) XML (Mask) Files

	**(Stage-B): Patch Retrieval Module**
	
	We used the following classifier models.

	1) Decision Tree
	2) K-Nearest Neighbors
	3) Bagging, and 
	4) Gradient Boost

	**(Stage-C): Segmentation Module**
	
	We used the following four different models.

	1) U-Net
	2) Seg-Net
        3) MultiResU-Net
        4) Refine-Net

	<br />

6. ***Commands To Use Docker Files:***

	To run a script from scratch you can use the following docker files.

	  git clone https://github.com/AIMILab/Radiomics.git
		
	A. Without CUDA Support:

	- Built the image from scratch (Docker.cpu file)

	  sudo docker build -t Radiomic_2024:Radiomic_2024-cpu -f DockerFiles/Dockerfile_cpu .

	  sudo docker run -it -v "$PWD"/Scripts:/root Radiomic_2023:Radiomic_2024-cpu

	B. With CUDA Support:

	- Built the image from scratch (Docker.gpu file)

	  sudo docker build -t Radiomic_2024:Radiomic_2024-gpu -f DockerFiles/Dockerfile_gpu .

	  sudo nvidia-docker run -it -v "$PWD"/Scripts:/root Radiomic_2024:Radiomic_2024-gpu
	<br />

<!-- 7. ***Results:***

	**A. Classifier Results**

	<img src="/Images/Classifier.jpg" width="500">
	<br />
	<br />

	**B. Segmentation Results & Visualization**

	<img src="/Images/Segmentation Reults 1.jpg" width="700">
	<br />
	<br />
	<img src="/Images/Segmentation Reults 2.PNG" width="700">

	<br />
	<br /> 
 -->

***!! NOTE: !!*** 

Each Jupyter notebook includes 

1) All of the above models (each case).
2) Our experimental strategy to segment variants of nuclei on WSI dataset.
3) We also added the confusion matrices and visualization analysis for each strategy.

To evaluate the performance results faster we recommend to use docker files. We used Quadro RTX 5000 16GB. RAM 128GB


<!-- # Citation:

If you find this code useful in your research, please consider citing:

@article{,
AUTHOR = {Sheikh, Taimoor Shakeel and Cho, Migyung},
TITLE = {Segmentation of Variants of Nuclei on Whole Slide Images by Using Radiomic Features},
JOURNAL = {Bioengineering},
VOLUME = {},
YEAR = {},
NUMBER = {},
ARTICLE-NUMBER = {},
URL = {https://},
ISSN = {},
DOI = {}
}
 -->
