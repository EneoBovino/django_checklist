# Models

Em Django, os models são classes Python que definem a estrutura e comportamento dos dados do aplicativo. Eles representam as tabelas do banco de dados que armazenam os dados do aplicativo.

Os models do Django herdam da classe "django.db.models.Model", que fornece funcionalidades para criar, ler, atualizar e excluir objetos do banco de dados. Cada atributo do modelo representa um campo da tabela do banco de dados. Existem vários tipos de campos que podem ser usados em um modelo, como "CharField" para campos de texto curtos, "TextField" para campos de texto longos, "IntegerField" para campos numéricos inteiros, "FloatField" para campos numéricos com ponto flutuante, entre outros.

Os models também permitem definir relações entre as tabelas do banco de dados, como relacionamentos de um-para-um, um-para-muitos e muitos-para-muitos. Isso é feito usando as classes "ForeignKey", "OneToOneField" e "ManyToManyField", respectivamente.

Os models são definidos em arquivos Python no arquivo "models.py" de cada aplicativo Django e podem ser criados e modificados usando migrações. Quando uma migração é executada, o Django cria ou altera as tabelas do banco de dados para refletir as alterações nos models.

Em resumo, os models no Django são a base para definir a estrutura de dados de um aplicativo e para armazenar esses dados em um banco de dados. Eles fornecem uma camada de abstração que permite manipular os dados do aplicativo de maneira eficiente e organizada.

## Criando uma tabela para dados do Produto

Abra o arquivo ```models.py``` na pasta ```produtos``` que representa nossa App.

Agora vamos adicionar as classes em python que irão contruir e representar nossas tabelas no banco de dados.

```python --wrap
from django.db import models

# Cada classe aqui representa uma tabela, suas colunas e definição dos dados no banco de dados
# O nome da classe será usado para definir o nome da tabela no banco
class Categoria(models.Model):
    # Cada atributo da classe é a representação de uma coluna no banco de dados
    # Neste caso o atributo "name" desta tabela é do tipo CharField que é usado para armazenar um texto com tamanho definido através do parâmetro "max_lenght".
    # O parâmetro "verbose_name" é utilizado para definir o nome de exibição do campo no sistema.
    name = models.CharField(max_length=50, verbose_name="Nome")
    # O tipo TextField é usado para textos mais longos onde o limite é indefinido.
    description = models.TextField(verbose_name="Descrição")
    
    # Esta definição faz com que seja exibido o nome da categoria, por exemplo na página de admin do Django
    def __str__(self):
        return self.name

class Produto(models.Model):
    name = models.CharField(max_length=50, verbose_name="Nome")
    description = models.TextField(verbose_name="Descrição")
    # O tipo DecimalField e FloatField são usados para armazenar números reais (com casa decimal)
    price = models.DecimalField(max_digits=8, decimal_places=2, verbose_name="Preço")
    # Neste campo utilizamos o tipo ForeignKey para criar a relação entre  as tabelas Produto com Categoria
    category = models.ForeignKey(Categoria, on_delete=models.CASCADE, verbose_name="Categoria")

    def __str__(self):
        return self.nome

```

Neste exemplo, temos duas classes de model: "Categoria" e "Produto". A classe "Produto" tem um campo ForeignKey para "Categoria", indicando que cada produto pertence a uma categoria.

Esse relacionamento é definido usando o tipo ForeignKey, que indica que a chave estrangeira está na tabela "Produto" e faz referência à tabela "Categoria". O parâmetro "on_delete=models.CASCADE" indica que, se uma categoria for excluída, todos os produtos associados a ela também serão excluídos (essa é apenas uma das opções disponíveis para definir o comportamento de exclusão).

Os relacionamentos entre tabelas SQL são importantes para permitir que os dados sejam organizados de maneira lógica e eficiente em diferentes tabelas, ao mesmo tempo que permitem que as tabelas sejam interconectadas para recuperar informações de maneira mais fácil e rápida. Esses relacionamentos são criados usando chaves estrangeiras, que permitem que uma tabela faça referência a outra tabela, usando uma coluna que contém os valores que correspondem a outra coluna em outra tabela.

Ao usar relacionamentos entre tabelas, podemos criar estruturas de banco de dados complexas que permitem que os dados sejam armazenados de maneira organizada e consistente, enquanto também permitimos a recuperação de informações de várias tabelas relacionadas de maneira eficiente. Isso é especialmente importante em aplicativos complexos que precisam gerenciar muitos tipos diferentes de dados e relacionamentos entre esses dados.

Você pode verificar todos os tipos disponíveis de campos [aqui](https://docs.djangoproject.com/en/3.2/ref/models/fields/#model-field-types)

## Preparando a migração

Somente escrever as classes no arquivo "models.py" não efetua nenhuma ação no banco de dados, para que as tabelas sejam criadas de fato, primeiramente precisamos preparar a migração através do comando ```python manage.py makemigrations```

O comando "makemigrations" do Django é usado para criar arquivos de migração que descrevem as alterações nos modelos de um aplicativo Django. Esses arquivos de migração são usados pelo Django para criar ou atualizar as tabelas do banco de dados correspondentes aos modelos do aplicativo.

Em termos simples, quando fazemos alterações nos modelos de um aplicativo Django, como adicionar ou remover campos, ou alterar os tipos de dados de um campo, o Django não sabe automaticamente como atualizar o banco de dados para refletir essas alterações. É aqui que o comando "makemigrations" entra em jogo.

Ao executar o comando "makemigrations", o Django analisa as alterações feitas nos modelos do aplicativo e cria um arquivo de migração que descreve essas alterações. Esse arquivo de migração é salvo no diretório "migrations" do aplicativo.

Uma vez que o arquivo de migração foi criado, o próximo passo é executar o comando "migrate" para aplicar as alterações no banco de dados. Esse comando lê os arquivos de migração no diretório "migrations" e executa as operações necessárias no banco de dados para criar ou atualizar as tabelas correspondentes aos modelos do aplicativo.

Em resumo, o comando "makemigrations" é usado para criar arquivos de migração que descrevem as alterações feitas nos modelos de um aplicativo Django. Esses arquivos são então usados pelo comando "migrate" para aplicar as alterações no banco de dados. Isso ajuda a garantir que o banco de dados corresponda sempre aos modelos do aplicativo.

Se tudo estiver correto você verá o seguinte no terminal:

![image](https://user-images.githubusercontent.com/33090552/226227586-946d065c-185d-4105-9e91-82db265fdf16.png)

## Verificando migrações pendentes

Alternativamente, quando necessário, você poderá verificar o status das suas migrações executando o comando ```python manage.py showmigrations```

![image](https://user-images.githubusercontent.com/33090552/226228273-0e500f4d-2a3e-4866-bd59-b655d058db1f.png)

Podemos observar que existem outras migrações além da que criamos, estas são migrações padrão das tabelas pré definidas do projeto Django, elas são responsáveis por varias facilidades que o Django oferece, como por exemplo, página de admin, controle de usuários e outras coisas.

Migrações já realizadas aparecerão com um X marcando os colchetes.

## Executando as migrações

Após isso precisamos executar o seguinte comando ```python manage.py migrate```.

O comando "migrate" do Django é usado para aplicar as alterações definidas nos arquivos de migração a um banco de dados.

Quando você cria ou atualiza um modelo em um aplicativo Django, o Django não sabe automaticamente como atualizar o banco de dados para refletir essas alterações. É aqui que o comando "migrate" entra em ação.

O comando "migrate" lê os arquivos de migração que foram gerados usando o comando "makemigrations" e executa as operações necessárias no banco de dados para criar ou atualizar as tabelas correspondentes aos modelos do aplicativo.

Por exemplo, se você adicionou um novo campo a um modelo e executou o comando "makemigrations", o Django gerará um arquivo de migração que descreve a alteração. Em seguida, você pode executar o comando "migrate" para aplicar essa alteração ao banco de dados.

Em resumo, o comando "migrate" é usado para aplicar as alterações definidas nos arquivos de migração a um banco de dados. Isso garante que o banco de dados corresponda sempre aos modelos do aplicativo e é uma parte importante do processo de desenvolvimento do Django.

![image](https://user-images.githubusercontent.com/33090552/226229684-e55885b9-3dd7-42e2-a577-48cb1513931f.png)

Se tudo foi feito corretamente você verá algo assim.
