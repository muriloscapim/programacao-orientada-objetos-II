## Interfaces

Interface é um tipo que define um conjunto de operações que uma classe deve implementar.

A interface estabelece um **contrato** que a classe deve cumprir.

```java
interface Shape {
    double area();
    double perimeter();
}
```

![why-use-java-interface](https://user-images.githubusercontent.com/56240254/90635436-96bb7880-e1ff-11ea-9beb-21d63592fbd7.jpg)

Uma interface é sintaticamente semelhante a uma classe abstrata pois podemos especificar um ou mais métodos sem corpo (métodos abstratos).

Estes métodos devem ser implementados por uma classe para que suas ações sejam definidas.

**Uma interface especifica o que deve ser feito, mas não como deve ser feito.**

Não há limite para o número de classes que podem implementá-lá. **E uma classe pode implementar qualquer número de interfaces.**

Para implementar uma interface, a classe deve implementar os métodos descritos nela.

Duas classes podem implementar a mesma interface de diferentes maneiras, mas ambas darão suporte ao mesmo conjunto de métodos.

A partir do JDK 8 é possível adicionar um método concreto a uma interface "default methods". Usando o modificador default.
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

### Implementando interfaces

Para implementar uma interface, inclua a cláusula **implements** em uma definição de classe e crie os métodos requeridos pela interface.

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
### Implementando várias interfaces

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

Exemplo no IntelliJ

```java
public interface FiguraGeometrica {
  
  public String getNomeFigura();
  public int getArea();
  public int getPerimetro();
}
```

```java
public class Quadrado implements FiguraGeometrica {

    private int lado;

    public int getLado() {
        return lado;
    }

    public void setLado(int lado) {
        this.lado = lado;
    }

    @Override
    public String getNomeFigura() {
        return "quadrado";
    }

    @Override
    public int getArea() {
        return lado * lado;
    }

    @Override
    public int getPerimetro() {
        return lado * 4;
    }
}
```

```java
public class Triangulo implements FiguraGeometrica {

    private int base;
    private int altura;
    private int ladoA;
    private int ladoB;
    private int ladoC;

    public int getAltura() {
        return altura;
    }

    public void setAltura(int altura) {
        this.altura = altura;
    }

    public int getBase() {
        return base;
    }

    public void setBase(int base) {
        this.base = base;
    }

    public int getLadoA() {
        return ladoA;
    }

    public void setLadoA(int ladoA) {
        this.ladoA = ladoA;
    }

    public int getLadoB() {
        return ladoB;
    }

    public void setLadoB(int ladoB) {
        this.ladoB = ladoB;
    }

    public int getLadoC() {
        return ladoC;
    }

    public void setLadoC(int ladoC) {
        this.ladoC = ladoC;
    }

    @Override
    public String getNomeFigura() {
        return "Triangulo";
    }

    @Override
    public int getArea() {
        return (base * altura) / 2;
    }

    @Override
    public int getPerimetro() {
        return ladoA + ladoB + ladoC;
    }
}
```
Ambas as classe seguiram o contrato da interface FiguraGeometrica, porém cada uma delas a implementou de maneira diferente.

Ao contrário da herança que limita uma classe a herdar somente uma classe pai por vez, é possível que uma classe implemente várias interfaces.

![abstract-class-vs-interface](https://user-images.githubusercontent.com/56240254/90635607-c66a8080-e1ff-11ea-987d-451b628af611.png)

![InterfaceVsAbstractClassJava8](https://user-images.githubusercontent.com/56240254/90635655-d5e9c980-e1ff-11ea-9ed6-8974995c5633.png)
