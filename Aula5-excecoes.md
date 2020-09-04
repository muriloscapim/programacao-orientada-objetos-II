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
