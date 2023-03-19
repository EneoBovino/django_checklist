# SECRET_KEY

A secret key é um valor aleatório usado para criptografar e proteger informações confidenciais, como senhas de usuários, tokens de autenticação e sessões de usuário em um projeto Django.

No Django, a secret key é definida no arquivo "settings.py" e é usada para:

- Autenticação e segurança: a secret key é usada para garantir que a comunicação entre o usuário e o servidor seja criptografada e protegida contra ataques maliciosos.

- Cookies e sessões: a secret key é usada para gerar um hash seguro para as sessões de usuário e cookies, garantindo que apenas o servidor possa ler e alterar as informações do usuário.

- Tokens de autenticação: a secret key é usada para gerar e verificar tokens de autenticação, que são usados para autenticar usuários em aplicativos de API REST.

Em resumo, a secret key é uma parte fundamental da segurança e autenticação em um projeto Django e deve ser mantida em segredo, nunca sendo compartilhada com outras pessoas ou publicada em código-fonte público.

## Protegendo a SECRET_KEY de exposição

Proteger a secret key é importante porque ela é usada para criptografar informações confidenciais e proteger a segurança do seu projeto. Se a sua secret key for exposta, ela pode ser facilmente usada por hackers mal-intencionados para comprometer a segurança do seu projeto e acessar informações confidenciais, como senhas de usuários, tokens de autenticação e sessões de usuário.

Ao expor a secret key no GitHub, você está tornando essa informação disponível publicamente para qualquer pessoa que acesse o seu repositório, o que inclui hackers e outros indivíduos mal-intencionados que podem usar essa informação para atacar o seu projeto.

Portanto, é altamente recomendável que você mantenha a sua secret key protegida e nunca a compartilhe publicamente. Para isso, você pode armazenar a secret key em um arquivo separado e não versioná-lo, ou configurar o seu projeto para ler a secret key de uma variável de ambiente que não é exposta no código-fonte do seu projeto. Isso ajuda a garantir que a sua secret key permaneça segura e protegida contra possíveis ataques.

Para protege-la usando um arquivo separado, podemos utilizar a biblioteca ```python-dotenv```.

O primeiro passo é criar um arquivo e nomea-lo como ```.env```, com um ponto no começo do nome mesmo, este arquivo deve ficar na raiz do projeto junto com o arquivo ```requirements.txt```.

Abrimos o arquivo ```settings.py``` e procuramos por ```SECRET_KEY```, aproximadamente na linha 23 do arquivo. Vamos copiar o valor desta variável, por exemplo ```django-insecure-0x09knp3=5^a+8io#b9c9@qfakeu#yrzr7eidy(w@q+f4kk5v&```, sem as aspas do começo e fim da string, e colar este valor no arquivo ```.env```, da seguinte forma:

```SECRET_KEY = django-insecure-0x09knp3=5^a+8io#b9c9@qfakeu#yrzr7eidy(w@q+f4kk5v&```

Salvamos e fechamos o arquivo ```.env```.

No arquivo ```settings.py``` iremos altera-lo para que, sempre que necessário, ele busque a SECRET_KEY no arquivo ```.env```.

A primeira alteração é a inclusão dos 'import' para duas bibliotecas/pacotes que utilizaremos.

Adicione logo abaixo de ```from pathlib import Path``` as seguintes linhas de código.

```
import os
from dotenv import load_dotenv

load_dotenv()
```

Isso irá importar os modulos necessários e também irá carregar o nosso arquivo ```.env``` que guarda a SECRET_KEY.

Agora é necessário corrigir a variável SECRET_KEY para que ela utilize a partir do arquivo ```.env```. Para isso faça a seguinte alteração:

```SECRET_KEY = str(os.getenv("SECRET_KEY"))```

Com isso sua SECRET_KEY não estará disponível diretamente no arquivo ```settings.py```.

# Configuração .gitignore

Antes de inicializarmos um repositório git para o projeto e fazer o upload dos arquivos para o repositório no GitHub, é importante configurar corretamente o arquivo ```.gitignore```.

Primeiro iremos cria-lo, na raiz do nosso projeto. Para isso crie um novo arquivo e nomeie como ```.gitignore```

![image](https://user-images.githubusercontent.com/33090552/226211705-a047b55c-c259-4f55-a552-4d5dd20a81da.png)

O arquivo ".gitignore" é uma ferramenta importante no controle de versão do Git. Ele permite que você especifique quais arquivos e diretórios não devem ser rastreados pelo Git, o que significa que o Git irá ignorá-los ao fazer o commit ou ao sincronizar o repositório com outros colaboradores.

A importância do arquivo ".gitignore" reside em várias razões:

- Evitar a inclusão de arquivos desnecessários: Se você estiver trabalhando em um projeto grande, pode haver muitos arquivos que não precisam ser controlados pelo Git, como arquivos de log, arquivos temporários, arquivos de cache, arquivos de configuração local, etc. Se você não especificar esses arquivos no ".gitignore", o Git irá rastreá-los e isso pode poluir o histórico de commits do repositório.

- Proteger informações sensíveis: Algumas informações, como senhas, chaves de acesso e tokens de autenticação, não devem ser compartilhadas publicamente. O ".gitignore" pode ser usado para excluir arquivos que contenham essas informações, evitando que sejam incluídos em um commit e acidentalmente compartilhados com outros colaboradores.

- Agilizar o processo de commit: Quando o Git tem menos arquivos para rastrear, o processo de commit é mais rápido e eficiente. Isso é especialmente importante em projetos maiores, onde o número de arquivos pode ser muito grande.

- Facilitar a colaboração: Se todos os colaboradores do projeto estiverem usando o mesmo arquivo ".gitignore", eles podem garantir que estão todos trabalhando com o mesmo conjunto de arquivos. Isso evita problemas de conflito e ajuda a manter a consistência do repositório.

Em resumo, o arquivo ".gitignore" é uma ferramenta importante para garantir a integridade do repositório e tornar o processo de controle de versão mais eficiente e seguro. É importante dedicar algum tempo para configurá-lo corretamente para evitar problemas no futuro.

## Gerando .gitignore automaticamente

É possível criar um arquivo ```.gitignore``` corretamente de maneira automatizada a partir do site [gitignore.io](https://www.toptal.com/developers/gitignore/)

Após acessar a página digite "django" no campo de busca e clique em criar.

![image](https://user-images.githubusercontent.com/33090552/226211501-19d42edb-4d81-4b65-b4fc-5ebb1008b1fd.png)

Algo assim aparecerá:

```
# Created by https://www.toptal.com/developers/gitignore/api/django
# Edit at https://www.toptal.com/developers/gitignore?templates=django

### Django ###
*.log
*.pot
*.pyc
__pycache__/
local_settings.py
db.sqlite3
db.sqlite3-journal
media

# If your build process includes running collectstatic, then you probably don't need or want to include staticfiles/
# in your Git repository. Update and uncomment the following line accordingly.
# <django-project-name>/staticfiles/

### Django.Python Stack ###
# Byte-compiled / optimized / DLL files
*.py[cod]
*$py.class

# C extensions
*.so

# Distribution / packaging
.Python
build/
develop-eggs/
dist/
downloads/
eggs/
...
```

Agora é só copiar todo o conteúdo gerado e colar no arquivo .gitignore do projeto. Não esqueça de salvar o arquivo.

**Certifique-se de copiar todo o conteúdo, são aproximadamente 174 linhas!**

# Publicando o projeto no GitHub

## Primeiro Método - Publicar diretamente a partir do VS Code

Se você estiver usando seu computador e já configurou corretamente o GitHub anteriormente, basta acessar a guia de controle de código-fonte do VS Code, clicar em Publicar no GitHub e seguir os passos que serão solicitados pelo próprio VS Code.

![image](https://user-images.githubusercontent.com/33090552/226211895-1f36978b-5a60-486c-abbc-53889f249777.png)

Dê um nome e escolha se o projeto ficará público ou privado no GitHub.

![image](https://user-images.githubusercontent.com/33090552/226211934-b52883f7-d09f-4f0b-9e0a-bbe957d0db78.png)

Após isso, o repositório será criado e será feito upload (push) de todo conteúdo restreável do seu projeto.

## Segundo Método - Publicar em um repositório criado a partir da página do GitHub

