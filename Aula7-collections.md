# Collections

Os Arrays são estáticos, tem capacidade fixa, não pode ser redimensionado.

As listas são estruturas de dados de armazenamento sequencial assim como os arrays.

As listas não possuem capacidade fixa.

List é uma interface Java.

As principais implementações da interface List são: Arraylist, LinkedList e Vector.

Em um array a quantidade de elementos é definida em sua declaração, um array de strings criado com 5 posições não terá a capacidade de armazenar mais strings do que essa quantidade.

```java
int[] idades = new int[5];
```

Disponível no pacote java.util, a API Collections é um conjunto de classes e interfaces que implementam Collection, possuíndo métodos de adição, remoção, ordenação de elementos em coleções de dados.

![image001](https://user-images.githubusercontent.com/56240254/94955304-bd3c2700-04c0-11eb-8bc0-ab3681984dc1.jpg)

## ArrayList

Um ArrayList é um array redimensionável, que pode ser encontrado no pacote java.util.

A classe de coleção ArrayList<T> pertence ao pacote java.util e implementa a interface List. T indica o tipo de elementos que a estrutura irá armazenar.

ArrayList é como um array cujo tamanho pode crescer.

A diferença entre um array e um ArrayList em Java é que o tamanho de um array não pode ser modificado, para adicionar ou remover elementos é necessário criar um novo array.

No ArrayList os elementos podem ser adicionados e removidos sempre que preciso.

Sintaxe de declaração:
```java
ArrayList<Objeto> nomeDoArrayList = new ArrayList<Objeto>();
```

```java
import java.util.ArrayList; // import the ArrayList class

ArrayList<String> cars = new ArrayList<String>(); // Create an ArrayList object
```
A classe ArrayList possui muitos métodos úteis. Para adicionar elementos ao ArrayList, usamos o método **add()**.

Exemplo no IntelliJ
```java
import java.util.ArrayList;

public class ArrayListDemo { 
  public static void main(String[] args) { 
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    System.out.println(cars);
  } 
}
```
Para acessar um elemento no ArrayList usamos o método **get()** com o índice do elemento.

```java
import java.util.ArrayList;

public class ArrayListDemo { 
  public static void main(String[] args) { 
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    System.out.println(cars.get(0));
  } 
}
```
Para modificar um elemento em uma posição usamos o método **set()** informando o índice do elemento.

```java
import java.util.ArrayList;

public class ArrayListDemo { 
  public static void main(String[] args) { 
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    cars.set(0, "Opel");
    System.out.println(cars);
  } 
}
```
Para remover um elemento usamos o método **remove()** informando o índice do elemento a ser removido.

```java
import java.util.ArrayList;

public class ArrayListDemo { 
  public static void main(String[] args) { 
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    cars.remove(0);
    System.out.println(cars);
  } 
}
```

Para remover todos os elementos de um ArrayList usamos o método **clear()**.

```java
import java.util.ArrayList;

public class MyClass { 
  public static void main(String[] args) { 
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    cars.clear();
    System.out.println(cars);
  } 
}
```
Para verificar a quantidade de elementos que o ArrayList possui usamos o método **size()**.

```java
import java.util.ArrayList;

public class ArrayListDemo { 
  public static void main(String[] args) { 
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    System.out.println(cars.size());
  } 
}
```

Exibindo todos os elementos de um ArrayList.

```java
import java.util.ArrayList;

public class MyClass { 
  public static void main(String[] args) { 
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    for (int i = 0; i < cars.size(); i++) {
      System.out.println(cars.get(i));
    }
  } 
```

Usando o laço de repetição for-each.

```java
import java.util.ArrayList;

public class MyClass { 
  public static void main(String[] args) { 
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    for (String i : cars) {
      System.out.println(i);
    }
  } 
}
```

Os elementos em um ArrayList são objetos. Nos exemplos criamos objetos do tipo String. *String em Java é um objeto (não um tipo primitivo).*

Criando um ArrayList para armazenar elementos do tipo Integer.

```java
import java.util.ArrayList;

public class ArrayListDemo { 
  public static void main(String[] args) { 
    ArrayList<Integer> myNumbers = new ArrayList<Integer>();
    myNumbers.add(10);
    myNumbers.add(15);
    myNumbers.add(20);
    myNumbers.add(25);
    for (int i : myNumbers) {
      System.out.println(i);
    }
  } 
}
```

## Ordenação: Collections.sort

A classe Collections possuí um método estático sort que recebe um List como argumento e o ordena por ordem crescente.

Exemplo no IntelliJ

```java
import java.util.ArrayList;
import java.util.Collections;

public class ArrayListDemo { 
  public static void main(String[] args) { 
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    
    Collections.sort(cars);

    for (String i : cars) {
      System.out.println(i);
    }
  } 
}
```
Ordenando um ArrayList de inteiros.

```java
import java.util.ArrayList;
import java.util.Collections;  // Import the Collections class

public class MyClass {
  public static void main(String[] args) {
    ArrayList<Integer> myNumbers = new ArrayList<Integer>();
    myNumbers.add(33);
    myNumbers.add(15);
    myNumbers.add(20);
    myNumbers.add(34);
    myNumbers.add(8);
    myNumbers.add(12);

    Collections.sort(myNumbers);  // Sort myNumbers

    for (int i : myNumbers) {
      System.out.println(i);
    }
  }
}
```
Para ordenar uma List de objetos deve implementar a interface Comparable<T> e implementar o método compareTo() definindo o critério de ordenação.

## Generics

Em qualquer lista é possível adicionar qualquer tipo de objetos.

```java
ContaCorrente cc = new ContaCorrente();

List lista = new ArrayList();
lista.add("Uma string");
lista.add(cc);
```

Na hora de recuperar esses objetos, como o método get devolve um Object, precisaríamos fazer um cast. Em uma lista com vários objetos de tipos diferentes, isso pode não ser tão simples.

O uso do Generics restringe as listas a um determinado tipo de objetos.

Com o recurso do Generics garantimos a tipagem de uma coleção no momento em que ela é criada.
A partir daí, o compilador não permitirá elementos não compatíveis com o tipo escolhido sejam adicionados na coleção.

```java
List<ContaCorrente> contas = new ArrayList<ContaCorrente>();
contas.add(c1);
contas.add(c2);
contas.add(c3);
contas.add("Uma string"); // erro!
```

O uso de Generics elimina a necessidade de casting, já que todos os objetos inseridos na lista serão do tipo definido.

### Operador diamante

```java
List<ContaCorrente> contas = new ArrayList<>();
```

## Interface List 

**Quando desenvolvemos procuramos sempre nos referir a interface e não às implementações específicas.**

O ideal é sempre trabalhar com a interface mais genérica possível.

Dessa forma obtemos um **baixo acoplamento**, podemos trocar a implementação, já que estamos programando voltado para a interface.

```java
class Empresa {

    private List<Funcionario> empregados = new ArrayList<>();
}
```
## Lambda

As expressões lambda foram adicionadas no Java 8.

Uma expressão lambda é um pequeno bloco de código que recebe parâmetros e retorna um valor.

As expressões lambda são semelhantes aos métodos, mas não precisam de um nome e podem ser implementadas diretamente no corpo de um método.

Sintaxe de uma expressão lambda mais simples com um único parâmetro e uma expressão.

```java
parameter -> expression
```
Sintaxe com mais de um parâmetro.

```java
(parameter1, parameter2) -> expression
```

As expressões lambda devem retornar um valor e não podem conter variáveis, atribuições ou instruções (if, for etc). O bloco de código pode ser usado com chaves. Se a expressão lambda retornar um valor, o bloco deve ter uma instrução return.

```java
(parameter1, parameter2) -> { code block }
```

Exemplo no IntelliJ

```java
public class LambdaExpressions {
  public static void main(String[] args) {
    ArrayList numbers = new ArrayList();
    numbers.add(5);
    numbers.add(9);
    numbers.add(8);
    numbers.add(1);
    numbers.forEach( (n) -> {
        System.out.println(n);
    });
  }
}
```
