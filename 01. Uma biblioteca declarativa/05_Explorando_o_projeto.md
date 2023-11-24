Paulo: Olá, bem vindo e bem vinda a continuação da nossa aula de React. Vinicios, como conversamos aqui no backstage, estou muito feliz com o andamento desse curso.

Como usamos o Create React App, ele criou muitos arquivos, uma estrutura de diretório específica, algumas dessas pastas não estamos utilizando, então vamos organizar um pouco eles. É isso?

Vincios: É, Paulo, vamos arrumar porque agora ele tem que ser o organo, certo? Ele não é mais uma aplicação genérica do Create Rreact App, ele já está ficando com a nossa cara. Então vamos repassar e remover alguns arquivos. Vamos tirar tudo o que o Create React trouxe por padrão e como exemplo também.

Vamos voltar pra o VSCode e olhar aqui no "App.js", ele está em "src". Notem que toda a parte de `Bem-vindo ao React!` e `Learn React` e a logo não são necessários nesse momento. Vamos pegar todo esse conteúdo e deletar sem dó, vamos deixar só o `Banner`.

``` javascript
import Banner from '/.componentes/Banner/Banner';

function App() {
    return (
        <div className="App">
            <Banner />
        </div>
    };
}

export default App;
```
Vinicios: Com isso, podemos aproveitar e remover os arquivos do projeto. Repare que ele tem aqui o "App.css", essa pasta fazia o logo girar, então vamos apagar também. O "App.test.js", ".test.js" quer dizer que um teste é automatizado, como não fazemos fazer testes nesse curso, podemos apagar.Agora temos o "index.css", esse index está colocando uma margem zero no  `body` e "setando" uma `font-family`. Vamos deixar por enquanto porque é ele quem está aplicando um estilo mais global da aplicação independente dos componentes. Agora temos o "index.js", essa pasta tem muitos códigos, Paulo, vamos dar uma olhada?

``` javascript
const root = ReactDOM.createRoot(document.getElementById('root'));
```
Vinios: A depender da versão que vocês vejam o projeto, isso pode ter um pouco mais ou menos de código, mas o conceito é o mesmo. Então, o que o React faz aqui, ele faz o `import` do React DOM e cria o `root` onde vai ficar o componente principal da aplicação, e o que passamos como argumento para esse `createRoot` é algo que estamos acostumados, um seletor `document.getElementByid`, então alguém procurou um elemento com o id `root` em algum lugar e vamos descobrir daqui a pouco onde é.

Depois de descobrirmos onde ele fez isso, ele renderizou o nosso `App`. Esse componente nada mais é do que o nosso "App.js". Então podemos falar que esse "index.js" é o que chamamos de bootstrap, o ponto de entrada. Esse é o primeiro arquivo que vai ser executado e que vai renderizar o primeiro componente e iniciar um movimento em cascata.

Em seguida ele chama o método `render` que é um métodos do React que vai renderizar lá dentro.

``` javascript
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
    <React.StrictMode
        <App />
    </React.StrictMode>
);
```
Vinicios: O `ReactStrictMode` é para nos ajudar enquanto Front-End. Ele em produção não fará nada, mas em ambiente de desenvolvimento, o fato dele estar aqui vai nos ajudar a prevenir erros e ter mensagens de erros mais amigáveis.

Já o `reportWebVitals()` é algo mais relacionado à analítica e a parte de performance e nós não vamos olhar para isos nesse momento, então vamos apagar também. Tranquilo até agora, Paulo?

Paulo: Vale lembrar que todo esse reportWebVitals(), o teste, são importantes no React e nos seu projeto. Tem pessoas que ficam com essa ansiedade de querer ver tudo de uma vez, mas vamos primeiro entender o React com algum profundidade antes de sair conectando tudo. Senão, ficamos muito rasos em tudo.

Vamos pegar o React mesmo, o core, e no final do curso vamos colocar algumas perguntas para o Vinicios. Mas agora é muito importante seguirmos o caminho que o Vinicios está nos dando.

Vinicios: Estamos deixando aqui o que nós realmente precisamos. Vamos apenas tirar o que não vamos olhar agora. Como você falou, são pontos muito importantes mas é o que não vamos estar olhando nesse momento. São passos de bebê.

Agora temos o "logo.svg" que também podemos deletar, o "reportWebVitals" também, que é o relatório de performance. E também o "setupTest.js".

Vamos agora descobrir se os arquivos deletados quebraram algo. Vamos no terminal para ver se tem uma mensagem de erro e em seguida no Navegador vamos pedir para recarregar a página.

Tudo certo! Agora ainda no navegador cliamos na tela com o botão direito do mouse e selecionamos a opção "Inspect Element" para abrir o developer tools. Está tudo certinho! Nosso console está sem erro, nosso componente de `Banner` já está lá e o que precisamos fazer agora é dar sequência em nosso Organo.

Pelo Figma, nosso próximo passo é criar esse formulário com botão, inputs e tudo mais. Na minha cabeça, conforme vou olhando o Figma eu já fico pensando em HTM. Agora acho que a casa já está arrumada, podemos seguir e partir para o próximo componente.

Paulo: Vamos lá!
