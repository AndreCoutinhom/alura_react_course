### Sobre Arrow Functions:

* Acesse o artigo [Conhecendo Arrow Functions](https://www.alura.com.br/artigos/conhecendo-arrow-functions?_gl=1*ot68ab*_ga*ODM1Nzk2OTUyLjE2OTgzNDc1Mjk.*_ga_1EPWSW3PCS*MTcwMDc5Mzc0NC4xOS4xLjE3MDA3OTY1OTIuMC4wLjA.*_fplc*emVNTG9XVDNpZG1aSE11ZGM3ZFFjOCUyQng4eVFwTkc5MnkzYndpOUwwZ0Y2T0FoY0JtMmN3JTJGanNLTzljJTJCQkx0bXFwRjROdVVTYUJYcGc1alNvczBOJTJCRUcxcmNFRUJRcmlCTjdZSnhKaG12byUyQlB0UjVEaTcwWm8wclNkQ24wdyUzRCUzRA..), do Felipe Nascimento]

> Confesso que não entendi muito bem o conceito de arrow functions pelo texto acima. Após perguntar ao GPT-4 do Bing recebi a seguinte resposta. Pode ser útil para quem teve o mesmo problema de entendimento que eu:

Uma arrow function é uma forma de escrever uma função em JavaScript de maneira mais simples e rápida. Uma função é um conjunto de instruções que realiza uma tarefa ou calcula um valor. Uma arrow function usa uma seta ( => ) para separar os parâmetros da função (o que ela recebe como entrada) do corpo da função (o que ela faz com os parâmetros). Por exemplo, a função abaixo recebe dois números como parâmetros e retorna a soma deles:

function somar (a, b) { return a + b; }

Essa função pode ser escrita como uma arrow function assim:

somar = (a, b) => a + b;

Note que a arrow function é mais curta e mais fácil de ler. Ela também não precisa da palavra-chave function nem da palavra-chave return. Além disso, ela não tem seu próprio valor de this, que é uma variável especial que se refere ao objeto que chamou a função. Isso pode ser útil em alguns casos, mas também pode causar confusão em outros.

A lógica matemática de códigos que envolvem “() => {}” é a seguinte: os parênteses contêm os parâmetros da função, que podem ser nenhum, um ou mais. A seta indica que o que vem depois é o corpo da função, que contém as instruções que serão executadas. As chaves delimitam o corpo da função, que pode ter uma ou mais linhas. Se o corpo da função tiver apenas uma linha, as chaves podem ser omitidas, assim como o return. Por exemplo, a função abaixo recebe um número como parâmetro e retorna o dobro dele:

dobrar = (x) => x * 2;

Essa função é equivalente a:

dobrar = (x) => { return x * 2; };

##

