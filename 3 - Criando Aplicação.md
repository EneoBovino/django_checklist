# Django App (Aplicações)

No projeto Django, um "App" é um componente reutilizável que encapsula uma funcionalidade específica da aplicação. Em outras palavras, um App é uma parte modular e independente da aplicação que pode ser adicionada ou removida sem afetar as outras partes do projeto.

Os Apps são criados como uma pasta dentro do projeto Django, contendo um arquivo "models.py" que define os modelos de dados relacionados à funcionalidade do App, bem como outros arquivos que possam ser necessários, como arquivos de visualização, modelos, arquivos estáticos, arquivos de migração etc.

Os Apps podem ser facilmente integrados a outras aplicações, permitindo que desenvolvedores reutilizem o código em diferentes projetos Django, economizando tempo e esforço. Além disso, o Django possui uma arquitetura baseada em Apps, o que significa que muitas funcionalidades da plataforma são implementadas como Apps, como o Admin, Auth, Messages etc.

Resumindo, um App no projeto Django é uma unidade modular que encapsula uma funcionalidade específica da aplicação e pode ser reutilizada em diferentes projetos Django.

Existem vários Apps que podem ser criados usando o Django para uma loja online. Aqui estão alguns exemplos:

App de Produto: Este App pode conter modelos de dados para armazenar informações sobre produtos, como nome, descrição, preço, categoria etc. Ele também pode conter visualizações para exibir produtos na página da web e permitir que os usuários filtrem e classifiquem os produtos.

App de Carrinho de Compras: Este App pode ser usado para gerenciar o carrinho de compras dos usuários. Ele pode armazenar informações sobre os produtos selecionados pelos usuários, quantidades, preços etc. Também pode fornecer funcionalidades para adicionar, remover ou atualizar itens no carrinho de compras.

App de Pagamento: Este App pode ser usado para integrar diferentes métodos de pagamento em uma loja online, como cartões de crédito, PayPal, transferência bancária, etc. Ele pode incluir visualizações para permitir que os usuários escolham o método de pagamento desejado e processem as transações.

App de Pedidos: Este App pode ser usado para gerenciar pedidos feitos pelos usuários. Ele pode armazenar informações sobre os pedidos, como produtos selecionados, endereços de entrega, informações de pagamento, status de entrega, etc.

App de Conta do Usuário: Este App pode fornecer funcionalidades para criar e gerenciar contas de usuário na loja online. Ele pode incluir modelos de dados para armazenar informações do usuário, como nome, endereço, histórico de pedidos, etc. Também pode fornecer funcionalidades para autenticação e autorização de usuários, como login, logout, registro etc.

Esses são apenas alguns exemplos de Apps que podem ser criados usando o Django para uma loja online. Com o Django, é possível criar vários Apps reutilizáveis que podem ser integrados para criar uma aplicação complexa e escalável.

## Criando um App no Django

Para criar um App no Django, siga os seguintes passos:

- Abra o terminal ou prompt de comando e navegue até o diretório raiz do projeto Django. Certifique-se de estar com o ambiente virtual ativo.

- Digite o seguinte comando para criar um novo App:

```python manage.py startapp nome_do_app```

Substitua "nome_do_app" pelo nome que deseja dar ao seu novo App. Este comando criará uma nova pasta com o nome do App dentro do diretório do projeto Django.

- Abra o arquivo "settings.py" dentro do diretório "setup" do projeto Django e adicione o nome do App recém-criado na lista "INSTALLED_APPS". Certifique-se de colocar o nome do App na ordem correta, abaixo dos Apps do Django e acima dos seus próprios Apps. Por exemplo:

```
INSTALLED_APPS = [
  'django.contrib.admin',
  'django.contrib.auth',
  'django.contrib.contenttypes',
  'django.contrib.sessions',
  'django.contrib.messages',
  'django.contrib.staticfiles',
  'nome_do_app',
]
```

A pasta que representa a sua App no projeto aparecerá deste modo, neste exemplo foi criada a App para "produtos":

![image](https://user-images.githubusercontent.com/33090552/226222443-08e2eda8-146c-41ab-8be6-269027e32481.png)
