
# *Exercicio Semana 12*

## *Exercicio:* Faça uma pesquisa sobre APIs gráficas e elabore um resumo sobre seus achados. Para cada API gráfica (descreva pelo menos duas), inclua como a pipeline é documentada pelos desenvolvedores da API e quais linguagens de shading (shaders) são suportadas por cada API.


## *Repostas:* 

## OpenGL

#### A api grafica OpenGL foi criada pela Silicon Graphics e hoje é gerida pela organização Khonos Group e se tornou uma das mais utilizadas apis do mercado. Ela consiste em uma API multiplataforma para rederização de graficos 2D e 3D, alem da interação com GPUS e compatibilidade com diversos sistemas operacionais. Os shadders utilizados no OpenGL são o Vertex shader, Geometry Shader e Tessellation. Um dos principais usos essa API é na portabilidade de jogos desenvolvidos em windows para serem jogados no SteamOS, sistema baseado em linux.

### Diagrama do pipeline da API:
![(https://www.khronos.org/opengl/wiki_opengl/images/RenderingPipeline.png)](https://www.khronos.org/opengl/wiki_opengl/images/RenderingPipeline.png)

### Codigo para renderizar um triangulo:
#### glBegin(GL_TRIANGLES);
#### glColor3f(0.1, 0.2, 0.3);
#### glVertex3f(0, 0, 0);
#### glVertex3f(1, 0, 0);
#### glVertex3f(0, 1, 0);
#### glEnd();
