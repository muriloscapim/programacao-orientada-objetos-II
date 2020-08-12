# Pacotes

Um pacote em Java é um namespace usado para agrupar um conjunto de interfaces e classes relacionadas.

Usamos pacotes para evitar conflitos de nomes e para escrever um código de melhor manutenção. Os pacotes são divididos em duas categoria:
- Pacotes integrados (pacotes da API Java) e os Pacotes definidos pelo usuário.

![Built-in-packages-in-java](https://user-images.githubusercontent.com/56240254/90011726-7ed07b80-dc78-11ea-8ae9-6c57e1c8a0cf.jpg)

Os pacotes ajudam a organizar o código e fornecem outra camada de encapsulamento. (controle de acesso).

As classes definidas dento de um pacote devem ser acessadas com o uso do nome de seu pacote.

Para usar uma classe ou pacote da biblioteca Java, usamos a palavra-chave **import**.

Sintaxe:

```java
import package.name.Class; // Import a single class
import package.name.*; // Import the whole package
```

### Importar uma classe

Exemplo no IntelliJ

```java
import java.util.Scanner; // import the Scanner class 

class MyClass {
  public static void main(String[] args) {
    Scanner myObj = new Scanner(System.in);
    String userName;
    
    // Enter username and press Enter
    System.out.println("Enter username"); 
    userName = myObj.nextLine();   
       
    System.out.println("Username is: " + userName);        
  }
}
```

**No exemplo java.util é um pacote, enquanto Scanner é uma classe do pacote java.util.**

### Pacotes definidos pelo usuário

O Java usa o diretório do sistema de arquivo para armazenar os pacotes.

Para criar um pacote, use a palavra-chave **package**.

>Usando a IDE: New > Package > mypack

```java
package mypack;

public class MyPackageClass {
  public static void main(String[] args) {
    System.out.println("This is my package!");
  }
}
```

## Pacotes e o acesso a membros

Os pacotes também participam do mecanismo de controle de acesso Java.

A visibilidade de um elemento é determinada por sua especificação de acesso **private, public, protected ou padrão** e o pacote em que ele reside.

A visibilidade de um elemento é determinada por sua visibilidade dentro de uma classe e sua visibilidade dentro de um pacote.

Se o membro de uma classe não tiver um modificador de acesso explícito, será default, poderá ser visto dentro de seu pacote, mas não fora dele. Privados para o pacote, mas públicos dentro dele.

Membros declarados como **public** podem ser vistos em todos os locais, inclusive classes e pacotes diferentes, pois não há restrição quanto ao seu uso ou acesso.

Um membro **private** só pode ser acessado por outros membros de sua classe. Ele não é afetado por sua associação a um pacote.

Um membro **protected** pode ser acessado dentro de seu pacote e por todas as subclasses, inclusive subclasses em outros pacotes.

**Uma classe tem dois níveis de acesso possíveis: padrão e público. Quando uma classe é declarada como public, pode ser acessada por qualquer código. O acesso padrão, só poderá ser acessada por um código do mesmo pacote.**

Acesso a membros de classes

| | Membro privado | Membro padrão | Membro protegido | Membro público |
| - | - | - | - | - |
| Visível dentro da mesma classe | Sim | Sim | Sim | Sim |
| Visível dentro do mesmo pacote pela subclasse | Não | Sim | Sim | Sim |
| Visível dentro do mesmo pacote por não subclasses | Não | Sim | Sim | Sim |
| Visível dentro de pacote diferente pela subclasse | Não | Não | Sim | Sim |
| Visível dentro de pacote diferente por não subclasses | Não | Não | Não | Sim |


## Entendendo membros protegidos

O modificador **protected** cria um membro que **pode ser acessado dentro de seu pacote e por subclasses de outros pacotes.**

Um membro protected pode ser usado por todas as subclasses, mas continua protegido contra o acesso arbitrário de códigos de fora de seu pacote.

```java
package mypack1;

public class Person {
  protected String fname = "John";
  protected String lname = "Doe";
  protected String email = "john@doe.com";
  protected int age = 24;
}
```

```java
package mypack2;

import mypack1.Person;

public class Student extends Person {
  private int graduationYear = 2018;
  
  public void Details() {
    System.out.println("Name: " + fname + " " + lname);
    System.out.println("Email: " + email);
    System.out.println("Age: " + age);
    System.out.println("Graduation Year: " + graduationYear);
  }
}
```

```java
package mypack2;

public class ProtectedDemo {
  public static void main(String[] args) {
    Student myObj = new Student();
    myObj.Details();
  }
}
```
