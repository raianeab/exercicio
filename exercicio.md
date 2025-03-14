# Raiane
- Faça uma cópia deste arquivo .md para um repositório próprio
- Resolva as 8 questões objetivas assinalando a alternativa correta e **justificando sua resposta.**
- Resolva as 2 questões dissertativas escrevendo no próprio arquivo .md
- Lembre-se de utilizar as estruturas de código como ``esta aqui com ` `` ou
`javascript
//esta aqui com `
let a = "olá"
let b = 10
print(a)
`
- Resolva as questões com uso do Visual Studio Code ou ambiente similar.
- Teste seus códigos antes de trazer a resposta para cá.
- Cuidado com o uso de ChatGPT (e similares), pois entregar algo só para ganhar nota não fará você aprender. Não seja dependente da máquina!
- Ao final, publique seu arquivo lista_01.md com as respostas em seu repositório, e envie o link pela Adalove. 

# Questões objetivas
**1) Considerando a execução do código abaixo, indique a alternativa correta e justifique sua resposta.**
`javascript
console.log(x);
var x = 5;
console.log(y);
let y = 10;
`
**Resposta:**
a) A saída será undefined seguido de erro 

**Justificativa:**
Ao tentar executar o código fornecido, ocorre a elevação de declaração (hoisting) em ambas as variáveis, mas o comportamento varia entre `var` e `let`. O JavaScript realiza o hoisting das declarações `var`, ou seja, a variável `x` é elevada ao topo do escopo com um valor inicial de undefined. Como a atribuição de valor à variável `x = 5` só ocorre depois da chamada `console.log(x);`, a saída da primeira linha será undefined.

Já o `let` também sofre hoisting, mas, diferente do `var`, ele não é inicializado automaticamente. Isso significa que a variável `y` entra em um estado chamado "Temporal Dead Zone" (TDZ) desde o início do escopo até o momento em que recebe um valor. Como `console.log(y);` tenta acessar `y` antes de sua declaração, isso resulta em um erro de referência (ReferenceError: Cannot access 'y' before initialization).



**2) O seguinte código JavaScript tem um erro que impede sua execução correta. Analise e indique a opção que melhor corrige o problema. Justifique sua resposta.**

`javascript
function soma(a, b) {
    if (a || b === 0) {
        return "Erro: número inválido";
    }
    return a + b;
}
console.log(soma(2, 0));
`
**Resposta:**
a) Substituir if (a || b === 0) por if (a === 0 || b === 0)

**Justificativa:**
O código busca verificar se as variaveis `a` e `b` tem valor nulo antes de proceguir com a soma, para isso é necessário editar a verificação `if (a || b === 0)`, que está incorreta, ela não verifica corretamente se qualquer um dos valores é igual a zero. A condição `if (a || b === 0)` é avaliada de forma errada devido à precedência dos operadores. Primeiro, `b === 0` é verificado, e se for `true`, a expressão `a || true` sempre será `true`, independentemente de `a`. Isso faz com que a condição seja sempre verdadeira quando `b` for 0. Se `b` não for 0, a verificação depende de `a`, mas o comportamento não é o esperado. Dessa maneira o correto é usar `if (a === 0 || b === 0)`, que realiza as verificações de forma independente e as relaciona para verificar se qualquer um dos valores é 0.

______
**3) Ao executar esse código, qual será a saída no console? Indique a alternativa correta e justifique sua resposta.**
`javascript
function calcularPreco(tipo) {
    let preco;

    switch(tipo) {
        case "eletrônico":
            preco = 1000;
        case "vestuário":
            preco = 200;
            break;
        case "alimento":
            preco = 50;
            break;
        default:
            preco = 0;
    }

    return preco;
}

console.log(calcularPreco("eletrônico"));
`

**Resposta:**
b) O código imprime 200.

**Justificativa:**
Nesse caso a saída será `200`, pois ao receber `1000` como valor a variável `preco` continua a receber valores no proximo case `vestuário` que atribui o valor `200`, só depois desse segundo valor que o `break` sai do `switch`, já com a variável é sobrescrita com `200`.


______
**4) Ao executar esse código, qual será a saída no console? Indique a alternativa correta e justifique sua resposta.**
`javascript
let numeros = [1, 2, 3, 4, 5];

let resultado = numeros.map(x => x * 2).filter(x => x > 5).reduce((a, b) => a + b, 0);

console.log(resultado);
`
**Resposta:**
d) 24

**Justificativa:**
No código acima temos métodos que estão editando os elementos do array `let numeros = [1, 2, 3, 4, 5]`. No primeiro método `map()` cada número do array foi multiplicado por 2 `numeros.map(x => x * 2`, resultando em: `[2, 4, 6, 8, 10]`. Depois, usamos o método `filter()` para filtrar os números que são maiores que 5: `numeros.filter(x => x > 5`, resultando em: `6, 8, 10]`. Por ultimo, usamos o método `reduce()` para somar os números do array resultante, começando com o valor inicial 0: `numeros.reduce((a, b) => a + b, 0)`. 
Primeira iteração: a = 0, b = 6 → a + b = 0 + 6 = 6
Segunda iteração: a = 6, b = 8 → a + b = 6 + 8 = 14
Terceira iteração: a = 14, b = 10 → a + b = 14 + 10 = 24
Após isso o resuktado atrivbuido a `resultado` é 24.

______
**5) Qual será o conteúdo do array lista após a execução do código? Indique a alternativa correta e justifique sua resposta.**

`javascript
let lista = ["banana", "maçã", "uva", "laranja"];
lista.splice(1, 2, "abacaxi", "manga");
console.log(lista);
`

**Resposta**
c) ["banana", "abacaxi", "manga", "laranja"]

**Justificativa**
O array inicial possui os seguintes elementos: `let lista = ["banana", "maçã", "uva", "laranja"];`, ao usar o método `(splice():` seguimos os três parâmetros indicados: 
Primeiro parâmetro `1`: Indica o índice onde a modificação começa (a partir do índice 1, que é o elemento `maçã`).
Segundo parâmetro `2`: Define o número de elementos a ser removido a partir do índice especificado (neste caso, 2 elementos: `maçã` e `uva`).
Terceiro e quarto parâmetros ("abacaxi", "manga"): São os elementos que serão adicionados no lugar dos elementos removidos.
Então, o que acontece é o seguinte:

A partir do índice 1, os elementos `maçã` e `uva` são removidos.
Os elementos `abacaxi` e `manga` são adicionados a partir do índice `1`.
Resultado do array após o `splice():`

Após a execução do `splice()`, o array lista fica assim:
`["banana", "abacaxi", "manga", "laranja"]`

______
**6) Abaixo há duas afirmações sobre herança em JavaScript. Indique a alternativa correta e justifique sua resposta**

I. A herança é utilizada para compartilhar métodos e propriedades entre classes em JavaScript, permitindo que uma classe herde os métodos de outra sem a necessidade de repetir código.  
II. Em JavaScript, a herança é implementada através da palavra-chave `extends`.

**Repsosta:**
a) As duas afirmações são verdadeiras, e a segunda justifica a primeira.

**Justificativa**
A primeira afirmação está correta já que em JavaScript, a herança permite que uma classe (subclasse) herde métodos e propriedades de outra classe (superclasse). Isso é uma prática fundamental em programação orientada a objetos, pois ajuda a evitar a repetição de código, promovendo o reuso de funcionalidades.
A segunda também é verdadeira, uma vez que a herança em JavaScript é implementada utilizando a palavra-chave extends, que permite que uma classe herde os métodos e propriedades de outra.
______
**7) Dado o seguinte código. Indique a alternativa correta e justifique sua resposta.**

`javascript
class Pessoa {
  constructor(nome, idade) {
    this.nome = nome;
    this.idade = idade;
  }

  apresentar() {
    console.log(`Olá, meu nome é ${this.nome} e tenho ${this.idade} anos.`);
  }
}

class Funcionario extends Pessoa {
  constructor(nome, idade, salario) {
    super(nome, idade);
    this.salario = salario;
  }

  apresentar() {
    super.apresentar();
    console.log(`Meu salário é R$ ${this.salario}.`);
  }
}
`


**Resposta**
a) I e II são verdadeiras.

**Justificativa**
**I) A classe Funcionario herda de Pessoa e pode acessar os atributos nome e idade diretamente.**
A primeira afirmação é verdadeira, uma vez que a classe Funcionario conseguiu herdar da classe Pessoa utilizando a palavra-chave extends. Isso significa que a classe Funcionario tem acesso aos atributos nome e idade da classe Pessoa, e pode usá-los diretamente. No código, o super(nome, idade) dentro do construtor de Funcionario chama o construtor da classe Pessoa e inicializa esses atributos. Depois, a classe Funcionario pode acessar esses atributos diretamente.

**II) O método apresentar() da classe Funcionario sobrepõe o método apresentar() da classe Pessoa, mas chama o método da classe pai usando super.**
Esta afirmação também é verdadeira. O método apresentar() da classe Funcionario sobrepõe o método apresentar() da classe Pessoa. No entanto, dentro do método apresentar() de Funcionario, o super.apresentar() é chamado, o que invoca o método apresentar() da classe Pessoa antes de adicionar a informação do salário com console.log(). Isso é uma sobrescrição de método (ou method overriding), onde o método da classe filha chama o método da classe pai.

**III) O código não funciona corretamente, pois Funcionario não pode herdar de Pessoa como uma classe, já que o JavaScript não suporta herança de classes.**
A afirmação é falsa. O JavaScript suporta herança de classes e consegue utiliza-las atraves da palavra-chave class e extends. A classe Funcionario herda de Pessoa sem problemas, como está descrito no código.
______

**8) Analise as afirmações a seguir. Indique a alternativa correta e justifique sua resposta.**

**Asserção:** O conceito de polimorfismo em Programação Orientada a Objetos permite que objetos de diferentes tipos respondam à mesma mensagem de maneiras diferentes.  
**Razão:** Em JavaScript, o polimorfismo pode ser implementado utilizando o método de sobrecarga de métodos em uma classe.

**Resposta:**
b) A asserção é verdadeira e a razão é falsa.

A primeira afirmação "Asserção" é verdadeira. O polimorfismo é um dos princípios fundamentais da Programação Orientada a Objetos (POO). Ele permite que objetos de diferentes tipos (ou classes) respondam de maneira diferente à mesma mensagem ou chamada de método. 

Já a segunda afirmação "Razão" é falsa. JavaScript não suporta sobrecarga de métodos da maneira tradicional, como em outras linguagens como Java ou C++. Em JavaScript, o polimorfismo é implementado de maneira diferente, principalmente por meio da sobrescrição de métodos, onde uma classe filha pode sobrescrever um método da classe pai.

______

# Questões dissertativas
9) O seguinte código deve retornar a soma do dobro dos números de um array, mas contém erros. Identifique os problema e corrija o código para que funcione corretamente. Adicione comentários ao código explicado sua solução para cada problema.

`javascript
function somaArray(numeros) {

    for (i = 0; i < numeros.size; i++) {
        soma = 2*numeros[i];
    }
    return soma;
}
console.log(somaArray([1, 2, 3, 4]));
`

**Resposta**

`javascript
function somaArray(numeros) {
    soma = 0; // Declarei a variável soma com 0 antes de usá-la para acumular os valores.
    for (i = 0; i < numeros.length; i++) { // Troquei 'numeros.size' por 'numeros.length' para obter o tamanho correto do array.
        soma = soma + 2*numeros[i]; // Corrigi a lógica para acumular corretamente o dobro dos números no array. 
    }
    return soma;
}
console.log(somaArray([1, 2, 3, 4]));
`

______
10) Crie um exemplo prático no qual você tenha duas classes:

- Uma classe `Produto` com atributos `nome` e `preco`, e um método `calcularDesconto()` que aplica um desconto fixo de 10% no preço do produto.
- Uma classe `Livro` que herda de `Produto` e modifica o método `calcularDesconto()`, aplicando um desconto de 20% no preço dos livros.

Explique como funciona a herança nesse contexto e como você implementaria a modificação do método na classe `Livro`.
