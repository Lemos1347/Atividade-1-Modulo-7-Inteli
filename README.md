# Atividade-1-Modulo-7-Inteli

## Como rodar

### Rodando com a imagem hospedada no dockerhub

A imagem construída foi subida para o dockerhub, ela pode ser encontrada em: [docker.io/lemos12/curriculo-docker](https://hub.docker.com/r/lemos12/curriculo-docker)

Para realizar o upload, foi utilizado do seguinte comando no termial:

```shell
docker push <IMAGE NAME>
```

Caso queira rodar com a imagem do dockerhub, rode os seguintes comandos no seu terminal:

```shell
docker pull lemos12/curriculo-docker
```

```shell
docker run -dp 3000:3000 lemos12/curriculo-docker
```

Pronto! Agora você pode acessar o currículo em:
[**http://localhost:3000/**](http://localhost:3000/)

### Realizando o build da imagem no seu computador

Para rodar a aplicação, clone primeiro esse repositório com esse comando em seu terminal:

```shell
git clone https://github.com/Lemos1347/Atividade-1-Modulo-7-Inteli.git
```

Depois navegue até a pasta dos aquivos e na 'root' desse projeto digite os seguintes comandos no seu terminal:

```shell
docker build -t curriculo-henrique .
```

_!Observação!: os primeiros números antes dos dois pontos representam a porta que o seu computador usará para acessar qualquer conteúdo do contairner, então qualquer problema que tiver se portas já em uso, alterar apenas o primeiro valor_

```shell
docker run -dp 3000:3000 curriculo-henrique
```

Pronto! Agora você pode acessar o currículo em:
[**http://localhost:3000/**](http://localhost:3000/)

Para parar a aplicação, primeiro pegue o ID do seu container com esse comando em seu terminal:

```shell
docker ps
```

Após localizar a imagem 'curriculo-henrique', rode o seguinte comando em seu terminal com o seu respectivo ID:

```shell
docker stop <CONTAINER ID>
```

## Hospedagem do HTML

Esse repositório tem como objetivo criar um conteiner para um servidor hospedar um arquivo `.html`.
Para isso foi criar um servidor em `fastapi` que pode ser visualizado no arquivo [app.py](/app.py). Nele há apenas uma rota responsável por servir um arquivo html.
Também, foi criado um 'currículo' template para apenas demonstrar o funcionamento apropriado do container, ele pode ser encontrado no arquiv [curriculo.html](/curriculo.html).

## Dockerfile

O Dockerfile foi construído, primeiro puxando a imagem mais atual do python 3, logo em seguida defino minha pasta de trabalho no meu container como `/app` copio o `requirements.txt` da minha aplicação para o container e baixo todas as dependências necessárias para o funcionamento do meu script python. Por fim, copio para o container todos os arquvivos da minha aplicação, exponho a porta 3000 e defino como comando de início do script como `python3 app.py`.
