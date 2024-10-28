import java.util.Scanner;

class Livro {
    String titulo;
    String autor;
    String dataNascimento;
    String idiomaOriginal;

    Livro(String titulo, String autor, String dataNascimento, String idiomaOriginal) {
        this.titulo = titulo;
        this.autor = autor;
        this.dataNascimento = dataNascimento;
        this.idiomaOriginal = idiomaOriginal;
    }
}

public class Programa {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Livro[] livros = new Livro[5];

        // Inicializando os livros
        livros[0] = new Livro("O Senhor dos Anéis", "J.R.R. Tolkien", "03/01/1892", "Inglês");
        livros[1] = new Livro("Dom Quixote", "Miguel de Cervantes", "29/09/1547", "Espanhol");
        livros[2] = new Livro("O Processo", "Franz Kafka", "03/07/1883", "Alemão");
        livros[3] = new Livro("Os Sertões", "Euclides da Cunha", "20/01/1866", "Português");
        livros[4] = new Livro("Madame Bovary", "Gustave Flaubert", "12/12/1821", "Francês");

        // Imprimindo os livros
        for (int i = 0; i < 5; i++) {
            System.out.println("Título: " + livros[i].titulo);
            System.out.println("Autor: " + livros[i].autor);
            System.out.println("Data de Nascimento: " + livros[i].dataNascimento);
            System.out.println("Idioma Original: " + livros[i].idiomaOriginal);
            System.out.println();
        }

        // Perguntando o idioma original
        for (int i = 0; i < 5; i++) {
            System.out.println("O idioma original do livro '" + livros[i].titulo + "' é:");
            System.out.println("1. Inglês");
            System.out.println("2. Espanhol");
            System.out.println("3. Alemão");
            System.out.println("4. Português");
            System.out.println("5. Francês");
            int escolha = scanner.nextInt();
            switch (escolha) {
                case 1:
                    System.out.println("Inglês");
                    break;
                case 2:
                    System.out.println("Espanhol");
                    break;
                case 3:
                    System.out.println("Alemão");
                    break;
                case 4:
                    System.out.println("Português");
                    break;
                case 5:
                    System.out.println("Francês");
                    break;
                default:
                    System.out.println("Opção inválida");
            }
            System.out.println();
        }
    }
}

