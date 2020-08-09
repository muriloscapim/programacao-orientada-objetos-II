## Interfaces

Uma interface é sintaticamente semelhante a uma classe abstrata pois podemos especificar um ou mais métodos sem corpo.

Estes métodos devem ser implementados por uma classe para que suas ações sejam definidas.

**Uma interface especifica o que deve ser feito, mas não como deve ser feito.**

Não há limite para o número de classes que podem implementá-lá. **E uma classe pode implementar qualquer número de interfaces.**

Para implementar uma interface, a classe deve implementar os métodos descritos nela.

Duas classes podem implementar a mesma interface de diferentes maneiras, mas ambas darão suporte ao mesmo conjunto de métodos.

A partir do JDK 8 é possível adicionar um método concreto a uma interface. Usando o modificador default.
    Todas as classes que implementarem esta interface já ganham uma implementação do método.
    Suas implementações não precisam necessariamente reescrevê-lo.
    É possível reescrevê-lo nas classes que implementam a interface.

Exemplo do uso do default

```java
public interface ICaixaEletronico {
  void sacar(float valor);
  
  default void verificaFraude(){
    System.out.println("Verificação de fraude iniciada");
  }
}
```

```java
public class CaixaEletronico implements ICaixaEletronico {

  @Override
  public void sacar(float valor) {
    System.out.println("Vou sacar " + valor);
  }
}
```

```java
public class Principal {
	public static void main(String[] args) {
		CaixaEletronico caixa = new CaixaEletronico();
		caixa.verificaFraude();
		caixa.sacar(10);
	}
}
```

Na forma tradicional de uma interface, **os métodos são declarados apenas seu tipo de retorno e assinatura. São métodos abstratos.**

A classe que incluir a interface deve implementar todos os seus métodos.

**Em uma interface, os métodos são implicitamente public.**

**As variáveis declaradas em uma interface não são variáveis de instância. São implicitamente public, final e static e devem ser inicializadas. São constantes.**

Exemplo no IntelliJ

```java
interface Animal {
  public void animalSound(); // interface method (does not have a body)
  public void sleep(); // interface method (does not have a body)
}
```

```java
// Pig "implements" the Animal interface
class Pig implements Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
  public void sleep() {
    // The body of sleep() is provided here
    System.out.println("Zzz");
  }
```

```java
class MyMainClass {
  public static void main(String[] args) {
    Pig myPig = new Pig();  // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}
```

implementando várias interfaces

```java
interface FirstInterface {
  public void myMethod(); // interface method
}
```

```java
interface SecondInterface {
  public void myOtherMethod(); // interface method
}
```

```java
class DemoInterfaces implements FirstInterface, SecondInterface {
  public void myMethod() {
    System.out.println("Some text..");
  }
  public void myOtherMethod() {
    System.out.println("Some other text...");
  }
}
```

```java
class MyMainClass {
  public static void main(String[] args) {
    DemoInterfaces myObj = new DemoInterfaces();
    myObj.myMethod();
    myObj.myOtherMethod();
  }
}
```
