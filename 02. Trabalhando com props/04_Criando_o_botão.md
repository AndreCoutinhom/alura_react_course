Paulo: Agora para complentarmos e continuarmos na trilha desse Figma, o único item que falta é o botão. Nós vamos usar um `input type="button"` normal do HTML, vamos criar um componente `Botao` ou vamos criar componnete criador de cards?

Vinicios: Vamos seguir na mesma linha de criar componentes reaproveitáveis. Se criássemos um componente criador de card, por exemplo, estaríamos muito acaplados a esse cenário e teríamos mais dificuldade de reapriveitá-los.

Vamos começar com o conhecendo básico que já temos. Em "componentes" do VS Code vamos criar uma pasta "Botao" e dentro dela criamos o "index.js" e o "Botao.css".

Na primeira linha do "index.js" fazemos o `import` do CSS, a constante arrow function recebendo `props` com o `return` de `button`. Dentro de `button` colocamos o `props.texto`, que é o texto do botão. E finalizamos com o `export default`.

``` javascript
import './Botao.css'

const Botao = (props) => {
    return (<button
        {props.texto}
    </button>)
}

export default Botao
```
Vinicios: Em seguida, fazemos o `import` em "Formulario" para ver como está ficando. Em `<form>`, logo abaixo de `ListaSuspensa` vamos chamar o `Botao`. Passamos a propriedade de `texto` que será `Criar Card`.

``` html
<section className="formulario">
    <form>
        <h2>Preencha os dados para criar o card do colaborador</h2>
        <CampoTexto label="Nome" placeholde="Digite seu nome"/>
        <CampoTexto label="Cargo" placeholder="Digite seu cargo"/>
        <CampoTexto label="Imagem" placeholder="Digite o endereço da imagem"/>
        <ListaSuspensa label="Time" itens={times}/>
        <Botao texto="Criar Card"/>
    </form>
</section>
```
Vinicios: Nosso botão já está no navegador!

![image](https://github.com/AndreCoutinhom/alura_react_course/assets/91290799/325762e3-42c4-4abc-ad7f-ba9f7a612600)

Vinicios: Ele está até com o comportamento normal dele! Se nós não instruirmos nada de diferentes, um botão dentro de um formlário por padrão submete o formulário. Então quando clicamos nele, ele submete o formulário.

Paulo: Perfeito! Para a própria URL.

Vinicios: Isso, para a própria URL. Agora vamos estilizar o botão. Novamente, começamos com o `className` em `Botao`.

``` jsx
const Botao = (props) => {
    return (<button className='botao'>
        {props.texto}
    </button>
}
```
Vinicios: Seguimos para o 'Botao.css" e começamos com `.botao` novamente pegando os estilos do Figma.

``` css
.botao {
    background-color: #6278f7;
    border-radius: 10px;
    font-weight: 700;
    font-size: 18px;
    padding: 32px;
    border: none; 
    cursor: pointer;
    color: #FFF;
    margin: 32px 0;
}
```
Vinicios: O que falta é a ideia do hover, que é só mudar a cor da fonte. Quando o `.botao` estiver com o mouse `hover`, queremos a cor `#95FFD4`.

``` css
.botao:hover {
    color: #95FFD4
}
```
Vinicios: Deu certo, mas podemos melhorar! O texto do botão nós estamos recebendo via `prop` o que para esse cenário funciona, porém, esse botão poderiam ser uma ícone, por exemplo, ou ter uma imagem dentro dele. Se fossem esses os caso, fazer isso via `props` seria complicado.

O React no traz uma outra maneira de passar elementos para dentro do componente que se parece com o HTML como nós o conhecemos.

Vamos abrir o "index.js" do "Formulario". Aqui, temos o `Botao`. Seria interessante se pudessemos fazer algo como

``` html
<Botao>

</Botao>
```
Vinicios: E dentro dele, no corpo, chamaríamos o `Criar card`. O React nos dá uma forma para fazer algo parecido. Por padrão, todo componente tem o que chamamos de children, que são os filhos.

Então, em vez de fazer o `props.texto` vamos fazer o `props.children` em `Botao`.

``` jsx
const Botao = (props) => {
    return (<button className='botao'>
        {props.children} 
    </button>)
}
```
Vinicios: Tudo que estiver dentro de `<Botao>` será passado pela propriedade `children`.

``` html
<Botao>
    Criar card
</Botao>
```
Vinicios: Se voltar para o navegador, o comportamento segue o mesmo! Porém, sempre que clicamos no botão, a página recarrega. Lembrem-se que comentamos anteriormente que o React surgiu para resolver esse tipo de comportamento? É isso que vamos fazer no próximo vídeo!

Paulo: No próximo vídeo nós vamos ver como prevenir o comportamento padrão, olha a dica, hein, Vinicios?
