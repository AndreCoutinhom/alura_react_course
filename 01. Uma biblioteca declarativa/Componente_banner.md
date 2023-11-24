Paulo: Olá! Agora queremos continuar implementando o que temos do nosso Figma usando o React. Por onde começamos?

Vinícios, você já usou a palavra "componente", que é uma palavra muito comum no React, sei que vai ficar mais claro com o tempo o que é um componente, mas pelo o que eu entendo é um pouco da mistura de um CSS, JavaScript e HTML que costumamos fazer separados e o React traz isso tudo junto.

Inclusive, nesse `function App()` já tem algo misturado, não é?

Vinicios: Aqui poderiamos fazer várias abordagens diferentes porque temos o Figma inteiro. O que eu costumo fazer é pegar primeiro a parte visual sem o comportamento. Então, vamos pensar em tranformar esse Figma em HTML e CSS, vamos colocar dessa forma.

Nosso primeiro passo é criar o cabeçalho do organo, onde temos "Pessoas e times organizados em um lugar"

![image](https://github.com/AndreCoutinhom/alura_react_course/assets/91290799/8cae6cac-6885-4090-a90d-0bf9b4a52d80)

Vinicios: Esse é um Banner. Essa não é a única imagem que vamos usar no projeto, e nós vamos disponibilizar o link para vocês baixarem todas as imagens.

O que vamos usar primeiro é o "banner". Vamos começar do jeito React. Você já apontou no vídeo anterior, Paulo, que tem algo aqui em HTML. Se de repente sairmos digitando HTML, vamos ver o que acontece.

Podemos tentar adicionando `h1` que é um tag HTML com `Olá, Mundo`.

``` javascript
    return (
        <div className="App">
            <h1>Olá, Mundo</h1>
    )
```

Vinicios: Repare, o fato de colocarmos aqui uma tag HTML, ele já vai lá adiciona no cabeçalho do Navegador!

![image](https://github.com/AndreCoutinhom/alura_react_course/assets/91290799/83a22d6e-2c3b-4a17-aeff-9ee8f7eb744e)

Paulo: Ficou ótimo!

Vinicios: Isso aqui é muito parecido com HTML, certo? Porém, se formos fazer toda essa aplicação aqui em um único arquivo, o que você acha que vai acontecer com esse arquivo, Paulo?

Paulo: Eu acho que vamos ser demitidos, não sei o arquivo.

Vinicios: Boa. Nós vamos ter uma salada de códigos e HTML, se quisermos reaproveitar depois, como faríamos isso? Reaproveitar código não é copiar ele de um lado para o outro, né, Paulo?

Paulo: É, porque esse Banner, nós até não vamos reaproveitar, mas mais abaixo do Figma, tem alguns cards que parece que vão ser reaproveitáveis, só vamos mudar o nome e as fotos.

Vinicios: Exatamente.

Paulo: Tem muito aqui que queremos reaproveitar, mas mesmo se nós não formos reaproveitar, pelo que entendo é uma boa prática separarmos porque "vai que" um dia nós queremos reaproveitar.

Vinicios: Exatamente. E até mesmo pela manutenção, não, Paulo? Imagine que se deixarmos ele bem organizado e com o passar do tempo, pode ter uma outra pessoa que vai dar manutenção no código que escrevemos. Então, se seguirmos as boas práticas e organizamos tudo direitinho e a pessoa quiser mexer no Banner, fica mais prático.

Agora que já conversamos sobre o que queremos fazer, vamos no VS Code e dentro da pasta "src" criaremos uma pasta "componentes".

A ideia é que todos os nossos componentes estejam dentro dessa pasta. Vamos criar uma outra pasta chamada "Banner", é aqui que vamos criar esse componente. Dentro dessa pasta, vamos criar um arquivo chamado "Banner.js".

Agora temos um arquivo JavaScript onde vamos escrever o nosso primeiro componentes. Repare que lá no "App.js" ele tem um function App() e embaixo ele faz um `export default App;`.

Aqui, quando estamos falando de função e um `export`, entamos falando de JavaScript. Qualquer módulo JavaScript pode ter um `export`.

Poderíamos seguir aqui desse mesmo jeito, fazendo uma análise do App para o Banner, vamos fazer algo assim.

``` javascript
function Banner() {

}

export default Banner
```

Vinicios: Temos a mesma estrutura: JavaScript sem o React ainda.

Paulo: Seguindo o modelo do "App.js" que dá um return, abre parênteses e inserimos um HTML lá dentro, faríamos algo parecido aqui. Certo?

Vinicios: Exatamente. Vamos fazer o return o parênteses que vamos abrir em seguida é para podermos fazer um return de múltiplas linhas. Em seguida, vamos colocar o <img> como primeira dessas muitas linhas.

``` javascript
return (
    <img />
)

```

Em seguida, vamos colocar um `src`, que é onde está a imagem. Em nossa estrutura de pastas, temos uma pasta chamada "public", dentro dela vamos criar a pasta chamada "imagens" e vamos trazer a imagem do Banner para ela arrastando com o mouse o arquivo dela para dentro da pasta.

Paulo: Eu como aluno, esse monte de diretório que o Create React App gerou. Ele gerou "node_modules", gerou "Public" que agora estou começando a entender. Ele também gerou o "src" e nós criamos "componentes", "Banner" e um "Banner.js", que eu imagino que não seja obrigatório, mas é o caminho normalmente tomado nesses casos.

Vinicios: Exatamente, Paulo. A ideia do "public" é que quando criarmos e formos publicar em algum lugar, tudo que chamamos de "imagem estáticas" será disponibilizado colocando dentro da pasta "public".

Repare que a pasta "public" é a raíz, então ela é o `/` e a partir dela queremos acessar a pasta de `imagens` e o `banner.png`.

## Imagens

* [Baixe aqui o zip com todas as imagens que serão utilizadas no projeto](https://github.com/alura-cursos/organo/raw/main/imagens.zip).

``` javascript
return (
    <img src="/imagens/banner.png" />
)
```
Vinicios: Note que essa linha está sublinhada em laranja no VS Code. Isso ocorre porque o VS Code está nos alertando que estamos colocando uma imagem e uma imagem deveria ter um texto alternativo, ou seja, um `alt`. Podemos colocar como `alt` o seguinte texto `O banner principal da página do Organo`.

``` javascript
return (
    <img src="/imagens/banner.png" alt="O banner principal da página do Organo"/>
)
```

Paulo: Funcionaria mesmo sem isso, não é?

Vinicios: Funcionaria, sim! Mas quando tem um alerta eu gosto de entender e resolver ele! Agora temos o nosso banner.

``` javascript
function Banner() {
    return (
        <img src="/imagens/banner.png" alt="O banner principal da página do Organo"/>
    )

}

export default Banner
```
Vinicios: Temos uma função que está sendo exportada e algo que parece HTML. Se temos agora o nosso primeiro componente, o que queremos em seguida é inserir ele em algum lugar. Como fazemos para encaixar essas peças agora em "App.js"?

Paulo: De alguma forma você deve chamar aquela função, porque você criou uma função. O nosso componente `banner()` "javascriptamente" falando é uma função que retorna um componente. Então devemos chamar `Banner()`, não sei se com ponto e vírgula ou não, mas meu chute é por aí.

Vinicios: É mais ou menos isso. Antes de importarmos, vamos entender o que é isso que eu disse que parece HTML, mas não é.

Isso é o que chamamos de JSX, esta é a forma como o React trabalha com a parte visual. Então isso parece um HTML, mas não é. O que o React vai fazer por debaixo nos panos é entender o que é isso e fazer o apende no DOM. É como se no modo clássico nós fizessos um `document.createElement` e criássemos o `img` e definíssemos o atributo `src` e o atributo `alt`. Então, o JSX é como o React lê isso e transforma em elementos no DOM. Ele parece HTML, mas não é, ele é JSX. Entraremos mais a fundo nisso conforme formos evoluindo.

Paulo: Tudo ao seu tempo.

Vinicios: Exatamente. Agora desmistificamos isso! O conceito de HTML são essas tags, certo? Temos `h1`, `p`, o próprio `img`... Temos muitas tags HTML e a idea do componente é seguir mais ou menos esse fluxo. Então, o que poderíamos fazer aqui é, como o nome do nosso componente é `Banner`, poderíamos abrir uma tag com esse nome `<Banner`.

O VS Code já automaticamente sugere o `import` do nosso componente, se clicarmos na sugestão, ele já faz o `import` automaticamente para nós.

``` javascript
import Banner from '/componentes/Banner/Banner';
```
Paulo: Não funcionaria sem esse `import` mesmo estando em uma estrutura?

Vinicios: Isso! Precisamos fazer o `import`.

Paulo: E nós chamamos ele em uma tag como se fosse HTML, mas é uma tag que nós criamos?

Vinicios: Isso!

```
< Banner /> 
```

Paulo: É assim que vamos fazer no React, vamos criando tags e usando tags que na verdade são componentes que misturam HTML, JavaScript e CSS de uma forma do React, que é chamado de JSX, um nome que nem aparece mais escrito.

Vinicios: Isso! Nas versões mais antigas do React esse nome ficava um pouco mais explícito, mas hoje ele fica bem escondido ali. De fato precisamos entender como vamos escrever esses componentes.

Agora se salvarmos isso, lá em nosso navegador já será possível visualizar nosso banner!

![image](https://github.com/AndreCoutinhom/alura_react_course/assets/91290799/9dac8e04-f5b3-4cd9-a162-edf18409390e)

Vinicios: Algo certo nós fizemos! Porém, ainda temos que mexer um pouco nele para deixarmos mais parecido com o que temos no Figma. Então precisamos um pouco de CSS para estilizarmos um pouco, ajustarmos ele ao tamanho da tela, colocarmos cor no fundo. Voltaremos a nossa estrutura de pastas, em "src > componentes/Banner" vamos criar um novo arquivo para chamarmos de "Banner.css".

A partir de agora, o que vamos fazer é CSS como ele é, aqui não vamos terá nada escondido. O que precisamos fazer é criar as propriedades que queremos e aplicar em nosso componente. Por exemplo, podemos chamar uma classe `.banner` com um `background-color`. Para a cor de fundo, vamos ver no Figma, que é o #6278F7.

Paulo: Costumamos receber isso pronto de quem faz o Figma, então?

Vincios: Exato. Esse é o nosso `background-color`:

``` css
.banner {
    background-color: #6278f7
}
```
Vinicios: Vamos querer também que a imagem fique centralizada dentro desse banner. Existem várias formas de fazer isso, mas vamos usar aqui uma bem clássica com `text-align: center`.

Além disso, queremos deixar a imagem responsiva, então vamos fazer um `.banner` selecionando o `img` e vamos dizer que o tamanha máxima `max-width` é de `100%`.

``` css
.banner {
    background-color: #6278f7
    text-align: center
}

.banner img {
    max-width: 100%;
}
```
Vinicios: Está aqui o nosso CSS. Como faremos agora para juntar isso?

Paulo: É, legal, porque os nomes batem "Banner.css" e "Banner.js" na mesma pasta, precisamos falar mais algo?

Vinicios: De alguma forma precisamos dizer para o React levar esse arquivo CSS em consideração. Essa é a forma mais básica de termos um pouco de CSS. Vamos em "Banner.js" pedir para ele fazer o `import` desse CSS, mas passaremos o caminho direto.

``` javascript
import './Banner.css'
```
Vincios: Para ficar merlhor, colocamos essa imagem dentro de um `header` HTML e colocamos `img` dentro dele.

``` javascript
function Banner() {
    return (
        <header>
            <img src="/imagens/banner.png" alt="O banner principal da página do Organo"/>
        </header>
    )

}

export default Banner
```
Vinicios: Agora sim temos algo próximo de CSS. Para colocar uma classe no elemento css, nós fazemos `class` igual a `banner`.

Porém, ele parece HTML e não, ele é js e `class` é uma palavra reservada do JavaScript para classes, então, como estamos trabalhando com React vamos usar `className`.

``` html
<header className="banner">
    <img src="/imagens/banner.png" alt="O banner principal da página do Organo"/>
</header>
```
Vinicios: Salvamos e vamos ver se funcionou em nosso navegador. Deu tudo certo! Criamos um componente e estilizamos ele!

Paulo: Muito bom, Vinicios! Gostaria de deixar duas terafas pequenas para quem está aprendendo aqui na Alura! A primeira é vocês olharemo o código fonte dessa página.

Queremos que no final desse curso, vocês publiquem esse projeto no seu portfólio, mas com a cara de vocês. Então esse organo-grama que vocês farão é de quem? Sua família, amigos? Faça do seu jeito!

Ficam aqui dois toques antes de irmos para o próximo vídeo.

Vinicios: Vejo vocês lá!
