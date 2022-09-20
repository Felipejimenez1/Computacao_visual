# *Exercicio Semana 4*

## *Exercicio:* Faça uma pesquisa sobre como é possível:

## 1. Realizar a limiarização de uma imagem usando Python e scikit-image.
## 2. Plotar o histograma de uma imagem tons de cinza usando Python, scikit-image e matplotlib.
## 3. Plotar o histograma de uma imagem colorida (um histograma por canal de cor) usando Python, scikit-image e matplotlib.
## 4. Equalizar o histograma de uma imagem usando Python e scikit-image.
## 5. Detectar (concluir) que uma foto está subexposta ou que está superexposta, analisando o histograma.
## 6. Detectar (concluir) se uma imagem está com baixo contraste ou alto contraste, analisando o histograma.

## Descreva o problema, a solução do problema e como o uso do filtro de suavização ajudou na solução. Procure incluir imagens que mostram o processo durante a solução do problema.

## *Reposta:*  

### Artigo de referencia: https://cchen156.github.io/paper/18CVPR_SID.pdf

### O artigo selecionado busca criar um software capaz de melhorar a performance de cameras em ambientes com pouca ou nenhuma luminosidade. O problema indentificado é que para conseguir ter boas fotos com pouca luz o aparelho pode aumentar a quantidade de luz que recebe no sensor, aumentando a visibilidade, mas tambem adicionando ruido e alterando o balanço de cores da foto. A solução para o problema foi a criação de uma inteligencia artificial que recebe diversas fotos da mesma cena, com diferentes exposições a luz. A foto com pouca entrada de luz, e portanto a com menos ruido, é a foto utilizada para aplicação dos filtros. As outras fotos, com mais detalhes visiveis por conta da maior quantidade de luz, são a amostra de treinamento da inteligencia artificial, que utiliza esses dados para aplicar um filtro de suavisação muito mais eficiente que metodos desenvolvidos anteriormente.

### aplicação do filtro na cena exemplo:

![https://i.imgur.com/QTopsHj.png](https://i.imgur.com/QTopsHj.png)

