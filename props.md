# Para que serve o props?

Na verdade quando colocamos props em uma arrow function, estamos definindo uma entrada de termos para serem usados como propriedades da arrow function.

Dessa forma, definimos como propriedade qualquer expressão que suceder `props.`. 

Consideremos os seguintes exemplos. São códigos que coordenam seus parâmetros visuais de formas diferentes, mas fazem exatamente a mesma coisa.

``` jsx
const Colaborador = (props) => {
    return (<div className='colaborador'>
        <div className='cabecalho'>
            <img src={props.imagem} alt={props.nome} />
        </div>
        <div className='rodape'>
            <h4>{props.nome}</h4>
            <h5>{props.cargo}</h5>
        </div>
    </div>

    )
}
```

Neste exemplo, `props` serve como uma entidade que determina o que será considerado um parâmetro de entrada. Qualquer propriedade do código que sucedê-lo, será considerado parte da função.

---

``` jsx
const Colaborador = ({ nome, imagem, cargo }) => {
    return (<div className='colaborador'>
        <div className='cabecalho'>
            <img src={imagem} alt={nome} />
        </div>
        <div className='rodape'>
            <h4>{nome}</h4>
            <h5>{cargo}</h5>
        </div>
    </div>

    )
}
```

Já neste exemplo, todos os parâmetros foram pré-definidos, e o código serve para determinar onde os parâmetros serão ativados. 

---

Os dois códigos chegam ao mesmo resultado, mas possuem diferenças de lógicas e são mais eficientes em comparação um com o outro, dependendo da dinâmica que se espera da aplicação.
