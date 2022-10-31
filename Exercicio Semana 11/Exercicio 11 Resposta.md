# *Exercicio Semana 11*

## *Exercicio:* Faça uma pesquisa sobre como é possível aplicar os operadores de gradiente:

### - Roberts
### - Prewitt
### - Sobel


## *Repostas:* 

## Operadores de Roberts

### Codigo em python:

#### import sys
#### import numpy as np
#### from scipy import ndimage
#### import matplotlib.pyplot as plt
#### from skimage import io
#### plt.rcParams['figure.figsize'] = [15, 10]
#### roberts_cross_v = np.array( [[ 0, 0, 0 ],
####                              [ 0, 1, 0 ],
####                              [ 0, 0,-1 ]] )
#### 
#### roberts_cross_h = np.array( [[ 0, 0, 0 ],
####                              [ 0, 0, 1 ],
####                              [ 0,-1, 0 ]] )
#### img = io.imread('https://i.imgur.com/Sd5QIs9.jpg')
#### img = img.astype('float64')
#### gray_img = np.dot(img[...,:3], [0.2989, 0.5870, 0.1140])
#### gray_img /= 255
#### vertical = ndimage.convolve( gray_img, roberts_cross_v )
#### horizontal = ndimage.convolve( gray_img, roberts_cross_h )
#### edged_img = np.sqrt( np.square(horizontal) + np.square(vertical))
#### plt.imshow(vertical, cmap=plt.get_cmap('gray'))
#### plt.show()
#### plt.imshow(horizontal, cmap=plt.get_cmap('gray'))
#### plt.show()
#### plt.imshow(edged_img, cmap=plt.get_cmap('gray'))
#### plt.show()

### Imagens resultantes da execução do codigo:

#### Imagem original
![(https://i.imgur.com/Sd5QIs9.jpg)](https://i.imgur.com/Sd5QIs9.jpg)

#### Imagem com operação horizontal
![https://i.imgur.com/zidR1kc.png](https://i.imgur.com/zidR1kc.png)

#### Imagem com operação vertical
![(https://i.imgur.com/pu1LFfX.png)](https://i.imgur.com/pu1LFfX.png)

#### Imagem após encontrar a magnitude do gradiente
![(https://i.imgur.com/HkQBlXv.png)](https://i.imgur.com/HkQBlXv.png)

 --------------------
 
## Operadores de Priwit

### Codigo em python:

#### import cv2
#### import numpy as np
#### img = cv2.imread('messi5.jpg')
#### gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
#### img_gaussian = cv2.GaussianBlur(gray,(3,3),0)
#### kernelx = np.array([[1,1,1],[0,0,0],[-1,-1,-1]])
#### kernely = np.array([[-1,0,1],[-1,0,1],[-1,0,1]])
#### img_prewittx = cv2.filter2D(img_gaussian, -1, kernelx)
#### img_prewitty = cv2.filter2D(img_gaussian, -1, kernely)
#### cv2.imshow("Prewitt X", img_prewittx)
#### cv2.imshow("Prewitt Y", img_prewitty)
#### cv2.imshow("Prewitt", img_prewittx + img_prewitty)

### Imagens resultantes da execução do codigo:

#### Imagem original
![(https://i.imgur.com/Sd5QIs9.jpg)](https://i.imgur.com/Sd5QIs9.jpg)

#### Imagem com operação horizontal
![https://i.imgur.com/zidR1kc.png](https://i.imgur.com/zidR1kc.png)

#### Imagem com operação vertical
![(https://i.imgur.com/pu1LFfX.png)](https://i.imgur.com/pu1LFfX.png)

#### Imagem após encontrar a magnitude do gradiente
![(https://i.imgur.com/HkQBlXv.png)](https://i.imgur.com/HkQBlXv.png)

 --------------------
## Operadores de Sobel

### Codigo em python:

#### import cv2
#### img = cv2.imread('test.jpg') 
#### cv2.imshow('Original', img)
#### cv2.waitKey(0)
#### img_gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
#### img_blur = cv2.GaussianBlur(img_gray, (3,3), 0) 
#### sobelx = cv2.Sobel(src=img_blur, ddepth=cv2.CV_64F, dx=1, dy=0, ksize=5) # Sobel Edge Detection on the X axis
#### sobely = cv2.Sobel(src=img_blur, ddepth=cv2.CV_64F, dx=0, dy=1, ksize=5) # Sobel Edge Detection on the Y axis
#### sobelxy = cv2.Sobel(src=img_blur, ddepth=cv2.CV_64F, dx=1, dy=1, ksize=5) # Combined X and Y Sobel Edge Detection
#### cv2.imshow('Sobel X', sobelx)
#### cv2.imshow('Sobel Y', sobely)
#### cv2.imshow('Sobel X Y using Sobel() function', sobelxy)

### Imagens resultantes da execução do codigo:

#### Imagem original
![(https://i.imgur.com/Sd5QIs9.jpg)](https://i.imgur.com/Sd5QIs9.jpg)

#### Imagem com operação horizontal
![(https://i.imgur.com/F3QMXfW.jpg)](https://i.imgur.com/F3QMXfW.jpg)

#### Imagem com operação vertical
![(https://i.imgur.com/ihoTh2j.jpg)](https://i.imgur.com/ihoTh2j.jpg)

#### Imagem após encontrar a magnitude do gradiente
![(https://i.imgur.com/9x6AHZQ.jpg)](https://i.imgur.com/9x6AHZQ.jpg)
