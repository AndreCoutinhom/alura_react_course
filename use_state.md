# O que é Use State?

Use State é uma biblioteca do React que permite o uso de uma função que renderiza os valores de uma variável sempre que são alterados.

Sempre que queremos que o componente reaja a alguma alteração no valor de uma variável e se renderize novamente, precisamos indicar isto utilizando o `useState`. Do contrário, o valor vai ser alterado mas o DOM não será atualizado.

### **Exemplo na atividade:**

``` javascript
// Aqui, a constante recebe dois parâmetros organizados como em uma array
// O useState vai organizar esses valores de forma que o sistema reconheça seus valores mesmo quando alterados

const [nome, setNome] = useState('')
```

