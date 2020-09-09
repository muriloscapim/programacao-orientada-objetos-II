# Exceções

Uma exceção é um erro que ocorre no tempo de execução. Ex: divisão por zero, arquivo não encontrado, conectar em um servidor inexistente, tentar escrever em um arquivo sobre o qual não se tem permissão de escrita.

Usando o tratamento de exceções do Java, podemos tratar erros de tempo de execução de maneira estruturada e controlada.

O tratamento de exceções otimiza o tratamento de erros, permitindo que o programa defina um bloco de código, chamado tratador de exceções, executado automaticamente quando um erro ocorre.

Não é necessário verificar manualmente o sucesso ou a falha de cada chamada de método ou operação específica. Se um erro ocorrer, ele será processado pelo tratador de exceções.

## Hierarquia de exceções

Em Java, todas as exceções são representadas por classes e todas as classes de exceções são derivadas de uma classe chamada **Throwable**. Quando uma exceção ocorre, um objeto de algum tipo de classe de exceção é gerado.

Há duas subclasses de Throwable: **Exception** e **Error**.

![img1-5928057](https://user-images.githubusercontent.com/56240254/90990671-a1686b80-e579-11ea-9df2-6cf2ffb56272.jpg)

As exceções de tipo Error estão relacionadas a erros que ocorrem na máquina virtual Java e não nos programas. Esses tipos de exceções geralmente os programas não lidam com elas.

Erros que resultam da atividade do programa são representados por subclasses de Exception. Por exemplo, erros de divisão por zero, que excedem os limites do array e relacionados a arquivos.

Uma subclasse importante de Exception é RuntimeException, que é usada para representar vários tipos comuns de erros de tempo de execução.

## Tratamento de exceções

O tratamento de exceções em Java é gerenciado por cinco palavras-chave: **try, catch, throw, throws e finally**.

## Usando try e catch

As palavras-chave **try** e **catch** formam a base do tratamento de exceções.

Forma geral dos bloco try/catch de tratamento de exceções:

```java
try {
  //  Block of code to try
}
catch(Exception e) {
  //  Block of code to handle errors
}
```

No bloco **try** são introduzidas todas as linhas de código que podem vir a lançar uma exceção.

No bloco **catch** é descrita a ação que ocorrerá quando a exceção for capturada.

Quando uma exceção é lançada, ela é capturada pela instrução **catch** correspondente, que então a processa.

Podemos ter mais de uma instrução catch associada a uma instrução try.

O tipo da exceção determina que instrução catch será executada.

:point_right: Se nenhuma exceção for lançada por um bloco try, nenhuma instrução catch será executada. As instruções catch só são executadas quando ocorre uma exceção.

### Exemplo no IntelliJ

Ao tentar acessar um array além de seus limites, a JVM lança uma **ArrayIndexOutOfBoundsException**.

O programa a seguir gera intencionalmente essa exceção e então a captura:

```java
public class MyClass {
  public static void main(String[] args) {
    try {
      int[] myNumbers = {1, 2, 3};
      System.out.println(myNumbers[10]);
    } catch (ArrayIndexOutOfBoundsException e) {
      System.out.println("Something went wrong.");
    }
  }
}
```

Capturar exceções Java impede que o programa seja encerrado de modo anormal. Quando uma exceção é lançada, ela deve ser capturada por um código em algum local.

Quando o programa não captura uma exceção, ela é capturada pela JVM. O tratador de exceções padrão da JVM encerra a execução e exibe um rastreamento de pilha e uma mensagem de erro.

```java
public class MyClass {
  public static void main(String[] args) {
    int[] myNumbers = {1, 2, 3};
    System.out.println(myNumbers[10]); // error!
  }
}
```
Toda e qualquer aplicação está sujeita a falhas e, por conta disso, precisa ter um tratamento dessas falhas.


## Lançando uma exceção

Até então capturamos exceções geradas automaticamente pela JVM.

Contudo, é possível lançar manualmente uma exceção usando a instrução **throw**.

Sua forma geral é:

**throw objExc**

objExc deve ser um objeto de uma classe de exceção derivada de Throwable.

Exemplo que mostra a instrução throw lançando manualmente uma ArithmeticException:

```java
public class MyClass {
  static void checkAge(int age) { 
    if (age < 18) {
      throw new ArithmeticException("Access denied - You must be at least 18 years old."); 
    } else {
      System.out.println("Access granted - You are old enough!"); 
    }
 } 
 
 public static void main(String[] args) { 
   checkAge(15); 
 } 
}
```

A instrução throw lança um objeto, logo, devemos criar um objeto usando o operador new para ela lançar.

## Usando finally

Podemos definir um bloco de código para ser executado na saída de um bloco try/catch.

Por exemplo, uma exceção poderia causar um erro que encerrasse o método atual, no entanto, esse método pode ter aberto uma conexão de rede ou arquivo que precise ser fechado.

Esses tipos de circunstâncias são comuns em programação e no Java podemos tratá-las dentro do bloco **finally**.

Para criar um bloco de código que será executado após os blocos try/catch, incluimos um bloco finally ao final de uma sequência try/catch.

Forma geral de um bloco try/catch que inclui um bloco finally:

```java
try {
	// bloco de código cujos erros estão sendo monitorados
}
catch (TipoExceção1 obj) {
	// tratador de TipoExceção1
}
catch (TipoExceção2 obj) {
	// tratador de TipoExceção2
}
finally {
	// código do bloco finally
}
```

**O bloco finally será executado sempre que a execução deixar um bloco try/catch, não importando as condições causadoras.**

Isto é, tendo o bloco try terminado normalmente (não ocorreu nenhuma exceção), ou devido a uma exceção, o último código executado será o definido por finally.

Exemplo no IntelliJ

```java
public class FinallyDemo {
  public static void main(String[] args) {
    try {
      int[] myNumbers = {1, 2, 3};
      System.out.println(myNumbers[10]);
    } catch (Exception e) {
      System.out.println("Something went wrong.");
    } finally {
      System.out.println("The 'try catch' is finished.");
    }
  }
}
```

## Usando throws

Em alguns casos, quando um método gera uma exceção que ele não trata, deve declará-la em uma clausa **throws**.

Lança exceções para fora do método, que serão tratadas por quem chamar o método.

A forma geral de um método que inclui uma cláusula throws é a seguinte:

```java
tipo-ret nomeMét(lista-parâm) throws lista-exceções {
	// corpo do método
}
```

lista-exceções é uma lista separada por vírgulas com as exceções que o método pode lançar para fora dele.

Exceções que são subclasses de Error e RuntimeException não precisam ser especificadas em uma lista throws. Todos os outros tipos de exceções têm de ser declaradas senão causará um erro de tempo de compilação.

```java
public class MyClass {
  static void checkAge(int age) throws ArithmeticException {
    if (age < 18) {
      throw new ArithmeticException("Access denied - You must be at least 18 years old.");
    }
    else {
      System.out.println("Access granted - You are old enough!");
    }
  }

  public static void main(String[] args) {
    checkAge(15); // Set age to 15 (which is below 18...)
  }
}
```


## Diferences between **throw** and **throws**:

![throw-throws](https://user-images.githubusercontent.com/56240254/92621726-8b0d2000-f29a-11ea-9c5f-69f99cd1fe49.PNG)

## Checked e Unchecked Exceptions

**Exceções Checked** são as exceções **verificadas em tempo de compilação**, aquelas no qual **somos obrigados a tratá-la**, seja com um bloco try-catch ou com um throws (relançando a mesma para outro local).

Se algum código dentro de um método lançar uma exceção verificada, o método deve tratar a exceção ou deve especificar a exceção usando a palavra chave throws.

**Exceções Unchecked** são as exceções que **não são verificadas em tempo de compilação**, não é obrigatório o tratamento da mesma, você pode tratar apenas se quiser, se for necessário para o bom funcionamento da sua aplicação.

Checked exceptions são utilizadas para erros recuperáveis enquanto que Unchecked exceptions são utilizadas para erros irrecuperáveis.

Exemplo no IntelliJ

```java
public class CheckedExceptions {
    public static void main(String[] args) {
        
        FileReader file = new FileReader("C:\\test\\test.txt");
        BufferedReader fileInput = new BufferedReader(file);

        // Print first 3 lines of file "C:\test\a.txt" 
        for (int counter = 0; counter < 3; counter++)
            System.out.println(fileInput.readLine());

        fileInput.close();
    }
}
```

FileReader lança uma exceção checada, somos obrigados a tratá-la.

Para corrigir o exemplo, precisamos especificar a lista de exceções usando throws ou usar o bloco try/catch.

*Como FileNotFoundException é uma subclasse de IOException, podemos apenas especificar IOException na lista de exceções do throws e assim tratar as exceções.*

```java
public class CheckedExceptions {
    public static void main(String[] args) throws IOException {

        FileReader file = new FileReader("C:\\test\\test.txt");
        BufferedReader fileInput = new BufferedReader(file);

        // Print first 3 lines of file "C:\test\a.txt"
        for (int counter = 0; counter < 3; counter++)
            System.out.println(fileInput.readLine());

        fileInput.close();
    }
}
```

```java
public class UncheckedExceptions {
    public static void main(String[] args) {
        int x = 0;
        int y = 10;
        int z = y/x;
    }
}
```
O exemplo compila normalmente, mas quando executado lança uma ArithmeticException. O compilador permitiu a compilação, porque ArithmeticException é uma **exceção não verificada**.

## Criando subclasses de exceções

Embora as exceções internas do Java tratem os erros mais comuns, o mecanismo do Java de tratameto de exceções não se limita a esses erros.

Com o uso de **exceções personalizadas**, podemos gerenciar erros que tenham relação direta com nosso aplicativo.

**Para criar uma classe de exceção, só temos de criar uma subclasse de Exception** (Exception é subclasse de Throwable).

A classe Exception não define um método próprio, mas herda os métodos fornecidos por Throwable. Logo, todas as exceções, inclusive as criadas por nós, têm os métodos definidos por Throwable.

```java
public class MyNewException extends Exception {

    public MyNewException(){
        super();
    }

    public MyNewException(String message){
        super(message);
    }
}

```

Caso você precisar criar uma exceção unchecked, precisará extender a classe RuntimeException.

:point_right: **Uma exception checada é aquela que requer que a exceção seja tratada em um bloco try/catch ou tenha uma cláusula throws na declaração do método.**
