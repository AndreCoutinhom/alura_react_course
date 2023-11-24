Paulo: Agora queremos saber como faremos para o `CampoTexto`, um componente React, receber parâmetros.

Como fazemos para nossa arrow function receber o `label` como parâmetro?

Vinicios: Lembrem que componentes são funcões, sendo assim, conseguimos passar parâmetros para funções.

``` html
<CampoTexto label="Nome"/>
<CampoTexto label="Cargo"/>
<CampoTexto label="Imagem"/>
```

Vincios: A partir do momento que passamos uma propriedade dessas, podemos pegar imadiatamente aqui do `CampoTexto()`.

Isso porque o React nos entrega implicitamente um parâmetro chamado `props`, que são as propriedades que esse componente recebeu.

``` javascript
const CaompoTexto = (props) => {}
```
Vinicios: Vamos começar devagar. Receberemos esse props e seguimos com uma técnica old school.

Vamos fazer o `console.log()` de `props`.

``` javascript
const CaompoTexto = (props) => {
    console.log(props)
}
```
Vinicios: Salvamos. Agora, na inspeção do navegador encontramos.

``` javascript
{label: 'Nome'}
{label: 'Nome'}
{label: 'Cargo'}
{label: 'Cargo'}
{label: 'Imagem'}
{label: 'Imagem'}
```
Vinicios: "Nome", "Cargo" e "Imagem" se repetem duas vezes. Lembram que o `React.StrictMode` nos ajuda a dizer se tem algo errado? Então, para conseguir validar isso ele faz renderizar adicionais do componente. Se desligarmos ele, ele só faz uma vez para cada componente.

Continuando, em "App.js" colocamos um `label` de `Nome`, `Cargo` e `Imagem` e foi isso o que recebemos nas props: um objeto JavaScript com uma propriedade `label` que vem com o valor que foi passado.

Ou seja, conseguimos passar o parâmetro para o componente. O que precisamos fazer agora é uma mistura de um valor de objeto JavaScript e imprimir ele no HTML.

No VS Code, em "CampoTexto", vamos fazer `props.label` e apagamos o `console.log()`, que não vamos mais utilizar.

``` javascript
const CaompoTexto = (props.label) => {

}
```
Vinicios: Agora teremos acesso ao valor que foi passado. Na tag `label` precisamos que tenha um `props.label`.

``` html
<label>props.label</label>
```
Vinicios: Porém, se apenas digitarmos assim livremente, o React vai entender isso como uma string qualquer.

Para indicarmos que queremos imprimir o valor dessa variável precisamos colocá-la entre chaves `{}`.

``` html
<label>{props.label}</label>
```
Vinicios: Agora o React está entendo que o que recebermos nessa propriedade, ele vai imprimir. Vamos salvar.

Também precisamos disso para o `placeholder`, então passaremos ele como argumento. Vamos apagar o `Digite seu Nome` do `placeholder`.

``` javascript
const CampoTexto = (props) => {
    return (
        <div className="campo-texto">
            <label>{props.label}</label>
            <input placeholder/>
        </div>
    )
}
```
Vincios: Em `label` nós imprimimos direto no HTML, agora em `placeholder`, nós queremos que o valor dele venha da variável. Nele, então, temos `placeholder=` e podemos colocar `{props.placeholder}`.

``` javascript
return (
    <div className="campo-texto">
        <label>
            {props.label}
        </label>
        <input placeholder={props.placeholder}/>
    </div>
)
```
Vinicios: Se salvarmos agora e voltarmos em React App, estará tudo em branco porque em nenhum momento nós passamos essas alterações. Então, em "App.js", vamos passar o `placeholder` com o texto.

``` html
<CampoTexto label="Nome" placeholde="Digite seu nome"/>
<CampoTexto label="Cargo" placeholder="Digite seu cargo"/>
<CampoTexto label="Imagem" placeholder="Digite o endereço da imagem"/>
```
Vinicios: Agora temos o `placeholder` sendo preenchido. Viu, Paulo, como conseguimos reutilzar e trabalhar com "argumentos"?

Paulo: Fiquei com uma dúvida. Vinicios, você pode ver no `CampoTexto`, esse nome `props` é o nome de uma variável. Poderia ser outro mais todo mundo usa `props`, é isso?

Vinicios: Sim.

Paulo: `props` de "propriedades".

Vinicios: Exatamente, `props` vem de "propriedades", mas poderia ser qualquer nome.

Paulo: E se precisassemos concatenar a string? Por exemplo, porque em `placeholder=` não precisamos das aspas `""`. E se precisassemos colocar `placeholder="Alguma coisa" {props.placeholder}`. Acho que isso se chama interpolação. Como ficaria a sintaxe nesse caso?

Vinicios: Vamos criar aqui do lado de fora uma constante `const` chamada `placeholderModificada`.

``` javascript
const placeholderModificada =
```
Vinicios: Com JavaScript existem muitas formas de fazer a interpolação, aqui vamos usar o template string usando crase.

Conseguimos fazer isso com `${props.placeholder}...`

``` javascript
const placeholderModificada = `${props.placeholder}...`
```
Vinicios: Assim conseguimos chamar o `placeholderModificado` em `input placeholder=`.

``` html
<input placeholder={placeholderModificado}/>
```
Vinicios: Se voltarmos no navegador, ele funciona, as reticências estão lá.

Paulo: Poderíamos ter feito tudo isso dentro do `placeholder=`?

Vinicios: Exatamente. Podemos apagar o `const placeholderModificada` e colocar `${props.placeholder}` direto no `placeholder=`.

``` html
<input placeholder=`${props.placeholder}.../>
```
Vinicios: O resultado é o mesmo! O `placeholder={}` espera uma variável JavaScript, se estamos criando ela do lado de fora ou dentro dele, para o JSX isso não importa. Nós, entretando, temos preferências organizacionais e até mesmo estéticas.

Nosso próximo passo é encaixar todos esses campos de texto dentro de um formulário.

Paulo: Uma caixa separadora. Então, até o próximo vídeo.

Vinicios: Vamos lá.
