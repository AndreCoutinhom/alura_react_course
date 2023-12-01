Paulo: Vinicios, para entendermos melhor todo o ciclo de vida e o poder do React temos que entender os disparos do evento, como gerenciar o estado das nossas variáveis e como o estado da nossa variável interna está associado aos componentes visuais.

Vinicios: O que precisamos agora é garantir que tanto a alteração da minha variável interna quanto a do usuário tem esse vínculo do componente que precisa ser atualizado novamente. A lógica para fazer isso é bem parecida com o que temos feito até aqui, mas com uma diferença crucial: em vez de termos o valor de `let`, nós chamaremos um hook.

Um hook é um gancho. É algo que o React nos entrega para que seja possível manter um estado dentro de uma função. O hook que vamos usar aqui é o `useState`. Sempre que encontrarem um o use, saibam que é um hook. O React já importa ele direto.

``` javascript
import { useState } from 'react'
```
Vinicios: O `useState` será uma string vazia `''`, queremos usar um estado de uma string que é um valor digitado no `input`. Porém, queremos guardar uma referência para ele.

``` javascript
const [] = useState('') 
```
Vinicios: Ele vai nos retornar dois valores, o valor em si e uma função que é nosso setter. Quando queremos alterar esse valor, vamos chamar essa função, não podemos alterar o valor direto por atribuição. Então temos as variáveis `valor` e `setValor`.

``` javascript
const [valor, setValor] = useState('') 
```
Vinicios: Essa sintaxe significa "quero desestruturar o meu array e pegar a primeira e a segunda posição do array". Aqui é JavaScript.

Paulo: Normalmente usaríamos `let valor = ''`, mas aqui usamos esse `useState` porque ele prepara uma pseudo variável, um objeto para ler e um para escrever, que é o setter. Dessa forma, se chamarmos pela setter, ele passa por uma séries de hooks, filtros, desparos do React para participar de seu ciclo de vida interno. É isso, Vinicios?

Vinicios: É exatamente isso, Paulo. E em vez de fazermos a atribuição direta de `valor = evento.target.value`, vamos fazer um `setValor`.

``` javascript
const aoDigitado = (evento) => {
    setValor(evento.target.value)
    console.log(valor)
}
```
Vinicios: Do jeito que está posto aqui temos que ter o mesmo efeito do `console.log()` e o digitar tem passar a funcionar. Ao voltar no navegador, é possível ver que isso está acontecendo. No VS Code, vamos voltar para o nosso valor padrão `'Guilherme Silveira'`.

``` javascript
const [valor, setValor] = useState('Guilherme Silvera') 
```
Vinicios: Salvamos e voltamos para o navegador. Novamente ele definiu todos os campos de texto como "Guilherme Silveira". Porém, quando alterávamos nada acontecia, ficava travado em "Guilherme Silveira" e agora conseguimos alterar.

Isso ocorre porque conforme esse valor muda, o nosso estado muda junto e se o estado muda junto, o React sabe que ele tem que renderizar o componente diferente. Com o `value` e o `State` atrelados, uma influencia o outro. Mapeamos a variável para o DOM, para o HTML.

Agora que está tudo funcionando, nós precisamos elevar esse estado. Cada campo de texto precisa ter seu estado individual, então ele não pode ficar do lado do componente `CampoTexto`, ele precisa vir de um lugar mais alto, do formulário.

Não teremos esse estado local e ele será recebido via `props`, então o `value` será o `props.valor`

``` html
<input value={props.valor} onChange={aoDigitado} required={props.obrigatorio} placeholder={placeholderModificada}/>
```
Vinicios: E o `onChange` vai chamar o evento `aoDigitado`, então a `props` será `aoAlterado()` e passamos o valor `evento.target.value`.

``` javascript
const aoDigitado = (evento) => {
    props.aoAlterado(evento.target.value)
}
```
Vinicios: Estamos elevando o estado, o `CampoTexto` está delegando o controle do estado para quem for usá-lo, ele em si não vai controlar seu própio estado.

Paulo: Mas para isso funcionar precisamos passar para o `CampoTexto` por meio de parâmetros o `valor`, que deve ser um state, e uma função que se chama `aoAlterado`. Você está considerando que esses dois existam, é isso?

Vinicios: Exatamente. Inclusive, se olharmos agora e tentarmos executar o código...

Paulo: Vai quebrar.

Vinicios: Ele vai dar um erro aqui dizendo que `aoAlterado` não é um função, porque ainda não passamos nada ali. É o que faremos a seguir.

Em "Formulario" > "index.js", o que precisamos ter?

Paulo: Três states, um para cada campo de texto e uma função para indicar o que deve ser feito quando houver uma alteração.

``` javascript
const [nome, setNome] = useState('')
const [cargo, setCargo] = useState('')
const [imagem, setImagem] = useState('')
```
Vinicios: Em seguida vamos, no primeiro `CampoTexto` vamos adicionar `valor` e `aoAlterar`. O `valor` dele é o `nome` e o `aoAlterado` é igual a `valor => setNome(valor)`. Faremos o mesmo para os outros dois.

``` html
<CampoTexto 
    obrigatorio={true} 
    label="Nome" 
    placeholde="Digite seu nome"
    valor={nome}
    aoAlterado={valor => setNome(valor)}
/>
<CampoTexto 
    obrigatorio={true} 
    label="Cargo" 
    placeholder="Digite seu cargo"
    valor={cargo}
    aoAlterado={valor => setCargo(valor)}
/>
<CampoTexto 
    label="Imagem" 
    placeholder="Digite o endereço da imagem"
    valor={imagem}
    aoAlterado={valor => setImagem(valor)}
/>
```
Vinicios: Agora temos os três estados! Ainda não temos o de `ListaSuspensa`, mas faremos ele depois. Vamos fazer o `console.log()` das outras variáveis e ver se conseguimos combinar tudo.

``` javascript
const aoSalvar = (evento) => {
    evento.preventDefault()
    console.log('Form foi submetido => ', nome, cargo, imagem)
}
```
Paulo: Fizemos um pouco de copypaste aqui, não é, Vinicios?

Vinicios: Isso. Aqui não tem muito o que fazer porque são três estados diferentes. Poderíamos até pensar em uma forma de ter um objeto e gravar tudo lá dentro, mas cada abordagem tem os prós e contras.

Paulo: Poderíamos com aquela abordagem que você começou a fazer, por exemplo. Se tivéssemos criado um `CampoTextoCargo`, `CampoTextoNome` e `CampoTextoImagem` como componentes separados, poderíamos deixar o estado dentro de cada componente, certo?

Então existem abordagens diferentes, umas mais reutilizáveis e outras menos. As mais reutilizáveis talvez tenham mais código fora, isso vai variar. Algumas decisões que o Vinicios tomou, vocês em casa poderiam tomar um pouco diferente. De novo, vocês podem exercitar isso, mantenham a curiosidade!

Porém, o mais importante é o conceito do state: temos valor, que é o que lemos, e o setter para o React saber que queremos uma alteração.

Vinicios: Vale a pena, inclusive, explorar possibilidade que conforme a aplicação vai evoluindo, você vai vendo qual faz mais sentindo em qual cenário. Esse termometro vem com a prática.

Agora falta testarmos todas as alterações que fizemos aqui. Na teoria, se submetermos o formulário, tem que aparece o nome, o cargo e a imagem.

No navegador vou preencher o "Nome" como "Vinicios", o meu "Carggo" como "Desenvolvedor" e a imagem um "http..." qualquer. E no Console, além de aparecer que o formulário foi submetido, aparece também os dados que eu submeti.

```
Form foi submetido => Vinicios 
Desenvolvedor http...
```
Vinicios: Agora temos o vínculo que precisávamos! Falta apenas um pequeno detalhe: o time! O "Time" é o componente de `ListaSuspensa` que é um `select` e não um `input`. Contudo, aqui é mais do mesmo, temos que fazer a mesma estrutura do evento, do state e do setState.

De volta ao VS Code, vamos abrir o "index.js" de "ListaSuspensa" e vamos fazer o mesmo que fizemos com o `input` porque as propriedades são as mesmas.

O `value` do `select` vamos receber via `props.valor` e no `onChange` vamos chamar o `props.aoAlterado`. Vamos manter o nome do evento para ficar consistente.

``` html
<select onChange={evento => props.aoAlterado(evento.target.value)} required={props.required} value={props.value}/>
```
Vinicios: Agora no select do "index.js" de "Formulario", criamos o estado do `time`.

``` javascript
const [time, setTime] = useState('')
```
Vinicios: E em `ListaSuspensa` adicionamos o `valor` e `aoAlterar`

``` html
<ListaSuspensa
    obrigatorio={true}
    label="Time"
    itens={times}
    valor={time}
    aoAlterar={valor => setTime(valor)}
/>
```
Vinicios: Para fechar, colocamos o `console.log()` de `time` também.

``` javascript
console.log('Form foi submetido => ', nome, cargo, imagem, time)
```
Vinicios: Novamente no navegador, preencho "Nome" como "Vinicios", "Cargo" como "Desenvolvedor", imagem um "http..." qualquer e "Time" de "Front-End". Mandamos criar o card e no Console está tudo exatamente como precisamos!

Agora precisamos pegar esse colaborador que acabou de ser cadastrado e mandar ele para algum lugar e guardá-lo para termos uma referência e exibirmos tal como está no Figma!

Paulo: Perfeito porque agora que temos o state `cargo`, o state `nome` e podemos pegar esses valores e trabalhar com eles e jogar no card de baixo, que é o principal movimento para completar tudo do nosso mecanismo principal.

Vinicios: Exatamente isso! Temos o colaborador nas mãos e precisamos pensar em uma maneira de guardar um referência para ele em algum lugar para que ele apareça em baixo nos cards.

Note que agora faremos uma comunicação entre os componentes. A responsabilidade do formulário é montar nosso colaborador, o que o restante da aplicação fará com ele, já não é mais responsabilidade do formulário. Teremos que criar algo intermediário para isso.

É o que vamos fazer a seguir, mas no próximo vídeo. Vamos lá, Paulo?

Paulo: Vamos!
