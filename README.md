# Coletor do Ministério Público do Maranhão

Esse coletor é baseado na tecnologia [Chrome DevTools Protocol(CDP)](https://chromedevtools.github.io/devtools-protocol/) e escrito em Go. Essa utiliza o módulo [chromedp](https://github.com/chromedp/chromedp). Diversos exemplos de utilização dessa tecnologia podem ser encontrados [aqui](https://github.com/chromedp/examples).

## Como usar

### Executando com Docker

 - Inicialmente é preciso instalar o [Docker](https://docs.docker.com/install/). 

 - Construção da imagem:

    ```sh
    $ docker build --pull --rm -t coletormpma:latest . 
    ```
    Criamos então o repositório onde ficarão armazenadas as planilhas (caso já não exista):
    ```sh
    $ mkdir /tmp/coletormpma
    ```
 - Execução:
 
    ```sh
    $ docker run -e YEAR={ano} -e MONTH={mês} -e OUTPUT_FOLDER=/output --name coletormpma --mount type=bind,src=/tmp/coletormpma,dst=/output coletormpma
    ```
    Os arquivos baixados pelo coletor poderão ser acessados através do diretório /tmp/coletormpma.

### Executando sem o Docker

 - Será necessário instalar a [Linguagem Go](https://go.dev/dl/).

 - Execução:

    ```sh
    YEAR={ano} MONTH={mês} OUTPUT_FOLDER={nome-repositório} go run .
    ```
    Neste caso, os arquivos baixados pelo coletor poderão ser acessados através do diretório informado à váriável de ambiente OUTPUT_FOLDER.