### 1. Paper title: Regularize implicit neural representation by itself, CVPR, 2023 
![image](https://github.com/user-attachments/assets/213b0bb2-a8b7-428c-8a8f-5de6e8f9e0a9)
### 2. Problem to solve:
Although INRs have strong representation ability of continous function, the generalization of INRs need to be improved, especially for the non-uniformly sampled data. The hyper-parameters of INRs (e.g., omega and phi) can control the smoothness degree of reconstruction results, however, the adjusting this hyper-parameter cannot make the non-uniformly missing case perform best, as different locations might have different missing rates. There figures show that the ways of sampling will affect the accuracy and reliability of reconstruction results, and the hyper-parameters need to be adjusted (the necessary of regularization). 

![image](https://github.com/user-attachments/assets/84c05c97-47a5-4407-971d-b87ebbf7df96)

![image](https://github.com/user-attachments/assets/bfe4a6e5-f53b-4862-a5fd-9ed39c0522c0)

Here are some methods can be used to enhance the generalization of INRs, like the adaptive and implicit regularization (AIR), total variance, tikhononv regularization, etc. However, some of these methods have fixed smooth effect or not enough smooth effect. 

Since the vanilla INR’s loss function is pixel-by-pixel, it ignores the structural features of images. Low rank is a well-known prior that describes the correlation between rows and columns. However, a low-rank matrix cannot express the details of a signal well because these details are located in the subspaces corresponding to the small singular value of the image. In this paper, we choose Dirichlet Energy (DE) to describe images’ local and non-local self-similarity. However, here are two problems in using DE: (a) laplace matrix is unknown and large-scale similarities cannot be captured. 

### 3. Major contribution:

Using tiny implicit neural representation to learn the laplace matrix in the learning process, which can introduce the smoothness of laplace matrix implicitly, and can restrict the rank of laplace matrix. As a regularizer both in a new form and with new meaning, INRR can be combined with other signal representation methods, such as deep matrix factorization (DMF). The contribution of INRR include the following:

![image](https://github.com/user-attachments/assets/7b1e9003-2fef-4919-9924-46dec7991ee1)

1. Neural Tangent Kernel (NTK) theoretically analyzes the generalization ability of INR and why INR performs poorly with nonuniform sampling is given.
2.  A tiny INR parameterized regularizer named INRR is proposed based on DE, which perfectly integrates the image’s self-similarity with the smoothness of the Laplacian matrix.
3.  A series of properties derived from INRR, including momentum methods, multi-scale similarity, and generalization ability, are revealed by well-designed numerical experiments. 

### 4. Theory and Experiment results:
Theorem 1 illustrates that the smoothness of represented signal is controlled by the hyper-parameter δ globally.

![image](https://github.com/user-attachments/assets/e6aa563a-0e83-4f03-a93c-fa44c70456db)

There are three requirments for the laplace matrix to make it (leanring the laplace matrix from training data) meaningful and practical: (a) positive semi-definite; (b) the sum of each row equals zero; (c) the laplace matrix should be smooth due to the smoothness of natural images. Therefore, we propose an implicit neural representation regularization (INRR) which is expressed as follows:  

![image](https://github.com/user-attachments/assets/e0e210f1-5705-4e39-a5e6-a25c164e3a75)


The reason why INRR performs better:

(a) Tiny INR can implicitly encode the smoothness into laplace matrix. 

![image](https://github.com/user-attachments/assets/c9b42151-dc34-4f3c-9a4e-c4d455948874)


(b) INRR behaves like a momentum. INRR and AIR keep the decaying trend for both observed and unobserved MSEs. Significantly, the proposed method INRR keeps the decaying trend better than the method AIR due to extra smoothness introduced into the laplace matrix.

![image](https://github.com/user-attachments/assets/c869f789-99f8-4fea-989e-1e31b4720759)


(c)  ReLU, FCN, and SIREN first fit the low-frequency components and then gradually fit the high-frequency components. More specifically, the effective rank of DMF with three factors, SIREN, and ReLU FCN, increases gradually as the line plot, where the effective rank can measure the effective dimension of the matrix with more accuracy than discrete rank.  

![image](https://github.com/user-attachments/assets/93b0db8e-aacc-4b28-87be-f183199ca4f5)


(d) INRR connects implicit bias with multi-scale self-similarity. Due to the implicit bias of fidelity term, INRR can capture different scales of data similarity. 

![image](https://github.com/user-attachments/assets/bf5da8f6-9dda-4f4e-bce6-658caa434b3d)


(e) the importance of learnable regularization.

![image](https://github.com/user-attachments/assets/52cf404c-3af4-440e-8476-1482e10b5dcc)

### 5. Lessons learnt:
A learnable regularization with Dirichlet Energy (DE), which represented by a tiny INR. The tiny INR inputs the coordinate of image and output the laplace matrix, which can implicitly encode the implicit bias, smoothness, multi-scale self-similarity into the regularization. 

I think it can be utilized in FWI, which can compare with classical regularization (e.g., TV and Tikhonov regularizations). And some experiments can be refered in INRs-based FWI methods.  









