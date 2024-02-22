# Stack guide.me

## Antes de começar

Esse é um planejamento pessoal, feito baseado nos conhecimentos que tenho sobre as tecnologias citadas, experièncias frustrantes em projetos de desafios para vagas de empregos e projetos pessoais.

Inclusive, este `guide.me` também é um projeto pessoal. Portanto sinta-se livre para fazer de acordo com o seu conhecimento da sua Stack.

### O que não será mencionado neste documento

__**Metodologias de Desenvolvimento de Softwares**__ como, TDD; DDD; e BDD _(Particularmente, preciso me aprofundar nessas duas últimas nessa abordagens)_;  não fazem parte deste planejamento.

_**Padrões de Design**_ Também não é citado modelos de arquiteturas como: MVC; MSC; HMVC; SOA; MVVM (Model-View-ViewModel); ou outros padrões de design, não serão abordados.

_**Design patterns**_ também não fazem parte deste documento.

_**Arquitetura do banco de dados**_ esta fora deste escopo

_**Deployment**_ não faz parte no momento.

Essas questões são relativas e tem um grande _**DEPENDE**_ para cada contexto, aplicação e experiência na área. Portanto, interpretações de **como** resolver os problema estão abertas.

---

#### Uma pequena história para relaxar...

> Mãe!!! Cadê aquela camisa que ganhei naquele kit OnBoard da minha primeira vaga de emprego?

Mãe: Está no guarda-roupas. 

> No guarda-roupas? Onde?

Mãe: Na primeira porta, segunda gaveta, do lado direito, debaixo das camisetas brancas.

> Não encontrei, Mãe!

`Já sabe o final da história, não é?!`

---

O que importa aqui é saber **onde estão as coisas que preciso** para **acrescentar**, **corrigir** ou **alterar** alguma parte do meu código.

Portanto, manter as coisas organizadas do jeito que entende não é questão de beleza, e sim eficiência.

Essa não é uma ideia universal. É a forma que consigo enxergar atualmente de forma solo. Caso seja um projeto colaborativo, essa a abordagem pode divergir.

## Introdução 
O propósito deste guia é ter em mãos projetos pré-configurados com as tecnologias principais para desenvolvimento web Fullstack.

Sim, isso mesmo `boilerplates`!

### Motivação

Seja para uma entrevista de emprego ou para desenvolvimento pessoal, há muito tempo perdido na configuração inicial do projeto. Com isso, um tempo valioso é perdido acessando a documentação da tecnologia X ou Y para integrar essas tecnologias.

**Um exemplo: pizzaria**

Imagine se toda vez que o garçom envia um pedido para a cozinha, o responsável tem que ir até o mercado comprar os ingredientes para o tipo de pizza naquele momento, voltar e entregar para o cozinheiro, para a partir daí, começar a fazer a pizza.

Não seria mais eficiente se os ingredientes já estivessem no armazem da cozinha e no freezes?

Pois, então! A ideia é a mesma.

**Exemplos**

Cada stack há dois atores principais que estão presentes em todas elas: `Variáveis de ambiente` e `Docker`.

Abaixo estão a descrição desses personagens importantes.

### Variáveis de ambiente

> Elas são parte do ambiente no qual um processo executa.

Resumidamente, algumas variáveis são definidas no ambiente (Sistema operacional) no qual um processo executa. Elas podem ser lidas, alteradas e adicionadas.

Elas são definidas antes da sua aplicação executar. Geralmente essas variáveis de ambiente armazenam algum dado importante como: usuario, senhas, portas, endereços, número de portas, mudar o comportamento da aplicação (DEVELOPER, PRODUCTION, TESTS, etc), endereços para APIs externas e muitas outras coisas que queira tornar `onipresente` em toda a aplicação no momento da sua execução.

No contexto de sistemas, geralmente elas são definidas em um arquivo chamado `.env`.

- `.env` Váriaveis de ambientes para produção
- `.env.example` Váriaveis de ambientes de exemplo, sem credencias válidas. Mas deve relacionar todas que a aplicação necessita para funcionar

## Docker

A tecnologia mais conhecida atualmente para disponibilizar aplicações de forma isolada é a Docker. Te permite isolar todos os processos que sua aplicação precisa para funcionar.

> Por exemplo, para rodar a versão `n` do NodeJS, em um processo Linux na versão `j`, com variável de ambiente `x` e na porta `y`

São utilizadas dois arquivos principais do Docker: `Dockerfile` e `docker-compose`. O Dockerfile para isolar o processo e o docker-compose para "orquestrar" esses processos.

#### Dockerfile

Cada componente deve ter configurado arquivos `Dockerfile` para a implantação da imagem. Os ambientes devem ter um arquivo de `variavéis de ambiente` para ambiente (_mínimo_).

Um arquivo Dockerfile não tem extensão, é somente `Dockerfile`. Mas, para fins de organização, um arquivo Dockerfile dentro de cada pasta aplicação. Somente um arquivo com nome `Dockerfile` deve estar presente na raiz do projeto. Mas nada impede de ter vários utilizando sufixos, como por exemplo:

Para ter mais de um arquivo desses na mesma estrutura de diretórios, você pode utilizar um sufixo de sua preferência. Nesta caso, estou utilizando nomes que representam a sua finalidade. Poderia ter vários outros arquivos Dockerfiles para organizar minha aplicação. Poderia ter além desses, outros para fins especificos, como por exemplo:

- Dockerfile.frontend (aplicação frontend)
- Dockerfile.backend (aplicacao backend)
- Dockerfile.staticfiles (armazenamento de arquivos estáticos)
- Dockerfile.cups (impressoras)
- Dockerfile.samba (servidores de arquivos)
- Dockerfile.redis (cache http)
- Dockerfile.squid (proxy e cache http)
- Dockerfile.database (banco de dados)
- Dockerfile.mongodb (banco de dados mongodb)
- Dockerfile.mysql (banco de dados mysql)
- Dockerfile.oracle (banco de dados oracle)
- Dockerfile.crawler (scrape Python)
- Dockerfile.java (aplicação feita em java)
- Dockerfile.php (aplicação feita em php)
- Dockerfile.payments (processador pagamentos)
- Dockerfile.ia.humanfaces (processador rostos de pessoas)
- Dockerfile.ia.voices (processador de vozes)
- Dockerfile.ia.speechtotext (converter voz em texto)
- Dockerfile.ia.omr (processador de marcações)
- Dockerfile.primo.joao (aplicação feita pelo meu primo João)
- Dockerfile.irma.maria (aplicação feita pela minha irmã Maria)
- Dockerfile.prima.irma.tio.amiga.leticia (já deu pra entender, né!?)

Cada arquivo `Dockerfile` deve realizar as seguintes etapas (_minímo_):

- Definir uma imagem
- Configurar portas para comunicação
- Copiar os arquivos do projeto para a imagem
- Instalar as dependências do projeto
- Inicializar o projeto

### Orquestação dos containers

Cada projeto de ter um arquivo `Dockerfile` para gerenciar os containers. É nele que podemos iniciar, parar, ver o status das aplicações, configurar redes, entre outras coisas.

Abaixo esta descrito o nome desse arquivo:

- `docker-compose.yaml`

O arquivo docke-compose deve ser reponsáveis por gerenciar as aplicações dos arquivo Dockerfiles, assim como definir redes de comunicação entre eles, etc.

## As Stacks

Cada stack são compostas pelos seguintes estruturas:

- FRONTEND
- BACKEND
- BANCO DE DADOS

As estruturas de `BACKEND` e `FRONTEND` devem ser separadas utilizando os padrões para cada propósito.

### Frontend

O frontend deve ter um layout mínimo composto por:
- Cabeçalho
- Navegação
- Conteúdo
- Rodapé

O componente `Frontend` deve ter as seguintes funcionalidades, separadas por cada um dos nívels:

#### Básico
- Página principal

#### Médio - API
- Navegação
- Página de contato
- Página de Posts
- Página de Detalhes do Post

#### Avançado 
- Autenticação via Tokens
- Formulário para usuários de auto-cadastro
- Página de login
- Página de recuperação de senha

#### Administrativo
  - CRUD do perfil do usuário
  - CRUD de posts
  - Upload de images

### Backend

O backend é uma das camadas principais de uma aplicação dinâmica. É nela que dados são salvos, lidos, alterados e excluídos.

Independente da tecnologia para backend escolhida, deve-se atentar as seguintes pilares da segurança da informação.

<details>
  <summary>Saiba mais</summary>

  #### Os 5 pilares da Segurança da Informação

  ##### Confidencialidade

  Garante que as informações sejam acessíveis apenas por pessoas autorizadas. Refere-se à proteção das informações contra acesso não autorizado. Incluindo medidas como criptografia, controle de acesso e políticas de segurança.

  ##### Integridade

  Assegura que as informações sejam precisas e completas, e que não sejam alteradas sem autorização.

  ##### Disponibilidade

  Garante que as informações estejam disponíveis para os usuários quando necessário.

  ##### Autenticidade
  Verifica a identidade das pessoas e dos sistemas que acessam as informações.

  ##### Não repúdio

  Impede que as pessoas neguem ter enviado ou recebido informações.


</details>


O componente `Backend` deve ter as seguintes funcionalidades, separadas por cada um dos nívels:


#### Básico
- Rodar tudo no arquivo server.js
- Rota `'/'` - exibir informações da API

#### Médio - 
- Rota `/posts` - uma lista de posts
- Rota `/posts/:id` - exibir um post pelo Id

#### Avançado 
- Autenticação via Tokens
- Cadastro de usuários
- Página de recuperação de senha

#### Administrativo
  - CRUD de usuários
  - CRUD de posts
  - Upload de images
  - `Root`
    - Gerenciar usuários
    - Gerenciar posts



## Tecnologias utilizadas

As tecnologias utilizadas para a criação são:
- Git e Github
- HTML
- CSS
- Docker
- Javascript
- Python
- PHP

### Frameworks

Os Frameworks/bibliotecas utilizados para cada tecnologia são:

### Stacks de desenvolvimento

#### Javascript

- Nodejs (express)
- ReactJS
- Jest
- Mocha
- Sinon
- Chai
- Chai-http
- Sinon
- Sinon-chai

#### Python

- Django
- Flask
- FastAPI
- Pytest
- Automação e/ou Webscrapping
  - Requests
  - Parsel
  - BeautifulSoup
  - Scrapy
  - Pyautogui

#### PHP

- Laravel
- CakePHP
- Codeigniter
- PHPUnit
