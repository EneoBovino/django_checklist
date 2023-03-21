# Models

Em Django, os models são classes Python que definem a estrutura e comportamento dos dados do aplicativo. Eles representam as tabelas do banco de dados que armazenam os dados do aplicativo.

Os models do Django herdam da classe "django.db.models.Model", que fornece funcionalidades para criar, ler, atualizar e excluir objetos do banco de dados. Cada atributo do modelo representa um campo da tabela do banco de dados. Existem vários tipos de campos que podem ser usados em um modelo, como "CharField" para campos de texto curtos, "TextField" para campos de texto longos, "IntegerField" para campos numéricos inteiros, "FloatField" para campos numéricos com ponto flutuante, entre outros.

Os models também permitem definir relações entre as tabelas do banco de dados, como relacionamentos de um-para-um, um-para-muitos e muitos-para-muitos. Isso é feito usando as classes "ForeignKey", "OneToOneField" e "ManyToManyField", respectivamente.

Os models são definidos em arquivos Python no arquivo "models.py" de cada aplicativo Django e podem ser criados e modificados usando migrações. Quando uma migração é executada, o Django cria ou altera as tabelas do banco de dados para refletir as alterações nos models.

Em resumo, os models no Django são a base para definir a estrutura de dados de um aplicativo e para armazenar esses dados em um banco de dados. Eles fornecem uma camada de abstração que permite manipular os dados do aplicativo de maneira eficiente e organizada.

## Tipos de Campos

O django oferece varias opções para definirmos tipos de dados que serão armazenados numa tabela. Abaixo estão alguns mais relevantes e seus parâmetros obrigatórios:

Adicionalmente, você pode verificar todos os tipos disponíveis [aqui](https://docs.djangoproject.com/en/3.2/ref/models/fields/#model-field-types)

<ul>
    <li> <details><summary><h2>Fields de TEXTO</h2></summary><blockquote>
            <details><summary><h3>CharField</h3></summary><blockquote>
                <p>Um campo de string, para strings de tamanho pequeno a grande.<br>
                Para grandes quantidades de texto, use TextField.</p>
                <h4>Parâmetros:</h4>
                <ul>
                <li><code>max_lenght</code> - O comprimento máximo (em caracteres) do campo.</li>
                </ul>
            </blockquote></details>
            <details><summary><h3>TextField</h3></summary><blockquote>
                <p>Um grande campo de texto.<br>
                Utilize este tipo de campo ao invés de CharField quando for armazenar textos muito longos.</p>
                <h4>Não possui parâmetros obrigatórios.</h4>
            </blockquote></details>
            <details><summary><h3>EmailField</h3></summary><blockquote>
                <p>Um CharField que verifica se o valor é um endereço de e-mail válido usando EmailValidator.</p>
                <h4>Parâmetros:</h4>
                <ul>
                <li><code>max_lenght</code> - O comprimento máximo (em caracteres) do campo.</li>
                </ul>
            </blockquote></details>
    </blockquote></details></li>
    <li> <details><summary><h2>Fields de INTEIROS</h2></summary><blockquote>
            <details><summary><h3>IntegerField</h3></summary><blockquote>
                <p>Um número inteiro. Valores de -2147483648 a 2147483647 são seguros em todos os bancos de dados suportados pelo Django.</p>
                <h4>Não possui parâmetros obrigatórios.</h4>
            </blockquote></details>
            <details><summary><h3>SmallIntegerField</h3></summary><blockquote>
                <p>Um número inteiro. Valores de -2147483648 a 2147483647 são seguros em todos os bancos de dados suportados pelo Django.</p>
                <h4>Não possui parâmetros obrigatórios.</h4>
            </blockquote></details>
            <details><summary><h3>BigIntegerField</h3></summary><blockquote>
                <p>Um inteiro de 64 bits, muito parecido com um IntegerField, exceto que é garantido que caberá números de -9223372036854775808 a 9223372036854775807.</p>
                <h4>Não possui parâmetros obrigatórios.</h4>
            </blockquote></details>
            <details><summary><h3>PositiveIntegerField</h3></summary><blockquote>
                <p>Como um IntegerField, mas deve ser positivo ou zero (0).<br>
                Valores de 0 a 2147483647 são seguros em todos os bancos de dados suportados pelo Django.<br>
                O valor 0 é aceito por motivos de compatibilidade com versões anteriores.</p>
                <h4>Não possui parâmetros obrigatórios.</h4>
            </blockquote></details>
            <details><summary><h3>PositiveSmallIntegerField</h3></summary><blockquote>
                <p>Como um PositiveIntegerField, mas só permite valores em um determinado ponto (dependente do banco de dados).<br>
                Valores de 0 a 32767 são seguros em todos os bancos de dados suportados pelo Django.</p>
                <h4>Não possui parâmetros obrigatórios.</h4>
            </blockquote></details>
            <details><summary><h3>PositiveBigIntegerField</h3></summary><blockquote>
                <p>Como um PositiveIntegerField, mas só permite valores em um determinado ponto (dependente do banco de dados).<br>
                Valores de 0 a 9223372036854775807 são seguros em todos os bancos de dados suportados pelo Django.</p>
                <h4>Não possui parâmetros obrigatórios.</h4>
            </blockquote></details>
    </blockquote></details></li>
    <li> <details><summary><h2>Fields de REAIS/FLOATS</h2></summary><blockquote>
            <details><summary><h3>DecimalField</h3></summary><blockquote>
                <p>Um número decimal de precisão fixa, ou seja, este tipo de campo permite que sejam determinados o número máximo de dígitos e casas decimais que serão armazenados.</p>
                <h4>Parâmetros:</h4>
                <ul>
                    <li><code>max_digits</code> - O número total de digitos aceitos, sempre deve ser maior que <code>decimal_places</code>. Por exemplo, para armazenar números até 999 com 2 casas decimais, o valor deve ser 5.</li>
                    <li><code>decimal_places</code> - O número total de casas decimais.</li>
                </ul>
            </blockquote></details>
            <details><summary><h3>FloatField</h3></summary><blockquote>
                <p>Um número de ponto flutuante representado em Python por um <code>float</code>.</p>
                <h4>Não possui parâmetros obrigatórios.</h4>
            </blockquote></details>
    </blockquote></details></li>
    <li> <details><summary><h2>Fields de BOOLEANOS</h2></summary><blockquote>
            <details><summary><h3>BooleanField</h3></summary><blockquote>
                <p>Um campo verdadeiro/falso.</p>
                <h4>Não possui parâmetros obrigatórios.</h4>
            </blockquote></details>
    </blockquote></details></li>
    <li> <details><summary><h2>Fields de DATA e HORA</h2></summary><blockquote>
            <details><summary><h3>DateField</h3></summary><blockquote>
                <p>Uma data, representada em Python por uma <code>datetime.date</code>. Tem alguns parâmetros opcionais extras:</p>
                <h4>Parâmetros:</h4>
                <ul>
                    <li><code>auto_now</code> - Define automaticamente o campo como agora toda vez que o objeto for salvo. Útil para carimbos de data/hora de “última modificação”. Observe que a data atual é sempre usada; não é apenas um valor padrão que você pode substituir.</li>
                    <li><code>auto_now_add</code> - Defina automaticamente o campo como agora quando o objeto for criado pela primeira vez.</li>
                </ul>
            </blockquote></details>
            <details><summary><h3>DateTimeField</h3></summary><blockquote>
                <p>Uma data e hora, representadas em Python por uma <code>datetime.datetime</code>. Recebe os mesmos argumentos extras que DateField.</p>
                <h4>Parâmetros:</h4>
                <ul>
                    <li><code>auto_now</code> - Define automaticamente o campo como agora toda vez que o objeto for salvo. Útil para carimbos de data/hora de “última modificação”. Observe que a data atual é sempre usada; não é apenas um valor padrão que você pode substituir.</li>
                    <li><code>auto_now_add</code> - Defina automaticamente o campo como agora quando o objeto for criado pela primeira vez.</li>
                </ul>
            </blockquote></details>
            <details><summary><h3>TimeField</h3></summary><blockquote>
                <p>Uma hora, representada em Python por uma <code>datetime.time</code>. Aceita as mesmas opções de preenchimento automático que DateField.</p>
                <h4>Parâmetros:</h4>
                <ul>
                    <li><code>auto_now</code> - Define automaticamente o campo como agora toda vez que o objeto for salvo. Útil para carimbos de data/hora de “última modificação”. Observe que a data atual é sempre usada; não é apenas um valor padrão que você pode substituir.</li>
                    <li><code>auto_now_add</code> - Defina automaticamente o campo como agora quando o objeto for criado pela primeira vez.</li>
                </ul>
            </blockquote></details>
            <blockquote><p><img src="https://img.shields.io/badge/-IMPORTANTE-orange"><br>
            As opções <code>auto_now_add</code>, <code>auto_now</code>, e <code>default</code> são mutuamente exclusivas, ou seja, só é possível utilizar uma opção de cada vez. Qualquer combinação dessas opções resultará em um erro.</p>
            <p><img src="https://img.shields.io/badge/-OBSERVAÇÃO-green"><br>
            As opções <code>auto_now</code> e <code>auto_now_add</code> sempre usarão a data no fuso horário padrão, aquele definido no arquivo <code>settings.py</code>, no momento da criação ou atualização.</p></blockquote>
    </blockquote></details></li>
    <li> <details><summary><h2>Fields para ARQUIVOS</h2></summary><blockquote>
            <details><summary><h3>FileField</h3></summary><blockquote>
                <p>Um campo de upload de arquivo.</p>
                <h4>Parâmetros:</h4>
                <ul>
                    <li><code>upload_to</code> - Esse atributo fornece uma maneira de definir o diretório de upload.</li>
                </ul><br>
                <p><img src="https://img.shields.io/badge/-EXEMPLOS-blue"></p>
                <p>O arquivo será armazenado em <code>MEDIA_ROOT/uploads</code><br>
                    <code>upload = models.FileField(upload_to='uploads/')</code></p>
                <p>O arquivo será armazenado em <code>MEDIA_ROOT/uploads/2023/03/20</code><br>
                    <code>upload = models.FileField(upload_to='uploads/%Y/%m/%d/')</code></p>
                <p><a href="https://docs.python.org/3/library/time.html#time.strftime">Mais opções e informações sobre formatação de data e hora.</p>
            </blockquote></details>
            <details><summary><h3>ImageField</h3></summary><blockquote>
                <p>Herda todos os atributos e métodos de FileField, mas também valida se o objeto carregado é uma imagem válida.</p>
                <p>Além dos atributos especiais que estão disponíveis para FileField, ImageField também possui atributos height e width.</p>
                <h4>Parâmetros:</h4>
                <ul>
                    <li><code>height_field</code> - Nome de um campo de modelo que será preenchido automaticamente com a altura da imagem sempre que a instância do modelo for salva.</li>
                    <li><code>width_field</code> - Nome de um campo de modelo que será preenchido automaticamente com a largura da imagem sempre que a instância do modelo for salva.</li>
                </ul><br>
                <p><img src="https://img.shields.io/badge/-IMPORTANTE-orange"><br>
                Requer a biblioteca <code>Pillow</code>. Para instalar execute <code>pip install Pillow</code></p>
                <p><img src="https://img.shields.io/badge/-OBSERVAÇÃO-green"><br>
                ImageField é criado em seu banco de dados como texto com um comprimento máximo padrão de 100 caracteres. Assim como em outros campos, você pode alterar o comprimento máximo usando o parâmetro <code>max_length</code></p>
            </blockquote></details>
    </blockquote></details></li>
    <li> <details><summary><h2>Fields de RELACIONAMENTO</h2></summary><blockquote>
            <details><summary><h3>ForeignKey</h3></summary><blockquote>
                <p>Uma relação muitos-para-um. Requer dois parâmetros: a classe à qual o modelo está relacionado e a on_delete.</p>
                <h4>Parâmetros:</h4>
                <ul>
                    <li><code>PARAM</code> - PARAM_TEXT</li>
                </ul><br>
            </blockquote></details>
            <details><summary><h3>ManyToManyField</h3></summary><blockquote>
                <p>FIELD_TEXT</p>
                <h4>Parâmetros:</h4>
                <ul>
                    <li><code>PARAM</code> - PARAM_TEXT</li>
                </ul><br>
            </blockquote></details>
            <details><summary><h3>OneToOneField</h3></summary><blockquote>
                <p>FIELD_TEXT</p>
                <h4>Parâmetros:</h4>
                <ul>
                    <li><code>PARAM</code> - PARAM_TEXT</li>
                </ul><br>
            </blockquote></details>
    </blockquote></details></li>
    <li> <details><summary><h2>Parâmetros adicionais opcionais</h2></summary><blockquote>
            <p>Os argumentos a seguir estão disponíveis para todos os tipos de campo. Todos são opcionais.</p>
            <details><summary><h3>null</h3></summary><blockquote>
                <p>Se True, o Django armazenará valores vazios como NULL no banco de dados. O padrão é False.</p>
                <p>Evite usar null em campos baseados em string, como CharField e TextField. Se um campo baseado em string tiver null=True, isso significa que ele tem dois valores possíveis para “sem dados”: NULL, e a string vazia. Na maioria dos casos, é redundante ter dois valores possíveis para “sem dados”; a convenção do Django é usar a string vazia, não NULL. Uma exceção é quando a CharField tem ambos unique=True e blank=True definido. Nessa situação, null=True é necessário evitar violações de restrição única ao salvar vários objetos com valores em branco.</p>
                <p>Para campos baseados em string e não baseados em string, você também precisará definir blank=True se deseja permitir valores vazios em formulários, pois o parâmetro null afeta apenas o armazenamento do banco de dados (consulte Recursos blank).</p>
            </blockquote></details>
            <details><summary><h3>blank</h3></summary><blockquote>
                <p>Se True, o campo pode ficar em branco. O padrão é False.</p>
                <p>Observe que isso é diferente de null. null é puramente relacionado ao banco de dados, enquanto blank é relacionado à validação. Se um campo tiver blank=True, a validação do formulário permitirá a entrada de um valor vazio. Se um campo tiver blank=False, o campo será obrigatório.</p>
            </blockquote></details>
            <details><summary><h3>choices</h3></summary><blockquote>
                <p>Se True, o campo pode ficar em branco. O padrão é False.</p>
                <p>Observe que isso é diferente de null. null é puramente relacionado ao banco de dados, enquanto blank é relacionado à validação. Se um campo tiver blank=True, a validação do formulário permitirá a entrada de um valor vazio. Se um campo tiver blank=False, o campo será obrigatório.</p>
            </blockquote></details>
    </blockquote></details></li>
</ul>



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
