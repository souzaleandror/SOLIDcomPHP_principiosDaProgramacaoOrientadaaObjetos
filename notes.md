#### 24/02/2024

Curso de SOLID com PHP: princípios da programação orientada a objetos

@01-Preparando o terreno 

@@01
Introdução

[00:00] Olá, pessoal. Sejam muito bem-vindos à Alura. Meu nome é Vinicius Dias, e eu vou guiar vocês nesse treinamento de SOLID e boas práticas de Orientação a Objetos.
[00:09] Vamos começar falando um pouco de alguns conceitos da Orientação a Objetos, conceitos muito importantes para darmos continuidade ao treinamento, e depois falaremos de cada um desses princípios: sobre Princípio de Responsabilidade Única, Princípio de Aberto e Fechado, Princípio de Substituição de Liskov, Princípio de Segregação de Interface, e Princípio da Inversão de Dependência.

[00:31] E além de ver e falar sobre esses princípios, vamos implementar na prática em um projeto bem simples, mas que vai dar base para entendermos como cada princípio é aplicado e quais as vantagens de cada um.

[00:42] No final, vamos ter um código, bem tranquilo, bem simples de entender representando um modelo fictício da Alura, onde nós temos um vídeo, onde nós temos a AluraMais que nada mais é do que um vídeo, só que você recebe pontuação por isso, nós temos um curso que você pode receber pontuação além de poder assisti-lo, vamos separar o feedback, onde ele vai ter suas próprias regras, enfim, vamos trabalhar bastante.

[01:08] Para esse treinamento eu espero que você já tenha conhecimento com Orientação a Objetos, porque nesse treinamento vamos falar sobre algumas boas práticas da Orientação a Objetos. Também espero que você já tenha o PHP instalado na sua máquina e que você baixe esse projeto no primeiro exercício dessa aula.

[01:24] Com isso, você já vai estar pronto para dar continuidade para esse treinamento. Te espero no próximo vídeo para começarmos a bater um papo sobre alguns conceitos da Orientação a Objetos.

@@02
Projeto inicial do treinamento

Baixe aqui o ZIP do projeto inicial deste treinamento, necessário para a continuidade do mesmo.

https://caelum-online-public.s3.amazonaws.com/1315-php-solid/01/aula1-projeto-inicial.zip

@@03
Coesão

[00:00] Vou deixar esse projeto aqui para vocês baixarem. É um projeto que representa bem por alto um modelo da Alura, onde temos cursos, tem vídeos da AluraMais, tem para o vídeo em si, tem um serviço para assistir cursos, vídeos etc, um calculador de pontuação para fazer aquele cálculo de quantos pontos você ganha por assistir um curso etc, enfim, bem resumido.
[00:26] Mas eu quero conversar com vocês sobre, obviamente, como é o assunto do curso, Orientação a Objetos. Se você estudou sobre Orientações a Objetos, e espero que você tenha estudado para chegar nesse treinamento já um pouco mais avançado, você com certeza já ouviu falar sobre alguns pilares da Orientação a Objetos como, herança, encapsulamento, polimorfismo, abstração, enfim, esses termos, esses pilares da Orientação a Objetos.

[00:52] Mas a Orientação a Objetos também traz, enquanto estamos desenvolvendo, utilizando esse paradigma da Orientação a Objetos, esbarramos em conceitos e problemas um pouco diferentes e nesse treinamento vamos falar mais sobre esses conceitos, e o primeiro que eu quero conversar com vocês é sobre a Coesão.

[01:09] O que é Coesão no sentido de desenvolvimento de software, de arquitetura de software? Uma classe coesa, ela faz só o que faz sentido, ela só tem implementado nela o que faz sentido, para sua definição, para seu modelo, para seu domínio.

[01:26] Um exemplo, no nosso projeto aqui, é a classe Video. O que a classe Video representa? Ela representa um vídeo da Alura, seja na AluraMais, seja um vídeo de um curso, independente do que for, é um vídeo. Esse vídeo pode ter sido assistido ou não, esse vídeo tem um nome, o vídeo tem uma duração, isso tudo faz, é referente ao vídeo e somente ao vídeo.

[01:48]Eu não tenho aqui dentro da classe Video alguma coisa fazendo menção a um curso, ou a AluraMais, ou a pontuação. Dessa forma, eu tenho a classe Video sendo responsável somente pelo que ela realmente deve ser responsável, ou seja, ela tem uma única responsabilidade, que é representar o vídeo.

[02:09] E vamos conversar um pouco melhor sobre responsabilidade em um capítulo futuro. Mas toda classe não é assim? Você só descreveu qualquer classe que faz só o que tem que fazer.

[02:22] Vou te dar um exemplo que provavelmente você já viu desenvolvendo no seu trabalho, nos seus estudos, que é sugerir aqui um exemplo de uma classe Pessoa, só que essa classe tem nome, telefone, endereço, até aí tudo bem, esses poderiam ser atributos de uma pessoa, mas tem a cor da casa onde essa pessoa mora, tem o modelo do celular que ela possui. Aqui já estamos entrando em responsabilidades, em atributos, propriedades que não são dessa classe, que não pertencem à pessoa.

[02:54] A cor da casa dessa pessoa podia muito estar dentro de um objeto casa. O modelo do celular, se eu realmente precisasse disso, estaria aqui dentro de telefone. Essa pessoa já está tendo atributos, tendo informações demais. E pior do que isso, ela tem responsabilidades, ela executa ações que não deveria.

[03:17] Como por exemplo, imprimir um relatório. Não é uma pessoa que deve imprimir um relatório, não é a classe Pessoa. A classe Pessoa serve para representar uma pessoa. E a representação de uma pessoa não faz impressão de um relatório, muito menos salva os dados em um banco de dados. A própria pessoa, além de representar seus dados vai se salvar no banco? Isso é uma péssima prática.

[03:41] Você tem muitas responsabilidades, você tem muitos atributos, você tem muita coisa dentro da mesma classe. Essa classe não está coesa. Essa classe não faz sentido para o modelo dela, ela está fazendo muito mais do que deveria.

[03:57] E isso acarreta em problemas que vamos discutir nesse treinamento, mas basicamente isso acarreta em classes difíceis de manter. Em vários momentos, por vários motivos diferentes, eu vou precisar vir aqui nessa classe Pessoa e editar o código dela.

[04:14] E sempre: editar um código que já existe pode gerar bugs. Você provavelmente já sabe disso, mas quando mexemos em código que já existe, podemos estar criando um bug novo, podemos estar quebrando uma funcionalidade que já funciona, fazer deixar de funcionar.

[04:29] Vamos também conversar sobre isso. Como evitar mexer em código que já está funcionando. Se eu precisar implementar alguma coisa nova, eu crio um código novo.

[04:38] Isso é o que é chamado de Coesão e vamos ver mais para frente como resolver um problema de uma classe que não é coesa. Agora, que já entendemos esse conceito de Coesão, já definimos bem o que é isso, vamos continuar conversando sobre outros problemas, outros conceitos que esbarramos durante o desenvolvimento do Orientação a Objetos.

@@04
Definição de uma classe coesa

No último vídeo, aprendemos sobre o conceito de coesão na programação orientada a objetos.
Qual a melhor definição de uma classe coesa?

Uma classe que executa bem as suas tarefas, independente de quantas
 
Alternativa errada! Uma classe coesa não pode executar várias tarefas.
Alternativa correta
Uma classe que executa bem a sua única tarefa, de forma concisa
 
Alternativa correta! Cada classe deve ser responsável por apenas uma coisa, e deve executar esta tarefa muito bem.
Alternativa correta
Uma classe que executa tudo muito bem

@@05
Encapsulamento

[00:00] Olá, pessoal. Bem-vindos de volta. No último vídeo eu falei no desenvolvimento da Orientação a Objetos, quem dera nós estivéssemos desenvolvendo esse paradigma, eu quis dizer, durante o desenvolvimento utilizando a Orientação a Objetos. Bom, continuando, o próximo conceito que eu quero falar com vocês é algo que vocês com certeza já ouviram falar, que é um daqueles pilares que eu citei, que é o encapsulamento.
[00:24] E o que é o encapsulamento? É ter as propriedades privadas e os métodos públicos, criar getter e setter. Se você tem essa visão, de que isso é encapsulamento, tenho uma má notícia para você. Não é isso. Encapsulamento não é só ter propriedades privadas e métodos públicos, até porque, se eu tiver todos os métodos públicos, eu estou fazendo exatamente o contrário do encapsulamento.

[00:49] Para entendermos bem o conceito do encapsulamento, vou dar um exemplo da vida real. Quando você compra um aparelho de DVD, existe lá um botão, independentemente do modelo do aparelho, pelo menos no controle com certeza tem, um botão de um triângulo deitado, um triângulo para o lado, e você sabe que esse triângulo representa o play. Se você pegar um videocassete, que é um aparelho mais antigo, e você encontrar esse botão, essa imagem, você vai saber que esse botão dá o play, que esse botão executa a reprodução.

[01:21] Isso é o encapsulamento. Por baixo dos panos, o que está acontecendo, como cada aparelho funciona, não importa para nós. O que importa é a ação que está disponibilizada para nós. Só que o aparelho, os desenvolvedores do aparelho encapsularam a ação de dar play através de um botão, simplificaram essa ação e disponibilizaram uma interface para nós, que é um botão.

[01:46] Isso, traduzindo em código, pode ser visto de forma semelhante aqui. Nós temos um assistidor, de curso, de vídeo da AluraMais, independente do que for, e se eu tenho um curso, eu preciso assistir de uma forma, tenho que pegar todos os vídeos e depois ir marcando um por um como assistido. Se for um vídeo da AluraMais, eu simplesmente marco ele e digo que eu quero assistir.

[02:13] Nós temos implementações diferentes, isso não está muito bem encapsulado, está bem claro aqui que eu preciso conhecer a implementação da classe Curso para saber como eu que eu marco o curso como assistido. Isso não é legal, e vamos ver como melhorar isso depois.

[02:27] Mas agora, outro exemplo também de algo que não está bem encapsulado é como recuperar a pontuação de cada um. Eu conheço a implementação de curso e sei aqui dentro da classe CalculadorPontuacao que um curso vale 100 pontos quando eu finalizo ele. Já um vídeo da Alura mais vale a quantidade de minutos que ela tem, multiplicado por dois. Então eu conheço a implementação, as regras de outras classes, eu estou ferindo aqui o encapsulamento.

[02:57] Já um exemplo do encapsulamento acontecendo é esse método: minutos de duração. Eu preciso saber quantos minutos de duração existe aqui nesse conteúdo. Que no caso eu sei que é um vídeo da Alura mais. Então eu preciso conhecer, saber quantos minutos de duração.

[03:11]Mas eu não quero saber como ele calcula esses minutos de duração, se ele pega um time-stamp e depois compara com outro time-stamp e me retorna a diferença, se ele faz o cálculo utilizando o relógio do sistema ou não, eu não quero saber. Aqui, a implementação está sendo feita através de uma classe DateInterval que é uma classe do PHP, mas tudo que ela me retorna é os minutos. Então, aqui temos um exemplo bem simples de como o encapsulamento pode nos ajudar.

[03:41] Se alguma pessoa nova vier para nossa equipe e precisar pegar os minutos de duração, ela não precisa conhecer a implementação da classe DateInterval, nem da classe Video, ela só vai pegar os minutos de duração. Ela sabe que isso retorna um inteiro para ela que representa os minutos.

[03:59] Com isso, com o encapsulamento, facilitamos a migração de funcionalidades, como, por exemplo, se eu quiser mudar de um vídeo cassete para um aparelho de DVD, ou de um aparelho de DVD para um aparelho de Blu-Ray, eu sempre vou ter o botão de play para começar a reproduzir o conteúdo.

[04:15] Aqui, se eu quiser marcar como assistido algum conteúdo, eu quero poder marcar como assistido qualquer conteúdo, eu quero encapsular esse comportamento dentro das minhas classes para que isso fique, para que a implementação interna de cada um fique por responsabilidade delas, eu só quero executar uma ação.

[04:35] O encapsulamento nos ajuda com isso. As classes que fornecem o encapsulamento de forma correta vão facilitar seu uso. Ou seja, outras pessoas que desenvolvem e vão utilizar essa classe, vão utilizar ela com mais facilidade e essa é a vantagem do encapsulamento.

[04:53] Agora que já entendemos o que é e em que pode nos ajudar a coesão, e também o encapsulamento, falta mais um conceito que eu quero passar com vocês antes de colocarmos a mão na massa e escrever código em si. Eu sei que essa parte teórica não é tão emocionante, tão divertida, mas é muito importante para darmos continuação a esse curso. Te espero no próximo vídeo para falarmos sobre acoplamento.

@@06
Protegendo o código

Começamos a entender agora que encapsulamento é uma forma de manter os objetos das nossas classes protegidos, fornecendo apenas o que é estritamente necessário para o mundo exterior.
Quais das seguintes alternativas estão corretas?

Getters e setters por si só não fornecem nenhum tipo de encapsulamento
 
Alternativa correta! O fato de criar getters e setters para tudo, na verdade, quebra o encapsulamento da nossa classe.
Alternativa correta
Encapsulamento ajuda no uso correto dos objetos
 
Alternativa correta! Ao encapsular o acesso a determinados dados, liberando acesso apenas ao necessário, os objetos da nossa classe se tornam mais fáceis de serem utilizados.
Alternativa correta
Getters e setters fornecem encapsulamento da melhor forma possível

@@07
Acoplamento

[00:00] Olá, pessoal. Bem-vindos de volta. Agora eu queria conversar com vocês sobre Acoplamento. Primeiro, o que é Acoplamento? Acoplamento basicamente significa, é quando uma classe depende de outra para seu funcionamento. Significa que uma classe conhece outra para que ela possa funcionar.
[00:20] Dando uma analisada bem rápida aqui em algumas das nossas classes, temos o CalculadorPontuacao que está acoplada com nossa classe Curso, a classe AluraMais.

[00:31] Esse calculador de pontuação precisa conhecer essas duas classes, ele é acoplado a essas duas classes. Se uma dessas duas mudar a sua implementação, talvez esse calculador de pontuação também precise mudar alguma coisa. Aqui na nossa classe Assistidor temos o acoplamento também com a classe Curso e a classe AluraMais.

[00:54] Se eu mudar a forma de marcar um curso como assistido, como por exemplo, se eu não precisar mais só assistir os vídeos, se para que meu curso possa ser marcado como assistido ele precisar marcar os exercícios como realizados também, eu vou ter que mudar essa minha classe. Existe esse acoplamento.

[01:13] E você pode estar se perguntando também: então parece que Acoplamento é ruim, mas você disse que cada classe tem que ser responsável por uma coisa só. Então necessariamente uma classe vai precisar de outra em alguns momentos, como funciona isso?

[01:27] Então, o acoplamento não é algo necessariamente ruim. Em determinados momentos, o Acoplamento é necessário, só que é interessante que o acoplamento, que se dependa de coisas mais estáveis, de coisas que não necessariamente vão mudar o tempo todo.

[01:46] Aqui estamos dependendo de uma classe concreta, de uma implementação que pode mudar a qualquer momento, e isso causa uma instabilidade no nosso código. Inclusive, existe uma ferramenta bem antiga do PHP chamada de “pdepend”, ou PHP depend que calcula, faz um cálculo de dependências entre as nossas classes e gera alguns gráficos, e um desses gráficos eu mostro aqui para vocês, eu dei um zoom.

Plano cartesiano de eixo x: Abstraction, variando de 0.0 a 1.0, e eixo y: Instability, variando de 0.0 a 1.0. Ambos com intervalos de 0.1. Há uma reta diagonal que passa pelos pontos: (0.0, 1.0); (0.1, 0.9); (0.2, 0.8);  (0.3, 0.7); (0.4, 0.6); (0.5, 0.5); (0.6, 0.4); (0.7, 0.3);  (0.8, 0.2); (0.9, 0.1); e (1.0, 0.0). No ponto (0.0, 1.0), há uma bola verde pequena, e, ao lado, em letras pretas e destaque azul, está escrito "Service". No ponto (0.0, 0.5), há uma bola laranja de tamanho médio, e, ao lado está escrito "Model".

[02:16] Aqui temos um pacote de Service, temos o assistidor e o calculador de pontuação e temos também o pacote de Model que tem o vídeo, o AluraMais e o curso.

[02:24] O nosso pacote de Model está fora da nossa linha de ideal. Já o nosso pacote de Service, o que acontece, ele não tem abstração nenhuma, esse gráfico é de abstração e instabilidade, não vou entrar em detalhes sobre esse gráfico, mas basicamente o que isso quer dizer é:

[02:40] o nosso Service não tem abstração nenhuma, só tem classes concretas lá, mas ninguém depende de nenhuma classe do Service, então tudo bem. Teoricamente tudo bem, não tem problema ele só ter classes concretas.

[02:53] Já a Model existem classes que dependem de classes aqui da Model, como por exemplo algumas classes do nosso Service. Então precisamos de algumas abstrações, porque essas abstrações tornam o pacote, o módulo mais estável.

[03:11] Uma abstração é menos propensa a modificações e vamos entender isso melhor no decorrer do curso, mas o que queremos alcançar com esse treinamento na hora de reduzir o Acoplamento não desejável, vamos chamar assim, é fazer com que esse pacote da Model se mova um pouco mais para perto da linha.

[03:32] Raramente vamos conseguir manter todos os nossos pacotes aqui nesse linha, mas pelo menos o mais próximo possível, então eu quero atingir pelo menos 0.3 de abstração até o final do treinamento, pelo menos esse resultado, onde a Model está perto da linha do ideal, ou seja, nós temos mais abstrações. Então, é com isso que vamos trabalhar a partir de agora nesse treinamento modificando o código já existente desse projeto.

Plano cartesiano de eixo x: Abstraction, variando de 0.0 a 1.0, e eixo y: Instability, variando de 0.0 a 1.0. Ambos com intervalos de 0.1. Há uma reta diagonal que passa pelos pontos: (0.0, 1.0); (0.1, 0.9); (0.2, 0.8);  (0.3, 0.7); (0.4, 0.6); (0.5, 0.5); (0.6, 0.4); (0.7, 0.3);  (0.8, 0.2); (0.9, 0.1); e (1.0, 0.0). No ponto (0.0, 1.0), há uma bola verde pequena, e, ao lado, está escrito "Service". No ponto (0.3, 0.5), há uma bola laranja de tamanho médio, e, ao lado está escrito "Model".

[03:56] Você provavelmente já baixou esse projeto, se não baixou ainda volta lá no primeiro exercício e baixa o código desse projeto e a partir de agora, a partir do próximo capítulo, vamos começar a fazer algumas modificações aqui para melhorar o código.

[04:10] Aplicando alguns conceitos que vamos começar a conversar também para atingir uma maior maturidade no nosso sistema, para que ele seja mais fácil de manter, para que seja menos propenso a inserção de bugs. Te espero no próximo capítulo onde finalmente vamos começar a colocar a mão na massa.

@@08
Dependências no código

Ao falar de acoplamento no último vídeo, vimos que é comum que classes dependam de outras para executar determinadas tarefas.
O que é correto afirmar sobre acoplamento?

É impossível criar um bom sistema sem nenhum tipo de acoplamento
 
Alternativa correta! É fato que, se estamos organizando o nosso código, seguindo as recomendações da orientação a objetos, algum acoplamento acontecerá. Algumas classes precisarão de outras, para que não tenham muitas responsabilidades. Cabe a nós medir quando faz sentido adicionar tal acoplamento com as dependências e como depender do que é seguro, ao invés de classes concretas. Falaremos mais sobre isso neste treinamento.
Alternativa correta
Acoplamento é uma técnica de segurança
 
Alternativa errada! Este treinamento trata apenas de práticas de orientação a objetos.
Alternativa correta
Acoplamento é sempre ruim. Não devemos ter nenhum tipo de dependência no nosso código

@@09
Consolidando o seu conhecimento

Chegou a hora de você pôr em prática o que foi visto na aula. Para isso, execute os passos listados abaixo.
1) Caso você ainda não tenha feito o download do projeto inicial deste treinamento, baixe-o aqui.

https://caelum-online-public.s3.amazonaws.com/1315-php-solid/01/aula1-projeto-inicial.zip

Continue com os seus estudos, e se houver dúvidas, não hesite em recorrer ao nosso fórum!

@@10
O que aprendemos?

Nesta aula, aprendemos:
Coesão
Uma classe coesa faz bem uma única coisa
Classes coesas não devem ter várias responsabilidades
Encapsulamento
Getters e setters não são formas eficientes de aplicar encapsulamento
É interessante fornecer acesso apenas ao que é necessário em nossas classes
O encapsulamento torna o uso das nossas classes mais fácil e intuitivo
Acoplamento
Acoplamento é a dependência entre classes
Acoplamento nem sempre é ruim, e que é impossível criar um sistema sem nenhum acoplamento
Devemos controlar o nível de acoplamento na nossa aplicação (falaremos mais sobre isso)