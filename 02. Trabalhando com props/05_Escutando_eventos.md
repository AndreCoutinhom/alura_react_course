Paulo: Vinicios, o que queremos agora é fazer o nosso botão reagir a um clique. Chegamos em um momento em que queremos, de acordo com o que acontece, poder fazer algo com a nossa aplicação.

O que você preparou para nós?

Vinicios: Agora nós vamos começar a interagir do jeito React com os eventos do HTML. Se tivessemos fazendo o HTML de modo tradicional com o JavaScript vanilla, nós provavelmente pegaríamos um `documento` e faríamos um `querySelector` procurando pelo `form`, algo mais ou menos assim:

``` javascript
const form = document.querySelector('form')

form.onsubmit = ()
```
Vincios: Seria algo nessa linha: iríamos encontrar o formunlário e ficar ouvindo a submissão dele. Com o React, a liha de raciocínio é mesma, mas é um pouco mais fácil.

Em `form`, em su própria linha, damos um espaço e fazemos um `onSubmit`. Poderíamos ouvir o `click` do botão, mas se optaramos por isso, não conseguiremos fazer com que exista pelo menos uma validação do HTML. Poderíamos dizer, por exemplo, que o `CampoTexto` é obrigatório ou não e se ouvirmos o `click` não teremos a validação do formulário HTML.

Por isso, vamos ouvir o `Submit`. Quando alguém submeter, criaremos uma arrow fuction `const aoSalvar`. Em seguida, mandamos o `console.log()` de `Form foi submetido`.

``` jsx
const aoSalvar = () => { 
    console.log('Form foi submetido')
}
```
Vinicios: E por fim, vamos dizer que quando o formulário for submetido, `aoSalvar` é a função que queremos executar.

``` html
<form onSubmit={aoSalvar}>
```
Vinicios: Quando clicarmos no botão, ele tem que executar esse código de `aoSalvar`.

Paulo: A sintaxe é, não, é `{aoSalvar}` entre chaves?

Vinicios: Exatamente, Paulo. Sempre que nós queremos linkar um variável JavaScript ali dentro, é o mesmo conceito: entre chaves e o valor que queremos. Como a nossa constante é uma função, essa função será executada quando esse evento `onSubmit` for chamado.

Podemos ver algumas variantes disso com arrow functins, por exemplo, `<form onSubmit={() => aoSalvar()}>`. Dessa forma, se quisermos manipular algo, nós conseguimos, mas como esse não é o nosso vamos deixar do jeito anterior apenas vinculando a função, sem executar. Assim, nós somente executamos ela se `onSubmit` acontecer.

Porém, no navegador, pelo Console, é possível observar que ele ainda está recarregando bem rapidamente. Isso acontece porque o comportamento padrão está sendo executado, que é fazer o `submit` da página para o próprio endereço.

Para isso parar, nós precisamos interceptar essa ação. Em nosso código, receberemos, por parâmetro, o evento do JavaScript, do próprio formulário. O que conseguimos fazer para evitar que isso ocorra, é chamando o método `event.preventDeafult()`, que previne o comportamento padrão.

``` jsx
const aoSalvar = () => { 
    evento.preventDefault()
    console.log('Form foi submetido')
}
```
Vinicios: Agora se salvarmos e voltarmos ao navegador, agora sim ele não carrega mais porque nós temos o controle da situação!

O HTML 5 tem uma validação por padrão, nós podemos dizer para o `input`, por exemplo, que ele é obrigatório.

Se fossemos até o componente e criássemos algo como `CampoTexto obrigatorio={true}`, poderíamos reaproveitar essa validação. Assim, de passamos aqui, vamos em "CampoTexto" e podemos dizer que o `input` é `required` se a `props` for `obrigatoria`.

``` jsx
return (
    <div className="campo-texto">
        <label>
            {props.label}
        </label>
        <input required={props.obrigatorio} placeholder={placeholder} />
    </div> 
)
```
Vinicios: Se o `obrigatório` for `true` o `input` vai ser `required`. Dessa forma, conseguimos vincular os dois mundos, ou seja, temos a validação nativa do HTML 5 e o formulário combinando com o estado do React. Sendo assim, se tentarmos submeter um formulário com esse campo em branco, o navegador não deveria deixar.

Ao voltar ao navegador, ele já está pedindo para que nós preenchamos o campo. E isso nós fizemos com HTML e não com o React.

Agora vamos deixar `ListaSuspensa` e todos os `CampoTexto` como `obrigatório`, com exceção da `Imagem`.

``` html
<CampoTexto obrigatorio={true} label="Nome" placeholde="Digite seu nome"/>
<CampoTexto obrigatorio={true} label="Cargo" placeholder="Digite seu cargo"/>
<CampoTexto label="Imagem" placeholder="Digite o endereço da imagem"/>
<ListaSuspensa obrigatorio={true} label="Time" itens={times}/>
```
Vinicios: No navegador, se adicionarmos todos os dados e apertar o botão, ele submete o formulário, mas de deixarmos, por exemplo, o "Cargo" de fora, ele não envia o formulário. Ou seja, o HTML 5 está trabalhando para nós e nós estamos ouvindo o evento de `Submit` quando necessário.

Paulo: E para pegarmos o nome e o cargo que digitarmos?

Vinicios: Você está dando um spoiler do nosso próximo vídeo, porque nós vamos fazer isso, mas não agora. Posso adiantar, porém, que ainda vamos pensar em ações orientadas à eventos. Vamos ouvir alguns eventos do `input` que vão nos ajudar a capturar o valor que foi digitado e guardar em uma variável.

Vamos ver como fazemos isso?

Paulo: Vamos!
