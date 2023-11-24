Paulo: Agora já temos três campos! Aposto que vocês estão criando os seu próprios campos, passando mais parâmetros. Explore!

Vamos criar o nosso formulário. Isto é, o nosso grande componente com componentes menores dentro, algo assim.

Vinicios: Você tocou na palavra chave, React é sobre componentes. Ou estamos criando um novo componente, ou estamos modificando um já existente. Em nosso caso, nós criamos um componente de texto que atendia parcialmente o que precisamos, modificamos e evoluímos.

Agora está na hora de encaixarmos os componentes de texto nesse formulário.

Ao lado direito do Figma, encontramos algumas sugestões do que podemos adicionar no CSS. Nem sempre são as melhores, mas ele nos dá algumas dicas.

![image](https://github.com/AndreCoutinhom/alura_react_course/assets/91290799/5c3ce1a1-a9f9-4453-8536-eae428e121e7)

Vincios: Dentro da pasta "componentes" vamos criar a pasta "Formulario", dentro dela vamos criar o "index.js". Nesse último, criamos a constante de `Formulario` recebendo uma arrow function e finalizamos com o `export` dele.

``` javascript
const Formulario = () => {

}

export default Formulario;
```
Vinicios: Além disso, criaremos o arquivo "Formulario.css". E em "index.js" fazemos o `import` dele.

``` javascript
import './Formulario.css';
```
Vinicios: Podemos começar a criar o formulário. Começamos com o `return` e fazemos uma `section` do HTML que conterá `form`. Dentro dele, vamos trazer os campos de texto do "App.js", recortando e colando no "index.js" do "Formulario".

import './Formulario.css';

``` javascript
const Formulario = () => {
    return (
        <section>
            <form>
                <CampoTexto label="Nome" placeholde="Digite seu nome"/>
                <CampoTexto label="Cargo" placeholder="Digite seu cargo"/>
                <CampoTexto label="Imagem" placeholder="Digite o endereço da imagem"/>
            </form>
        </section>
    )
}

export default Formulario
```
Vinicios: O VS Code diz que ele não sabe quem é `CampoTexto`, porque ele ainda não foi definido. Com "Ctrl + Espaço" nós importamos ele.

Para finalizar, tiramos o `import` do CampoTexto do "App.js".

Agora vamos salvar. Ao voltarmos para o navegador, vocês verão que só temos o Banner porque o formulário ainda não foi importado.

Então, no VS Code, em "App.js", vamos trazer o `Formulario`, ao dar "enter" ele já importa para nós.

``` javascrip
import Banner from './componentes/Vanner';
import Formulario from './componentes/Formulario';

function App() {
    return (
        <div className="App">
            <Banner />
            <Formulario />
        </div>
    )
}

export default App;
```
Vinicios: Agora ele aparece dentro do navegador já dentro do formulário. Agora podemos partir para estilização. O primeiro passo é colocarmos o título "Preencha os dados para criar o card do colaborador:".

Em "index.js" do "Formulario", dentro de `section` vamos adiconar um `h2` porque é um subtítulo.

``` html
<h2>Preencha os dados para criar o card do colaborador:</h2>
```
Vinicios: E ele aparece no navegador. Precisamos agora deixar o formulário um pouco menor e centralizá-lo na tela.

Para isso, vamos dar uma `className` de `formulario` para o `section`, que é a classe principal do componente. A partir da classe principal, vamos selecionar os filhos.

Em "formulario.css" criamos o `.formulario` com `display: flex` alinhado, `justify-content`, no `center` para centralizar. E uma margem de `80px` para cima e para baixo e `0px` para a direita e para a esquerda.

``` css
.formulario {
    display: flex;
    justify-content: center;
    margin: 80px 0;
}
```
Vincios: Agora em `form` vamos dizer que o tamanho máximo dele é de `80%`.

``` css
.formulario form {
    max-width: 80%;
}
```
Vinicios: Salvamos e vemos as mudanças no navegador. Ainda no `form` coloamos o `background-color` dele como `#F2F2F2`. Arrendamos as bordas dele com `border-radius` de `20px` e um `padding` de `36px` para cima e para baixo e de `64px` para os lados.

Paulo: Lembrando que todos esses detalhes estão no Figma.

Vinicios: Exatamente. Vale comentar que algumas vezes o que o designer planejou acaba sendo uma pouco difícil, nesses casos nós negociamos com eles o que fica melhor para os dois lados.

Para finalizarmos, falta apenas o `box-shadow` de `8px 8px 16px` e o `rgba(0, 0 ,0, 0.08)` para adicionarmos a opacidade.

``` css
.formulario form {
    max-width: 80%;
    background-color: #F2F2F2
    border-radius: 20px;
    padding: 36px 64px;
    box-shadow: 8px 8px 16px rgba(0, 0 ,0, 0.08);
}
```
Vinicios: Para o formulário, era isso o que precisávamos. Criamos um pacote com todos os campos de texto dentro dele. Os próximos passos é fazermos o botão para a submeter os dados do formulário. Além disso, o "Time" não é um campo de texto padrão, ele será um "select" com algumas opções pré definidas.

Antes de partirmos para isso, vale a pena refletirmos um pouco sobre o que fizemos até agora e entender um pouco mais como é a reatividade do React.

Paulo: Vamos entender a palavra "reação" e finalmente citar alguns fatos históricos.

Vinicios: Vamos lá!
