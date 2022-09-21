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

## 3. 

### Codigo em python:

#### image = skimage.io.imread(fname="data/plant-seedling.jpg")
#### fig, ax = plt.subplots()
#### plt.imshow(image)
#### colors = ("red", "green", "blue")
#### channel_ids = (0, 1, 2)
#### plt.figure()
#### plt.xlim([0, 256])
#### for channel_id, c in zip(channel_ids, colors):
####     histogram, bin_edges = np.histogram(
####         image[:, :, channel_id], bins=256, range=(0, 256)
####     )
####     plt.plot(bin_edges[0:-1], histogram, color=c)
#### plt.title("Color Histogram")
#### plt.xlabel("Color value")
#### plt.ylabel("Pixel count")

### Imagem resultante da execução do codigo:

![https://i.imgur.com/tuiTPiV.jpg](https://i.imgur.com/tuiTPiV.jpg)

## 4. 

### Codigo em python:

#### import matplotlib
#### import matplotlib.pyplot as plt
#### import numpy as np
#### from skimage import data, img_as_float
#### from skimage import exposure
#### matplotlib.rcParams['font.size'] = 8
#### def plot_img_and_hist(image, axes, bins=256):
####     image = img_as_float(image)
####     ax_img, ax_hist = axes
####     ax_cdf = ax_hist.twinx()
####     # Display image
####     ax_img.imshow(image, cmap=plt.cm.gray)
####     ax_img.set_axis_off()
####     ax_hist.hist(image.ravel(), bins=bins, histtype='step', color='black')
####     ax_hist.ticklabel_format(axis='y', style='scientific', scilimits=(0, 0))
####     ax_hist.set_xlabel('Pixel intensity')
####     ax_hist.set_xlim(0, 1)
####     ax_hist.set_yticks([])
####     img_cdf, bins = exposure.cumulative_distribution(image, bins)
####     ax_cdf.plot(bins, img_cdf, 'r')
####     ax_cdf.set_yticks([])
####     return ax_img, ax_hist, ax_cdf

#### img = data.moon()
#### p2, p98 = np.percentile(img, (2, 98))
#### img_rescale = exposure.rescale_intensity(img, in_range=(p2, p98))
#### img_eq = exposure.equalize_hist(img)
#### fig = plt.figure(figsize=(8, 5))
#### axes = np.zeros((2, 4), dtype=np.object)
#### axes[0, 0] = fig.add_subplot(2, 4, 1)
#### for i in range(1, 4):
####     axes[0, i] = fig.add_subplot(2, 4, 1+i, sharex=axes[0,0], sharey=axes[0,0])
#### for i in range(0, 4):
####     axes[1, i] = fig.add_subplot(2, 4, 5+i)
#### ax_img, ax_hist, ax_cdf = plot_img_and_hist(img, axes[:, 0])
#### ax_img.set_title('Low contrast image')
#### y_min, y_max = ax_hist.get_ylim()
#### ax_hist.set_ylabel('Number of pixels')
#### ax_hist.set_yticks(np.linspace(0, y_max, 5))
#### ax_img, ax_hist, ax_cdf = plot_img_and_hist(img_rescale, axes[:, 1])
#### ax_img.set_title('Contrast stretching')
#### ax_img, ax_hist, ax_cdf = plot_img_and_hist(img_eq, axes[:, 2])
#### ax_img.set_title('Histogram equalization')
#### ax_img, ax_hist, ax_cdf = plot_img_and_hist(img_adapteq, axes[:, 3])
#### ax_img.set_title('Adaptive equalization')
#### ax_cdf.set_ylabel('Fraction of total intensity')
#### ax_cdf.set_yticks(np.linspace(0, 1, 5))
#### fig.tight_layout()
#### plt.show()

### Imagem resultante da execução do codigo:

![https://i.imgur.com/cJqTyjE.png](https://i.imgur.com/cJqTyjE.png)

## 5. 

### Metodo:

#### Para detectar se uma foto esta subexposta ou superexposta atraves de seu histograma devemos observar se sua curva colide com um dos lados da imagem. Se a curva colidir com lado esquerdo provavelmente a foto esta subexposta e se colide do lado direito superexposta.

![https://i.imgur.com/yYuvGJx.jpg](https://i.imgur.com/yYuvGJx.jpg)

## 6. 

### Metodo:

#### Já em relação ao contraste percebe-se que imagens com pouco contraste tem seu histograma com grande volume de pixels concentrados em uma pequena faixa de tons. Já a imagem com muito contraste normalmente ira ter uma vasta distribuição de tons e predominanmente separado em grupos.

![https://i.imgur.com/sQxgTim.jpg](https://i.imgur.com/sQxgTim.jpg)




