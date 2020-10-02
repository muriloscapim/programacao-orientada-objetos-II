# Collections

Em um array a quantidade de elementos é definida em sua declaração, um array de strings criado com 50 posições não terá a capacidade de armazenar mais strings do que essa quantidade.

```java
int[] idades = new int[50];
```

Disponível no pacote java.util, a API Collections é um conjunto de classes e interfaces que implementam Collection, possuíndo métodos de adição e remoção de elementos em coleções de dados.

![image001](https://user-images.githubusercontent.com/56240254/94955304-bd3c2700-04c0-11eb-8bc0-ab3681984dc1.jpg)

## ArrayList

Um ArrayList é um array redimensionável, que pode ser encontrado no pacote java.util.

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

Ordenar um ArrayList

Outra classe útil do pacote java.util é a classe Collections que inclui o método **sort()** para ordenar os elementos de um ArrayList em ordem alfabética ou númerica.

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





