## Interfaces

Interface é um tipo que define um conjunto de operações que uma classe deve implementar.

A interface estabelece um **contrato** que a classe deve cumprir.

Nas aplicações orientadas a objetos podemos criar um "contrato" para definir um conjunto de métodos que devem ser implementado pelas classes que "assinarem" este contrato.

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

Podemos definir uma interface (contrato) para padronizar as assinaturas dos métodos oferecidos pelos objetos que representam as contas em um sistema de um banco.

```java
interface Conta {
  void deposita(double valor);
  void saca(double valor);
  double getSaldo();
}
```

Os métodos de uma interface não possuem corpo (implementação) pois serão implementados nas classes que implementarem a interface.

:pushpin: Todos os métodos em uma interface são **públicos** e **abstratos**. Os modificadores public e abstract são opcionais.

```java
class ContaPoupanca implements Conta {
   private double saldo;
   
   public void deposita(double valor) {
      this.saldo += valor;
   }
   
   public void saca(double valor) {
      this.saldo -= valor;
   }
   
   public double getSaldo() {
      return this.saldo;
   }
}
```

```java
class ContaCorrente implements Conta {
   private double saldo;
   private double taxaPorOperacao = 0.45;
   
   public void deposita(double valor) {
      this.saldo += valor - this.taxaPorOperacao;
   }
   
   public void saca(double valor) {
      this.saldo -= valor + this.taxaPorOperacao;
   }
   
   public double getSaldo() {
      return this.saldo;
   }
}
```

:pushpin: As classes concretas que implementam a interface são obrigadas a possuir uma implementação para cada método declarado na interface. Caso contrário, ocorrerá um erro de compilação.

:pushpin: **Como vantagens de utilizar interfaces é a padronização das assinaturas dos métodos oferecidos por um determinado conjunto de classes.**

:pushpin: **A garantia que as classes implementem certos métodos.**

:pushpin: **Polimorfismo**.

## Polimorfismo

Se uma classe implementa uma interface, podemos aplicar a ideia do polimorfismo assim como na herança.

Podemos guardar a referência de um objeto do tipo ContaCorrente em uma variável do tipo Conta.

Podemos passar uma variável do tipo ContaCorrente para um método que o parâmetro seja do tipo Conta.

```java
class GeradorDeExtrato {
  public void geraExtrato(Conta c) {
      System.out.println("EXTRATO *** SALDO: " + c.getSaldo());
  }
}
```

```java
public class DemoInterface {
   public static void main(String[] args) {
   
      ContaCorrente cc = new ContaCorrente();
      ContaPoupanca cp = new ContaPoupanca();
      
      cc.deposita(500);
      cp.deposita(500);
      
      cc.saca(100);
      cp.saca(150);
       
      GeradorDeExtrato extrato = new GeradorDeExtrato();
      extrato.geraExtrato(cc);
      extrato.geraExtrato(cp);
   }
}
```
![abstract-class-vs-interface](https://user-images.githubusercontent.com/56240254/90635607-c66a8080-e1ff-11ea-987d-451b628af611.png)

![InterfaceVsAbstractClassJava8](https://user-images.githubusercontent.com/56240254/90635655-d5e9c980-e1ff-11ea-9ed6-8974995c5633.png)
