### Sobre Arrow Functions:

* Acesse o artigo [Conhecendo Arrow Functions](https://www.alura.com.br/artigos/conhecendo-arrow-functions?_gl=1*ot68ab*_ga*ODM1Nzk2OTUyLjE2OTgzNDc1Mjk.*_ga_1EPWSW3PCS*MTcwMDc5Mzc0NC4xOS4xLjE3MDA3OTY1OTIuMC4wLjA.*_fplc*emVNTG9XVDNpZG1aSE11ZGM3ZFFjOCUyQng4eVFwTkc5MnkzYndpOUwwZ0Y2T0FoY0JtMmN3JTJGanNLTzljJTJCQkx0bXFwRjROdVVTYUJYcGc1alNvczBOJTJCRUcxcmNFRUJRcmlCTjdZSnhKaG12byUyQlB0UjVEaTcwWm8wclNkQ24wdyUzRCUzRA..), do Felipe Nascimento]

##

Paulo: Olá, alunos e alunas! Estamos aqui para continuar as nossas aulas de React com o Vinicios! Estou realmente gostando muito, não consigo esconder! Estamos em um ritmo muito bom mostrando o que importa e deixando de lado as arestas que depois vão aparecer para vocês no momento certo.

Vinicios, estamos com nosso projeto mais organizado, mais ambientados. Gostaria de lembrar que ainda estamos com o nosso npm rodando, não é? Se ele parar, tudo para! Agora o próximo passo é atacarmos outros componentes. E qual componente seria melhor do que um de texto? Precisamos exercitar bastante isso de criar componentes e compor componentes dentro um do outro.

Quais problemas vamos atacar agora, quais nossos próximos passos, Vinicios?

Vinicios: A ideia é partirmos agora para a ideia do formulário.

![image](https://github.com/AndreCoutinhom/alura_react_course/assets/91290799/849d595c-ce2c-4546-89cc-cfa7c5b6c996)

Imagem de um formulário. O título "Preencha os dados para criar o card do colaborador" está centarlizado em letras grandes. Logo abaixo "Nome" está em letras menores seguidos por uma campo de texto em branco, abaixo o texto "Cargo" também é seguido por um campo de texto em branco e "Imagem" também está seguida por um campo de texto em branco. "Time" é seguido por uma campo de seleção com uma pequena seta apontando para baixo preta no canto direito do campo de texto. No final do formulário uma botão azul com as bordas arredondadas tem "Criar card" escrito em letras pequenas e pretas 

Vinicios: Notem como vamos utilizar o campo de texto três vezes, porque temos os campos de "Nome", "Cargo" e "Imagem", esse último onde estará a URL da imagem. Portanto, além de termos um bom componente, precisamos conseguir reaproveitar ele de forma fácil. Esse é o nosso desafio agora.

Começaremos pelo componente de texto. Vamos colocar ele funcionando e depois vemos como vamos organizar ele dentro do formulário. Por ora, vamos pensar em colocar ele para funcionar, a estrutura com a label e com o input. Aqui estamos falando apenas da camada visual, não vamos pensar em comportamento.

Paulo: O componente de input não é só aquele componente HTML tradicional, queremos criar o input com algo escrito em cima. Você está chamando de componente de input algo que é um pouco maior do que o que estamos acostumados a ver em HTML puro.

Vinicios: Exatamente. O que conseguimos com HTML puro é no máximo o campo para digitarmos, o space holder. O "digite seu nome", por exemplo, como se fosse uma sugestão. Precisamos disso combinado com uma label, um etiqueta.

Paulo: Você vai fazer até a sombra?

Vinicios: Até a sombra!

Paulo: Agora eu quero ver.

Vinicios: Vamos lá. Voltando no VS Code, já temos dentro de "src" a pasta "componentes" onde estamos organizando. Com o botão direito do mouse vamos criar a pasta "CampoTexto".

O que você acha desse nome, Paulo? Nomear é difícil, né?

Paulo: É. Vale lembrar que aqui na Alura nós tentamos fazer o máximo em Português para não ser uma barreira, mas é importante lembrar que no trabalho do dia a dia, a maioria das empresas usam Inglês.

Vinicios: Agora dentro de "CampoTexto" criamos o "CampoTexto.js" e o "CampoTexto.css". Porém, agora vamos fazer algo um pouco diferente do Banner. Quando criamos o componente do Banner, nós fizemos um função e exportamos ela por padrão.

Pensando na organização do código, nós não costumamos criar como função assim, geralmente colocamos um função dentro de uma constante e importamos ela. Criaremos `const` chamada `CampoTexto` e dentro dela colocamos uma arrow function `{} =>` e fazemos o `export` dela no final.

``` javascript
const CampoTexto = () => {

}

export default CampoTexto
```

Vinicios: O resultado é o mesmo, é só uma forma mais organizada de fazer isso. É um estilo de código que não afeta necessariamente a performance dele. Não existe certo e errado, o importante é fazermos padronizado.

Paulo: Isso é o mesmo que se tivéssemos declarado um `function CampoTexto() {}`?

Vinicios: Isso.

Paulo: Aqui temos uma variável que é igual a essa sintaxe de função que se chama arrow function. Inclusive, temos uma formação de JavaScript que aborda bastante essa sintaxe, não se assustem. Vale a pena se aprofundar, vocês precisam dominar JavaScript.

Vinicios: A dica que dou para quem quiser entender um pouco mais sobre arrow function é procurar quais problemas ela resolve. No caso do JavaScript, ela veio para nos ajudar com problemas relacionados ao escopo de variáveis.

Paulo: Vamos deixar conteúdo da Alura+ relacionados a isso aqui.

Vinicios: Execelente. Agora seguimos com nosso `return` com parentes para retornarmos várias linhas. Se fossemos retornar, por exemplo, só um h1 poderíamos deixar sem os parênteses. Agora queremos encapsular nosso campo de texto. Olhando no Figma, ele é um conjunto de "Nome" que o label e input, isso são tags HTML padrão. Criaremos um `div` que terá um `label` chamada Nome e nosso `input`.

``` javascript
const CampoTexto = () => {
    return (
        <div>
            <label>Nome</label>
            <input />
        </div>
    )
}
```
Vinicios: Por enquanto é só isso. Agora vamos voltar ao navegador para vermos a evolução dele.

Paulo: Boa. Em nosso "App.js" precisamos agora chamar o `CampoTexto` e para isso vamos usar novamente o formato de tag HTML.

Vinicios: Exato.

Paulo: Eu comecei a perceber que o VS Code deixa em verde quando a tag é componente React e deixa em azul quando a tag é HMTL clássico.

Vincios: Exatamente, Paulo, ele nos indica quando é um componente React. Então em "App.js" digitamos CampoTexto e ele já sugere para nós norvamente.

``` javascript
functions App() {
    return (
        <div className="App">
            <Banner />
            <CampoTexto />
        </div>
    )
}
```
Vinicios: Salvamos e vamos para o navegador.

![image](https://github.com/AndreCoutinhom/alura_react_course/assets/91290799/e92b80d3-00a0-48a0-8f6a-67f615416bb2)

Vincios: Está aqui, o nome e o input. O que precisamos fazer agora é adicionar um pouco de estilo.

Note que estamos fazendo o `import` de `Banner` e de `./componente/Banner/Banner` sem o `.js` no final. Se nós tentarmos forçar esse `.js`, ele vai continuar funcionando porque podemos omitir a extensão do arquivo.

Porém, estamos repetindo `Banner/Banner` e `CampoTexto/CampoTexto`. Existe uma forma de fazermos isso sem repetir. Em vez de criarmos o "CampoTexto.js" vamos renomear esse arquivo para "index.js".

O VS Code imediatamente sugere que nós façamos os updates dos `imports`, contudo, dessa vez vamos dizer que não para fazermos na mão.

Não temos mais "CampoTexto.js" e lá no navegador já deu erro. Lembram que eu estava falando do strict mode? Aqui ele fala que o módulo não foi encontrado e não foi possível resolver o `./componentes/CampoTexto/CampoTexto`. Isso ocorre porque ele não existe mais. Nesse cenário, como o nosso arquivo.js se chama "index" podemos apagar o ultimo `CampoTexto` e deixar apenas o nome da página.

``` javascript
import CampoTexto from './componentes/CampoTexto;
```
Vinicios: Salvamos e agora ele vai nessa pasta "CampoTexto", ele percebe que existe o "index.js" dentro dela e pega para nós. Agora não precisamos mais duplicar a palavra na hora de importar. Voltando no navegador ele já está funcionando novamente. É uma maneira diferente de organizar os arquivos para facilitar a importação.

Paulo: Perfeito. Eu vi que o padrão costuma ser mais usar "index.js" como nome.

Vinicios: Acredito que não tenha um consenso porque existem pessoas que preferem usar duplicado, mas normalmente é dessa forma. Em "Banner" vamos usar outro exemplo que já vi algumas pessoas fazendo. Criamos um "index.js" em "Banner" e não fazemos mais o `export default Banner` fazemos `export const Banner` com uma arrow function.

``` javascript
export const Banner = () => {

}
```
Vincios: Em seguida, em "index.js" fazemos o `import` e um `export default Banner`.

``` javascript
import { Banner } from "./Banner";

export default Banner
```
Paulo: É só um atalho para o outro.

Vinicios: Isso, mas é comum ver dessa forma. O que ganhamos com isso é que "Banner.js" é o componente, o "index" é apenas o que estamos exportando. Assim se tivermos uma composição de componentes aqui poderemos escolher quais deles vamos exportar.

Paulo: Para não ficar tudo global e todo mundo ter acesso a tudo.

Vinicios: É essa a ideia.

Paulo: Isso é mais uma questão de organização de JavaScript puro. Agora se o que você pegou primeiro e está mais confortável com ele, com o tempo você cria as suas preferência e/ou se adapta ao que seu time costuma fazer.

Vinicios: Para finalizar, em "App.js" devemos mudar o `import`.

``` javascript
import Banner from './componentes/Banner';
```
Vincios: Aqui, seguiremos com essa abordagem do CampoTexto com esse "index.js" com o componente e o css do lado.

Nosso próximo passo agora será criar o nosso estilo. Vamos fazer novamente o className e vamos dar a classe campo-texto.

``` html
<div className="campo-texto">
```
Vincios: No css, vamos chamar essa classe `.campo-texto`.

``` css
.campo-texto {

}
```
Vincios: Em seguida, precisamos colocar uma margem `magin` para cima e para baixo de `24px` e de uma lado para o outro de `0px`.

``` css
.campo-texto {
    magin: 24px 0;

}
```
Vincios: Dando sequência, selecionamos a label dentro de `campo-texto`.

``` css
.campo-texto label {

}
```
Vinicios: Queremos que a label quebre a linha e não fique do lado do input, então vamos pedir um `display` de bloco, `block`.

Também adicionaremos um margem para baixo com `margin-bottom` de `8px`. Vamos colocar o tamanho da fonte, `font-sixe`, de `24px`. Essas informações estamos tirando do Figma que nos passaram.

``` css
.campo-texto label {
    display: block;
    margin-bottom: 8px;
    font-size: 24px;
}
```
Vincios: Repare que adicionamos o estilo aqui, mas nada disso refletiu no navegador.

Paulo: Faltou o import, né?

Vinicios: Isso. Precisamos importar o css no `CampoTexto`. Em "index.js" vamos fazer o `import` de `CampoTexto.css`.

``` javascript
import './CampoTexto.css'
```
Vincios: Agora sim, na mesma hora que fazemos o import, ele altera o estilo. "Nome" está com a fonte maior" e o input quebrou uma linha e foi pra baixo.

Já que estamos em "CampoTexto" vamos colocar o `placeholder` de `Digite o seu nome`.

``` javascript
return (
    <div className="campo-texto">
        <label>Nome</label>
        <input placeholder='Digite o seu nome'>
    </div>
)
```
Vinicios: Vamos para o estilo do `input`. No css, vamos selecionar ele dentro do elemento `campo-texto` da mesma maneira que fizemos com a `label`.

``` css
.campo-texto input {

}
```
Vinicios: Faremos o `background-color` dele como branco, ou seja, `#FFF`. Também faremos um `box-shadow` para adicionarmos o sombreado com os valores `10px 10px 30px` com a cor `rgba(0, 0, 0.06)`

``` css
.campo-texto input {
    background-color: #FFF;
    box-shadow: 10px 10px 30px rgba(0, 0, 0.06);
}
```
Paulo: Normalmente os designers que fazem o Figma passam isso para nós, né?

Vincios: Exatamente. Além disso, vamos pedir para ele pegar 100% da tela com `width`. Vamos usar essa estratégia porque se pedirmos para pegar `100%` da tela quem vai dizer o tamanho é onde colocarmos ele, certo?

Paulo: Vamos criar um outro componente na próxima aula que é o Formulário onde colocamos vários campos que também será um componente React.

Vinicios: Isso. Com o tempo vamos pegando esses "macetes". Uma boa estratégia é bom ser `100%` porque quem vai limitar o tamanho dele é o seu container.

Vamos tirar a borda, então `border` será `none`, vamos aumentar o tamanho da fonte para `24px` e daremos um `padding` interno de `24px`.

``` css
.campo-texto input {
    background-color: #FFF;
    box-shadow: 10px 10px 30px rgba(0, 0, 0.06);
    width: 100%;
    border: none;
    font-size: 24px;
    padding: 24px;
}
```
Vinicios: Vamos salvar. Aqui tem um trick de css. Ele está vazando para fora, ele tem 100% da tela, mas ele está indo além porque ele não está considerando o `padding` com os `100%`.

Queremos que ele tenha o tamanho de `100%` levando em consideração tudo. Então, temos que fazer o `box-sizing` como `border-box`.

``` css
.campo-texto input {
    background-color: #FFF;
    box-shadow: 10px 10px 30px rgba(0, 0, 0.06);
    width: 100%;
    border: none;
    font-size: 24px;
    padding: 24px;
    box-sizing: border-box;
}
```
Vincios: Agora ele não está mais vazando para o lado. Olhando assim, parece que está bem similar ao que temos no Figma.

![image](https://github.com/AndreCoutinhom/alura_react_course/assets/91290799/bf0c4cd5-bbd4-47dd-8621-ae50865eb789)

Paulo: Está, sim.

Vinicios: Temos a base pronta do campo de texto, porém, no Figma temos "Nome", "Cargo" e "Imagem".

Aqui, no `CampoTexto` nós fizemos o a label como hard coded. Não conheço nenhuma boa tradução para isso, mas ele está "forçadamente no código". Já ouvi o termo "marretado no código". Ou seja, nossa `label` está "marretada" no código e como vamos reaproveitar ela dessa forma?

Não seria legal se pudéssemos dizer que a `label` fosse `Nome`, por exemplo assim:

``` html
<CampoTexto label="Nome"/>
```

Paulo: Receber como parâmetro, perfeito.

Vinicios: Exato. E ficaria assim com todos.

``` html
<CampoTexto label="Nome"/>
<CampoTexto label="Cargo"/>
<CampoTexto label="Imagem"/>
```
Paulo: E se fizermos assim agora e salvar ele vai simplesmente ignorar esse parâmetro e vai criar os mesmos porque estão escritos.

Vinicios, tenho uma ideia! Como esse vídeo teve bastante detalhes, vamos fazer essa passagem de parâmetros no próximo vídeo?

Vinicios: Vamos lá!
