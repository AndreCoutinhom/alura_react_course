# Dicas de depuração de código - Por Vinicios Neves

* `debugger` é um comando que interrompe o fluxo de um determinado código. É muito bom para que possamos entender o que está acontecendo em determinados algoritmos quando são acionados em nossa aplicação

### Exemplo:

``` jsx
 const aoNovoColaboradorAdicionado = (colaborador) => {
    debugger
    setColaboradores([...colaboradores, colaborador])
  }
```

Aqui, sempre que a contante `aoNovoColaboradorAdicionado` for chamada, o debugger impedirá o fluxo do site para que se possa interpretar o código através da inspeção do site.

> Essa é uma ferramente muito boa no dia a dia quando não entendemos porque algumas coisas não estão funcionando.

---

* `Fragment` é uma ferramenta do React também muito boa para interpretar alguns erros. Ele permite que se coloque um elemento HTML na aplicação sem necessariamente se colocar uma `div`.

### Exemplo:

``` jsx
<Fragment>
  <h1>Hello World</h1>
</Fragment>
```

Neste exemplo, ao invés de constar no console que foi criado um novo componente `h1` dentro de uma `div`, o componente aparece de forma livre enquanto o `Fragment` não ocupa espaço no código inspecionado.

> O mesmo resultado pode ser adquirido ao simplesmente abrir e fechar o DOM `HTML`:

``` jsx
<>
  <h1>Hello World</h1>
</>
```

---

