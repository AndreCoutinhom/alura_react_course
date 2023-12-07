# Por que foi utilizado `.map` no código?

Porque usando `.map` é possível que uma nova array de elementos seja retornado a partir de outra array. Já que precisamos escolher entre diversas escolas Alura no último campo, então precisamos usar essa função.

---

### Exemplo:

``` jsx
const ListaSuspensa = (props) => {
    return (
        <div className="lista-suspensa">
            <label>{props.label}</label>
            <select onChange={evento => props.aoAlterado(evento.target.value)} required={props.required} value={props.value}>
                    {props.itens.map(item => <option key={item}>{item}</option>)}
            </select>
        </div>
    )
}

```
