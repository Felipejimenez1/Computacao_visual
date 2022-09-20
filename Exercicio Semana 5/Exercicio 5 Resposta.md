# *Exercicio Semana 4*

## *Exercicio:* Faça uma pesquisa sobre como é possível:

### 1. Realizar a limiarização de uma imagem usando Python e scikit-image.
### 2. Plotar o histograma de uma imagem tons de cinza usando Python, scikit-image e matplotlib.
### 3. Plotar o histograma de uma imagem colorida (um histograma por canal de cor) usando Python, scikit-image e matplotlib.
### 4. Equalizar o histograma de uma imagem usando Python e scikit-image.
### 5. Detectar (concluir) que uma foto está subexposta ou que está superexposta, analisando o histograma.
### 6. Detectar (concluir) se uma imagem está com baixo contraste ou alto contraste, analisando o histograma.


## *Repostas:*  

## 1. 

### Codigo em python: 

#### import matplotlib.pyplot as plt
#### from skimage import data
#### from skimage.filters import threshold_otsu

#### image = data.camera()
#### thresh = threshold_otsu(image)
#### binary = image > thresh
#### fig, axes = plt.subplots(ncols=3, figsize=(8, 2.5))
#### ax = axes.ravel()
#### ax[0] = plt.subplot(1, 3, 1)
#### ax[1] = plt.subplot(1, 3, 2)
#### ax[2] = plt.subplot(1, 3, 3, sharex=ax[0], sharey=ax[0])
#### ax[0].imshow(image, cmap=plt.cm.gray)
#### ax[0].set_title('Original')
#### ax[0].axis('off')
#### ax[1].hist(image.ravel(), bins=256)
#### ax[1].set_title('Histogram')
#### ax[1].axvline(thresh, color='r')
#### ax[2].imshow(binary, cmap=plt.cm.gray)
#### ax[2].set_title('Thresholded')
#### ax[2].axis('off')
#### plt.show()

### Imagem resultante da execução do codigo:

![https://i.imgur.com/QTopsHj.png](https://i.imgur.com/9CTXamF.png)


## 2. 

### Codigo em python: 

#### import numpy as np
#### import skimage.color
#### import skimage.io
#### import matplotlib.pyplot as plt
#### %matplotlib widget
#### image = skimage.io.imread(fname="data/plant-seedling.jpg", as_gray=True)
#### fig, ax = plt.subplots()
#### plt.imshow(image, cmap="gray")
#### histogram, bin_edges = np.histogram(image, bins=256, range=(0, 1))
#### plt.figure()
#### plt.title("Grayscale Histogram")
#### plt.xlabel("grayscale value")
#### plt.ylabel("pixel count")
#### plt.xlim([0.0, 1.0])
#### plt.plot(bin_edges[0:-1], histogram)

### Imagem resultante da execução do codigo:

![https://i.imgur.com/kKlpsD2.png](https://i.imgur.com/kKlpsD2.png)


