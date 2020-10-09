```java
public interface Produto {

    public abstract Integer getId();
    public abstract double getValor();
    public abstract String getNome();
    public abstract String getDescricao();
}
```

```java
public interface Promocional {

    boolean aplicaDescontoDe(double porcentagem);
}
```

```java
public class Autor {

    private String nome;
    private String email;
    private String cpf;

    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    public String getCpf() {
        return cpf;
    }

    public void setCpf(String cpf) {
        this.cpf = cpf;
    }

    public void mostrarDetalhes() {
        System.out.println("Mostrando detalhes do autor");
        System.out.println("Nome: " + nome);
        System.out.println("Email: " + email);
        System.out.println("CPF: " + cpf);
    }
}
```

```java
public abstract class Livro implements Produto {

    private Integer id;
    private String nome;
    private String descricao;
    private double valor;

    private Autor autor;

    public Livro(Autor autor) {
        this.autor = autor;
    }

    public abstract void mostrarDetalhes();

    @Override
    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }

    @Override
    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    @Override
    public String getDescricao() {
        return descricao;
    }

    public void setDescricao(String descricao) {
        this.descricao = descricao;
    }

    @Override
    public double getValor() {
        return valor;
    }

    public void setValor(double valor) {
        this.valor = valor;
    }

    public Autor getAutor() {
        return autor;
    }

    public void setAutor(Autor autor) {
        this.autor = autor;
    }
}
```

```java
public class LivroFisico extends Livro implements Promocional {

    public LivroFisico(Autor autor) {
        super(autor);
    }

    @Override
    public void mostrarDetalhes() {
        System.out.println("Mostrando detalhes do livro físico");
        System.out.println("Id: " + getId());
        System.out.println("Nome: " + getNome());
        System.out.println("Descrição: " + getDescricao());
        System.out.println("Valor: " + getValor());
        getAutor().mostrarDetalhes();
        System.out.println();
    }

    @Override
    public boolean aplicaDescontoDe(double porcentagem) {
        if (porcentagem > 0.3) {
            return false;
        }
        double desconto = getValor() * porcentagem;
        setValor(getValor() - desconto);
        return true;
    }
}
```

```java
public class Ebook extends Livro implements Promocional {

    private String waterMark;

    public Ebook(Autor autor) {
        super(autor);
    }

    @Override
    public boolean aplicaDescontoDe(double porcentagem) {

        if (porcentagem > 0.15) {
            return false;
        }
        double desconto = getValor() * porcentagem;
        setValor(getValor() - desconto);
        return true;
    }

    public String getWaterMark() {
        return waterMark;
    }

    public void setWaterMark(String waterMark) {
        this.waterMark = waterMark;
    }

    @Override
    public void mostrarDetalhes() {
        System.out.println("Mostrando detalhes do ebook");
        System.out.println("Nome: " + getNome());
        System.out.println("Descrição: " + getDescricao());
        System.out.println("Valor: " + getValor());
        System.out.println("WaterMark: " + getWaterMark());
        getAutor().mostrarDetalhes();
        System.out.println();
    }
}
```

```java
import java.util.ArrayList;
import java.util.List;

public class CarrinhoDeCompras {

    private double total;
    private List<Produto> produtos;

    public CarrinhoDeCompras() {
        this.produtos = new ArrayList<>();
    }

    public void adiciona(Produto produto) {
        this.produtos.add(produto);
    }
    public void remove(int posicao) {
        this.produtos.remove(posicao);
    }

    public double getTotal() {
        return total;
    }

    public List<Produto> getProdutos() {
        return produtos;
    }
}
```

```java
import java.util.List;

public class RegistroDeVendas {

    public static void main(String[] args) {

        Autor autor = new Autor();
        autor.setNome("Rodrigo");

        LivroFisico fisico = new LivroFisico(autor);
        fisico.setNome("Test Driven Development");
        fisico.setValor(59.90);

        Ebook ebook = new Ebook(autor);
        ebook.setNome("Test Driven Development");
        ebook.setValor(29.90);

        CarrinhoDeCompras carrinho = new CarrinhoDeCompras();
        carrinho.adiciona(fisico);
        carrinho.adiciona(ebook);

        List<Produto> produtos = carrinho.getProdutos();

        produtos.forEach(p -> {
            if (p instanceof LivroFisico) {
                ((LivroFisico) p).mostrarDetalhes();
            } else if (p instanceof Ebook) {
                ((Ebook) p).mostrarDetalhes();
            }
        });

        /*
        for (Produto produto : produtos) {
            System.out.println(produto);
        }
        */
    }
}
```
