# analise-de-mapas

![Captura de tela de 2024-01-17 07-03-52](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/ccf2b72b-e52e-4f29-92c6-d1c86910b983)
![Captura de tela de 2024-01-17 06-56-03](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/506aba90-6690-4fb9-8c35-3ebc1d3afb01)


## Atribui a variável `project` a uma instância do objeto `QgsProject`
project = QgsProject.instance()

## Lê o projeto `dados_sing.qgs` do diretório `/home/romilson/*** Projetos em Desenvolvimento ***/PYQGIS/dados/`
project.read('/home/romilson/*** Projetos em Desenvolvimento ***/PYQGIS/dados/dados_sing.qgs')

## Grava o projeto `dados_sing.qgs` no diretório `/home/romilson/*** Projetos em Desenvolvimento ***/PYQGIS/dados/`
project.write('/home/romilson/*** Projetos em Desenvolvimento ***/PYQGIS/dados/dados_sing.qgs')

## Define a cor de fundo do projeto para `#3399FF`
project.setBackgroundColor(QColor(51, 153, 255))

## Imprime o número de camadas do projeto
print(project.count())


# Automatizando tarefas
![Captura de tela de 2024-01-17 07-39-18](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/183adb4c-f72b-4db3-84bc-05f50e9db625)

# Define a variável `path` como o caminho para o diretório que contém as camadas vetoriais shapefile.
path = os.getcwd() + '/*** Projetos em Desenvolvimento ***/PYQGIS/dados'

# Imprime o caminho do diretório.
print(path)

<hr>

## Percorre o diretório `path` recursivamente.
for root, diretory, files in os.walk(path):

    # Percorre os arquivos no diretório atual.
    for file in files:

        # Verifica se o arquivo termina com a extensão .shp.
        if file.endswith('.shp'):

            # Cria o caminho completo para o arquivo .shp.
            path_vector = os.path.join(path, file)

            # Cria um objeto QgsVectorLayer a partir do arquivo shapefile.
            layer = QgsVectorLayer(path_vector, file[0:-4], "ogr")

            # Adiciona a camada ao projeto QGIS.
            QgsProject.instance().addMapLayer(layer)

            # Imprime o nome do arquivo.
            print(file)

## Define o título do projeto para "CURSO PYQGIS".
project.setTitle('CURSO PYQGIS')


## Imprime o título do projeto
print(project.title())

<hr>

## O código acima faz duas coisas:

* Carrega todas as camadas vetoriais shapefile de um diretório específico no projeto QGIS atualmente aberto.
* Define o título do projeto para "CURSO PYQGIS".

## A primeira parte do código funciona da seguinte forma:

* A linha for root, diretory, files in os.walk(path) inicia um loop que percorre o diretório path recursivamente.
* A linha for file in files inicia um loop que percorre os arquivos no diretório atual.
* A linha if file.endswith('.shp') verifica se o arquivo termina com a extensão .shp.

## Se o arquivo terminar com a extensão .shp, as linhas seguintes são executadas:
* A linha path_vector = os.path.join(path,file) cria o caminho completo para o arquivo .shp.
* A linha layer = QgsVectorLayer(path_vector, file[0:-4],"ogr") cria um objeto QgsVectorLayer a partir do arquivo shapefile.
* A linha QgsProject.instance().addMapLayer(layer) adiciona a camada ao projeto QGIS.
* A linha print(file) imprime o nome do arquivo.
* Ao final da execução do código, todas as camadas vetoriais shapefile do diretório especificado serão carregadas no projeto QGIS.

A segunda parte do código funciona da seguinte forma:

A linha project.setTitle('CURSO PYQGIS') define o título do projeto para "CURSO PYQGIS".
A linha print(project.title()) imprime o título do projeto.
Ao final da execução do código, o título do projeto será alterado para "CURSO PYQGIS".

Aqui está um resumo mais conciso do que o código faz:

Carrega todas as camadas vetoriais shapefile de um diretório e define o título do projeto.
