
<h1 align="center">
  **GEOPROCESSAMENTO DE IMAGENS COM PYQGIS**
</h1>

<div align="center">
  <img src="https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/6944fdb3-c7e0-4b32-ba57-0e1f8416fb89" alt="PyQGIS">
</div>
<br>
<br>
Geoprocessamento de imagens é o conjunto de técnicas e métodos utilizados para capturar, armazenar, processar, analisar e visualizar dados espaciais. As imagens são um tipo de dado espacial que pode ser usado para representar uma variedade de características, como a topografia de um terreno, a distribuição de vegetação ou a densidade de população.

O geoprocessamento de imagens é uma ferramenta poderosa que pode ser usada para diversas aplicações, incluindo:

* **Monitoramento ambiental:** O geoprocessamento de imagens pode ser usado para monitorar o meio ambiente, como a qualidade da água, a cobertura vegetal ou a ocorrência de desastres naturais.

* **Planejamento urbano:** O geoprocessamento de imagens pode ser usado para planejar o desenvolvimento urbano, como a construção de rodovias, a expansão de bairros ou a identificação de áreas de risco.

* **Gestão de recursos naturais:** O geoprocessamento de imagens pode ser usado para gerenciar recursos naturais, como a agricultura, a pesca ou a exploração mineral.

* **Defesa:** O geoprocessamento de imagens pode ser usado para fins militares, como a vigilância de fronteiras ou a identificação de alvos.

O geoprocessamento de imagens é uma área de pesquisa e desenvolvimento em constante evolução. As novas tecnologias estão permitindo que o geoprocessamento seja usado de novas maneiras e para aplicações mais complexas.

Algumas das principais tendências que estão impulsionando a evolução do geoprocessamento de imagens incluem:

O aumento da disponibilidade de dados de imagens: O avanço da tecnologia de sensoriamento remoto está levando ao aumento da disponibilidade de dados de imagens de alta qualidade. Esses dados estão tornando possível realizar análises mais complexas e obter insights mais profundos sobre o mundo ao nosso redor.
O desenvolvimento de novas técnicas de processamento de imagens: As novas técnicas de processamento de imagens estão tornando possível identificar e extrair informações de dados de imagens de forma mais eficiente e precisa. Essas técnicas estão permitindo que o geoprocessamento seja usado para aplicações mais sofisticadas, como a identificação de mudanças ambientais ou a classificação de imagens de satélite.

* **O surgimento de novas aplicações:** O geoprocessamento de imagens está sendo usado para uma variedade de novas aplicações, incluindo a realidade aumentada, a inteligência artificial e a computação em nuvem. Essas aplicações estão expandindo o potencial do geoprocessamento para resolver problemas do mundo real.

O geoprocessamento de imagens é uma ferramenta poderosa que tem o potencial de impactar positivamente a sociedade e as empresas. À medida que as novas tecnologias continuam a evoluir, o geoprocessamento continuará a se tornar uma ferramenta ainda mais valiosa. Por isso, Hoje, vamos falar sobre como a linguagem de programação Python com QGIS está facilitando o trabalho de profissionais no campo do geoprocessamento de imagens.

Como vimos, o geoprocessamento de imagens é uma ferramenta poderosa que pode ser usada para diversas aplicações. No entanto, o uso de ferramentas tradicionais de geoprocessamento, como o QGIS, pode ser limitante para aplicações mais complexas.

Aqui estão alguns dos desafios que os profissionais do geoprocessamento de imagens enfrentam ao usar ferramentas tradicionais:

* **Complexidade:**  As ferramentas tradicionais de geoprocessamento podem ser complexas de aprender e usar. Isso pode dificultar a implementação de novas técnicas e metodologias.

* **Limitação de recursos:**  As ferramentas tradicionais de geoprocessamento geralmente são limitadas em termos de recursos, como memória e processamento. Isso pode dificultar a execução de análises complexas.

* **Repetição de tarefas:**  As ferramentas tradicionais de geoprocessamento geralmente exigem que os usuários repitam tarefas manuais, como a criação de scripts e a depuração de código. Isso pode ser demorado e propenso a erros.
Python com QGIS

Python é uma linguagem de programação de propósito geral que é amplamente utilizada em uma variedade de áreas, incluindo ciência de dados, inteligência artificial e aprendizado de máquina. Python é uma linguagem poderosa e flexível que pode ser usada para automatizar tarefas, criar scripts e desenvolver aplicações personalizadas.

QGIS é um software de Sistema de Informação Geográfica (SIG) de código aberto que é amplamente utilizado por profissionais do geoprocessamento. QGIS é uma ferramenta poderosa e versátil que pode ser usada para visualizar, analisar e editar dados espaciais.

A combinação de Python com QGIS oferece uma série de benefícios para profissionais do geoprocessamento de imagens, incluindo:

* **Aumento da produtividade:**  Python pode ser usado para automatizar tarefas repetitivas, o que pode liberar tempo para os profissionais se concentrarem em atividades mais estratégicas.
  
* **Maior flexibilidade:**  Python é uma linguagem flexível que pode ser usada para implementar uma variedade de técnicas e metodologias.

* **Redução de erros:**  Python pode ser usado para criar scripts que são mais fáceis de depurar e manter do que scripts escritos em outras linguagens.





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

## Criar novos atributos (novos campos)
### Tipos de campos: String, Double e Int
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
<hr>

## FILTRO EM CAMADA

![Captura de tela de 2024-01-18 17-13-58](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/f9a31883-c4b4-4e9c-8f6b-1ce16a547f5b)

```python
# Atribui a variável `path` o caminho completo para a pasta `dados` no diretório atual do projeto QGIS.
path = os.getcwd() + '/*** Projetos em Desenvolvimento ***/PYQGIS/dados'

# Inicia um loop `for` para percorrer os arquivos da pasta `dados`.
for root, diretory, files in os.walk(path):

    # Atribui a variável `file` cada arquivo no loop.
    for file in files:

        # Verifica se o arquivo termina com a extensão `.shp`.
        if file.endswith('.shp'):

            # Atribui a variável `path_vector` o caminho completo para o arquivo.
            path_vector = os.path.join(path, file)

            # Cria uma camada vetorial a partir do arquivo `path_vector`.
            layer = QgsVectorLayer(path_vector, file[0:-4], "ogr")

            # Adiciona a camada vetorial ao projeto QGIS.
            QgsProject.instance().addMapLayer(layer)

# Atribui a variável `municipios` a primeira camada vetorial com o nome `municipios` no projeto QGIS.
municipios = QgsProject.instance().mapLayersByName("municipios")[0]

# Imprime o número de features na camada `municipios`.
print(f"O número de features na camada `municipios` é: {municipios.featureCount()}")

# Aplica um filtro à camada `municipios` para selecionar apenas as features cujo atributo `uf` tem o valor `RJ`.
municipios.setSubsetString("uf = 'RJ'")

# Imprime o número de features na camada `municipios` após a aplicação do filtro.
print(f"O número de features na camada `municipios` após a aplicação do filtro é: {municipios.featureCount()}")

# Remove o filtro da camada `municipios`.
municipios.setSubsetString("")

```


## Resumo:

O código acima carrega todas as camadas vetoriais do formato .shp na pasta dados no projeto QGIS. Em seguida, o código imprime o número de features na camada municipios. Por fim, o código aplica um filtro à camada municipios para selecionar apenas as features cujo atributo uf tem o valor RJ. O código imprime o número de features na camada municipios após a aplicação do filtro.

### Sobre o filtro em camada:

O filtro em camada é uma operação que permite selecionar apenas um subconjunto de features de uma camada vetorial. O filtro pode ser aplicado com base em qualquer atributo da camada.

No código acima, o filtro é aplicado com base no atributo uf da camada municipios. O valor do filtro é RJ. Isso significa que o filtro selecionará apenas as features cujas uf têm o valor RJ.

O filtro pode ser aplicado de forma permanente ou temporária. No código acima, o filtro é aplicado de forma temporária. Isso significa que o filtro é aplicado apenas quando o código é executado. Se você quiser aplicar o filtro de forma permanente, você pode usar o método setSubsetString() da camada vetorial.

No exemplo acima, o método setSubsetString() é usado para aplicar o filtro de forma permanente. A linha municipios.setSubsetString("uf = 'RJ'") aplica o filtro à camada municipios. A linha municipios.setSubsetString("") remove o filtro da camada municipios.

<hr>

## Exportando um arquivo vetorial:

![Captura de tela de 2024-01-18 19-12-25](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/4c1fd2e2-96a4-45b9-8052-12fdef0ab303)
![Captura de tela de 2024-01-18 19-13-10](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/22520377-f6cc-438e-b30d-be27cc65a6f9)
![Captura de tela de 2024-01-18 19-14-01](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/5dcd8c09-09f0-413a-9a26-f3fd9bcb3239)

```python
# Cria um objeto de opções de gravação para especificar configurações adicionais durante a exportação da camada vetorial.
options = QgsVectorFileWriter.SaveVectorOptions()

# Monta o caminho completo para o arquivo de saída, que será um GeoPackage com o nome "municipiosrj.gpkg" na pasta "results".
out_path = os.path.join(path, 'results/municipiosrj.gpkg')

# Obtém o contexto de transformação do projeto QGIS, que contém informações sobre o sistema de coordenadas e as transformações necessárias para a exportação.
transform = QgsProject.instance().transformContext()

# Grava a camada vetorial `municipios` no formato GeoPackage (`.gpkg`) no caminho especificado, utilizando o contexto de transformação e as opções de gravação definidas.
QgsVectorFileWriter.writeAsVectorFormatV2(municipios, 
                                          out_path,
                                          transform,
                                          options
                                          )
```

## Resumo
Este código exporta uma camada vetorial para um arquivo GeoPackage.

### Observações

As opções de gravação podem ser usadas para especificar configurações como o tipo de geometria, o esquema de atributos e o sistema de coordenadas do arquivo de saída.
O contexto de transformação contém informações sobre o sistema de coordenadas do projeto QGIS e do arquivo de saída. É importante utilizar o contexto de transformação correto para garantir que os dados sejam exportados corretamente.

O formato GeoPackage é um formato de arquivo de dados espaciais aberto e flexível que pode ser utilizado para armazenar dados vetoriais e raster.

<hr>

## RAMPA DE CORES RASTER

O propósito da rampa raster é associar um valor de cor a cada valor do raster. Isso permite que os valores do raster sejam representados de forma mais visual e intuitiva.

No código fornecido, a rampa raster é usada para representar os valores do raster de elevação. Os valores mais baixos do raster são representados pela cor vermelha, os valores mais altos pela cor azul. Isso permite que o usuário visualize a distribuição da elevação no terreno.

As rampas raster podem ser usadas para representar uma variedade de dados raster, incluindo dados de elevação, dados de temperatura, dados de vegetação e muito mais.

Aqui estão alguns exemplos específicos de como as rampas raster podem ser usadas:

Representar dados de elevação: Uma rampa raster pode ser usada para representar os valores de elevação de um terreno. Isso pode ser útil para visualizar a topografia do terreno, identificar áreas com elevações semelhantes e analisar as mudanças na elevação ao longo do tempo.
Representar dados de temperatura: Uma rampa raster pode ser usada para representar os valores de temperatura de um local. Isso pode ser útil para visualizar as áreas com temperaturas mais altas ou mais baixas, identificar padrões de temperatura ao longo do tempo e analisar as mudanças climáticas.
Representar dados de vegetação: Uma rampa raster pode ser usada para representar os tipos de vegetação de uma área. Isso pode ser útil para identificar áreas com diferentes tipos de vegetação, visualizar as mudanças na vegetação ao longo do tempo e analisar o impacto da atividade humana na vegetação.
As rampas raster são uma ferramenta poderosa que pode ser usada para melhorar a visualização de dados raster.

![Captura de tela de 2024-01-18 23-34-53](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/40414fe0-7d48-4476-9b98-51c4983d6348)
![Captura de tela de 2024-01-19 11-31-53](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/49012375-c4b5-4a6b-8e48-1bd2ed83f4cc)
![Captura de tela de 2024-01-19 11-33-06](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/77e0614e-fd51-452d-a331-ba94959ecd14)

```python
#### RAMPA DE CORES RASTER ####

# Carrega o raster
raster = os.getcwd() + '/*** Projetos em Desenvolvimento ***/PYQGIS/dados/merge.tif'
rlayer = QgsRasterLayer(raster,"dem")

# Cria o objeto de rampa de cores
fcn = QgsColorRampShader()
fcn.setColorRampType(QgsColorRampShader.Interpolated)

# Define os pontos da rampa de cores
lst = [
QgsColorRampShader.ColorRampItem(0, QColor(255, 0, 0)),
QgsColorRampShader.ColorRampItem(300, QColor(255, 153, 0)),
QgsColorRampShader.ColorRampItem(900, QColor(255, 255, 102)),
QgsColorRampShader.ColorRampItem(1100, QColor(153, 255, 0)),
QgsColorRampShader.ColorRampItem(1600, QColor(0, 51, 0))
]

# Define a lista de pontos da rampa de cores para o objeto de rampa de cores
fcn.setColorRampItemList(lst)

# Cria o objeto de sombreador
shader = QgsRasterShader()
shader.setRasterShaderFunction(fcn)

# Cria o objeto de renderização
renderer = QgsSingleBandPseudoColorRenderer(rlayer.dataProvider(),1,shader)

# Define o objeto de renderização para a camada raster
rlayer.setRenderer(renderer)

# Força a camada raster a ser redesenhada
rlayer.tringgerRepaint()

# Adiciona a camada raster ao projeto
QgsProject.instance().addMapLayer(rlayer)

```

## Resumo

Este código aplica uma rampa de cores a uma camada raster. A rampa de cores é definida por uma lista de pontos, cada um dos quais representa um valor do raster e uma cor correspondente.

### O código segue os seguintes passos:

Carrega a camada raster.
Cria o objeto de rampa de cores.
Define os pontos da rampa de cores.
Define a lista de pontos da rampa de cores para o objeto de rampa de cores.
Cria o objeto de sombreador.
Define o objeto de sombreador para a camada raster.
Força a camada raster a ser redesenhada.
Adiciona a camada raster ao projeto.
A rampa de cores definida no código neste caso é a seguinte:

Valor | Cor
------- | --------
0 | Vermelho
300 | Laranja
900 | Amarelo
1100 | Verde
1600 | Azul
Assim, os valores do raster entre 0 e 300 serão representados pela cor vermelha, os valores entre 300 e 900 pela cor laranja, e assim por diante.

<hr>

## FUNÇÕES

![Captura de tela de 2024-01-21 14-40-20](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/ac26386a-5699-40a0-a3af-6534a8035f9c)
```python
## Define a função `list_files()`
def list_files(path, type):
    ## Cria uma lista vazia para armazenar os nomes dos arquivos encontrados
    lst = []

    ## Percorre todos os diretórios e arquivos dentro do caminho especificado
    for root, directory, files in os.walk(path):
        ## Percorre cada arquivo encontrado
        for file in files:
            ## Verifica se a extensão do arquivo corresponde à extensão especificada
            if file.endswith(type):
                ## Adiciona o nome do arquivo à lista
                lst.append(file)

    ## Retorna a lista de nomes de arquivos encontrados
    return lst


def open_vector_layers(path, type):
    ## Obtém a lista de arquivos com a extensão especificada dentro do caminho
    files = list_files(path, type)

    ## Cria um dicionário vazio para armazenar as camadas vetoriais carregadas
    vectors = {}

    ## Percorre cada arquivo encontrado
    for file in files:
        ## Extrai o nome do arquivo sem a extensão
        filename = file.split('.')[0]

        ## Tenta carregar o arquivo como uma camada vetorial no QGIS
        vector = iface.addVectorLayer(os.path.join(path, file), filename, "ogr")

        ## Se a camada foi carregada com sucesso, adiciona-a ao dicionário
        if vector is not None:
            vectors.update({filename: vector})

    ## Retorna o dicionário contendo as camadas carregadas
    return vectors


## Define o caminho para o diretório contendo as camadas
path = os.getcwd() + '/*** Projetos em Desenvolvimento ***/PYQGIS/dados'

## Carrega as camadas vetoriais com extensão 'gpkg' do diretório especificado
camadas = open_vector_layers(path, 'gpkg')

## Imprime o dicionário contendo as camadas carregadas
print(camadas)
```

### Explicação parte 1:

* A função list_files() recebe dois argumentos: o caminho para o diretório a ser pesquisado e o tipo de arquivo a ser procurado.
* A função começa criando uma lista vazia para armazenar os arquivos.
* Em seguida, a função itera sobre os diretórios e arquivos no caminho especificado.
* Para cada arquivo, a função verifica se o arquivo termina com o tipo especificado.
* Se o arquivo terminar com o tipo especificado, a função adiciona o arquivo à lista.
* Finalmente, a função retorna a lista de arquivos.

### Importância da função para otimização de tarefas:

A função list_files() pode ser usada para otimizar tarefas que envolvem a pesquisa de arquivos em um diretório. Por exemplo, a função pode ser usada para:

Localizar todos os arquivos de um determinado tipo em um diretório.
Listar todos os arquivos em um diretório.
Excluir todos os arquivos em um diretório.
A função list_files() pode economizar tempo e esforço ao automatizar essas tarefas.

Função open_vector_layers()

### Explicação parte 2:

* A função open_vector_layers() recebe dois argumentos: o caminho para o diretório a ser pesquisado e o tipo de arquivo a ser procurado.
* A função começa chamando a função list_files() para obter a lista de arquivos no diretório especificado.
* Em seguida, a função cria um dicionário para armazenar as camadas.
* A função itera sobre a lista de arquivos.
* Para cada arquivo, a função obtém o nome do arquivo sem a extensão.
* Em seguida, a função abre o arquivo como uma camada vetorial.
* Finalmente, a função adiciona a camada ao dicionário.
* A função retorna o dicionário de camadas.

### Importância da função para otimização de tarefas:

A função open_vector_layers() pode ser usada para otimizar tarefas que envolvem a abertura de camadas vetoriais em um diretório. Por exemplo, a função pode ser usada para:

* Abrir todas as camadas vetoriais de um determinado tipo em um diretório.
* Listar todas as camadas vetoriais em um diretório.
* Carregar todas as camadas vetoriais em um diretório em uma camada única.
A função open_vector_layers() pode economizar tempo e esforço ao automatizar essas tarefas.

Resumo:

As funções list_files() e open_vector_layers() podem ser usadas para otimizar tarefas que envolvem a pesquisa e abertura de arquivos em um diretório. Essas funções podem economizar tempo e esforço ao automatizar essas tarefas.

## MAPA EM 3D

[Mapa QGIS 3D](https://youtu.be/Oza3phqhMtA)

<hr>

## AUTOMATIZANDO PROCESSOS

![Captura de tela de 2024-01-22 17-09-54](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/8e957324-4c46-4108-af90-d26f02616fe6)

```python
# Importa os módulos necessários
import os
import processing
from qgis.core import *
from qgis.utils import iface
from PyQt5.QtCore import QVariant

# Define a função `list_files()`
def list_files(path, type):
    # Cria uma lista vazia para armazenar os nomes dos arquivos encontrados
    lst = []

    # Percorre todos os diretórios e arquivos dentro do caminho especificado
    for root, directory, files in os.walk(path):
        # Percorre cada arquivo encontrado
        for file in files:
            # Verifica se a extensão do arquivo corresponde à extensão especificada
            if file.endswith(type):
                # Adiciona o nome do arquivo à lista
                lst.append(file)

    # Retorna a lista de nomes de arquivos encontrados
    return lst


# Obtém a lista de arquivos com a extensão especificada dentro do caminho
def open_vector_layers(path, type):
    # Obtém a lista de arquivos com a extensão especificada
    files = list_files(path, type)

    # Cria um dicionário vazio para armazenar as camadas vetoriais carregadas
    vectors = {}

    # Percorre cada arquivo encontrado
    for file in files:
        # Extrai o nome do arquivo sem a extensão
        filename = file.split('.')[0]

        # Tenta carregar o arquivo como uma camada vetorial no QGIS
        vector = iface.addVectorLayer(os.path.join(path, file), filename, "ogr")

        # Se a camada foi carregada com sucesso, adiciona-a ao dicionário
        if vector is not None:
            vectors.update({filename: vector})

    # Retorna o dicionário contendo as camadas carregadas
    return vectors


# Adiciona um novo atributo a uma camada vetorial
def new_attribute(layer, field_name, type):
    # Verifica o tipo de campo
    if type == 1:
        field_type = QVariant.String
    elif type == 2:
        field_type = QVariant.Int
    else:
        field_type = QVariant.Double

    # Inicia o modo de edição da camada
    layer.startEditing()

    # Adiciona o novo campo à camada
    layer.addAttribute(QgsField(field_name, field_type))

    # Confirma as alterações na camada
    layer.commitChanges()

    return


# Cria uma nova pasta
def create_folder(path):
    # Verifica se a pasta existe
    if not os.path.exists(path + 'reproject'):
        # Cria a pasta
        os.makedirs(path + 'reproject')


# Reprojeta uma camada vetorial para uma nova CRS
def reproject(path, epsg):
    # Cria a nova pasta
    create_folder(path)

    # Percorre todos os arquivos shape
    for shape in list_files(path, '.shp'):
        # Obtém o caminho completo do arquivo
        input_path = path + shape

        # Obtém o caminho do arquivo reprojetado
        out_path = path + '/reproject/' + str(epsg) + '_' + shape

        # Reprojeta a camada
        processing.run("native:reprojectlayer", {
            'INPUT': input_path,
            'TARGET_CRS': QgsCoordinateReferenceSystem(f'EPSG:{epsg}'),
            'OUTPUT': out_path
        })

    return

```

### Pasta reproject criada

![Captura de tela de 2024-01-22 17-14-44](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/9a615502-24eb-4783-8400-52e725f4366c)
![Captura de tela de 2024-01-22 17-20-34](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/c8fab9f2-6bb1-4199-9aec-0791451a4b5a)

## CRIANDO FUNÇÃO DE FILTROS (continuando o processo de automação)

![Captura de tela de 2024-01-24 16-02-19](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/cc73cec9-1b20-4d43-a6a4-e68dbb6904d3)

```python
##### ADICIONANDO COR EM CAMADAS  #####

# Importa as bibliotecas necessárias.
import sys
sys.path.insert(0, os.path.join(os.getcwd(), '*** Projetos em Desenvolvimento ***/PYQGIS/tutoriais/'))
from script_funcoes import list_files, open_vector_layers, new_attribute, reproject

# Carrega as camadas de vetores do diretório especificado.
path = '/home/romilson/*** Projetos em Desenvolvimento ***/PYQGIS/dados/'
camadas = open_vector_layers(path+'reproject/','.shp')

#### APLICANDO CAMADAS DE COR VERMELHO RGB ###

# Aplica um filtro à camada '31981_aeroportos' para selecionar apenas os aeroportos do Paraná.
camadas['31981_aeroportos'].setSubsetString("uf = 'PR'")

# Seleciona a camada ativa no QGIS.
layer = iface.activeLayer()

# Obtém o renderizador da camada ativa.
renderer = layer.renderer()

# Obtém o símbolo único do renderizador.
symbol = renderer.symbol()

# Define a cor do símbolo para vermelho.
symbol.setColor(QColor(255, 0, 0))


#### ADICIONANDO UMA FUNÇAO PARA FILTROS ####

# Declara a função 'apply_filter()'.
def apply_filter(layer,field,param):
  # Define o valor global da função 'apply_filter()'.
  global apply_filter
  # Aplica a função 'apply_filter()' à camada especificada.
  return layer.setSubsetString(f"{field} = '{param}'")

# Aplica a função 'apply_filter()' à camada '31981_aeroportos' para selecionar apenas os aeroportos do Rio de Janeiro.
apply_filter(camadas['31981_aeroportos'],'UF', 'RJ')

# Aplica a função 'apply_filter()' à camada '31981_aeroportos' para selecionar apenas os aeroportos de Mato Grosso.
apply_filter(camadas['31981_aeroportos'],'uf', 'MT')

```
<hr>

## ANÁLISE BUFFER

![Captura de tela de 2024-01-25 10-43-19](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/81d257ee-7fc0-46e3-9b7f-97c8fd1af177)

![Captura de tela de 2024-01-25 10-42-21](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/1a865967-ada6-4163-8d0e-e2bd8d438b71)

```python
##### FUNÇOES BUFFER #####

# Importa o módulo sys do Python
import sys

# Insere o caminho do diretório '*** Projetos em Desenvolvimento ***/PYQGIS/tutoriais/' no início do caminho do módulo
sys.path.insert(0, os.path.join(os.getcwd(), '*** Projetos em Desenvolvimento ***/PYQGIS/tutoriais/'))

# Importa as funções list_files, open_vector_layers, new_attribute, reproject, e alerta_aero do módulo script_funcoes
from script_funcoes import list_files, open_vector_layers, new_attribute, reproject, alerta_aero

# Define a variável path como o caminho para o diretório de dados
path = '/home/romilson/*** Projetos em Desenvolvimento ***/PYQGIS/dados/'

# Abre as camadas vetoriais no diretório path+'reproject/' com a extensão .shp
# A função open_vector_layers() retorna um dicionário com as camadas abertas
camadas = open_vector_layers(path+'reproject/','.shp')

# Aplica um filtro à camada 31981_aeroportos para selecionar apenas as linhas com o campo uf igual a PR
camadas['31981_aeroportos'].setSubsetString("uf = 'PR'")

# Define a função apply_filter()
def apply_filter(layer,field,param):
    global apply_filter
    return layer.setSubsetString(f"{field} = '{param}'")

# Define a função alerta_aero()
def alerta_aero(layer, param, path, field, state):
    apply_filter(layer,field,state)
    if param == 'seco':
        buffer = 200
    elif param == 'chuva':
        buffer = 1000
    else:
        buffer = 3000
    processing.run("native:buffer",
                  {'INPUT':layer,
                   'DISTANCE':buffer,
                   'SEGMENTS':5,
                   'END_CAP_STYLE':0,
                   'JOIN_STYLE':0,
                   'MITER_LIMIT':2,
                   'DISSOLVE':True,
                   'OUTPUT':path+'buffer.shp'})
    iface.addVectorLayer(path+'buffer.shp', "analise", "ogr")
    return

# Chama a função alerta_aero() com os seguintes parâmetros:
#   * layer: A camada 31981_aeroportos
#   * param: O valor do campo UF para o filtro
#   * path: O caminho para o diretório de saída
#   * field: O nome do campo para o filtro
#   * state: O valor do campo UF para o filtro
alerta_aero(camadas['31981_aeroportos'],
            'chuva',
            path+'reproject/',
            'UF',
            'PR')
```

### Arquivos buffer criado
![Captura de tela de 2024-01-24 19-45-41](https://github.com/Romilsonlonan/analise-de-mapas/assets/90980220/29406550-6161-4273-9202-de8d4124d3f4)
