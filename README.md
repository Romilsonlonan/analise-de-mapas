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

## Define o título do projeto para `CURSO PYQGIS`
project.setTitle('CURSO PYQGIS')

## Imprime o título do projeto
print(project.title())

