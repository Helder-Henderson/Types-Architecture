# Types-Architecture

## Arquitetura monolítica 

A arquitetura monolitica é um sistema unico, nao divido, que roda em um unico processo, ou seja, é uma aplicação na qual diferentes componentes estão ligados a um unico programa dentro de uma unica plataforma.

Na arquitetura monolitica o nucleo do comportamento da aplicação é executado em seu proprio processo e a aplicação inteira é implantada como uma unica unidade

Um aplicativo criado com essa arquitetura pode escalar verticalmente aumentando o poder das maquinas  em que a aplicação roda ou horizontalmente com adição de instancias atras de um Load Balancer

### Vantagens 

- Mais simples de desenvolvero : a organização fica concentrada em um único sistema e muitos desenvolvedores estão familiarizados com este modelo sendo que o desenvolvimento inical é mais rápido

- Simples de fazer o deploy para o servidor: Fazemos o deploy de um único pacote final;

- Exige uma equipe menor - necessita de um time menor para desenvolver e manter a aplicação 

### Desvantagens 

- Manutenção: A aplicação se torna cada vez maior de acordo com o seu tamanho, o código será cada vez mais difícil de entender e o desafio de fazer alterações rápidas e ter que subir para o servidor só cresce. 

- ALterações : Para cada alteração feita, é necessário realizar um novo deploy de toda a aplicação 

- Fragilidade: Uma linha decódigo que subiu errada pode quebrar todo o sistema e ele ficar totalmente inoperante

-----------------------

## Arquitetura em camadas

Visa a criação de aplicativos modulares, de forma que cada camada possui uma responsabilidade e onde a camada superior se comunica com a camada inferior e assim por diante, fazendo com que uma camada seja dependente apenas da camada imediatamente inferior.

Podemos assim dividir um sistema em uma, duas, três ou n camadas dependendo do objetivo e da complexidade do sistema

Dependendo do contexto as camadas podem ser lógicas ( Layers ) ou físicas ( Tiers ).

A mais conhecida é a arquitetura em três camadas, onde temos as camadas de interface (UI), a camada lógica dos negócios(BLL), e a camada de acesso aos dados (DAL).

### Vantagens

- Com a organização de código em camadas podemos reutilizar a funcionalizade de baixo nível em todo o aplicativo

- Com uma arquitetura em camadas, os aplicativos podem impor restrições sobre quais camadas podem se comunicar com outras camadas.

- Essa arquitetura ajuda a atingir o encapsulamento

- Quando uma camada é alterada ou substituida, apenas as camadas que interagem com ela serão afetadas

- As camadas tornam muito mais facil substituir a funcionalidade dentro do projeto

### Desvantagens 

- As dependencias em tempo de compilação são executadas de cima para baixo

- Assim a camada de negócios (BLL) depende dos detalhes de implementação da camada de acesso aos dados.

- Testar a lógica de negócio nesta arquitetura é dificil pois exige um banco de dados de teste.

------------------

## Arquitetura Cebola

Está baseada no principio da inversão de controle e é composta por várias camadas ceoncêntricas que se interconectam em direção ao núcleo que representa o domínio. Ela não depende da camada de dados como nas arquiteturas em várias camadas, mas dos modelos de domínio reais.

A Onion Architecture resolveu o problema do acoplamento entre as camadas definindo camadas a partir do núcleo para a infraestrutura

Ela aplica a regra fundamental movendo todos os acoplamentos em direção ao centro, sendo que no centro da Onion está o modelo de domínio, que representa os objetos de negócios e o comportamento.

Ao redor da camada de dominio existem outras camadas ( UI, Infra, Repositorios, Interfaces) com mais comportamentos.

![image](https://user-images.githubusercontent.com/59569208/182026781-bb20edb4-74fd-4b0e-afae-0f0b832511bd.png)


- A camada de domínio (Domain Model) - Representa os objetos de negócios e o comportamento , e, pode conter interfaces de domínio. Esta camada não possui nenhuma dependência. 

- A camada de serviços do Domínio (Domain Services) - cria uma abstração entre as entidades do domínio e a lógica de negócios do aplicativo. Nesta camada, temos as interfaces que fornecem o comportamento de salvar e recuperar objetos,geralmente envolvendo um repositório que acessa a fonte de dados.

- A camada de serviço da Aplicação (Application Services) - A camada de serviços da aplicação mantém interfaces com operçaões comuns, como Adicionar, Salvar, Editar e Excluir. Além disso, essa camada é usada para se comunicar com a camada da interface do usuário e a camada do repositório. 

- As camadas externas (UI, Infraestructure, tests) - No anel mais externo temos os componente que mudam com frequencia. A camada de apresentação, o acesso aos dados, e os testes.

![image](https://user-images.githubusercontent.com/59569208/182026955-0dc58c59-b498-445a-97f1-5fbc5f6ede0c.png)

### Vantagens

- As camadas da onion Architecture são conectadas através de interfaces. As implementações são fornecidas durante o tempo de execução.

- A arquitetura do aplicativo é construída sobre um modelo de donínio.

- Toda dependência externa, como acesso ao banco de dados e chamadas de serviço, é representada em camadas externas; 

- Não há nenhuma dependência da camada Interna com camadas externas.

- Pode ser testada rapidamente porque o núcleo do aplicativo, o domínio, não depende de nada

- Os acoplamentos estão voltados para o centro (Regra de dependência)

### Desvantagens

- Não é fácil de entender para iniciantes.

- Tem uma curva de aprendizado

- Pode ser dificil fazer a divisão das responsabilidades entre as camadas

- Utiliza Interfaces em profusão

### Resumo 

- Aplicativo construido em torno de um modelo de objeto independente (dominio)

- camadas internas definem interfaces. As camadas externas implementam interfaces

- A direção do acoplamento é em direção ao centro

- Todo o código principal do aplicativo pode ser compilado e executado separadamente da infraestrutura.










