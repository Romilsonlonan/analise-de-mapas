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

<hr>

## Obter o ID da camada

### Dados Vetoriais
path = os.getcwd() + '/*** Projetos em Desenvolvimento ***/PYQGIS/dados'

### abrindo uma camada vetorial
path_layer = path + '/aeroportos.shp'

layer = QgsVectorLayer(path_layer, "Aeroportos", "ogr")

### Adicionar a camada canvas 
QgsProject.instance().addMapLayer(layer)

## Obter o id
print(layer.id())

### extent da camada
print(layer.extent())

### Criar novos atributos (novos campos)
layer.startEditing()
layer.addAttribute(QgsField('area', QVariant.Double))
layer.commitChanges()

## Tipos de campos: String, Double e Int

## Obter informaçes de campos
print(layer.fields().names())

## Deletando um campo
layer.startEditing()
layer.deleteAttribute(15)
layer.commitChanges()

#
print(layer.fields().names()[4])


## Informaço das features
count = 0
for feature in layer.getFeatures():
    while count < 5:
        print(feature.attributes())
        count += 1
        
        
## Informaço do atributo [4]
count = 0
for feature in layer.getFeatures():
    while count < 5:
        print(feature.attributes()[4])
        count += 1        
        
        
        
## Alterando e update de campos
## Deletando um campo
layer.startEditing()
layer.deleteAttribute(14)
layer.commitChanges()


count = 0
for feature in layer.getFeatures():
    while count < 5:
        print(feature.geometry().asPoint()[0])
        count += 1   
        
        

## update 
layer.startEditing()
layer.addAttribute(QgsField('x', QVariant.Double))
layer.commitChanges()

layer.startEditing()
for feature in layer.getFeatures():
    id = feature.id()
    x = feature.geometry().asPoint()[0]
    attr_value = {14:x}
    layer.changeAttributeValues(id, attr_value)

layer.commitChanges()                   
    
'''
O código modifica uma camada vetorial, adicionando um novo campo "y" de tipo double 
e atualizando os valores desse campo com as coordenadas y das geometrias de cada feição.
'''

## Inicia a edição da camada para permitir modificações
layer.startEditing()

## Adiciona um novo campo de double chamado "y" à camada
layer.addAttribute(QgsField('y', QVariant.Double))

## Confirma as alterações realizadas na camada
layer.commitChanges()

## Reinicia a edição para modificar os valores dos atributos
layer.startEditing()

# Percorre cada feição da camada
for feature in layer.getFeatures():

    # Obtém o ID da feição atual
    id = feature.id()

    # Extrai a coordenada y da geometria da feição
    y = feature.geometry().asPoint()[1]

    # Cria um dicionário com o valor de y para o atributo 15
    attr_value = {15: y}

    # Atualiza os valores de atributos da feição com o novo valor de y
    layer.changeAttributeValues(id, attr_value)

## Confirma as alterações realizadas nos atributos
layer.commitChanges()

## seleçao por expresso
layer.selectByExpression("TipoAero = 'Nacional'", QgsVectorLayer.SetSelection)

## Inverso de seleçao
layer.invertSelection()

## Adiçao a seleçao
layer.selectByExpression("nome ilike 'N%'", QgsVectorLayer.AddToSelection)

# remove da seleçao
layer.selectByExpression("nome ilike 'N%'", QgsVectorLayer.RemoveFromSelection)

## Criar um objeto com a seleçao
selection = layer.selectedFeatures()
for feature in selection:
    print(feature.attributes())

<hr>    

## Automatizando tarefas
![Captura de tela de 2024-01-17 07-39-18](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/183adb4c-f72b-4db3-84bc-05f50e9db625)

# Define a variável `path` como o caminho para o diretório que contém as camadas vetoriais shapefile.
path = os.getcwd() + '/*** Projetos em Desenvolvimento ***/PYQGIS/dados'

## Imprime o caminho do diretório.
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

## A segunda parte do código funciona da seguinte forma:

* A linha project.setTitle('CURSO PYQGIS') define o título do projeto para "CURSO PYQGIS".
* A linha print(project.title()) imprime o título do projeto.
* Ao final da execução do código, o título do projeto será alterado para "CURSO PYQGIS".

## Aqui está um resumo mais conciso do que o código faz:

* Carrega todas as camadas vetoriais shapefile de um diretório e define o título do projeto.
