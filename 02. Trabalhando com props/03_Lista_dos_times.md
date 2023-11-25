Paulo: Vinicios, para continuarmos nosso projeto do Figma, temos um quarto campo do formulário que passamos batido. É esse "Time" que tem até uma flecha, um combo box que é um `select` no HTML para listar os times. É isso que vamos aprender a fazer agora, mais um componente que tem alguns recursos a mais?

Vinicios: Exatamente, Paulo. Ele ficou por último justamente porque é diferente dos demais. O input é um componente mais simples em relação a funcionalidade, ele é apenas uma caixa de texto.

O "Times" precisa mostrar uma lista pré definida. Ou seja, vamos criar a lista e para cada item vamos adiconar uma opção.

Além do time ter o nome dele, cada time tem duas cores auxiliares: uma pro fundo e outra para o detalhe do card. Então, precisamos tomar o cuidado de fazer a lista já considerando isso.

Nossa lista precisa estar preparada para receber todos esses valores. Ou seja, não podemos simplesmente colocar tudo no HTML, de alguma forma precisamos ter essa lista de algum lugar.

De volta ao VS Code, vamos criar outro componente que, por debaixo dos panos, vai utilizar a tag `select` e option do HTML. Seguindo o padrão que usamos em português, nossa lista será chamada "ListaSuspensa", que é a tradução mais parecida que encontrei de DropDown. É uma lista de elementos pré determinados.

Paulo: Essa lista não é só no time, Vinicios? Ela pode servir para outros times?

Vinicios: Exatamente. Vamos supor que em algum determinado momento os cargos que estamos trabalhando aqui como texto puro sejam pré determinados, então poderemos utilizar essa ListaSuspensa para esses cargos. Ou seja, ela é o componente mais genérico e abragente. É uma lista de strings, não importa do que seja.

Vamos seguir com a mesma estrutura e criar a subpasta "index.js" para fazermos o componente e o "ListaSuspensa.css" para aplicar o estilo.

Em "index.js" repetimos a fórmula com o `import` do css, a constante de `ListaSuspensa` recebendo a arrow function e o `export`.

``` javascript
import './ListaSuspensa.css'

const ListaSuspensa = () => {

}

export default ListaSuspensa;
```
Vincios: Da mesma forma que fizemos no `CampoTexto`, vamos fazer um `return` com uma `div` e uma `label`. Agora não precisamos mais fazer estático porque já sabemos como trabalhar com props. Podemos colocar as `props` em `ListaSuspensa` e o `props.label` em `label`.

``` javascript
const ListaSuspensa = (props) => {
    return (
        <div>
            <label>{props.label}</label>
        </div>
    )
}
```
Vincios: Logo depois da `label` teremos o `select` e ele terá algumas `options`.

Precisamos de alguma forma interar em cima dessa lista, ou seja, de alguma maneira precisamos receber uma props.itens e para cada item dessa lista temos que renderizar o `options`.

Com o React nós temos um jeito muito específico de realizar isso, que é uma forma de iterar em cima desse elemento renderizando o HTML para cada item da lista.

Para quem já trabalhou com outros frameworks do tipo Angular ou View, normalmente para fazer isso, nós utilizamos um `for` dentro do `option` com se fosse uma diretiva. No caso do React, nós não temos isso, precisamos fazer isso de um modo mais parecido com o JavaScript.

Precisamos de um método que faça uma iteração dessa lista e retorno uma lista diferentes. Queremos uma lista de strings e queremos que depois dessa iteração, tenha uma lista de elementos do JSX. Para fazer isso com o React, vamos utilizar o `map`.

Todo o array `[]` JavaScript pode fazer esse métodos `.map`. Para cada item da lista ele vai retornar um array novo manipulado. É como se tívessemos uma lista de nomes e vamos trasnformá-la em uma lista de `options`: ele vai percorrer, mas vai retornar algo diferente. Perceu a diferença, Paulo?

Paulo: Percebi, porque se fosse só o `forEach` ele ia percorrer e fazer algo. O `map`, não, ele percorre, faz algo e devolve uma nova lista transformada. É a grande diferença de um mapa para um `forEach`, esse último devolve um `void`, ele não devolve nada, ele apenas executa uma ação.

O `map` executa e cria uma nova caixa, um novo array com itens já tranformados, mapeados por uma transformação. É isso?

Vinicios: Exatamente. Para quem quiser ir mais a fundo nesse tema, vamos deixar em uma atividade um conteúdo do Mario Souto que fala justamenet sobre a diferença de um `forEach` e um `map`.

Seguindo com o código, dentro de `select` vamos fazer um `props.itens.map`. Para percorrermos aqui, teremos para cada item da lista, um `item`. Vamos passar uma arrow function porque para cada `item` queremos retornar uma `<option>`.

E dentro de `<option>` queremos imprimir o valor desse `item`. Portanto, teremos uma lista de strings `{item}

``` javascript
return (
    <div>
        <label>{props.label}</label>
            <`select`>
                {props.itens.map(item => <option> </option>)}
            </`select`>
    </div>
)
```
Vincios: Aqui pode ser um pouco complicado, Paulo. Como só temos uma instrução e o resultado dela estamos retornando, a arrow function fica muito enxuta. Porém, fazer isso é o mesmo que abrir chaves e fazer um return dele.

``` jsx
<select>
    {props.itens.map(item => {
        return <option>{item}</option>
    })}
</select>
```
Vinicios: Como fizemos tem o mesmo efeito, é apenas uma forma de escrever menos código. Nesse caso, é uma instrução muito simples: para cada `item`, retorna uma `<option>`.

Paulo: Vale lembrar: não podemos nos assustar com isso, porque isso aparece o tempo inteiro com React. Do map não tem como fugir. O map aparece com muita frequência. `if` e `for` não aparecem, o que aparece é `map` e mais alguns que veremos adiante.

Vinicios: Exatamente. A quantidade de recursos que podemos usar dentro do JSX é bem limitada. Esse `map` vai sempre aparecer quando tivermos uma iteração em cima de uma lista renderizando na tela.

Na teoria, temos a casca do que precisamos para começar. Vamos testar isso! Em "Formulario > index.js" vamos adicionar `<ListaSuspensa>`. Em seguida precisamos passar a lista de `itens` que serão nossos times.

``` jsx
<ListaSuspensa itens={times}/>
```
Vinicios: Para isso, criaremos uma `const` chamada `times` com uma lista de strings. Começamos pela escola de `Programação` seguida por `Front-End`, `Data Science`, `Devops`, `UX Design`, `Mobile` e `Inovação e Gestão`.

``` javascript
const times = [
'Programação',
'Front-End',
'Data Science',
'Devops',
'UX e Design',
'Mobile',
' Inovação e Gestão'
]
```
Vinicios: Na teoria, isso é tudo que precisamos antes de começarmos a estilizar. Se olharmos para o HTML, nossa lista está funcinando. Porém, o Console está nos alertando que cada item da nossa lista deveria ter uma chave única chamada `key`.

O React precisa disso para controlar a renderização e saber quando ele precisa atualizar um item ou não. Em nosso caso, podemos usar o próprio nome do time como chave.

Em "index.js" de "ListaSuspensa" vamos adicionar a propriedade `key`.

``` jsx
{props.itens.map(item => {
    return <option key={item}>{item}</option>
})}
```
Paulo: Isso é um erro ou um alerta?

Vinicios: Nesse caso ele é um erro, mas que não é um bloqueio, ele passaria. Nesse nosso caso, a lista é simples de um componente simples, mas ele poderia ser um componente muito complexo e sem essa chave o React perde o controle de quando renderizar de novo.

Aproveitando a pergunta, vou dar uma outra dica. O `map` nos dá o `item`, o valor, e o `index`, a posição dele no array. Poderíamos pegar a posição do `item` no array, que é única e colocar como chave e isso funcionaria.

Entretanto, se por algum motivos trabalharmos em remover algum item dessa lista, o React pode ser perder e não analizar o índice anterior porque a chave é a mesma.

Agora precisamos aplicar o estilo do `select` para ele ficar mais parecido com nosso campo de texto. Em "ListaSuspensa.css".

``` css
.lista-suspensa {

}

.lista-suspensa `select` {

}
```
Vincios: Como a estilização do `select` é muito parecida com de `campo-texto input` podemos copiar os estilos e fazer as alterações necessárias.

``` css
.lista-suspensa select {
    background-color: #fff;
    box-shadow: 10px 10px 30px rgba(0, 0, 0, 0.06);
    width: 100%;
    border: none;
    font-size: 24px;
    padding: 24px;
    box-sizing: border-box;
}
```
Vinicios: A `label` de `ListaSuspensa` também é parecida com a `label` de `campo-texto` então podemos copiar ela também.

``` css
.lista-suspensa {
    display: block;
    margin-bottom: 8px;
    font-size: 24px;
}
```
Vinicios: Está perfeito! Agora está faltando o último elementos do `form`, que é o botão e precisamos pensar como vamos mandar os dados preenchidos para alguma lugar! Ou seja, está na hora de darmos comportamento para os nossos componentes.

Paulo: E então vamos ver uma das maiores vantagens do React também!

Vinicios: Exatamente. Vamos começar a linkar o valor do seu input com uma variável, o que chamamos de data binding. Vamos lá?
