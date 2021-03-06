## ##Update
- Adopt new layers of EfficientNet-B1 to extract feature maps. The accuracy of small face detection increses obviously. 
- Add report and slides

## DSFD: Dual Shot Face Detector ##
[A PyTorch Implementation of Dual Shot Face Detector](https://arxiv.org/abs/1810.10220?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+arxiv%2FQSXk+%28ExcitingAds%21+cs+updates+on+arXiv.org%29)

### Description
We use basenet [VGG16](https://drive.google.com/file/d/1iQRZcHhc7SjuuRwzt-5jO6YLJjUTGxwn/view), [EfficientNet-B0](http://storage.googleapis.com/public-models/efficientnet/efficientnet-b0-355c32eb.pth) and [EfficientNet-B1](http://storage.googleapis.com/public-models/efficientnet/efficientnet-b1-f1951068.pth) to train DSFD, the model can be downloaded in [DSFD with VGG](https://pan.baidu.com/s/17cpDHEwYVxWmOIPqUy5zCQ).
 
The AP using VGG16 in AFW,PASCAL,FDDB as following:

| 	AFW     |   PASCAL	|   FDDB   |
| --------- |-----------| ---------|
|	  99.89   |   99.11   |   98.3   |

The performance on small face detection using EfficientNet-B0 and EfficientNet-B1 is not good enough, we are still working on it.  
 
### Requirement
* pytorch 0.3 
* opencv 
* numpy 
* easydict

### Prepare data 
1. download WIDER face dataset
2. modify data/config.py 
3. ``` python prepare_wider_data.py```


### Train 
``` 
python train.py --batch_size 4 
		--model vgg\efficient_b0\efficient_b1 
		--lr 5e-4
``` 

### Evalution
According to yourself dataset path,modify data/config.py 
1. Evaluate on AFW.
```
python tools/afw_test.py
```
2. Evaluate on FDDB 
```
python tools/fddb_test.py
```
3. Evaluate on PASCAL  face 
``` 
python tools/pascal_test.py
```
4. test on WIDER FACE 
```
python tools/wider_test.py
```
### Demo 
you can test yourself image
```
python demo.py
```
### Result
#### VGG16
<div align="center">
<img src="https://github.com/mexiQQ/DSFD-VGG16-EfficientNet/blob/master/VGG16/test1.jpg" height="300px" alt="demo" >
<img src="https://github.com/mexiQQ/DSFD-VGG16-EfficientNet/blob/master/VGG16/test6.jpg" height="300px" alt="demo" >
</div>

#### EfficientNet-B0
<div align="center">
<img src="https://github.com/mexiQQ/DSFD-VGG16-EfficientNet/blob/master/EfficientNet-B0/test1.jpg" height="300px" alt="demo" >
<img src="https://github.com/mexiQQ/DSFD-VGG16-EfficientNet/blob/master/EfficientNet-B0/test6.jpg" height="300px" alt="demo" >
</div>

#### EfficientNet-B1
<div align="center">
<img src="https://github.com/mexiQQ/DSFD-VGG16-EfficientNet/blob/master/EfficientNet-B1/test1.jpg" height="300px" alt="demo" >
<img src="https://github.com/mexiQQ/DSFD-VGG16-EfficientNet/blob/master/EfficientNet-B1/test6.jpg" height="300px" alt="demo" >
</div>

### About:

This page (code, report and presentation) is the group C submission for Final project for CS256: Selected Topic in Artificial Intelligence, Section 2. Leb by Instructor: Mashhour Solh, Ph.D.
The group members are:. "Jianwei Li, Peilu Liu, Ruchira Gothankar, Akash Budholia, Akshar Panchal".

The code maybe used for educational and commercial use under no warranties. For questions on this project and code please reach out to: "ljw040426@gmail.com"

### Credits:

This project was conducted with free credits provided by AWS educate team.

### References
* [Dual Shot Face Detector](https://arxiv.org/abs/1810.10220?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+arxiv%2FQSXk+%28ExcitingAds%21+cs+updates+on+arXiv.org%29)
* [ssd.pytorch](https://github.com/amdegroot/ssd.pytorch)
* [DSFD.pytorch](https://github.com/yxlijun/DSFD.pytorch)
* [EfficientNet-PyTorch](https://github.com/lukemelas/EfficientNet-PyTorch)
