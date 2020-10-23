## Set<T>

A interface Set representa um conjunto de elementos (similar ao da álgebra), é uma coleção que não permite elementos duplicados.

Não admite repetições

Elementos não possuem posição

Acesso, inserção e remoção de elementos são rápidos

Possue operações eficientes de conjunto: interseção, união, diferença.

Estruturas do tipo Set aceitam apenas valores únicos, qualquer valor duplicado inserido em um set será automaticamente excluído.

Principais classes que implementam a interface Set:

* HashSet - mais rápido e não garante ordenação dos elementos da ordem que foram inseridos
* TreeSet - mais lento
* LinkedHashSet - velocidade intermediária e garante ordenação dos elementos na ordem em que são adicionados

## Alguns métodos importantes

**add(obj), remove(obj), contains(obj), clear(), size(), removeIf(predicate)**

**addAll(other) - união:** adiciona no conjunto os elementos do outro conjunto, sem repetição

**retainAll(other) - interseção:** remove do conjunto os elementos não contidos em other

**removeAll(other) - diferença:** remove do conjunto os elementos contidos em other

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

```java
cars.removeIf(x -> x.length() >= 4);

cars.removeIf(x -> x.charAt(0) == 'F');
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

### Operações de conjunto

```java
import java.util.Arrays;
import java.util.Set;
import java.util.TreeSet;

public class Main {
  public static void main(String[] args) {

    Set<Integer> a = new TreeSet<>(Arrays.asList(0,2,4,5,6,8,10));
    Set<Integer> b = new TreeSet<>(Arrays.asList(5,6,7,8,9,10));

    // union
    Set<Integer> c = new TreeSet<>(a); // cria uma cópia do conjunto a para o c
    c.addAll(b); // união do conjunto c com o b
    System.out.println(c);

    // intersection
    Set<Integer> d = new TreeSet<>(a);
    d.retainAll(b); // interseção do conjunto d com b
    System.out.println(d); // somente elementos que tem em comum nos conjuntos

    // difference
    Set<Integer> e = new TreeSet<>(a);
    e.removeAll(b); // interseção do conjunto d com b
    System.out.println(e); // elementos do conjunto a que não tem em b
  }
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
