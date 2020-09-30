# Arrays

Um array é um conjunto de variáveis do mesmo tipo, referenciadas por um nome comum.

Os arrays podem ter uma ou mais dimensões, o array unidimensional é o mais usado.

Embora os arrays Java possam ser usados da mesma forma que os arrays de outras linguagens de programação, eles são implementados como objetos.

Para declarar um array unidimensional usamos a forma:

*tipo nome-array[] = new tipo[tamanho];*

O *tipo* determina o tipo de dado de cada elemento contido no array.

O número de elementos que o array conterá é determinado por *tamanho*.

Um elemento de um array é acessado com o uso de um **índice**. Um índice descreve a posição de um elemento dentro de um array.

Em Java, **todos os arrays têm zero como o índice de seu primeiro elemento.**

Exemplo no IntelliJ

```java
public class ArrayDemo {
    public static void main(String args[]) {
        /* Cria um array int de 10 elementos e o vincula a uma variável de referência de array chamada sample */
        int sample[] = new int[10];
        int i;

        for (i = 0; i < 10; i++){
            sample[i] = i;
        }

        for (i = 0; i < 10; i++){
            System.out.println("sample[" + i + "]: " + sample[i]);
        }
    }
}
```

![array](https://user-images.githubusercontent.com/56240254/94719031-fa6db100-0328-11eb-8509-6c2c2a6dd596.PNG)

Os arrays podem ser inicializados quando são criados.

A forma geral de inicialização de um array unidimensional é:

*tipo nome-array[] = { val1, val2, val3, ... , valN };*

O Java aloca automaticamente um array grande o suficiente para conter os valores especificados.

Não há a necessidade de usar o operador new explicitamente.

```java
String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
System.out.println(cars[0]); // Acessando um elemento do array
// Outputs Volvo
```

Demonstra uma situação que excede um array.

```java
public class ArrayError {
  public static void main(String[] args) {
    int sample[] = new int[10];
    int i;

    for(i = 0; i < 100; i++) {
        sample[i] = i;
    }  
  }
}
```
Assim que i alcançar 10, uma exceção ArrayIndexOutOfBoundsException será gerada e o programa será encerrado.

## Sintaxe alternativa para a declaração de arrays

Há uma segunda forma que pode ser usada na declaração de um array:

*type[] var-name;*

Os colchetes vêm depois do especificador de tipo, e não do nome da variável de array.
As declarações são equivalentes:

```java
int counter[] = new int[3];
int[] counter = new int[3];
```

```java
char table[][] = new char[3][4];
char[][] table = new char[3][4];
```

Essa forma de declaração alternativa é conveniente na declaração de vários arrays do mesmo tipo. Por exemplo:

```java
int[] nums, nums2, nums2; // cria três arrays
```

É o mesmo que escrever:

```java
int nums[], nums2[], nums3[];
```

A forma de declaração alternativa é útil na especificação de um array como tipo de retorno de um método. Por exemplo:

```java
int[] someMeth() {

}
```

## Arrays de referências

É comum ouvirmos "array de objetos". Porém quando criamos um array de uma classe, ele possui referências. O objeto está na memória principal, e no array, só ficam guardadas as referências (endereços).

```java
Conta[] minhasContas = new Conta[10];
```

Foram criados 10 espaços para guardar uma referência a uma Conta.
Por enquanto, eles não guardam nenhuma referência (null).

```java
Conta conta = new Conta();
conta.deposita(1000.0);
minhasContas[0] = conta;
```

![array_contas](https://user-images.githubusercontent.com/56240254/94719190-39036b80-0329-11eb-82df-bab39965a94c.PNG)

:point_right: *Um array de tipos primitivos guarda valores, um array de objetos guarda referências.*

## O laço for de estilo for-each

Usando arrays é comum termos situações em que um array deve ser percorrido do início ao fim, elemento a elemento. 
Ex: para calcular a soma dos valores contidos em um array, cálculo de uma média, na busca de um valor, na cópia de um array.

O Java define uma segunda forma do laço for que otimiza a operação, implementa um laço de estilo for-each.

*Um laço for-each percorre um conjunto de objetos, como um array, de forma sequencial, do ínicio ao fim.*

O estilo for-each de for também é chamado de laço for melhorado, e é muito popular.

A forma geral do laço for de estilo for-each é:

```java
for (type variable : arrayname) {
    // código
}
```
**type** especifica o tipo e **variable** especifica o nome de uma variável de iteração que receberá os elementos de um array, um de cada vez, do início ao fim. O array que está sendo percorrido é especificado por **arrayname**.

:point_right: Já que a variável de iteração recebe valores do conjunto, seu tipo de ser o mesmo dos (ou compatível com) elementos armazenados no array.

Exemplo do IntelliJ
```java
public class DemoForeach {
  public static void main(String[] args) {
    String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
    for (String car : cars) {
      System.out.println(car);
    }    
  }
}
```
## Membro length

Já que os arrays são implementados como objetos, **cada array tem uma variável de instância length** associada, que contém o seu número de elementos.

**length contém o tamanho do array.**

Exemplo no IntelliJ

```java
public class ArrayLength {
  public static void main(String[] args) {
    String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
    System.out.println(cars.length);
  }
}
```

```java
public class ArrayLength {
  public static void main(String[] args) {
    String[] cars = {"Volvo", "BMW", "Ford", "Mazda"};
    System.out.println(cars.length);

    for(int i = 0; i < cars.length; i++) {
        System.out.println(cars[i]);
    }
  }
}
```
## Arrays multidimensionais

Arrays podem ter mais de uma dimensão.

A forma mais simples de array muldimensional é o array bidimensional.

Um array bidimensional é, na verdade, uma lista de arrays unidimensionais.

![array_bidimensional](https://user-images.githubusercontent.com/56240254/94719433-84b61500-0329-11eb-8c4a-95e995790f8c.PNG)

Este tipo de array é declarado como tendo duas dimensões e é usado para representar tabelas de valores organizadas em linhas e colunas.

Para acessar os elementos de um array bidimensional, especificamos dois índices: um para linha e outro para coluna.

![array_bidimensional_2](https://user-images.githubusercontent.com/56240254/94719459-8e3f7d00-0329-11eb-9c23-6dae28ac3160.jpg)

Para declarar um array bidimensional:

```java
int m[][] = new int[2][4];
```

```java
int[][] myNumbers = { {1,2,3,4}, {5,6,7} };
System.out.println(myNumbers[1][2]); // Outputs 7
```

Exemplo no IntelliJ

```java

public class MyClass {
   public static void main(String[] args) {
     int[][] myNumbers = { {1, 2, 3, 4}, {5, 6, 7} };

     for (int i = 0; i < myNumbers.length; ++i) {
        for(int j = 0; j < myNumbers[i].length; ++j) {
           System.out.println(myNumbers[i][j]);
        }
     }
   }
}

```
