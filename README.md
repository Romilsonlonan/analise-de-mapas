# analise-de-mapas

![Captura de tela de 2024-01-17 07-03-52](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/ccf2b72b-e52e-4f29-92c6-d1c86910b983)
![Captura de tela de 2024-01-17 06-56-03](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/506aba90-6690-4fb9-8c35-3ebc1d3afb01)

```python
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
```
<hr>

## Obter o ID da camada
```python
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
```

### Criar novos atributos (novos campos)
## Tipos de campos: String, Double e Int
```python
layer.startEditing()
layer.addAttribute(QgsField('area', QVariant.Double))
layer.commitChanges()


## Obter informaçes de campos
print(layer.fields().names())
```

## Deletando um campo
```python
layer.startEditing()
layer.deleteAttribute(15)
layer.commitChanges()

#
print(layer.fields().names()[4])
```
```python
## Informaço das features
count = 0
for feature in layer.getFeatures():
    while count < 5:
        print(feature.attributes())
        count += 1
```
                
## Informaço do atributo [4]
```python
count = 0
for feature in layer.getFeatures():
    while count < 5:
        print(feature.attributes()[4])
        count += 1        
```        
        
        
## Alterando e update de campos
```python
# Deletando um campo
layer.startEditing()
layer.deleteAttribute(14)
layer.commitChanges()
```
```python
count = 0
for feature in layer.getFeatures():
    while count < 5:
        print(feature.geometry().asPoint()[0])
        count += 1   
```        
## Adiciona um novo campo de double chamado "x" à camada
## update 
```python
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
```
<hr>

## Adiciona um novo campo de double chamado "y" à camada
```python
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
```

## seleçao por expressao
```python
layer.selectByExpression("TipoAero = 'Nacional'", QgsVectorLayer.SetSelection)

## Inverso de seleçao
layer.invertSelection()
```

## Adiçao a seleçao
```python
layer.selectByExpression("nome ilike 'N%'", QgsVectorLayer.AddToSelection)
```

## remove da seleçao
```python
layer.selectByExpression("nome ilike 'N%'", QgsVectorLayer.RemoveFromSelection)
```

## Criar um objeto com a seleçao
```python
selection = layer.selectedFeatures()
for feature in selection:
    print(feature.attributes())
```
<hr>    

## Automatizando tarefas
![Captura de tela de 2024-01-17 07-39-18](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/183adb4c-f72b-4db3-84bc-05f50e9db625)

```python
# Define a variável `path` como o caminho para o diretório que contém as camadas vetoriais shapefile.
path = os.getcwd() + '/*** Projetos em Desenvolvimento ***/PYQGIS/dados'

## Imprime o caminho do diretório.
print(path)

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
```

<hr>

## Define o título do projeto para "CURSO PYQGIS".
```python
project.setTitle('CURSO PYQGIS')

## Imprime o título do projeto
print(project.title())
```

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
* 

# FILTRO EM CAMADA

![Captura de tela de 2024-01-18 17-13-58](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/f9a31883-c4b4-4e9c-8f6b-1ce16a547f5b)

```python
path = os.getcwd() + '/*** Projetos em Desenvolvimento ***/PYQGIS/dados'

for root, diretory, files in os.walk(path):
    for file in files:
        if file.endswith('.shp'):
            path_vector = os.path.join(path,file)
            layer = QgsVectorLayer(path_vector, file[0:-4],"ogr")
            QgsProject.instance().addMapLayer(layer)
            
municipios = QgsProject.instance().mapLayersByName("municipios")[0]
print(municipios.featureCount())

municipios.setSubsetString("uf = 'RJ'")
print(municipios.featureCount())

municipios.setSubsetString("")
```


## Resumo geral:

O código acima carrega todas as camadas vetoriais do formato .shp na pasta dados no projeto QGIS. Em seguida, o código imprime o número de features na camada municipios. Por fim, o código aplica um filtro à camada municipios para selecionar apenas as features cujo atributo uf tem o valor RJ. O código imprime o número de features na camada municipios após a aplicação do filtro.

## Sobre o filtro em camada:

O filtro em camada é uma operação que permite selecionar apenas um subconjunto de features de uma camada vetorial. O filtro pode ser aplicado com base em qualquer atributo da camada.

No código acima, o filtro é aplicado com base no atributo uf da camada municipios. O valor do filtro é RJ. Isso significa que o filtro selecionará apenas as features cujas uf têm o valor RJ.

O filtro pode ser aplicado de forma permanente ou temporária. No código acima, o filtro é aplicado de forma temporária. Isso significa que o filtro é aplicado apenas quando o código é executado. Se você quiser aplicar o filtro de forma permanente, você pode usar o método setSubsetString() da camada vetorial.

No exemplo acima, o método setSubsetString() é usado para aplicar o filtro de forma permanente. A linha municipios.setSubsetString("uf = 'RJ'") aplica o filtro à camada municipios. A linha municipios.setSubsetString("") remove o filtro da camada municipios.
