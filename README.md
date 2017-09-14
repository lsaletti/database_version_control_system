Docker-Flyway (Geofusion)
-------------------------

Este repositório contém o arquivo docker-compose.yml, que inicia o funcionamento do docker-flyway.


##### ***Informações***

###### Para utilização do docker-flyway será necessário alguns pré-requisitos:

 - Imagem em Debian - official ou semelhante  
   docker pull debian (https://hub.docker.com/_/debian/)
 - Install Docker
 - Install Docker Compose

##### ***Instalação***


```sh
$ git clone https://git.geofusion.com.br/lucas.saletti/flyway.git
```


##### ***Construir imagem***

Se precisar de pacotes extras, altere o Dockerfile antes de rodar o comando a seguir:

```sh
$ cd flyway/files/
$ docker build -t flyway .
```
ou


```sh
$ make build
```


##### ***Usar***

Será necessário parametrizar o arquivo docker-compose.yml, com as informações do seu projeto.

Alguns exemplos estão disponibilizados na pasta abaixo:


```sh
$ cd flyway/files/files_compose/
$ ls -ltr
```

***Exemplo:***

> ##### ***GIT_URL=*** git.geofusion.com.br/lucas.saletti/flyway.git         
> ##### ***GIT_DIRECTORY=*** /flyway   
> ##### ***GIT_DIRECTORY_FILE =*** filesystem:/flyway/sql   
> ##### ***FLYWAY_USER =*** flyway  
> ##### ***FLYWAY_PASSWORD =*** Mudar123   
> ##### ***FLYWAY_DATABASE =*** jdbc:oracle:thin:@doforte:1521:gfn   
> ##### ***FLYWAY_MIGRATE =*** M  
> ##### ***FLYWAY_TARGET =*** 7.12.1.03

------------------------------



##### ***Descrição dos parâmetros***


**GIT_URL**

HTTPS do projeto que deve ser clonado para o versionado.

Obs: favor desconsiderar o Início "https://"

**GIT_DIRECTORY**

Nome do projeto ou caminho do diretorio a ser criado.

**GIT_DIRECTORY_FILE**

Caminho da pasta que possuem os scripts .SQL

**FLYWAY_USER**

Usuário do banco de dados

**FLYWAY_PASSWORD**

Senha do banco de dados

**FLYWAY_DATABASE**

Conexão do banco de dados que o flyway irá conectar.

**FLYWAY_MIGRATE**

* ***[ M ] MIGRATE -*** Irá executar os scripts no banco de dados parametrizado
* ***[ R ] REPAIR -*** Irá reparar o script executado com falha, para possível execução do "MIGRATE"

**FLYWAY_TARGET**

Deve apontar até que versão os scripts versionados serão executados.

------------------------------

##### ***Executando o FLYWAY***

- Depois de configurar o arquivo docker-compose.yml, executar o procedimento abaixo:

```sh
$ cd flyway/
$ docker-compose up
```
ou

```sh
$ make run
```
