<h1 align="left">
  Desenvolvendo sua aplicação com C# usando DDD
</h1>

<h4 align="left">Agenda</h4>

<ul>
  <li><a href="#DDD">Conceito sobre DDD</a></li>
  <li><a href="#MDD">Criando um Modelo de Domínio (MDD)</a></li>
  <li>Regras para Modelagem</li>
  <li>Exemplos de Implementação</li>
  <li>Considerações Finais</li>
</ul>

<hr>

<section id="DDD">

<h4 align="left">Domain Driven Design</h4>

<p align="center">Sobre</p>

<p align="left">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"É uma abordagem de design de software disciplinada que reúne um conjunto de conteitos, técnicas e princípios para construção de softwares baseados em um modelo de domínio".<br />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"Domínio é todo e qualquer conhecimento utilizado em uma determinada área".
</p>

<p align="center">Um pouco de história</p>

<p align="left">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Ele veio do título do livro escrito por Eric Evans, dono da DomainLanguage, uma empresa especializada em treinamento e consultoria para desenvolvimento de software.<br />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;O livro de Evans é um grande catálogo de Padrões, baseados em experiências do autor ao longo de mais de 20 anos desenvolvendo software utilizando técnicas de Orientação a Objetos.
</p>

<p align="center">Principais conceitos do DDD</p>

<ul>
    <li><strong>Alinhamento do código com o negócio:</strong> o contato dos desenvolvedores com os especialistas do domínio é algo essencial quando se faz DDD (o pessoal de métodos ágeis já disso faz tempo). Se faz necessário o uso de uma linguagem úbiqua (comum entre todos) para descrever o domínio e suas regras;</li>
    <li><strong>Favorecer reutilização:</strong> os blocos de construção, que veremos adiante, facilitam aproveitar um mesmo conceito de domínio ou um mesmo código em vários lugares;</li>
    <li><strong>Mínimo de acoplamento:</strong> Com um modelo bem feito, organizado, as várias partes de um sistema interagem sem que haja muita dependência entre módulos ou classes de objetos de conceitos distintos; e</li>
    <li><strong>Independência da Tecnologia:</strong> DDD não foca em tecnologia, mas sim em entender as regras de negócio e como elas devem estar refletidas no código e no modelo de domínio. Não que a tecnlogia usada não seja importante, mas essa não é uma preocupação de DDD.</li>
</ul>

</section>

<hr>

<section id="MDD">

<h4 align="left">Criando um modelo de domínio (MDD)</h4>

<p align="center">Sobre</p>

<p align="left">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A ideia por trás de MDD é a de que o seu modelo abstrato deve ser uma representação perfeita do sue domínio. Tudo que existe no seu negócio deve aparecer no modelo. Só aparece no modelo aqui que está no negócio.<br />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;O desenho do modelo é criado em conjunto entre especialistas de negócio e domínio, analistas, arquitetos e desenvolvedores, utilizando a linguegem úbiqua para que todos tenha o mesmo entendimento do domínio.<br />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;O processo de maturação de um sistema desenvovlido usando MDD deve ser contínuo. O modelo servirá de guia para a criação do código e, ao mesmo tempo, o código ajuda a perfeiçoar o modelo.

<p align="center">Blocos de Construção do MDD</p>

<p align="left">
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Uma vez que decidimos criar um modelo usando MDD, precisamos, incialmente, isolar o modelo de domínio das demais partes que compõem o sistema. Essa separação pode ser feita utilizando-se uma arquitetura em camadas, que dividirá nossa aplicação em quatro partes:
</p>

<ul>
    <li>Interface de Usuário - parte responsável pela exibição de informações do sistema ao usuário e também por interpretar comandos do usuário;</li>
    <li>Aplicação - essa camada não possui lógica de negócio. Ela é apenas uma camada fina, responsável por conectar a Interface de Usuário às camadas inferiores;</li>
    <li>Domínio - representa os conceitos, regras e lógicas de negócio. Todo o foco de DDD está nessa camada. Nosso trabalho, daqui para frente, será aperfeiçoar e compreender profundamente essa parte; e</li>
    <li>Infra-estrutura - fornece recursos técnicos que darão suporte às camadas superiores. São normalmente as partes de um sistema responsáveis por persistência de dados, conexões com banco de dados, envio de mensagens por redes, gravação e leitura de discos, etc.</li>
</ul>

</section>