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

