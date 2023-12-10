# Como se fazem funções em React?

A lógica `if else` é uma das mais usadas em diversas linguagens de programação. No entanto, usando o React, é possível chamar essa função com um simples comando `&&` ou com um `?`.

No exemplo abaixo a propriedade `(props.colaboradores.lenght > 0)` é o que está definindo as condições da função, exatamente como a propriedade que sucederia a propriedade `if`.

As propriedades que sucedem o comando `&&` representam a ação respondente à condição. Portanto se o tamanho de `props.colaboradores` for maior que 0, então tudo o que estiver depois de `&&` irá acontecer.

``` jsx
return (
        (props.colaboradores.lenght > 0) && <section className='time' style={css}>
            <h3 style={{ borderColor: props.corPrimaria }}>{props.nome}</h3>
            <div className='colaboradores'>
                {props.colaboradores.map( colaborador => <Colaborador 
            nome={colaborador.nome} 
            cargo={colaborador.cargo} 
            imagem={colaborador.imagem} />)}
            </div>
        </section>
    )
```


---

O mesmo efeito pode ser alcançado pelo exemplo abaixo. Antes do `?` está o corpo condicional. O que sucede `?` responde à condição, e o que está depois de `:` será acionado caso a condição não seja verdadeira, assim como a o comando `else`.
 
``` jsx
return (
        (props.colaboradores.lenght > 0) ? <section className='time' style={css}>
            <h3 style={{ borderColor: props.corPrimaria }}>{props.nome}</h3>
            <div className='colaboradores'>
                {props.colaboradores.map( colaborador => <Colaborador 
            nome={colaborador.nome} 
            cargo={colaborador.cargo} 
            imagem={colaborador.imagem} />)}
            </div>
        </section>
        : ''
    )
```

