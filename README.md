# Extrator_POIS
Extrator de pontos de interesse em uma região do globo terrestre baseado no serviço Open Street Maps 


# Tutorial para o mapeamento de áreas com Open Street Maps



O seguinte tutorial apresenta os passos para a instalação de ferramentas necessárias para o mapeamento de uma determinada área geográfica utilizando o OpenStreetMap (as instruções seguintes são para o S.O Linux).

## 1. Instalação - Ferramentas

Neste tópico, será apresentado o passo a passo como instalar o Osmosis API e o QGIS Desktop no terminal Linux para realizar as tarefas voltadas, essencialmente, ao recorte, bem como extração dos dados.

Abra o terminal Linux. Você pode fazer isso clicando no ícone do terminal ou pressionando as teclas "Ctrl + Alt + T" no teclado. Para instalar o Osmosis API, digite o seguinte comando no terminal e pressione "Enter":

` sudo apt-get install osmosis `

Osmosis é um aplicativo Java de linha de comando para processamento de dados OSM. A ferramenta consiste em componentes conectáveis que podem ser encadeados para realizar uma operação maior. Este comando instalará o Osmosis API em seu sistema.

Para instalar o QGIS Desktop, digite o seguinte comando no terminal e pressione "Enter": este comando instalará o QGIS Desktop e o plugin Grass em seu sistema.

`sudo apt-get install qgis`

Agora você pode usar o Osmosis API e o QGIS Desktop em seu terminal Linux para processamento de dados OSM e visualização de mapas, respectivamente.

## 2. Fazer o recorte da Área (polígono)

Nesse tópico será o passo a passo de como obter os arquivos de saída “.osm”, por intermédio de comandos disponíveis nesta seção.

Escreva este comando no terminal Linux para gerar os arquivos “.osm”, mais abaixo está a descrição de cada arquivo presente neste comando para gerar os arquivos “.osm”:

`osmosis --read-xml file="sudeste.osm" --bounding-polygon file="103.txt" --write-xml file="103.osm"`

- file = "sudeste.osm": Nome do arquivo de entrada. Contém todos os dados do Open Street Maps do Sudeste (Verificar em Anexos como obter arquivo)
- file="103.txt": Nome do arquivo de entrada. Arquivo contendo as coordenadas que já estão mapeadas
- file="103.osm": Nome do arquivo de saída. Arquivo .osm que será gerado da região que foi mapeada


Para agilizar os processos e realizar a geração dos comandos osm de forma rápida, utilize o comando Screen:

O "screen" é um comando do sistema operacional Linux que permite criar e gerenciar sessões de terminal virtuais em um único terminal físico ou em uma sessão remota, disponível na seção de anexos o passo a passo de como usar. 

Dentro da sessão screen execute no repositorio Extrator_POIS/Codes/ o comando  

```bash
script_recorte.sh
```

Com isso será feito o recorte de todas as áreas disponiveis no diretório /mapas.

## 3. Contagem/Extração dos Pontos de Interesse 

Buscar no repositório Extrator_POIS/Codes/ e executar o notebook contagem_POIs.ipynb.

É recomendado ter o Anaconda instalado.

## 4. Datasets

O resultado da execução do código acima é o CSV com os Pontos de Interesses disponíveis em cada Departamento de Polícia mapeado no Open Street Maps.

## 5. Anexos 

### 5.1 Como obter arquivo de saída sudeste.osm?

Primeiramente, baixe o **sudeste-latest.osm.pbf** [aqui.](http://download.geofabrik.de/south-america/brazil/sudeste.html). 

Segundamente, instale as  ferramentas auxiliares no Linux que dão suporte a arquivos .osm com o seguinte comando:

`sudo apt install osmctools`


Apoś ter baixado o arquivo “.pbf”, ter invocado os comandos na ferramenta Linux, utilize o comando abaixo para converter o arquivo baixado acima em .osm (arquivo de saída):

`osmconvert nome_arquivo.pbf > nome_arquivo_saida.osm`


### 4.2 - Tudo sobre Screen 

É um comando do sistema operacional Linux que permite criar e gerenciar sessões de terminal virtuais em um único terminal físico ou em uma sessão remota. Com o "screen", é possível executar várias tarefas em diferentes sessões de terminal, desanexar ou anexar sessões para reconexão posterior e compartilhar sessões de terminal com outros usuários.

Para processar este comando no terminal Linux, siga os seguintes passos:

1. Abra um terminal no Linux: Você pode abrir um terminal em distribuições baseadas em GNOME, como Ubuntu ou Debian, pressionando "Ctrl + Alt + T". Em distribuições baseadas em KDE, como o Kubuntu, você pode usar o atalho "Ctrl + Shift + T". Você também pode pesquisar pelo terminal no menu de aplicativos.

2. Crie uma nova sessão do "screen": Digite o comando `screen` no terminal e pressione "Enter". Isso criará uma nova sessão do "screen" dentro do terminal atual. Você verá uma mensagem de boas-vindas do "screen" e uma nova linha de comando.

3. Execute os comandos ou programas desejados: Dentro da sessão do "screen", você pode executar comandos ou programas como faria em um terminal normal. Por exemplo, você pode digitar `ls` para listar o conteúdo do diretório atual.

4. Desanexe a sessão: Para desanexar a sessão do "screen" e retornar ao terminal normal, pressione "Ctrl + a" e, em seguida, pressione "d". Isso não encerrará a sessão do "screen", mas permitirá que você saia da sessão e continue usando o terminal normalmente.

5. Reconecte-se à sessão do "screen": Para se reconectar à sessão do "screen" posteriormente, digite o comando `screen -r` seguido do identificador da sessão. Se você tiver apenas uma sessão ativa, o "screen" reconectará automaticamente à sessão. Se tiver várias sessões ativas, use o comando `screen -ls` para listar todas as sessões e seus identificadores.

6. Compartilhe uma sessão do `screen`: Para compartilhar uma sessão do `screen` com outro usuário, você precisará conceder permissão de acesso a ele. Você pode fazer isso definindo as permissões adequadas com os comandos `chmod` ou `chown`. Depois, informe ao usuário o identificador da sessão do `screen` e peça que ele se conecte usando o comando `screen -x`.
