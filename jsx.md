# O que é JSX?

JSX ou Javascript XML é uma linguagem derivada do Javascript que funciona como uma forma de integrar DOMs de HTML em funções Javascript.

---

### Exemplo:

``` jsx
export const Banner = () => {
    //JSX
    return (
        <header className="banner">
            <img src="/images/banner.png" alt="O banner principal da página do Organo"/>
        </header>
    )
}
```
