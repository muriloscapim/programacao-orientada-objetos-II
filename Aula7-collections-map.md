## Map<K,V>

Nos arrays os itens são armazenados em uma coleção ordenada e acessados com um número de índice do tipo int.

Map é uma interface Java que contém uma estrutura de dados que permite trabalhar com uma estrutura de chave e valor.

É uma coleção de pares chave/valor.

Não admite repetições do objeto chave.

Os elementos são indexados pelo objeto chave (não possuem posição).

Acesso, inserção e remoção de elementos são rápidos.

Uso comum: cookies, local storage, qualquer modelo chave-valor.

Principais implementações da interface Map:
* HashMap
* TreeMap
* LinkedHashMap

### Alguns métodos

put(key, value), remove(key), containsKey(key), get(key), clear(), size(), keySet() - retorna um Set<K>, values() - retorna um Collection<V>.

### Exemplo no IntelliJ

```java

import java.util.HashMap;

public class MyClass {
  public static void main(String[] args) {
    // HashMap<String, String> capitalCities = new HashMap<String, String>();
    Map<String, String> capitalCities = new HashMap<>();
  }
```

### Adicionar itens

O método **put()** é usado para adicionar elementos.

```java
// Add keys and values (Country, City)
capitalCities.put("England", "London");
capitalCities.put("Germany", "Berlin");
capitalCities.put("Norway", "Oslo");
capitalCities.put("USA", "Washington DC");
System.out.println(capitalCities);
```

### Acessar um item

O método **get()** é usado para acessar um valor informando a chave.

```java
capitalCities.get("England");
```

### Remover um item

O método **remove()** é usado para remover um item informando a chave.

```java
capitalCities.remove("England");
```

O método clear() é usado para remover todos os itens.

```java
capitalCities.clear();
```
O método size() é usado para verificar quantos itens existem, devolve o tamanho da coleção.

```java
capitalCities.size();
```

### Iterando os itens

O método keySet() devolve as chaves e o método values() os valores.

```java
// Print keys
for (String i : capitalCities.keySet()) {
  System.out.println(i);
}
```

```java
// Print values
for (String i : capitalCities.values()) {
  System.out.println(i);
}
```

```java
// Print keys and values
for (String i : capitalCities.keySet()) {
  System.out.println("key: " + i + " value: " + capitalCities.get(i));
}
```

Exemplo
```java
// Import the HashMap class
import java.util.HashMap;

public class MyClass {
  public static void main(String[] args) {

    // Create a HashMap object called people
    Map<String, Integer> people = new HashMap<>();

    // Add keys String and values Integer (Name, Age)
    people.put("John", 32);
    people.put("Steve", 30);
    people.put("Angie", 33);

    for (String i : people.keySet()) {
      System.out.println("Name: " + i + " Age: " + people.get(i));
    }
  }
}
```
