# Instruções para começar um projeto

## Python e pacotes necessários inicias

Primeiramente, verifique se você possui o python instalado.

Após isso verifique se já possui o pacote ```virtualenv``` instalado no seu python, se não, instale utilizando o seguinte comando no prompt ou terminal ```pip install virtualenv```

## Preparando Ambiente do Projeto

Crie uma pasta onde ficará armazenado o projeto.

Abra esta pasta no VSCode.

Com a pasta aberta no VSCode, primeiro é preciso criar o ambiente virtual python para o projeto. Para isso, abra o terminal do VSCode e execute o comando ```virtualenv venv``` para criar o ambiente com nome 'venv'.

Após isso precisamos ativar o ambiente no terminal. Verifique se você está na pasta do projeto no caminho ativo do terminal e execute ```venv/Scripts/Activate```. Com isso aparecerá no caminho do terminal o nome do ambiente entre parênteses, algo como ```(venv) C:\Users\Nome\caminho_projeto\Pasta_do_Projeto>```

Com o ambiente ativo agora é necessário instalar os pacotes python para o projeto.

- Execute ```pip install django``` para instalar o Django.
- Execute ```pip install python-dotenv``` para instalar o python-dotenv.

Após a instalação destes 2 pacotes é necessário criar um arquivo para registrar quais pacotes o nosso projeto está utilizando. Para fazer isso execute no terminal ```pip freeze > requirements.txt```, este arquivo será criado e guardará o nome dos pacotes e suas respectivas versões.

## Criando a Estrutura para o projeto com o Django

Para criar o projeto Django execute no terminal ativo ```django-admin startproject setup .```

Este comando irá criar a estrura básica do seu projeto, chamamos o projeto de 'setup' no comando para facilitar futuramente, pois nesta pasta criada são onde ficam os arquivos responsáveis pelo setup e configuração de várias coisas no nosso projeto, ao final do comando colocamos um ponto '.' para que esta seja criada no exato lugar em estamos no terminal, sem criar nenhuma sub-estrutura de arquivos, isso também facilita a visualização e navegação no projeto.

## Primeiras configurações

Com a estrutura criada, antes de verificar se o projeto está funcionando corretamente, podemos alterar algumas configurações iniciais básicas, como por exemplo o idioma e localização do nosso site web no projeto.

Para isso, no arquivo ```settings.py```, localizado em ```setup```, aproximadamente na linha 106, alteramos ```LANGUAGE_CODE``` para ```'pt-br'``` e ```TIME_ZONE``` para ```'America/Sao_Paulo'```, salvamos o arquivo após estas alterações.

## Run Server

Agora podemos fazer a primeira verificação se está tudo certo executando o servidor django, para fazer isso, no terminal ativo do ambiente, executamos o comando ```python manage.py runserver```.

Se tudo estiver OK, você verá no terminal uma informação, geralmente em vermelho, de que existem 18 migrations não aplicadas e logo a seguir as informações sobre a data e hora atual, a versão do Django em execução e a URL para acessar a página no browser.

```
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).

You have 18 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.
March 15, 2023 - 17:09:26
Django version 3.2.18, using settings 'setup.settings'
Starting development server at http://127.0.0.1:8000/ 
Quit the server with CTRL-BREAK.
```

Se você visualizar a página abaixo ao acessar a URL no browser, estará tudo certo até aqui.

![image](https://user-images.githubusercontent.com/33090552/225431593-5bf91f8a-a6c2-4eed-bcb3-1236d8398f51.png)

