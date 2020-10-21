## Set

A interface Set representa um conjunto, é uma coleção que não permite elementos duplicados.

Estruturas do tipo Set aceitam apenas valores únicos, qualquer valor duplicado inserido em um set será automaticamente excluído.

Principais classes que implementam a interface Set:
* HashSet
* LinkedHashSet
* TreeSet

TreeSet, HashSet e LinkedHashSet implementam a interface Set, temos os mesmos métodos para as três estruturas, o que difere cada uma é a forma com que  a estrutura de dados é implementada.

## HashSet

HashSet é uma das estruturas de dados fundamentais na API Collections.

A classe HashSet faz parte do pacote java.util e implementa a interface Set.

Não tem ordenação dos elementos. A ordem em que os elementos são armazenados pode não ser a ordem na qual eles foram inseridos no conjunto. Faz com que seja rápido.

Exemplo no IntelliJ

Sintaxe para criar um objeto HashSet que armazenará strings:
```java
// Import the HashSet class
import java.util.HashSet; // Import the HashSet class

Set<String> cars = new HashSet<>();
````


### Adicionar itens
O método **add()** serve para adicionar itens.

```java
// Import the HashSet class
import java.util.HashSet;

public class MyClass {
  public static void main(String[] args) {
    Set<String> cars = new HashSet<>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("BMW");
    cars.add("Mazda");
    System.out.println(cars);
  }
}
```

### Verificar se existe um item

O método **contains()** verifica se um item existe em um HashSet.

```java
cars.contains("Mazda");
```

### Remover um item

O método **remove()** serve para remover um item.

```java
cars.remove("Volvo");
```

O método **clear()** serve para remover todos os itens.

```java
cars.clear();
```

### Tamanho do HashSet

O método **size()** serve para retornar quantos intens existem no HashSet.

```java
cars.size();
```

Para iterar os itens em um HashSet com um laço for-each:

```java
for (String i : cars) {
  System.out.println(i);
}
```
Exemplo

```java
// Import the HashSet class
import java.util.HashSet;

public class MyClass {
  public static void main(String[] args) {

    // Create a HashSet object called numbers
    HashSet<Integer> numbers = new HashSet<Integer>();

    // Add values to the set
    numbers.add(4);
    numbers.add(7);
    numbers.add(8);

    // Show which numbers between 1 and 10 are in the set
    for(int i = 1; i <= 10; i++) {
      if(numbers.contains(i)) {
        System.out.println(i + " was found in the set.");
      } else {
        System.out.println(i + " was not found in the set.");
      }
    }
  }
```
