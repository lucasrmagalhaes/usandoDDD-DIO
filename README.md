<h1 align="left">
  Desenvolvendo sua aplicação com C# usando DDD
</h1>

<h4 align="left">Agenda</h4>

<ul>
  <li><a href="https://github.com/lucasrmagalhaes/usandoDDD-DIO#domain-driven-design">Conceito sobre DDD</a></li>
  <li><a href="https://github.com/lucasrmagalhaes/usandoDDD-DIO#criando-um-modelo-de-dom%C3%ADnio-mdd">Criando um Modelo de Domínio (MDD)</a></li>
  <li><a href="https://github.com/lucasrmagalhaes/usandoDDD-DIO#regras-para-modelagem-do-dom%C3%ADnio">Regras para Modelagem</a></li>
  <li><a href="https://github.com/lucasrmagalhaes/usandoDDD-DIO#exemplos-de-implementa%C3%A7%C3%A3o">Exemplos de Implementação</a></li>
</ul>

<hr />

<h4 align="left">Domain Driven Design</h4>

<p align="left">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"É uma abordagem de design de software disciplinada que reúne um conjunto de conteitos, técnicas e princípios para construção de softwares baseados em um modelo de domínio".<br />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"Domínio é todo e qualquer conhecimento utilizado em uma determinada área".
</p>

<h6 align="center">Um pouco de história</h6>

<p align="left">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Ele veio do título do livro escrito por Eric Evans, dono da DomainLanguage, uma empresa especializada em treinamento e consultoria para desenvolvimento de software.<br />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;O livro de Evans é um grande catálogo de Padrões, baseados em experiências do autor ao longo de mais de 20 anos desenvolvendo software utilizando técnicas de Orientação a Objetos.
</p>

<h6 align="center">Principais conceitos do DDD</h6>

<ul>
    <li><strong>Alinhamento do código com o negócio:</strong> o contato dos desenvolvedores com os especialistas do domínio é algo essencial quando se faz DDD (o pessoal de métodos ágeis já disso faz tempo). Se faz necessário o uso de uma linguagem úbiqua (comum entre todos) para descrever o domínio e suas regras;</li>
    <li><strong>Favorecer reutilização:</strong> os blocos de construção, que veremos adiante, facilitam aproveitar um mesmo conceito de domínio ou um mesmo código em vários lugares;</li>
    <li><strong>Mínimo de acoplamento:</strong> Com um modelo bem feito, organizado, as várias partes de um sistema interagem sem que haja muita dependência entre módulos ou classes de objetos de conceitos distintos; e</li>
    <li><strong>Independência da Tecnologia:</strong> DDD não foca em tecnologia, mas sim em entender as regras de negócio e como elas devem estar refletidas no código e no modelo de domínio. Não que a tecnlogia usada não seja importante, mas essa não é uma preocupação de DDD.</li>
</ul>

<hr />

<h4 align="left">Criando um modelo de domínio (MDD)</h4>

<p align="left">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A ideia por trás de MDD é a de que o seu modelo abstrato deve ser uma representação perfeita do sue domínio. Tudo que existe no seu negócio deve aparecer no modelo. Só aparece no modelo aqui que está no negócio.<br />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;O desenho do modelo é criado em conjunto entre especialistas de negócio e domínio, analistas, arquitetos e desenvolvedores, utilizando a linguegem úbiqua para que todos tenha o mesmo entendimento do domínio.<br />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;O processo de maturação de um sistema desenvovlido usando MDD deve ser contínuo. O modelo servirá de guia para a criação do código e, ao mesmo tempo, o código ajuda a perfeiçoar o modelo.

<h6 align="center">Blocos de Construção do MDD</h6>

<p align="left">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Uma vez que decidimos criar um modelo usando MDD, precisamos, incialmente, isolar o modelo de domínio das demais partes que compõem o sistema. Essa separação pode ser feita utilizando-se uma arquitetura em camadas, que dividirá nossa aplicação em quatro partes:
</p>

<ul>
    <li>Interface de Usuário - parte responsável pela exibição de informações do sistema ao usuário e também por interpretar comandos do usuário;</li>
    <li>Aplicação - essa camada não possui lógica de negócio. Ela é apenas uma camada fina, responsável por conectar a Interface de Usuário às camadas inferiores;</li>
    <li>Domínio - representa os conceitos, regras e lógicas de negócio. Todo o foco de DDD está nessa camada. Nosso trabalho, daqui para frente, será aperfeiçoar e compreender profundamente essa parte; e</li>
    <li>Infra-estrutura - fornece recursos técnicos que darão suporte às camadas superiores. São normalmente as partes de um sistema responsáveis por persistência de dados, conexões com banco de dados, envio de mensagens por redes, gravação e leitura de discos, etc.</li>
</ul>

<h6 align="center">Arquitetura Padrão do MDD</h6>

<p align="left">
  <img src="https://github.com/lucasrmagalhaes/usandoDDD-DIO/blob/main/img/Arquitetura%20Padr%C3%A3o%20do%20MDD.jpg" alt="Arquitetura Padrão do MDD">
</p>

<hr />

<h4 align="left">Regras para Modelagem do Domínio</h4>

<ul>
    <li><strong>Entidades -</strong> classes de objetos que necessitam de uma identidade. Normalmente são elementos do domínio que possuem ciclo de vida dentro de nossa aplicação: um Cliente, por exemplo, se cadastra no sistema, faz compras, se torna inativo, é excluído, etc.;</li>
    <li><strong>Objetos de Valores -</strong> objetos que só carregam valores, mas que não possuem distinçao de identidade. Bons exemplos de objetos de objetos de valores seria: strings, números ou cores. Por exemplo: se o lápis de cor da criança acabar e você der um novo lápis a ela, da mesma cor, só que de outra caixa, ela não vai se importar. Para a criança, o lápis vermelho de uma caixa é igual ao lápis vermelho de outra caixa. As instâncias de Objetos de Valores são imutáveis, isto é, uma vez criados, seus atributos internos não poderão mais ser modificados.;</li>
    <li><strong>Agregados -</strong> compostos de Entidades ou Objetos de Valores que são encapsulados numa única classe. O Agregado serve para manter a integridade do modelo. Elegemos uma classe para servir de raiz do Agregado. Quando algum cliente quiser manipular dados de uma das classes que compõem o Agregado, essa manipulação só poderá ser feita através da entidade raiz;</li>
    <li><strong>Fábricas -</strong> classes responsáveis pelo processo de criação dos Agregados ou dos Objetos de Valores. Algumas vezes, Agregados são relativamente complexos e não queremos manter a lógica de criação desses Agregados nas classes que o compõem. Extraímos então as regras de criação para uma classe externa: a fábrica;</li>
    <li><strong>Serviços -</strong> classes que contém lógica de negócio, mas que não pertence a nenhuma Entidade ou Objetos de Valores. É importante ressaltar que Serviços não guardam estado, ou seja, toda chamada a um mesmo serviço, dada uma mesma pré-condição, deve retornar sempre o mesmo resultado;</li>
    <li><strong>Repositórios -</strong> classes responsáveis por administrar o ciclo de vida dos outros objetos, normalmente Entidades, Objetos de Valor e Agregados. Os repositórios são classes que centralizam operações de criação, alteração e remoção de objetos.; e</li>
    <li><strong>Módulos -</strong> abstrações que têm por objetivos agrupar classes por um determinado conceito do domínio. A maioria das linguagens de programação oferecem suporte a módulos (pacotes em Java, namespaces em .NET ou módulos em Ruby).</li>
</ul>

<hr>

<h4 align="left">Exemplos de Implementação</h4>

<ul>
  <li><a href="https://github.com/alexalvess/aurora-api-project">Aurora API Project</a></li>
</ul>