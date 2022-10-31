# *Exercicio Semana 11*

## *Exercicio:* Faça uma pesquisa sobre como é possível aplicar os operadores de gradiente:

## - Roberts
## - Prewitt
## - Sobel


## *Repostas:*  

## Gradiente de Roberts

### Codigo em python:

import cv2
img = cv2.imread('test.jpg') 
cv2.imshow('Original', img)
cv2.waitKey(0)
img_gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
img_blur = cv2.GaussianBlur(img_gray, (3,3), 0) 
sobelx = cv2.Sobel(src=img_blur, ddepth=cv2.CV_64F, dx=1, dy=0, ksize=5) # Sobel Edge Detection on the X axis
sobely = cv2.Sobel(src=img_blur, ddepth=cv2.CV_64F, dx=0, dy=1, ksize=5) # Sobel Edge Detection on the Y axis
sobelxy = cv2.Sobel(src=img_blur, ddepth=cv2.CV_64F, dx=1, dy=1, ksize=5) # Combined X and Y Sobel Edge Detection
cv2.imshow('Sobel X', sobelx)
cv2.imshow('Sobel Y', sobely)
cv2.imshow('Sobel X Y using Sobel() function', sobelxy)
edges = cv2.Canny(image=img_blur, threshold1=100, threshold2=200) # Canny Edge Detection
cv2.imshow('Canny Edge Detection', edges)

### Imagens resultantes da execução do codigo:

#### Imagem original
![(https://i.imgur.com/Sd5QIs9.jpg)](https://i.imgur.com/Sd5QIs9.jpg)

#### Imagem com operação horizontal
![(https://i.imgur.com/F3QMXfW.jpg)](https://i.imgur.com/F3QMXfW.jpg)

#### Imagem com operação vertical
![(https://i.imgur.com/ihoTh2j.jpg)](https://i.imgur.com/ihoTh2j.jpg)

#### Imagem após encontrar a magnitude do gradiente
![(https://i.imgur.com/VkjIQuW.png)](https://i.imgur.com/VkjIQuW.png)
