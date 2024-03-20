# atividade-complementares-



package loja;

import java.util.Scanner;

public class Loja {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Instanciando objetos da classe Eletronico e aplicando desconto
        Eletronico eletronico = new Eletronico(1, "Smartphone", 1500.0, 12);
        eletronico.descontarBlackFriday();

        // Instanciando objeto da classe Livro
        Livro livro = new Livro(2, "O Senhor dos Anéis", 50.0, "J.R.R. Tolkien");

        // Exibindo detalhes dos produtos
        System.out.println("Detalhes do Eletrônico:");
        eletronico.exibirDetalhes();
        System.out.println("\nDetalhes do Livro:");
        livro.exibirDetalhes();

        scanner.close();
    }
}


package loja;

class Livro extends Produto {
    private String autor;

    public Livro(int codigo, String nome, double precoUnitario, String autor) {
        super(codigo, nome, precoUnitario);
        this.autor = autor;
    }

    public String getAutor() {
        return autor;
    }

    public void setAutor(String autor) {
        this.autor = autor;
    }

    public void exibirAutor() {
        System.out.println("Autor: " + autor);
    }

    @Override
    public void exibirDetalhes() {
        super.exibirDetalhes();
        exibirAutor();
    }
}

package loja;

class Eletronico extends Produto {
    private int garantiaMeses;

    public Eletronico(int codigo, String nome, double precoUnitario, int garantiaMeses) {
        super(codigo, nome, precoUnitario);
        this.garantiaMeses = garantiaMeses;
    }

    public int getGarantiaMeses() {
        return garantiaMeses;
    }

    public void setGarantiaMeses(int garantiaMeses) {
        this.garantiaMeses = garantiaMeses;
    }

    public int calculaGarantiaEstendida() {
        return garantiaMeses + 12;
    }

    @Override
    public void exibirDetalhes() {
        super.exibirDetalhes();
        System.out.println("Garantia: " + garantiaMeses + " meses");
    }
}

package loja;

class Produto {
    private int codigo;
    private String nome;
    private double precoUnitario;

    public Produto(int codigo, String nome, double precoUnitario) {
        this.codigo = codigo;
        this.nome = nome;
        this.precoUnitario = precoUnitario;
    }

    public int getCodigo() {
        return codigo;
    }

    public void setCodigo(int codigo) {
        this.codigo = codigo;
    }

    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public double getPrecoUnitario() {
        return precoUnitario;
    }

    public void setPrecoUnitario(double precoUnitario) {
        this.precoUnitario = precoUnitario;
    }

    public void exibirDetalhes() {
        System.out.println("Código: " + codigo);
        System.out.println("Nome: " + nome);
        System.out.println("Preço Unitário: R$" + precoUnitario);
    }

    public void descontarBlackFriday() {
        this.precoUnitario *= 0.8; // Aplica desconto de 20%
    }
}
