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

#### 25/02/2024

@02-Melhorando a coesão

@@01
Extraindo o feedback

[00:00] Olá, pessoal. Bem-vindos a mais um capítulo desse nosso treinamento de SOLID e boas práticas de Orientação a Objetos, e já demos uma passada bem rápida em alguns conceitos muito importantes da Orientação a Objetos e vimos que nosso projeto, embora tenha parte boas, não é de todo ruim, tem alguns pontos que merecem uma certa atenção, merecem melhorias.
[00:22] Primeiro, vamos pegar aqui nossa classe Curso e ver algumas regras que ela tem. Ela tem o meu construtor, ela define o nome e inicializa aqui dois arrays. Recuperar vídeos é só um getter. Adicionar vídeo já tem alguma regra.

[00:40] Essa regra indica que os vídeos para fazerem partes de um curso precisam ter pelo menos 3 minutos, isso é uma regra do curso, faz sentido. Agora, receber feedback. Eu estou recebendo uma nota e um possível depoimento que não é obrigatório.

[00:59] Mas, se a nota for menor que 9, e o depoimento estiver vazio eu vou lançar um erro, ou seja, com uma nota menor que 9 o depoimento é obrigatório para eu receber feedback, e isso é uma regra, como eu estou dizendo, de um feedback. Isso é uma validação de feedback, não é uma validação de curso.

[01:18] Um curso continua válido independente de qual feedback ele recebe. Um curso tem suas regras intactas, independente do feedback que ele recebe. Agora, o feedback para ser válido ele tem essas regras. Então aqui, isso é um forte candidato para estar em outro lugar e não dentro da classe Curso. Por isso, vamos criar agora uma classe chamada feedback. Vou criar aqui uma nova classe, feedback.

[01:46] Vou remover o comentário /* Created by PhpStorm. …/.

[01:50] Aqui no Contrutor e no PhpStorm eu posso digitar underline underline, começar a digitar Construtor, quando eu teclo “enter” ele já cria para mim eu posso dizer que recebo uma nota e um depoimento opcional. Isso aqui vai caracterizar o nosso feedback.

[02:08] Vou apertar “Alt + enter” e vir em “Initialize Fields”, seleciono os dois, clico em “OK” e ele já inicializa aqui para nós. Vou colocar tudo isso em uma linha só.

[02:21] Se em algum momento desse treinamento você já estiver utilizando o PHP 7.4 você pode remover os comentários /** @var int */ e /** @var string|null */, porque o PHP 7.4 já permite essa sintaxe, já permite as propriedades tipadas. Mas como eu ainda estou utilizando o 7.3 eu ainda não posso utilizar essa feature.

[02:39] Tenho aqui, agora, um feedback já bem definido. Agora eu já tenho a validação na classe correta. Se eu precisar em algum lugar de pegar nota ou pegar depoimento, eu crio aqui um getDepoimento, um getNota, e aí eu consigo utilizar, mas a regra de validação de um feedback, a responsabilidade de garantir que um feedback está válido ou não vai ficar aqui.

[03:04] Mas você ainda não implementou validação nenhuma, então vamos mover if ($nota < 9 && empty($depoimento) ) {throw new \ DomainException (message: ‘Depoimento Obrigatório’);} de Curso para Feedback. Se a minha nota for menor do que 9 e eu não tiver um depoimento: erro. O depoimento é obrigatório. Eu nem consigo criar esse feedback, caso contrário.

[03:22] Com isso, já temos a regra de validação implementada na classe correta, então não preciso mais receber int $nota, $string $depoimento separadamente nem fazer nenhuma validação, eu posso simplesmente receberFeedback, e aqui na nossa rede de feedback s eu adiciono esse $feedback.

[03:40] Agora, olha só como a nossa classe Curso está bem mais enxuta e não tem a responsabilidade da validação de um feedback . Se em algum momento a regra de Feedback mudar, por exemplo, agora o depoimento só é obrigatório se a nota for menor que 7, isso não vai afetar em nada a nossa classe Curso.

[03:58] Ela vai continuar funcionando perfeitamente sem nenhum problema. Com isso, eu reduzo esses problemas de se uma regra mudar, quais classes têm que ser alteradas, se outra classe precisar receber um feedback , eu já tenho a regra implementada, eu não preciso duplicar esse código.

[04:14] Então, esse conceito, esse princípio de manter cada classe com a sua responsabilidade tem um nome, e eu vou falar mais sobre esse princípio no próximo vídeo.

@@02
Extraindo classe

No último vídeo, executamos uma refatoração conhecida como Extrair classe.
O que é uma refatoração?

É uma alteração no código para corrigir bugs
 
Alternativa correta
É uma alteração no código que visa melhorar sua clareza e entendimento
 
Alternativa correta! Refatorações servem para melhorar o design do código, e não o funcionamento do sistema. Uma refatoração não deve influenciar em nada no funcionamento.
Alternativa correta
É uma alteração no código que visa a melhoria de performance

@@03
Single Responsibility Principle

[00:00] Olá, pessoal. Sejam muito bem-vindos de volta, e o que implementamos no último vídeo, aquela refatoração que fizemos tem um nome, e esse nome é Single Responsibility Principle, ou Princípio de Responsabilidade Única. Aqui tem uma imagem engraçada de um canivete suiço com esteróides e uma legenda.
[00:22] Só porque você pode, só porque você consegue, não significa que você deve.

[00:27] Trazendo isso para código, trazendo isso para desenvolvimento de software, só porque você pode criar todo o seu programa em um único arquivo, não significa que você deve fazer isso. Imagina dar manutenção para isso.

[00:41] Você provavelmente já pegou um arquivo gigante e precisava mudar uma linha e ficou horas procurando essa linha. Esse é o problema que o Princípio da Responsabilidade Única tenta resolver, tenta mitigar utilizando o Princípio da Coesão.

[00:59] Esse princípio, esse nome dado ao Princípio da Coesão e Responsabilidade Única foi dado por uma das grandes mentes de desenvolvimento de software, Robert C. Martin, o tio Bobby, o uncle Bobby, como é mais conhecido. A frase utilizada por ele para definir esse princípio é que uma classe deve ter um, e apenas um, motivo para mudar, para ser reescrita.

[01:25] Isso quer dizer que, por exemplo, uma classe que monta um relatório e exibe ele na tela tem dois motivos para mudar. Como assim, dois? Primeiro, se os dados que vão ser exibidos mudarem, essa classe vai precisar mudar, provavelmente.

[01:41] E se o formato desse relatório mudar, ou seja, se eu precisar mudar de CSV para Json, essa classe também vai precisar mudar. Com isso, começamos a pensar nos motivos para uma classe mudar e com isso ir separando em classes menores.

[01:56] Voltando para o nosso projeto, nossa classe Curso tinha mais de uma razão para mudar. Primeiro, se a regra de quantos minutos um vídeo pode ter mudasse e se a regra de qual nota, a partir de qual nota o depoimento é obrigatório ou não mudasse. Agora, ela só tem um motivo para mudar, se a nossa regra do curso mudar e eu ia precisar mexer nessa classe.

[02:26] Caso contrário, se a regra para feedback mudar não importa mais para essa classe, ela não vai ser alterada. E a nossa classe Feedback tenha também só um motivo para mudar, se a regra referente ao feedback , se a regra referente ao depoimento ser obrigatório ou não mudar, e aí eu vou precisar mudar essa classe.

[02:43] Com isso, acatamos, vamos dizer assim, o princípio da responsabilidade única com uma simples implementação, com uma simples refatoração e as vantagens são imensas.

[02:55] Agora que já definimos muito bem isso, o que é o Princípio da Responsabilidade Única e como aplicar na prática, vou te dar outro exemplo, muito famoso, onde eu tenho a classe Pessoa, ou a classe Post, de blog, e essa classe, além de representar seus dados, ela também sabe se salvar no banco de dados.

[03:18] E esse padrão chamado Active Record se foi implementado dessa mesma forma que eu descrevi, onde essa mesma classe representa seus dados e salva seus dados, ela está violando o Princípio de Responsabilidade Única.

[03:32] Se os meus dados mudarem, eu preciso alterar essa classe. Se a minha forma de persistência mudar, se eu mudar o banco de dados, se minha tabela for alterada, eu também preciso mudar essa classe. Isso aumenta, como eu comentei no primeiro capítulo, a possibilidade de inserir novos bugs, alterando o código que já funcionava anteriormente.

[03:50] Tendo entendido esse conceito, tendo pegado os exemplos, está na hora de pensarmos como estender o nosso projeto, por exemplo, eu tenho aqui um CalculadorPontuacao, e eu tenho a pontuação por um curso, a pontuação para o Alura+. Agora imagina se eu tiver um novo modelo de conteúdo, eu tenho que adicionar aqui um outro else if.

[04:11] E se eu tiver outro conteúdo, outro else if. Então essa classe CalculadoraPontuacao nunca vai parar de crescer, então vamos conversar sobre alguma forma de modificar isso, de garantir que ela esteja coesa e seja extensível no próximo capítulo.

@@04
Definição de SRP

Ao extrair uma nova classe, vimos que agora temos classes com menos responsabilidades, o que facilita na manutenção. Esse é o conceito de Single Responsibility Principle.
Qual é a definição mais formal do princípio de responsabilidade única?

Uma classe deve fazer bem tudo que se propõe a fazer
 
Alternativa correta
Uma classe (ou módulo, função, etc) deve ter um e apenas um motivo para mudar
 
Alternativa correta! Esta é uma das definições mais conhecidas do SRP (Single Responsibility Principle).
Alternativa correta
Uma classe deve ter apenas uma funcionalidade e não deve servir para mais nada

@@05
Consolidando o seu conhecimento

Chegou a hora de você pôr em prática o que foi visto na aula. Para isso, execute os passos listados abaixo.
1) No projeto baixado na aula anterior, crie um novo arquivo na pasta Model, chamado Feedback.php, com o seguinte conteúdo:

<?php

namespace Alura\Solid\Model;

class Feedback
{
    private $nota;
    private $depoimento;

    public function __construct(int $nota, ?string $depoimento)
    {
        if ($nota < 9 && empty($depoimento)) {
            throw new \DomainException('Depoimento obrigatório');
        }

        $this->nota = $nota;
        $this->depoimento = $depoimento;
    }

    public function recuperarNota(): int
    {
        return $this->nota;
    }

    public function recuperarDepoimento(): ?string
    {
        return $this->depoimento;
    }
}COPIAR CÓDIGO
2) Na classe Curso, edite o método receberFeedback, para que ele não receba mais os dois parâmetros originais, e sim receba apenas um Feedback:

public function receberFeedback(Feedback $feedback): void
{
    $this->feedbacks[] = $feedback;
}COPIAR CÓDIGO

Continue com os seus estudos, e se houver dúvidas, não hesite em recorrer ao nosso fórum!

@@06
O que aprendemos?

Nesta aula, aprendemos:
Que classes/métodos/funções/módulos devem ter uma única responsabilidade bem definida
Que, segundo o Princípio de Responsabilidade Única (SRP), uma classe deve ter um e apenas um motivo para ser alterada
Como realizar uma refatoração no nosso sistema
Como extrair uma classe

#### 26/02/2024

@03-Trabalhando no acoplamento

@@01
Projeto da aula anterior

Caso queira, você pode baixar aqui o projeto do curso no ponto em que paramos na aula anterior.

https://caelum-online-public.s3.amazonaws.com/1315-php-solid/02/aula-2-completa.zip

@@02
Extraindo a pontuação

[00:00] Olá, pessoal. Bem-vindos de volta mais um capítulo desse treinamento de SOLID. Só para recapitular o que fizemos no último capítulo: modificamos nossa classe Curso para que ela passasse a receberFeedback como objeto já montado e todas suas regras já estivessem previamente verificados, previamente definidas. Nessa classe Feedback só teria um __construtct, onde a lógica para garantir que esse feedback é válido seria aplicada.
[00:27] Implementei aqui, por baixo dos panos, dois métodos de getters, dois métodos acessores, vamos chamar assim, o recuperarNota e o recuperarDepoimento. Que só retornam os valores da nota e do depoimento.

[00:40] Agora, o que eu quero implementar é, eu tenho aqui é um CalculadorPontuacao, e como eu falei essa classe pode crescer infinitamente, conforme eu tenho novos conteúdos na plataforma eu vou precisar ficar modificando essa classe aqui e isso não é bom, sabemos que não.

[00:27] Vamos pensar em uma forma de unificar o que eu estou chamando aqui de $conteúdo. Um conteúdo que pode ser pontuável, vamos dizer assim, que pode ter uma pontuação e definir essa pontuação em cada um dos conteúdos.

[01:10] A primeira coisa que eu vou fazer aqui é definir esse conteúdo unificado, esse pontuável, se há algo que pode ser implementado por outras classes, é uma interface. Então eu vou criar aqui uma nova interface “Pontuavel”.

[01:32] Criada essa interface, deixa eu apagar o comentário /** Created by PhpStorm. …*/, criada a interface, eu vou definir um único método public function, que é recuperaPontuação, e retorna um inteiro. Pode ser ou recuperaPontuação ou somente Pontuação, isso não importa muito, como você preferir.

[01:55] Agora que temos interface “Pontuavel” definida, vamos ver quais conteúdos são pontuáveis aqui. Eu tenho Curso e AluraMais ,por enquanto. Aqui no Curso eu vou implementar a interface Pontuável, “Alt + enter” no PhpStorm e ele já adiciona o método lá no final para mim, e aqui, um curso tem uma pontuação fixa. Todos os cursos têm uma pontuação de 100.

[02:21] Agora, o nosso AluraMais, implementa “Pontuável” “Alt+ enter”, já adicionou embaixo do código. Aqui é um pouco diferente, em um vídeo da AluraMais, a pontuação $this -> minutosDeDuracao () * 2. Tenho aqui a implementação. E agora, eu posso muito bem aqui no meu CalculadorPontuacao receber um conteúdo Pontuável, independente de qual classe for seja Curso, seja AluraMais, qualquer coisa, eu só return $conteudo->recuperaPontucao( ).

[03:00] Aqui no lugar de recupera deveria ser recuperar. Vou dar um “Shift + F6” para o PhpStorm renomear esse método para mim. Recuperar. Repara que ele já modifica em todas as classes que o implementam e já modifica aqui no return também.

[03:19 Isso só para manter os nossos métodos como verbos no infinitivo. É uma boa prática, mas não vou entrar muito em detalhes agora, só um preciosismo da minha parte, vamos dizer assim.

[03:30] Agora, olha só o nosso métodorecuperarPontucao simplesmente delega a chamada para o próprio $conteúdo. Então, preciso dessa classe ainda? Não. Agora não preciso dela mais, ela se fez desnecessária conforme refaturamos o nosso projeto.

[03:47] Agora eu sei que em qualquer lugar que precisar de uma pontuação eu vou precisar de um objeto do tipo “Pontuavel”, seja ele qual for. E aí se futuramente eu tiver, por exemplo, uma classe AluraLive, basta que eu implemente a interface Pontuável e aqui dentro recupero a pontuação baseado nas regras da pontuação da AluraLive,

[04:12] e o nosso CalculadorPontuacao, ou a classe que for que estiver dependendo de algum conteúdo pontuável não vai precisar ser alteráda. Então, com isso, a conseguimos estender o nosso projeto, sem precisar editar código já existente, e isso obviamente tem um nome é um princípio já conhecido que vamos conversar mais no próximo vídeo.

@@03
Muitos Ifs

Encontramos nesta aula um problema na classe CalculadorPontuacao.
O que pudemos identificar sobre o problema desta classe?

Esta classe continha muitas responsabilidades
 
Alternativa correta
Esta classe poderia crescer para sempre
 
Alternativa correta! Enquanto novas formas de conteúdo pontuável fossem criadas, novas condições deveriam ser adicionadas a esta classe, fazendo-a crescer interminavelmente.
Alternativa correta
Esta classe violava a lei de Demeter

@@04
Open Closed Principle

[00:00] Olá, pessoal. Bem-vindos de volta, e no último vídeo deixamos, fizemos com que nosso projeto nosso módulo de pontuação fosse extensível. Ou seja, eu posso agora ter outros conteúdos que sejam pontuáveis que implementem aquela nossa interface “Pontuavel”, mas agora as nossas classes estão fechadas para modificação.
[00:23] Não precisamos mais modificar alguma classe concreta para estender essa funcionalidade, para adicionar um conteúdo novo e isso é exatamente o que o princípio Open/Closed Principle ou Princípio de Aberto/Fechado quer dizer. Aqui temos uma imagem interessante e uma frase.

[00:43] Open chest surgery is not needed when putting a coat , uma cirurgia de peito aberto não é necessária quando você vai colocar um casaco. Você não precisa expor toda a funcionalidade do seu projeto para uma única ação.

[00:57] Não precisamos expor como a pontuação é implementada, como a pontuação é recuperada simplesmente para pegar pontuação, não precisamos de tanta complicação para uma única implementação simples.

[01:11] Esse princípio de uma forma um pouco mais formalmente explicada, diz que entidades de software, sejam classes, módulos, funções, qualquer coisa, conjunto de classes, devem ser abertas para expansão, porém fechadas para modificação.

[01:24] Bertrand Mayer, que é originalmente citado como autor desse princípio, diz que uma classe, um módulo, um conjunto de classes é dito como aberto quando é possível estender, ou seja, no nosso caso conseguimos criar uma nova classe que implemente Pontuavel e o nosso CalculadorPontuacao, por exemplo, continua utilizando sem modificação nenhuma, sem problema nenhum.

[01:50] Só que esse módulo, classe, conjunto de classes é dito como fechado se ele já pode ser utilizado em outras classes, ou seja, a sua interface foi bem definida, os métodos, a forma de acessar foi bem definida a ponto de ser acessível para outros módulos e outras classes.

[02:08] E justamente isso que a nossa interface “Pontuavel” está fazendo. Definimos uma interface, um método, assinatura de um método, que vai poder ser utilizado em outras classes.

[02:20] Isso faz com que o nosso projeto seja extensível, que consigamos criar novas funcionalidades, novos conteúdos com pontuação, sem que eu precise ficar modificando uma classe adicionando if e isso, como já comentamos, antes pode gerar erros pode gerar bugs, dependendo do nosso projeto.

[02:40] Agora, já vimos dois princípios muito famosos e conhecidos: o Princípio de Single Responsibility ou Princípio de Responsabilidade Única, e agora o Open/Closed Principle, que é o Princípio de Aberto/Fechado. Está na hora de ver um princípio bem interessante e um pouco mais complexo na sua definição formal, mas que a vamos ver que é bem simples quando colocado na prática. Te espero no próximo capítulo para falar sobre isso.

@@05
Garantindo que o sistema seja extensível

O Open Closed Principle, embora complexo em sua definição, é muito útil e pertinente.
O que podemos fazer para garantir que nosso sistema seja extensível da forma correta?

Manter poucas classes
 
Alternativa correta
Garantir que cada ação/responsabilidade esteja na classe correta
 
Alternativa correta! Esta é uma das formas de garantir que o sistema seja extensível.
Alternativa correta
Ter certeza de que escolhemos a melhor tecnologia/linguagem de programação

06
Consolidando o seu conhecimento

Chegou a hora de você pôr em prática o que foi visto na aula. Para isso, execute os passos listados abaixo.
1) Crie um arquivo chamado Pontuavel.php, na pasta Model, com o seguinte conteúdo:

<?php

namespace Alura\Solid\Model;

interface Pontuavel
{
    public function recuperarPontuacao(): int;
}COPIAR CÓDIGO
2) Edite a classe AluraMais para que ela implemente a interface recém-criada, da seguinte forma:

class AluraMais extends Video implements PontuavelCOPIAR CÓDIGO
3) Implemente o método necessário na classe AluraMais:

public function recuperarPontuacao(): int
{
    return $this->minutosDeDuracao() * 2;
}COPIAR CÓDIGO
4) Edite a classe Curso para que ela também implemente a interface Pontuavel:

<?php

namespace Alura\Solid\Model;

class Curso implements Pontuavel
{
    // ...

    public function recuperarPontuacao(): int
    {
        return 100;
    }
}COPIAR CÓDIGO
5) Agora, edite a classe CalculadorPontuacao, para que ela dependa apenas desta interface:

<?php

namespace Alura\Solid\Service;

use Alura\Solid\Model\Pontuavel;

class CalculadorPontuacao
{
    public function recuperarPontuacao(Pontuavel $conteudo)
    {
        return $conteudo->recuperarPontuacao();
    }
}

@@07
O que aprendemos?

Nesta aula, aprendemos:
Que cada classe deve conhecer e ser responsável por suas próprias regras de negócio
Que o princípio Aberto/Fechado (OCP) diz que um sistema deve ser aberto para a extensão, mas fechado para a modificação
Isso significa que devemos poder criar novas funcionalidades e estender o sistema sem precisar modificar muitas classes já existentes
Uma classe que tende a crescer "para sempre" é uma forte candidata a sofrer alguma espécie de refatoração

#### 26/02/2024

@04-Quebra de confiança

@@01
Projeto da aula anterior

Caso queira, você pode baixar aqui o projeto do curso no ponto em que paramos na aula anterior.

https://caelum-online-public.s3.amazonaws.com/1315-php-solid/03/aula-3-completa.zip

@@02
Corrigindo URLs

[00:00] Olá, pessoal. Sejam muito bem-vindos de volta a mais um capítulo desse treinamento de SOLID. Já vimos aqui o Princípio de Responsabilidade Única, onde um módulo, uma construção do software, deve ter um e apenas um motivo para mudar.
[00:14] Vimos o Princípio de Aberto/Fechado, onde o módulo, um conjunto de classes, deve ser aberto para extensão, mas fechado para modificação. Agora eu quero conversar com vocês sobre uma modificação muito simples, mas para exemplificar um conceito bem complexo um princípio bem complexo.

[00:33] Dando uma olhada aqui na nossa classe AluraMais, vemos que ela extends Video, porque a AluraMais, o conteúdo AluraMais, nada mais é que um vídeo que possui uma categoria. Isso eu estou dizendo aqui no modelo que estamos criando, o nosso modelo fictício da Alura.

[00:49] Não estou falando que de verdade é só isso, mas no nosso modelo aqui um conteúdo da AluraMais nada mais é do que um vídeo que possui uma categoria. só que existe uma diferença na hora de recuperarUrl.

[01:05] A URL da AluraMais possui o conteúdo da sua categoria, na verdade, a implementação está até errada, era para depois da categoria ter o nome também, mas vamos focar aqui em outro detalhe. Na AluraMais ,na URL, temos a categoria. Agora, no vídeo temos http_build_query ([‘nome’ => $this->nome]);. São modelos diferentes de URL, só que repara que aqui no Video eu estou devolvendo uma URL válida http://videos.alura.com.br , um domínio que eu coloquei aqui aleatoriamente.

[01:47] Agora, aqui na “AluraMais”, estamos devolvendo uma string, então assinatura do método está correto eu não estou quebrando o contrato com minha classe base, mas eu não estou devolvendo uma URL eu estou devolvendo uma string qualquer. Se a categoria fosse "boas práticas", por exemplo, eu estaria devolvendo’boas-práticas’.

[02:12] Então estamos meio que devolvendo algo que quem está utilizando, quem espera um vídeo se receber uma instância de AluraMais não vai saber resolver, não vai saber, por exemplo, mandar esse usuário para a URL correta, porque não temos uma URL aqui.

[02:28] É uma solução muito simples, eu posso simplesmente colocar a URL return ‘http://vídeos.alura.com.br’ na classe AluraMais, e com isso já resolvo essa quebra de contrato. Mas repara que essa quebra de contrato não está acontecendo realmente baseado na interface do nosso método, na assinatura do nosso método, está acontecendo baseado na implementação, ou seja, na forma como recuperarUrl funciona.

[02:55] Eu espero que um vídeo, ao chamar o método recuperarUrl de um vídeo, espero que ele me devolva uma URL contendo o caminho para o vídeo. E se a AluraMais é um vídeo, eu não posso quebrar essa confiança de quem depende de um vídeo, porque, deixa eu criar um novo arquivo temporário.

[03:18] Imagina que eu tenho aqui uma função qualquer, vamos dizer function (), e nessa function eu recebo um vídeo, um vídeo qualquer, e aqui eu quero fazer, eu quero redirecionar o usuário Location para a URL desse vídeo. Então, $vídeo->recuperarUrl() );. Esse código deve funcionar, porque eu sei que o recuperarUrl me retorna uma URL válida.

[03:58] Agora, se eu vier aqui, faltou o nome da função: function redirecionar. Se eu vier aqui e passar, se eu chamar redirecionar (new \Alura\Solid\Model\AluraMais (nome: ‘Open closed’, categoria ‘Boas praticas’, esse código, deixa eu quebrar a linha aqui para você ver melhor, esse código é totalmente funcional.

[04:33] De certa forma porque a AluraMais é do tipo vídeo, então a função function redirecionar vai receber sem problema, e recuperarUrl está retornando uma string, então aqui não vou receber erro nenhum. Só que o comportamento vai ser inesperado porque eu não estou devolvendo a URL completa .

[04:51] Então, se eu estiver executando esse código em outro domínio, eu posso ter um resultado inesperado, posso ter um redirecionamento para página errada, enfim eu estou proporcionando um comportamento inesperado na minha aplicação. Isso porque a implementação da minha classe filha, da minha classe derivada de Video.

[05:10] Ou seja, implementação de AluraMais não seguiu as mesmas diretrizes e quebrando isso, quebramos a confiança de quem está utilizando a nossa classe, podemos introduzir bugs. E isso obviamente, esse respeito à implementação, é um princípio que tem nome e vamos discutir ele com alguns exemplos que talvez deixem isso pouco mais claro no próximo vídeo.

@@03
Herança

Sabemos que, ao estender uma classe através da herança, devemos sempre respeitar os contratos (interfaces) de seus métodos.
Por que nossa classe AluraMais estava estendendo de forma indesejada um comportamento?

Porque não estava respeitando o tipo de retorno do método
 
Alternativa correta
Porque não estava respeitando o número e tipos dos argumentos
 
Alternativa correta
Embora a assinatura do método estivesse correta, o comportamento era diferente da classe base
 
Alternativa correta! O método da classe filha não recebia parâmetros e retornava uma string, assim como o método da classe base. O problema era no domínio. Enquanto a classe base devolvia uma URL, a classe filha devolvia uma string comum. Isso poderia levar a comportamentos indesejados e bugs.

@@04
Liskov Substitution Principle

00:00] Olá pessoal. Bem-vindos de volta, e no último vídeo fizemos uma implementação simples, porque eu disse que seria um princípio complexo. Esse princípio é chamado de Princípio de Substituição de Liskov.
[00:13] Liskov foi uma mulher, eu vou explicar um pouco melhor, mas ela disse que se, seja q(x) uma propriedade que se pode provar do objeto x do tipo T. Então q(y) também é possível provar para o objeto y do tipo S, sendo S um subtipo de T. Essa foi a frase dita pela Barbara Liskov.

[00:35] O que ela acabou de falar? Não entendi absolutamente nada. Pois é, eu também não entendi nada, mas tentando traduzir é basicamente isso: classes filhas nunca devem infringir definições de tipo ou de funcionalidade da classe pai, da classe base, e o exemplo dado aqui é:

[00:55] se parece um pato, se faz o barulho do pato, mas precisa de bateria, então talvez se tenha a abstração errada, e provavelmente isso não é um pato, isso é um brinquedo, é alguma coisa diferente, não é um pato propriamente dito.

[01:09] E o exemplo mais clássico que existe da violação do Princípio de Substituição de Liskov é as classes Retangulo e Quadrado. Eu tenho aqui uma classe Retangulo que tem altura e largura, criei aqui os setters para essas duas propriedades, e eu tenho um método que calculaArea, e a área de um retângulo é this->altura * $this ->largura.

[01:36] E geometricamente falando o que é um quadrado? Um quadrado é um retângulo que tem altura e largura iguais. Então posso dizer que ‘class Quadrado extends Retangulo` e quando eu defino a altura, eu defino também a largura com o mesmo valor. Se eu defino a largura eu defino também a altura com o mesmo valor.

[01:56] Parece tudo certo, então tenho aqui criei um new Retangulo () e defini altura defineAltura (5);defineLargura (10). Se calculaArea, eu espero que seja 50, e se eu executar este script eu tenho 50.

[02:12] Agora, se eu trocar new Retangulo para new Quadrado, o que acontece? Eu recebo 100 como retorno. Ou seja, eu estou quebrando aqui a definição da minha classe base, da minha classe mãe, minha classe pai, como você preferir chamar que diz que eu tenho duas propriedades com valores diferente.

[02:32] Eu estou quebrando esse contrato, e por mais que a assinatura dos métodos esteja correto, a implementação está causando um comportamento inesperado.

[02:40] É exatamente a mesma coisa que a vivenciamos com a classe AluraMais, onde ela estava ela estava retornando uma string, ou seja, o tipo está correto, mas a implementação estava errada, e o exemplo de Quadrado e Retangulo é o mais clássico se você pesquisar Princípio de Substituição de Liskov, esse exemplo mais clássico que você vai encontrar.

[03:03] Sempre precisa fazer com que as classes derivadas, as classes filhas, respeitem qualquer definição imposta pelas classes bases, pelas classes mãe, ou seja se Retangulo diz que eu tenho duas propriedades com valores diferentes, eu não posso simplesmente, deliberadamente, definir o valor delas como igual quando eu bem entender.

[03:23] Se eu tenho minha classe pai definindo minha, classe mãe definindo, que eu devolva uma URL, eu não posso simplesmente vir aqui devolver uma string qualquer. Isso pode causar comportamentos inesperados

[03:38] Então basicamente o que toda essa frase de Liskov quis dizer é se eu estou esperando um objeto de determinado tipo seja x ,do tipo T , e eu receber um objeto do tipo y sendo que esse y é do tipo S, e S é um subtipo de T, ou seja basicamente é, se eu receber uma instância de S sendo S filho de T, eu preciso ter o mesmo resultado, eu preciso receber o mesmo resultado de qualquer operação desses subtipos, dessa classe filha, dessa classe derivada.

[04:15] Então, além de respeitar os tipos, isso, a compilação, o processo de execução do programa, já garante para nós, ou seja, se eu definir aqui que o meu vídeo retorna uma string eu não posso vir aqui na AluraMais e retornar um inteiro isso não funciona, e o PhpStorm já diz que não funciona.

[04:34] Então, a definição de tipo já é cuidada para nós, já é tratado para nós, sem que precise conhecer esse princípio, mas a implementação fica por nossa conta, garantir que devolva o que o usuário espera fica por nossa conta.

[04:48] Esse é o Princípio de Substituição de Liskov, ele diz que eu posso a qualquer momento substituir uma classe base por qualquer uma de suas derivadas e eu não vou receber um comportamento inesperado. Esse, como eu falei, é um princípio muito complexo. Você pode parar com calma, rever esses dois vídeos, pesquisar um pouco mais, depois voltar nos exercícios, mas é um princípio que se ferirmos podemos causar muitos bugs indesejáveis. Então, é bem interessante que você estude com bastante calma esse princípio.

[05:19] Te espero no próximo capítulo para entender um pouco melhor sobre quando o acoplamento é interessante, quando não é, e como fazer com que o acoplamento trabalhe a nosso favor.

@@05
Mudando o comportamento de um método

Vimos que não só as assinaturas dos métodos devem ser respeitadas, mas também o seu comportamento intrínseco.
Por que não podemos mudar o comportamento de um método de uma classe que pode ser estendida?

Porque se não, geraremos um erro de compilação/interpretação
 
Alternativa correta
Porque, segundo o Princípio de Substituição de Liskov, uma classe base deve poder ser substituída por suas classes filhas em qualquer lugar do código
 
Alternativa correta! Se algum código depende de uma classe, qualquer classe que a estenda deve poder ser utilizada no lugar. Com isso, se um comportamento for alterado no método, resultados inesperados podem ocorrer.
Alternativa correta
Porque contratos foram feitos para ser respeitados
 
Alternativa errada! Esta resposta é um "porque sim" mais bonito, e isso não deve ser uma resposta aceitável.

@@06
Consolidando o seu conhecimento

Chegou a hora de você pôr em prática o que foi visto na aula. Para isso, execute os passos listados abaixo.
1) No método recuperarUrl, da classe AluraMais, adicione o domínio ao retorno:

public function recuperarUrl(): string
{
    return 'http://videos.alura.com.br/' . str_replace(' ', '-', strtolower($this->categoria)) . '/' . str_replace(' ', '-', strtolower($this->nome));
}COPIAR CÓDIGO
2) (Opcional) Crie uma classe chamada Slug (ou um nome que você acredite fazer mais sentido), com o seguinte conteúdo:

<?php

namespace Alura\Solid\Model;

final class Slug
{
    private $slug;

    public function __construct(string $conteudo)
    {
        $this->slug = str_replace(' ', '-', strtolower($conteudo));
    }

    public function __toString(): string
    {
        return $this->slug;
    }
}COPIAR CÓDIGO
3) (Opcional) Agora, no método recuperarUrl, de Video e AluraMais, utilize a classe Slug nas partes da URL que fizerem sentido.

Continue com os seus estudos, e se houver dúvidas, não hesite em recorrer ao nosso fórum!

@@07
O que aprendemos?

Nesta aula, aprendemos:
Que, embora a assinatura de um método esteja sendo respeitada em uma herança, ainda assim podemos estar quebrando algum contrato
Que o Princípio de Substituição de Liskov (LSP) diz que devemos poder substituir classes base por suas classes derivadas em qualquer lugar, sem problema
Que não devemos alterar um comportamento de um método estendido, mesmo que a assinatura seja mantida

#### 28/02/2024

@05-Encapsulando melhor

@@01
Projeto da aula anterior

Caso queira, você pode baixar aqui o projeto do curso no ponto em que paramos na aula anterior.

https://caelum-online-public.s3.amazonaws.com/1315-php-solid/04/aula-4-completa.zip

@@02
Assistindo com simplicidade

[00:00] Olá pessoal. Bem-vindos de volta a mais um capítulo desse nosso treinamento de SOLID, e está na hora de atacarmos esse acoplamento com a implementação de curso ou de AluraMais, enfim nossa classe Assistidor ainda está bem acoplada e não do jeito bom.
[00:18] Então vamos lá, a primeira coisa que eu quero fazer é encapsular um método assistir no meu curso, e esse método assistir vai simplesmente marcar todos os vídeos como assistidos. Vou lá na minha classe Curso e vou criar no final dela um método com o pubf , dei “Enter” , PhpStorm já monta aqui para mim o esqueleto public function assistir (). Aqui, tudo que eu vou fazer foreach ($this->vídeo as $video) { $video->assistir ().

[01:00] Posso inclusive chamar o nosso método recuperarVideos caso tenha alguma diferença, caso precise manipular futuramente os vídeos, eu já estou aqui utilizando o nosso getter.

[01:10] Agora, a nossa classe Curso tem seu próprio método assistir, a nossa classe Curso consegue ser assistida, ou seja, eu posso chegar para o curso e dizer: quero assistir esse curso e ele vai marcar todos os vídeos como assistidos.

[01:29] Então, aqui agora, no Assistidor, eu não dependo mais da implementação de assistir um curso, de pegar a cada vídeo, assistir vídeo a vídeo agora eu só dependo da interface $curso_>assistir(), só isso e nada além disso.

[01:46] Eu posso remover foreach ($curso->recuperarVideos () as $video){ $video ->assistir();}. Se em algum momento, eu além de assistir todos os vídeos, precisar marcar os exercícios como finalizados, por exemplo, eu vou modificar na classe Curso e não na classe Assistidor, não na classe que utiliza o curso.

[02:02] Então agora, eu encapsulei a lógica de assistir meu curso. Com isso, eu garanto que o meu curso, que meu assistidor, consiga trabalhar tanto com AluraMais quanto com curso de forma simples, eu estou dependendo da interface desse método $assistir.

[02:19] E repara, tanto “Curso” quanto “AlluraMais”, agora possuem esse método assistir e outra coisa que eles têm em comum é que ambos implementam interface Pontuável, tanto AluraMais quanto o Curso. Então eu posso adicionar aqui nessa interface Pontuavel public function assistir.

[02:41] Se eu fizer isso, aqui em Assistidor eu posso ter um único método, o public function assistir, que vai assistir qualquer conteúdo que seja pontuável, eu posso chamar o meu assistir.

[02:58] Com isso, eu não dependo mais da implementação de cada um dos meus conteúdos, eu dependo agora da interface deles, do que eles me fornecem de funcionalidade que é o método assistir. E, obviamente, isso também possui um nome. Esse princípio já foi bem definido e é sobre ele que vamos conversar no próximo vídeo.

@@03
Expondo o necessário

A nossa classe que era responsável por assistir os conteúdos precisava conhecer a implementação de cada um dos conteúdos, para marcá-los como assistidos.
De qual conceito da orientação a objetos nós estamos fazendo mau uso?

Selecione uma alternativa

a orientação a objetos nós estamos fazendo mau uso?

Alternativa correta
Encapsulamento
 
Alternativa correta! Nossa funcionalidade de assistir cada conteúdo não estava encapsulada.
Alternativa correta
Polimorfismo
 
Alternativa correta
Abstração
 
Alternativa correta
Herança

@@04
Dependency Inversion Principle

[00:00] Olá, pessoal. Bem-vindos de volta, e no último vídeo implementamos e separamos, na verdade encapsulamos uma parte, uma funcionalidade na nossa classe Curso, e deixamos de depender da implementação dela, de saber como que a lógica de assistir funciona, passamos a depender da interface, do método que ela fornece para nós. Esse princípio é chamado de Dependency Inversion Principle, ou Princípio da Inversão de Dependência.
[00:28] Aqui tem uma frase interessante que pergunta: você soldaria uma lâmpada em uma tomada diretamente no fio elétrico de uma parede, você faria isso aqui? Não, você usa o interruptor, você não pega os fios de cada aparelho eletrônico e solda lá nos fios dentro da parede. Não, você usa a interface que está ali disponível para você, que é o interruptor.

[00:54] Então, esse princípio, ele diz que, na verdade, ele tem duas partes, ele diz que módulos de alto nível não devem depender de módulos de baixo nível, e que ambos devem depender de abstrações.

[01:09] Essa é uma parte, e uma parte um pouco mais complicada do conceito, do princípio, mas a segunda parte diz que abstrações não devem depender de implementações, implementações devem depender de abstrações. Isso, nos tempos modernos, basicamente foi traduzido para: classes concretas devem depender de interfaces e classes abstratas, mas classes abstratas e interfaces não devem depender de classes concretas.

[01:37] Mas, não necessariamente precisamos depender da estrutura de linguagem interface ou de uma classe abstrata, podemos depender de uma classe concreta, desde que estejamos dependendo da interface dessa classe, que estejamos dependendo, por exemplo, só do método assistir de Curso, por exemplo.

[01:59] Isso não teria problema, agora se estamos dependendo de como o assistir funciona, ou seja, recuperaVideos, em cada vídeo chamo método assistir, aí temos um problema, porque se essa implementação mudar, o nosso código vai quebrar. Esse é o problema, é por isso que devemos inverter a dependência, devemos passar a depender das interfaces.

[02:20] Para isso, óbvio, existe a construção de linguagem para nos ajudar, existem as classes abstratas que podem nos ajudar, mas não se atente ao fato de que você só pode depender de interfaces ou de classes abstratas. Não, não vamos ser radicais. Você não pode depender implementações concretas de algoritmos que estejam presentes em outras classes, esse é o problema dessa classe.

[02:47] Um exemplo muito clássico, além desse que demos aqui, é um exemplo de como se você estivesse utilizando banco de dados. Ao invés de você receber como parâmetro em algum lugar que você precisa da conexão, ao invés de você receber uma Instância de conexão com uma SQL, recebo a instância de conexão com qualquer banco de dados relacional ou não inclusive.

[03:11] Dessa forma, se você precisar mudar, migrar de banco de dados, você não precisa alterar essa parte do código. Esse é um exemplo bem clássico, que você provavelmente vai encontrar nos seus estudos.

[03:22] Inversão de Dependência é um princípio muito simples teoricamente, mas muitas das vezes não utilizamos, não é tão simples de aplicar, então também recomendo que você estude com bastante afinco, pesquise um pouco mais por fora, abra dúvidas no fórum.

[03:37] Vamos implementar um pouco, uma outra modificação porque isso me incomoda muito não sei se está te incomodando, mas eu tenho uma interface Pontuavel, ou seja, quem implementa ela contém pontos, consegue recuperar a pontuação dela. Agora, quem é pontuável necessariamente é assistível? Posso assistir qualquer coisa que tenha ponto? Não. Nós vamos conversar sobre isso no próximo vídeo.

@@05
Vantagem ao depender de interfaces

No último vídeo, aprendemos o conceito de Dependency Inversion Principle. Muitas vezes este conceito é interpretado de forma rasa, dizendo que devemos depender apenas de classes abstratas e interfaces (a construção de linguagem interface). Na verdade, devemos depender de interfaces em geral, ou seja, não devemos conhecer como determinado método é implementado.
Que vantagem temos ao depender de interfaces e não de implementações?

Depender de implementações pega mal na comunidade de hypes
 
Alternativa correta
Caso uma determinada implementação mude, não seremos afetados, pois dependemos apenas de sua interface
 
Alternativa correta! Se um método muda a forma como realiza sua tarefa, desde que a interface se mantenha, não vamos precisar nos preocupar nem em editar o nosso código.
Alternativa correta
Ao depender de interfaces, temos gráficos mais interessantes, gerados por ferramentas automatizadas

@@06
Separando as interfaces

[00:00]Olá pessoal, sejam muito bem-vindos de volta, e como eu falei no último vídeo, public function recuperarPotuacao(): int; public function assistir ():void; está muito desagradável.
[00:06] Imagina que eu tenho além de Curso e AluraMais, eu também tenho uma classe de dúvida no fórum, e quando eu respondo uma dúvida no fórum eu também ganho uma pontuação, então ela implementa a interface Pontuavel, mas eu também tenho como assistir uma dúvida no fórum? Não é assistível. Então, eu obrigaria a minha classe dúvida do fórum a implementar o método assistir e não fazer nada, só para poder implementar essa interface.

[00:36] Isso não parece nada legal, então vamos criar uma nova interface, vamos separar essa interface Pontuavel em duas. Eu vou chamar de Assistível, eu posso apagar, vou remover esse código public function assistir ():void da interface Pontuável adicionar na interface Assistível.

[00:59] Já tenho aqui a minha interface, de qualquer conteúdo que seja assistível, que tenha um método assistir. Então, posso vir aqui, além de implementar Pontuavel, implementar Assistível, o meu Curso tem pontuação e tem método assistir, a mesma coisa a AluraMais, implementa Pontuavel e Assistivel, sem problema.

[01:21] Com isso, eu consigo fazer com que outras classes, por exemplo, uma dúvida no fórum implemente a interface Pontuavel, mas não precise implementar o método assistir, ela não é Assistivel. Não devemos nunca forçar que uma classe implemente um método de uma interface só para atender alguns requisitos. Isso não é interessante.

[01:42] Então, essa simples modificação, esse conceito tão simples, também é um princípio bem conhecido, e um princípio que vale a pena comentar e é sobre ele que vamos falar no próximo vídeo.

@@07
Interfaces grandes

Ao termos interfaces com muitos métodos, podemos nos deparar com alguns problemas.
Das alternativas abaixo, qual é um problema causado por esta abordagem?

qual é um problema causado por esta abordagem?

Alternativa correta
Podemos ter arquivos maiores do que a tela do monitor pode exibir
 
Alternativa correta
Podemos ter bugs inesperados
 
Alternativa correta
Podemos ter classes que implementam métodos de forma errada, ou só implementam sem funcionalidade nenhuma
 
Alternativa correta! Tendo interfaces com métodos demais, às vezes nem relacionados, pode fazer com que as classes que venham a implementar precisem definir métodos que não façam sentido.

@@08
Interface Segragation Principle

[00:00] Olá pessoal, bem-vindos de volta. No último vídeo, fizemos uma implementação bem simples, mas essa simples implementação é demonstração de um padrão bem conhecido, um princípio bem conhecido, o Princípio de Interface Segregation ou Princípio de Segregação de Interface, e essa imagem exemplifica exatamente que queremos.
[00:22] Temos aqui um açaí, podemos tomar um açaí com canudo, mas tem bananas, outras frutas, granola, seja lá o que você gostar de colocar no açaí. Então, nós temos algo para beber, algo que conseguimos beber utilizando canudo, e algo que conseguimos comer.

[00:38] Então, nós temos duas interfaces, uma interface de algo comestível, e algo que eu posso beber, não uma única interface de comer e beber, não, eu tenho duas interfaces e aqui essa implementação específica implementa as duas.

[00:53] Esse princípio foi cunhado também pelo Uncle Bobby. Esse princípio diz que uma classe não pode ser forçada a depender de métodos que ela não utilizará, como seria o caso de uma dúvida ter que implementar o método assistir.

[01:08] Ela não vai utilizar o método assistir uma dúvida não pode ser assistida, então, ela teria que implementar esse método para atender a interface, mas esse método seria inútil. Isso não é legal, pois faz com que tenhamos métodos inúteis e nos torna dependentes de métodos que não vão ser executados.

[01:26] Se eu passasse uma dúvida para um método que espera algum conteúdo assistível, que na época, antes de fazermos a implementação era pontuável, poderiamos ter um comportamento inesperado, o que também quebra Princípio de Substituição de Liskov que já conversamos antes.

[01:42] Então, repara que todos esses conceitos que trabalhamos aqui estão interligados, todos esses conceitos conversam entre si e a junção nesses conceitos é chamada de SOLID. O S de Single Responsibility Principle, Open/Closed Principle é o O, L de Liskov Substitute Principle, I de Interface Segregation Principle e D de Dependency Inversion Principle.

[02:16] Todos esses conceitos, todos esses princípios de boas práticas em Orientação a Objetos formam o acrônimo SOLID. E com isso, se você tentar seguir todos esses princípios, você realmente alcança um código mais sólido, um código mais manutenível, mais bem testável, enfim, você atinge um estado da arte mais interessante.

[02:37] E uma vez, um grande mestre do desenvolvimento da comunidade de desenvolvimento PHP aqui no Brasil, Júnior Grossi, ele falou que SOLID não é um processo, não é o processo. SOLID é o objetivo.

[02:50] Você mira em escrever um código SOLID, e com isso o seu processo vai ser otimizado, você vai acabar escrevendo código mais bem escrito, um código melhor por estar tentando alcançar o objetivo de escrever um código SOLID. Ele também diz, e eu concordo com ele, que é impossível escrever um código 100% SOLID.

[03:11] Vou dar um exemplo bem rápido do nosso projeto que é tão simples. O nosso Curso, além de ter a regra de um vídeo tem a regra de assistir, então meio que demos uma quebrada no princípio do S, sim, e está ok, porque tudo está relacionado ao vídeo.

[03:29] Então, você tem que medir, não pode ser extremista, tentar separar classes para qualquer coisa que às vezes nem faz sentido, mas é interessante você tentar atingir um código SOLID, atingir esses princípios, não quebrar esses princípios.

@@09
Definição do ISP

Vimos no último vídeo que, ao separar as interfaces, implementamos o Interface Segregation Principle.
Qual a definição formal deste princípio?

Classes devem ter um e apenas um motivo para mudar
 
Alternativa correta
Implementações devem depender de abstrações e não o contrário
 
Alternativa errada! Esta é uma simplificação do DIP.
Alternativa correta
Classes não devem ser obrigadas a implementar métodos que não irão precisar
 
Alternativa correta! Uma classe não deve ser obrigada a implementar um método de determinada interface, se ele não será útil. Para isso, uma interface deverá ser extraída apenas com os métodos necessários.

10
Consolidando o seu conhecimento

Chegou a hora de você pôr em prática o que foi visto na aula. Para isso, execute os passos listados abaixo.
1) Adicione o método assistir na interface Pontuavel:

interface Pontuavel
{
    public function recuperarPontuacao(): int;
    public function assistir(): void;
}COPIAR CÓDIGO
2) Implemente este novo método na classe Curso:

public function assistir(): void
{
    foreach ($this->videos as $video) {
        $video->assistir();
    }
}COPIAR CÓDIGO
3) Faça com que a classe Assistidor dependa apenas na interface Pontuavel:

<?php

namespace Alura\Solid\Service;

use Alura\Solid\Model\Pontuavel;

class Assistidor
{
    public function assistir(Pontuavel $conteudo)
    {
        $conteudo->assistir();
    }
}COPIAR CÓDIGO
4) Note que não faz sentido o método assistir na interface Pontuavel. Remova-o desta interface e crie uma interface:

<?php

namespace Alura\Solid\Model;

interface Assistivel
{
    public function assistir(): void;
}COPIAR CÓDIGO
5) Faça com que a classe Curso implemente esta nova interface:

class Curso implements Pontuavel, Assistivel
// ...COPIAR CÓDIGO
6) Implemente-a também na classe Video:

class Video implements Assistivel
// ...COPIAR CÓDIGO
7) Faça com que a classe Assistidor dependa desta nova interface:

<?php

namespace Alura\Solid\Service;

use Alura\Solid\Model\Assistivel;

class Assistidor
{
    public function assistir(Assistivel $conteudo)
    {
        $conteudo->assistir();
    }
}

Continue com os seus estudos, e se houver dúvidas, não hesite em recorrer ao nosso fórum!

@@11
Projeto do curso

Caso queira, você pode baixar aqui o projeto completo implementado neste curso.

https://caelum-online-public.s3.amazonaws.com/1315-php-solid/05/aula-5-completa.zip

@@12
O que aprendemos?

Nesta aula, aprendemos:
Que é mais interessante e mais seguro para o nosso código depender de interfaces (classes abstratas, assinaturas de métodos e interfaces em si) do que das implementações de uma classe
Que as interfaces são menos propensas a sofrer mudanças enquanto implementações podem mudar a qualquer momento
Que o Princípio de Inversão de Dependência (DIP) diz que implementações devem depender de abstrações e abstrações não devem depender de implementações
Que as interfaces devem definir apenas os métodos que fazem sentido para seu contexto
Que uma classe pode implementar diversas interfaces
Que o Princípio de Segregação de Interfaces (ISP) diz que uma classe não deve ser obrigada a implementar um método que ela não precisa;
Os conceitos aprendidos neste treinamento formam o acrônimo SOLID
Single Responsibility Principle
Open Closed Principle
Liskov Substituition Principle
Interface Segregation Principle
Dependency Inversion Principle

@@13
Conclusão

[00:00] Olá, pessoal. Bem-vindos ao final desse treinamento de SOLID e boas práticas em Orientação a Objetos em PHP. Primeiro queria te parabenizar por chegar ao final, esse conteúdo é muito importante para sua carreira como desenvolvedor ou desenvolvedora, independente da área de desenvolvimento que você vai seguir, as boas práticas sempre devem ser seguidas.
[00:19] Se você for trabalhar com outro paradigma de programação, que não orientado a objetos, com certeza existem boas práticas e princípios a seguir, e os princípios SOLID são os princípios mais famosos, e me arrisco a dizer, os mais importantes do desenvolvimento orientado a objetos.

[00:37] Nós vimos nesse treinamento todos eles: o Princípio de Responsabilidade Única, Aberto/Fechado, Substituição de Liskov, Segregação de Interface, Inversão de Dependência, e conforme, fomos passando por cada princípio, vimos as vantagens de cada um e como implementar, e as vantagens dessa implementação em si.

[00:56] No final chegamos com um código bem mais manutenível, com um código mais extensível. Se precisarmos implementar novos conteúdos que tenham pontuação, temos uma classe Pontuavel, se precisarmos implementar novos conteúdos que tenham método de assistir, sejam assistíveis, criamos uma interface para isso.

[01:19] Nosso Feedback agora é separado em uma classe só para ele para que tenha suas próprias regras, nosso Curso não trata mais disso, nosso Curso agora tem sua própria pontuação, tem encapsulado seu método de assistir, enfim fizemos muitas modificações, trabalhamos com bastante coisa e tornamos nosso código um pouco mais sucinto, um pouco mais SOLID.

[01:43] Como eu comentei no vídeo passado, um grande mestre do desenvolvimento de software, Júnior Grossi, comenta que, ele diz que SOLID não é o processo, SOLID não é algo que você vai trabalhando, SOLID é o objetivo, você tenta alcançar o código SOLID seguindo os princípios;

[02:00] E não é viável, não é corriqueiro, você ter um código 100% SOLID, seguindo 100% todos os princípios. Então, não se martirize por ter algum problema, alguma coisa que parece infringir algum dos princípios, desde que faça sentido.

[02:18] Como, por exemplo, no nosso caso, o curso parece ter algumas responsabilidades a mais, parece ter mais de um motivo para mudar, mas todos esses são relacionados à classe Curso, então faz sentido.

[02:29] Existe uma frase bastante famosa, não me lembro qual foi o filósofo que falou, mas que a simplicidade é o mais alto grau de sofisticação, então não tente complicar seu código para implementar vários princípios e padrões. Mantenha o seu código simples, mantenha o seu código sucinto, mantenha seu código SOLID.

[02:55] Espero que você tenha curtido e aproveitado esse treinamento e espero te ver em Futuros treinamentos aqui na Alura. Forte abraço e até a próxima.