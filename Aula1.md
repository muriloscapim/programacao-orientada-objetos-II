## IDE

A IDE IntelliJ pode se baixada em: https://www.jetbrains.com/pt-br/idea/download/#section=windows

## Membros estáticos

* Normalmente, um membro de uma classe é acessado por intermédio de um objeto.

* Podemos definir um membro de uma classe para ser usado independentemente de qualquer objeto dessa classe.

* Para isso, antes da declaração do membro colocamos a palavra-chave **static**.

* Quando um membro (variáveis e métodos) é static, pode ser acessado sem ser criado um objeto de sua classe.

* Para usar um membro static, especificamos o nome de sua classe seguido pelo operador ponto.

> Exemplo: Atribuir o valor 10 a uma variável static chamada count pertencente à classe Timer.

```java
Timer.count = 10;
```

> Um método static pode ser chamado da mesma forma.

* Exemplo no IntelliJ

```java
public class StaticMethod {

    static void myStaticMethod() {
        System.out.println("Static methods can be called without creating objects");
    }

    public void myPublicMethod() {
        System.out.println("Public methods must be called by creating objects");
    }
}
```
```java
public class StaticMethodDemo {
    public static void main(String[] args) {
        StaticMethod.myStaticMethod(); // Call the static method

        StaticMethod myObj = new StaticMethod();
        myObj.myPublicMethod();
    }
}
```
* Exemplo

A classe Math do Java

```java
Math.sqrt();
```

## Classes e métodos abstratos

Quando temos uma superclasse que define uma forma generalizada.

Este tipo de classe determina a natureza dos métodos que as subclasses devem implementar, mas não fornece uma implementação desses métodos.

Ocorre quando uma superclasse não pode criar uma implementação significativa de um método, por ser muito abstrato.

Um **método abstrato** assegura que uma subclasse sobreponha todos os métodos necessários.

O método abstrato é criado pela especificação do modificador de tipo **abstract**.

**Ele não tem corpo e, portanto, não é implementado pela superclasse. Logo, uma subclasse deve sobrescrevê-lo**.

Para declarar um método abstrato, use esta forma:

**abstract *tipo* *nome(lista-parâmetros);***

**Não há corpo no método**.

O modificador abstract só pode ser usado em métodos de instância. Ele não pode ser aplicado a métodos static ou a construtores.

**Uma classe que contém um ou mais métodos abstratos também deve ser declarada como abstrata** precedendo sua declaração class com o modificador abstract.

**Um método abstrato pertence a uma classe abstrata.**

Já que uma classe abstrata não define uma implementação completa, **não podem existir objetos dessa classe**.

Ao tentar criar um objeto de uma classe abstrata usando new resultará em um erro de tempo de compilação.

**Quando uma subclasse herda uma classe abstrata, ela deve implementar todos os métodos abstratos da superclasse.**

Uma classe abstrata também pode conter métodos concretos que uma subclasse possa usar da forma em que se encontram.

**Os métodos declarados como *abstract* têm que ser sobrepostos (sobreescritos) pelas subclasses.**

Exemplo no IntelliJ

```java
public abstract class Shape {

    private double width;
    private double height;
    private String name;

    // Construtor padrão
    public Shape() {
    }

    // Construtor parametrizado
    public Shape(double width, double height, String name) {
        this.width = width;
        this.height = height;
        this.name = name;
    }

    public double getWidth() {
        return width;
    }

    public void setWidth(double width) {
        this.width = width;
    }

    public double getHeight() {
        return height;
    }

    public void setHeight(double height) {
        this.height = height;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void showDim() {
        System.out.println("Width and height are " +
                width + " and " + height);
    }

    // area() é um método abstrato
    public abstract double area();
}
```

```java
public class Triangle extends Shape {

    private String style;

    public Triangle() {
    }

    public Triangle(double width, double height, String style) {
        super(width, height, "triangle");
        this.style = style;
    }

    @Override
    public double area() {
        return getWidth() * getHeight() / 2;
    }

    void showStyle() {
        System.out.println("Triangle is " + style);
    }
}
```

```java
public class Rectangle extends Shape {

    public Rectangle() {
    }

    public Rectangle(double width, double height) {
        super(width, height, "rectangle");
    }

    @Override
    public double area() {
        return getWidth() * getHeight();
    }
}
```

```java
public class AbsShape {
    public static void main(String[] args) {
        // Shape shape = new Shape(); // Erro!

        Shape shape = new Triangle(8.0, 12.0, "outlined");
        System.out.println("Object is " + shape.getName() +
                " Area is " + shape.area());
        Shape shape2 = new Rectangle(10.0, 4.0);
        System.out.println("Object is " + shape2.getName() +
                " Area is " + shape2.area());
    }
}
```
