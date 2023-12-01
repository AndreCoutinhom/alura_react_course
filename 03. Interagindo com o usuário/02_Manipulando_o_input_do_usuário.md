Paulo: Olá, alunos e alunas! Estamos aqui com o Vinicios dando esse show de como mergulharmos no React com JavaScript! O Vinicios ainda não sabe, mas no final do curso vou fazer uma sessão de perguntas e respostas com ele. Porque ainda existem muitas questões para sanar como o tal do Typescript, o GraphQL, ou "será que devemos estudar o Node"? E o npx e npm que estão rodando?

Já passamos por alguns passos muito importantes nas outras aulas do funcionamento geral e agora chegou na parte principal: como vamos pegar os dados que digitamos no campo de texto?

Nós demos um `console.log()` e ele disse que o formulário foi submetido, mas não é isso o que queremos. Nós queremos pegar esse valor e chamar uma API de um micro serviço e guardar em um banco de dados. Queremos pegar o cadastro e criar um card do Organo.

Vinicios: Se estivessemos fazendo isso com o JavaScript vanilla, nós varreríamos o DOM, procuraríamos o `input` e pegaríamos o valor dele. Algo mais ou menos assim, no React é diferente.

No VS Code, vamos em "CampoTexto" > "index.js".

``` javascript
const CampoTexto = (props) => {

    const placeholderModificada = `${props.placeholder}...`

    return (
        <div className="campo-texto">
            <label>
                {props.label}
            </label>
            <input required={props.obrigatorio} placeholder={placeholderModificada}/>
        </div>
    )
}

export default CampoTexto
```
Vinicios: O que nós queremos aqui é, de alguma forma, ficar "ouvindo" o `input` e toda vez que ele for alterado executar algo. Então vamos fazer um `onChange` nele. Toda vez que ele for alterado, ou seja, a cada letra que o usuário digitar, queremos executar uma função `aoDigitado`

``` html
<input onChange={aoDigitado} required={props.obrigatorio} placeholder={placeholderModificada}/>
```
Vinicios: Em seguida fazemos uma `const` da arrow function `aoDigitado`.

``` javascript
const aoDigitado = () => {

}
```
Vinicios: Aqui, teremos acesso ao `evento` de digitação. É o mesmo conceito do formulario, porém, para esse caso o evento não é de Submit e sim de `Change`.

Dado nosso evento, vamos fazer um `console.log()` do que está sendo digitado. Nós pegamos o valor do que está sendo digitado com `evento.target.value`. O `target` é um evento do JavaScript. Agora sempre que alguém digitar algo no campo de texto, faremos o `console.log()` desse valor.

``` javascript
const aoDigitado = (evento) => {
    console.log(evento.target.value)
}
```
Vinicios: No navegador, ao digitar cada letra, o Console já nos mostra o valor final em paralelo. Então, está funcionando! Com isso, já é possível guardar esse valor. Voltando ao VS Code, vamos criar uma variável `let` que chamaremos de `valor` e diremos que ela começa como uma string vazia.

``` javasctipy
let valor = ''
```
Vinicios: Cada vez que alguém digitar vamos atribuir o evento.target.value e então fazemos o console.log() desse valor.

``` javascript
const aoDigitado = (evento) => {
    valor = evento.target.value
    console.log(valor)
}
```
Vinicios: Agora estamos guardando a referência em uma variável. O comportamento visual deveria ser o mesmo, mas tendo uma variável, conseguimos brincar e fazer com ela o que precisarmos. Temos o valor em uma variável então se dissermos que o `valor` inicial é `Guilherme Silveira`, o que você acha que vai acontecer lá no navegador, Paulo?

```
let valor = 'Guilherme Silveira'
```
Paulo: O valor vai aparecer pronto.

Vinicios: Não, ainda não temos o valor lá, está em branco! O que fizemos foi ouvir o `onChange` do `input` e conforme esse valor mudava, nós fomos capturando.

Paulo: Nós nunca colocamos o valor, né?

Vinicios: Exatamente! Porque nós só fizemos de um lado, precisamos agora fazer para o outro lado! Nós queremos vincular os dois então tanto a variável quanto o que está digitado lá no navegador tem que ser consistentes. Então, o `input` tem um `value` que será `valor`.

``` html
<input value={valor} onChange={aoDigitado} required={props.obrigatorio} placeholder={placeholderModificada}/>
```
Vinicios: Agora fechamos o ciclo, certo? Temos o valor, temos o value do input e quando esse valor for alterado, vamos atribuir. Salvamos e vamos testar no navegador!

Ele já começou tudo como "Guilhermo Silveira" porque só temos um campo de texto, então o valor padrão é o mesmo para todos. Agora, quando tentamos digitar, o Console apenas repete `Guilherme Silveira` várias vezes.

Paulo: Toda hora ele está excutando `let valor = 'Guilherme Silveira'`.

Vinicios: Porém, ele não está alterando no HTML. O React funciona baseado no JavaScript, porém, se o componente não tiver certeza de que precisa ser renderizado novamente, ele não vai atualizar o DOM. Se nós quisermos que ele reaja a isso, precisamos fazer de um jeito muito específico.

Agora precisamos fazer com que esse valor seja definido em duas vias para que se definirmos, por algum motivo como vindo de uma API ou pegando um valor padrão, nós queremos que isso reflita no HMTL.

Isso nós chamamos de estado do componente. Se o estado for alterado, o componente precisa ser renderizado novamente. Precisamos usar algo do React que indique essa mudança de estado.

Paulo: Vou colocar uma observação porque gostei bastante dessa exploração. Você usou um `onChange` e o `value` do nosso `input`, que são tags do HTML padrão, e você foi brincando com o `console.log()`. É muito importante para quem está estudando agora fazer essas brincadeiras para entender o que chamamos de ciclo de vida.

Chegou um momento em que o Vinicios está nos mostrando de uma maneira muito delicada o ciclo de vida. Como é o estado, quem o React chama ou deixa de chamar e ele está fazendo isso enquanto exploramos. Assim, o conteúdo vai ficando mais óbvio, nós vamos entendendo o funcionamento do React enquanto aprendemos a usá-lo. Dessa forma nem a a teoria vem antes da prática e nem a prática vem antes da teoria, aqui na Escola Front-End nós buscamos misturar os dois em um compasso bem delicado.

Então, até o próximo vídeo!

Vinicios: Vamos lá que agora está na hora de mexermos no coração do React, que é o estado do componente.
