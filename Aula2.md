## Final

Em Java, com o uso da palavra-chave **final** impedimos que um método seja sobreposto ou uma classe seja herdada.

### A palavra-chave final impede a sobreposição

Para impedir que um método seja sobreposto, especifique **final** como modificador no início de sua declaração.

**Métodos declarados como final não podem ser sobrepostos.**

```java
public class A {
    
    final void meth() {
        System.out.println("This is a final method.");
    }
}
```

```java
public class B extends A {
    
    // Erro! não pode sobrepor
    void meth() {
        System.out.println("Illegal!");
    }
}
```
O método **meth()** é declarado como **final**, não pode ser sobreposto em B. Ocorrerá um erro em tempo de compilação.

### A palavra-chave final impede a herança

Para impedir que uma classe seja herdada precedemos sua declaração com **final**.

**A declaração de uma classe como final também declara implicitamente todos os seus métodos como final.**

É inválido declarar uma classe como **abstract** e **final**, uma vez que uma classe abstrata é individualmente incompleta e depende de suas subclasses para fornecer implementações completas.

:pushpin: O Java não permite a existência de uma classe que possua a seguinte assinatura: **public abstract final class Exemplo { ... } ou public final asbtract class Exemplo { ... }.**

Do ponto de vista conceitual, não é relevante ter uma classe que não poderia ser herdada e instanciada.

Porém, por exemplo, uma classe utilitária, geralmente não precisa ser herdada e instanciada, pois todos seus métodos são estáticos. Poderiamos tornar o construtor dessa classe como private, para não poder ser instanciada.

Exemplo:

```java
public final class A {
}
```

```java
public class B extends A {
}
```
:pushpin: É inválido B herdar A, já que A é declarada como final.

### Atributos final

O final também pode ser aplicado a variáveis, para criar **constantes**.

Ao preceder o nome da variável de uma classe com final, seu valor não poderá ser alterado durante todo o tempo de vida do programa.

```java
public class FinalVariable {

final int x = 10;
}
```

```java
public class DemoFinalVariable {
  public static void main(String[] args) {
    FinalVariable obj = new FinalVariable();
    obj.x = 25; // will generate an error: cannot assign a value to a final variable
    System.out.println(obj.x);
  }
}
```
:pushpin: Por uma questão estilística, muitos programadores de Java usam identificadores maiúsculos em constantes final, não é uma regra fixa.
