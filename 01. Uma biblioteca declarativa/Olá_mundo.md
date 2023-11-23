Paulo: Boas vindas a nossa primeira aula desse curso de React com o famosíssimo Vinicius Neves que conhece mais de um Framework de Front-End!

 ![image](https://github.com/AndreCoutinhom/alura_react_course/assets/91290799/f2ba6d99-9694-4aeb-a55c-a0cc112cc34c)


Paulo: Aqui temos a tela do Figma, um software que faz parte da vida de quem desenvolve Front-End. Normalmente quem é do design entrega para nós um projeto no Figma e pede para implementarmos ele.

Transformar isso em HTML, CSS, JavaScript -usando ou não um Framework - é um desafio muito real que enfrateremos aqui.

Vinicios, você que trabalha em Portugal em uma empresa grande de tecnologia acho que é algo que todo mundo de uma equipe de Front-End de uma startup internacional passa, não é?

O Figma, aliás, é um produto muito forte da Alura, nós temos uma formação só de Figma!

Vinicios: O Figma é o nosso primeiro passo, é como se fosse a planta da casa que vamos construir. O que temos que fazer no final é uma aplicação que tenha todo esse comportamento.

O Organo é a aplicação que vamos desenvolver aqui. Ele vai permitir que a configuremos e cadastremos a organização da nossa empresa. Nessas imagens vocês encontrar o rosto dos nossos instrutores separados pelas Escolas das quais eles fazem parte. A ideia é conseguirmos adicionar dinamicamente pessoas a esses times.

Vai ser bem legal, temos bastante o que fazer e estou ansioso para começar, vamos lá?

Paulo: Vamos lá! Recebemos um projeto já com layout bacana. Depois vou deixar como desafio aqui para o pessoal mudar um pouco o Organo, que foi uma ideia que o pessoal da escola de Front-End trouxe para nós.

Vinicios: Então, Paulo, se estivessemos fazendo isso da forma tradicional, nós iriamos começar criando um index HTML e começando a digitar nossas tags, importando CSS e importando JavaScript e estariamos pronto para começar sem maiores problemas.

Porém, como vamos utilizar o React, é um pouquinho diferente porque quando optamos por desenvolver uma aplicação desse tipo, temos toda uma base necessária para ter o React disponível.

Esse processo é um pouco complicado, mas é comum de ser feito porque ele tem uma "receita de bolo" para seguirmos. Quando queremos criar uma aplicação React, ele já tem um comando no npx que é um atalho em que basicamente vamos pedir para o React pedir uma aplicação base. É isso o que precisamos fazer por meio do npx Create React App.

Paulo: É claro que existem outras formas de criar uma aplicação no React, estamos usando uma das formas porque é algo que tanto o Vinicios quanto a Escola de Front-End da Alura consideram muito usado no mercado. Vocês verão que existem outras versões e com o tempo entenderão outras maneiras de criar.

Viny, esse npx é algo que chamamos de "gerenciador de pacotes do Node", quem está trabalhando com React agora não precisa entender de Node, certo? Só precisa ter o npx instalado.

Vinicios: É exatamente isso, Paulo. Uma vez que temos o Node instalado em nossa máquina, nós conseguimos rodar o comando, por exemplo, pedindo a versão dele, porém não precisamos entender como o Node funciona por "baixo dos panos". Nesse curso vamos usar ele apenas como ferramenta.

Agora com o Terminal no Node aberto, podemos chamar o npx.

``` shell
vinny > node -v
v16.13.2
vinny > npx create-react-app organo
```

Vinicios: Aqui `organo` é o nome do projeto que vamos criar.


Agora esperamos ele carregar, o que pode demorar um pouco a depender da velocidade do HD e da internet.

Paulo: Aqui o que eles está fazendo não tem muito segredo, ele está se preparando, puxando alguns pacotes para nos ajudar a trabalhar com React, está preparando diretórios em nossos arquivos para poder separar onde fica o CSS e onde fica o JavaScript. Essa preparação é o que chamamos de template.

Isso é uma receita, poderia ser feito de outras formas, mas quem trabalha bastante com React está acostumado dessa maneira e aqui nós veremos as práticas mais comuns do mercado.

Vinicios: No dia a dia nós tendemos a trabalhar mais em projetos existente e não criar projetos novos todo dia, mas existem algumas formas de fazer isso e essa é uma forma padrão.

Enquanto estávamos conversando, o Node terminou de preparar o ambiente para nós. Eles nos diz que deu tudo certo e o projeto foi criado na pasta `/User/vinny/organo.`

``` shell
npm start 
         Starts the development server.

npm run build
        Bundles the app into static files for productions.


npm test
        Starts the test runner.

npm run eject
        Removes this tool and copies build dependencies, configurations files and scripts into the app directory. If you do this, you can't go back!
```

Uma vez que ele está intalado, podemos começar algumas ações, uma delas é iniciar o projeto, que é justamente o que desejamos agora.

Vamos entrar dentro da pasta que ele criou, então digitamos `cd organo`. Se olharmos no diretório, vamos pedir para ele listar tudo que tem lá dentro com `ls - la`.

``` shell
vinny ) cd organo
organo ) ls - la
```

Ele tem uma pasta `crs`, uma pasta `public`, um `package.json`, `package-lock.json` entre outras. Nossa receita de bolo está pronta, o bolo está assado para nós começarmos a enfeitá-lo.

Agora, vamos rodar aquele comando que é para iniciar o projeto, `npm start`. Agora não usamos o `npx` mas sim o `npm`, a diferença é que o `npm` nós vamos utilizar para rodar coisas locais, quando rodamos o `npx` quer dizer que estamos rodando o script de forma remota, não está muito vinculado ao ambiente local.

Paulo: `npm`, `npx`, Node, para quem vem do Front-End puro as vezes é assustador, né, Vinicios? Isso é normal! Nesse momento em que você está entrando em React, se a sua carreira está ainda no começo, deixa o `npm`, o `npx` e o `node` como o Vinícius colocou no começo: é uma ferramenta.

Depois de um tempo quando vocês ganharem maturidade e experiência com React, ou se você já vem do Back-End, então será interessante estudar um pouco de Node, um pouco de `npm`, que tem relação com o Dev em T que falamos bastante na Alura.

Vinicios: Exatamente, Paulo. Sempre que aparecer algo importante vamos comentar sobre isso senão vamos tratar como um ferramenta para focarmos no que é mais importante no momento.

Agora rodaremos o `npm start`, que é o comando que vai subir a aplicação. Reparem que quando estamos vendo do HTML e CSS vamos para os arquivo estático. Aqui, porém, é um pouco diferente: aqui temos a base pronta do projeto e quando vamos trabalhar com React nós acessamos o `localhost`, que é onde a aplicação está rodando.

Então, o que esse comando fez foi preparar o ambiente de desenvolvimento para começamor a trabalhar e subirmos a aplicação. Podemos, inclusive, acessá-la.

Copiamos o endereço "httpm://localhost:3000" e colamos no navegador. O projeto React está lá funcionando!

![image](https://github.com/AndreCoutinhom/alura_react_course/assets/91290799/76ae0c77-41d1-42fd-9634-7e493c00699a)

Ele, inclusive, dá uma dica para editarmos dentro de SRC o `App.js` e salvarmos para recarregar a página.

Paulo: Essa é a App que o Creat React App criou para nós? Ele criou uma app que tem algo escrito, um link e um gif animado, é isso?

Vinicios: Exatamente. Vamos agora abrir a pasta "organo" no VS Code. Em "organo > src > App.js" encontramos o seguinte código.

``` html
import  logo from './logo.svg';
import '.App.css';

function App() {
    return (
        <div className="App">
            <header className="App-header">
            <img src={logo} classNode="App-logo" alt="logo" />
            <p>
                Edit <code>src/App.js</code> and save to reload.
            </p>
            <a
                className="App-link"
                href='https://reactjs.org"
                target="_blank"
                rel="noopener noreferrer"
                >
                    Learn React
                </a>
            </header>
        </div>
    );
}
```

Vinicios: Notem que tudo que está escrito lá no navegador é exatamente igual ao que está aqui: Edit e src/App.js. Vamos traduzir para o português.

```
Edite <code>src/App.js</code> e salve para recarregar.
```

Vinicios: Pronto, agora salvamos o arquivo.
Paulo: Eu me assustei um pouco, Vinicios, porque tem essa `function` e dentro dela tem um `return` que abre parenteses, um HTML. Eu que venho do Front-End mais simples, nunca vi um `return` de JavaScript retornar HTML. Ele não tem nem aspas, não é? Aqui já estamos em um modo React, posso falar assim? Já é algo característico do React.

Vinicios: Exatamente. Isso aqui nada mais é do que um componente React, por isso que vemos um pouco de JavaScript com algo que parece HTML.

Agora, a forma de trabalharmos é com a forma React. Então em vez de criarmos os elementos e irmos fazendo `document.querySelector`, `document.createElement` para manipularmos o DOM, vamos utilizar o React e uma dessas formas de fazermos isso é criar componentes. Então, o que vocês veem aqui em `function App()` nada mais é do que uma forma de escrever um componente React.

Uma vez que alteramos o código, não vamos nem olhar para o restante por enquanto, vamos apenas pensar no pedaço que alteramos. Na teoria, se voltar para o navegador, ele vai estar atualizado.

![image](https://github.com/AndreCoutinhom/alura_react_course/assets/91290799/0b75c99d-4c7e-4831-bc9d-307a1d67954f)

Vinicios: Ele está traduzido e não precisamos nem atualizar a página! Na hora que trocamos de tela, ela já estava atualizada.

Paulo: Você nem deu reload, né? De alguma forma aquele servidor em que estamos rodando `npm start` percebe que houve alguma alteração. Tem uma magia acontecendo aqui atrás, não é, Vinicios? É uma das várias vantagens do React, tem essa mágica entre servidor e Front-End em manter tudo alinhado. Se formos fazer com o JavaScript do modo "rústico" daria muito trabalho, não é?

Vinicios: Sim. É possível, mas teríamos que desenvolver tudo isso na mão. É por isso, inclusive, que usamos o `npx` porque ele já nos trás isso pronto e assim podemos nos preocupar em de fato desenvolvermos os componentes. No fim das contas, o React é sobre como desenvolver componentes.

Para finalizarmos esse vídeo aqui e partimos para o próximo, onde de fato criaremos esse primeiro componente, vamos fazer mais um teste. Abriremos o VSCode mas vamos separar a tela entre ele e o navegador para vermos funcionando ao vivo.

Vamos alterar o texto para `Bem-vindo ao React`.

``` html
<p>
    Bem-vindo ao React
<p>
```
![image](https://github.com/AndreCoutinhom/alura_react_course/assets/91290799/9b4c7490-cf97-44dd-ad18-6012a1de7e1d)

Vinicios: Deu certo! Agora, Paulo, já temos um ambiente de desenvolvimento bem bacana, certo? Nós vamos no arquivo, alteramos e já vemos o resultado imediatamente.

Com isso, temos a base toda pronta para começarmos de fato a criar os nossos componentes e então entenderemos o que é essa função, o que é o HTML no retorno, e tudo mais.

Paulo: Vou apenas deixar um desafio aqui: façam esse teste que o Vinicios fez! Sempre explore, se vocês tem alguma curiosidade aqui, vá além do Create React App e do que fazemos aqui. Sinta-se a vontade, mas é claro que vamos explorar juntos no próximo vídeo.

Vinicios: Vamos lá!
