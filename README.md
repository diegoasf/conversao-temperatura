# Projeto Conversão de Temperatura

## Sobre o Projeto

O "Conversão de Temperatura" é uma aplicação simples desenvolvida em Node.js. Este projeto serve como um exemplo prático de como configurar um ambiente de desenvolvimento e executar uma aplicação Node.js, com foco em automação via script Shell para ambientes WSL (Windows Subsystem for Linux).

A aplicação permite a conversão entre diferentes escalas de temperatura e é exposta através de uma interface web.

## Funcionalidades

* Conversão entre Celsius, Fahrenheit e Kelvin (ajuste conforme as funcionalidades reais).
* Interface web simples para interação.

## Observações do Projeto

* A aplicação, quando em execução, é exposta na porta **8080**.
    * Você poderá acessá-la em seu navegador através de `http://localhost:8080`.
* Os logs da aplicação (saída do `console.log`, erros, etc.) serão direcionados para o arquivo `app.log` dentro do diretório do projeto.

## Pré-requisitos (para rodar com o script de automação no WSL)

Antes de executar o script de automação, certifique-se de que você tem os seguintes pré-requisitos instalados e configurados no seu ambiente WSL:

1.  **WSL (Windows Subsystem for Linux)**: Obviamente, você precisa ter o WSL instalado e uma distribuição Linux funcional (como Ubuntu).
2.  **Git**: Necessário para clonar este repositório. O script tentará instalar o Git se não o encontrar, mas é bom já tê-lo.
    * Para verificar: `git --version`
    * Para instalar (em distros baseadas em Debian/Ubuntu, conforme o script):
        ```bash
        sudo apt-get update -qq && sudo apt-get install -y git
        ```
3.  **Permissões `sudo`**: O script de automação usará `sudo` para instalar pacotes (como Git e Node.js, se necessário). Certifique-se de que seu usuário no WSL pode executar comandos com `sudo`.

## Como Executar (Usando o Script de Automação no WSL)

Este projeto inclui um script chamado `iniciar_app_direto_wsl.sh` que automatiza todo o processo de configuração do ambiente e execução da aplicação diretamente no seu WSL.

1.  **Clone este repositório:**
    Abra seu terminal WSL, navegue até o diretório onde deseja clonar o projeto e execute:
    ```bash
    git clone [https://github.com/diegoasf/conversao-temperatura.git](https://github.com/diegoasf/conversao-temperatura.git)
    ```

2.  **Navegue até o diretório do projeto:**
    ```bash
    cd conversao-temperatura
    ```

3.  **Dê permissão de execução ao script:**
    Este passo só é necessário uma vez.
    ```bash
    chmod +x iniciar_app_direto_wsl.sh
    ```

4.  **Execute o script:**
    ```bash
    ./iniciar_app_direto_wsl.sh
    ```
    O script irá:
    * Verificar e instalar o Git (se necessário).
    * Verificar e instalar o Node.js na versão especificada no script (atualmente configurado para Node.js 20.x) usando o NodeSource.
    * Instalar as dependências do projeto (`npm install`).
    * **Iniciar a aplicação (`node server.js`) em segundo plano.** O terminal ficará livre após a execução do script.
    * Informar o PID (Process ID) da aplicação iniciada.

5.  **Acesse a aplicação:**
    Após o script iniciar a aplicação com sucesso, abra seu navegador e acesse:
    `http://localhost:8080`

## Visualizando os Logs da Aplicação

Como a aplicação agora roda em segundo plano, sua saída (logs, erros, etc.) não aparecerá diretamente no terminal após a execução do script. Ela será salva no arquivo `app.log` dentro do diretório do projeto.

Para visualizar os logs em tempo real:
```bash
tail -f app.log
