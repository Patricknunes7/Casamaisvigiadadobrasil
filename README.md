# Casa mais vigiada do brasil
[![NPM](https://img.shields.io/npm/l/react)](https://github.com/devsuperior/sds1-wmazoni/blob/master/LICENSE) 

# Sobre o projeto
Este código Java implementa um programa simples para simular uma votação de eliminação, como aquelas vistas em programas de reality show

## Requisitos
Registro de Participantes:
Os participantes do programa são armazenados em uma lista (ArrayList<Jogador>), inicializada com nomes pré-definidos.
Votação:
O programa solicita aos usuários que votem em quem desejam eliminar do programa.
Os votos são registrados e contabilizados para cada participante.
Os usuários podem encerrar a votação digitando "sair".
Apuração de Votos:
Ao final da votação, o programa calcula os votos recebidos por cada participante.
O participante com o maior número de votos é considerado eliminado.
Feedback ao Usuário:
Durante a votação, o programa fornece feedback sobre os votos registrados.
Ao final da votação, o programa anuncia o participante eliminado e o número de votos recebidos por ele.

# Codigo completo
## Questão um
import java.util.ArrayList;
import java.util.Scanner;

class Jogador {
    private String nome;
    private int votos;

    public Jogador(String nome) {
        this.nome = nome;
        this.votos = 0;
    }

    public String getNome() {
        return nome;
    }

    public int getVotos() {
        return votos;
    }

    public void incrementaUmVoto() {
        this.votos++;
    }
}

public class CasaMaisVigiada {
    public static void main(String[] args) {
        ArrayList<Jogador> participantes = new ArrayList<>();
        inicializaParticipantes(participantes);

        Scanner scanner = new Scanner(System.in);

        System.out.println("Votação para eliminação (digite 'sair' para encerrar):");
        while (true) {
            System.out.print("- Em quem você vota para sair da casa? ");
            String voto = scanner.nextLine().trim();
            if (voto.equalsIgnoreCase("sair")) {
                break;
            }

            Jogador jogadorVotado = encontraJogador(participantes, voto);
            if (jogadorVotado != null) {
                jogadorVotado.incrementaUmVoto();
                System.out.println("Voto computado para " + jogadorVotado.getNome() + ".");
            } else {
                System.out.println("Participante não encontrado. Por favor, insira um nome válido.");
            }
        }

        scanner.close();

        Jogador eliminado = apuraVotos(participantes);

        System.out.println("Se eu conseguir mover montanhas, se eu conseguir surfar um tsunami, se eu conseguir domar o sol,");
        System.out.println("se eu conseguir fazer o mar virar sertão, e o sertão virar mar, se eu conseguir dizer o que eu nunca");
        System.out.println("vou conseguir dizer, aí terá chegado o dia em que eu vou conseguir te eliminar com alegria.");
        System.out.println("Com " + eliminado.getVotos() + " votos, é você quem sai " + eliminado.getNome());
    }

    private static void inicializaParticipantes(ArrayList<Jogador> participantes) {
        String[] nomes = {"Alane Dias", "Beatriz Reis", "Davi Brito", "Deniziane Ferreira", "Fernanda Bande", "Giovanna Lima",
                          "Giovanna Pitel", "Isabelle Nogueira", "Juninho", "Leidy Elin", "Lucas Henrique", "Lucas Luigi",
                          "Lucas Pizane", "Marcus Vinicius", "Matteus Amaral", "Maycon Cosmer", "MC Bin Laden", "Michel Nogueira",
                          "Nizam", "Raquele Cardozo", "Rodriguinho", "Thalyta Alves", "Vanessa Lopes", "Vinicius Rodrigues",
                          "Wanessa Camargo", "Yasmin Brunet"};

        for (String nome : nomes) {
            participantes.add(new Jogador(nome));
        }
    }

    private static Jogador encontraJogador(ArrayList<Jogador> participantes, String nome) {
        for (Jogador jogador : participantes) {
            if (jogador.getNome().equalsIgnoreCase(nome)) {
                return jogador;
            }
        }
        return null;
    }

    private static Jogador apuraVotos(ArrayList<Jogador> participantes) {
        Jogador eliminado = participantes.get(0);

        for (Jogador jogador : participantes) {
            if (jogador.getVotos() > eliminado.getVotos()) {
                eliminado = jogador;
            }
        }

        return eliminado;
    }
}
## Questão dois

}

public class CasaMaisVigiadaGUI {
    public static void main(String[] args) {
        ArrayList<Jogador> participantes = new ArrayList<>();
        inicializaParticipantes(participantes);

        String votoEm;

        JOptionPane.showMessageDialog(null, "Votação para eliminação (clique em 'Cancelar' para encerrar):");

        while (true) {
            votoEm = JOptionPane.showInputDialog(null, "Em quem você vota para sair da casa?");

            if (votoEm == null) {
                break;
            }

            Jogador jogadorVotado = encontraJogador(participantes, votoEm);
            if (jogadorVotado != null) {
                jogadorVotado.incrementaUmVoto();
                JOptionPane.showMessageDialog(null, "Voto computado para " + jogadorVotado.getNome() + ".");
            } else {
                JOptionPane.showMessageDialog(null, "Participante não encontrado. Por favor, insira um nome válido.");
            }
        }

        Jogador eliminado = apuraVotos(participantes);

        JOptionPane.showMessageDialog(null, "Se eu conseguir mover montanhas, se eu conseguir surfar um tsunami, se eu conseguir domar o sol,\n"
                + "se eu conseguir fazer o mar virar sertão, e o sertão virar mar, se eu conseguir dizer o que eu nunca\n"
                + "vou conseguir dizer, aí terá chegado o dia em que eu vou conseguir te eliminar com alegria.\n"
                + "Com " + eliminado.getVotos() + " votos, é você quem sai " + eliminado.getNome());
    }

    private static void inicializaParticipantes(ArrayList<Jogador> participantes) {
        String[] nomes = {"Alane Dias", "Beatriz Reis", "Davi Brito", "Deniziane Ferreira", "Fernanda Bande", "Giovanna Lima",
            "Giovanna Pitel", "Isabelle Nogueira", "Juninho", "Leidy Elin", "Lucas Henrique", "Lucas Luigi",
            "Lucas Pizane", "Marcus Vinicius", "Matteus Amaral", "Maycon Cosmer", "MC Bin Laden", "Michel Nogueira",
            "Nizam", "Raquele Cardozo", "Rodriguinho", "Thalyta Alves", "Vanessa Lopes", "Vinicius Rodrigues",
            "Wanessa Camargo", "Yasmin Brunet"};

        for (String nome : nomes) {
            participantes.add(new Jogador(nome));
        }
    }

    private static Jogador encontraJogador(ArrayList<Jogador> participantes, String nome) {
        for (Jogador jogador : participantes) {
            if (jogador.getNome().equalsIgnoreCase(nome)) {
                return jogador;
            }
        }
        return null;
    }

    private static Jogador apuraVotos(ArrayList<Jogador> participantes) {
        Jogador eliminado = participantes.get(0);

        for (Jogador jogador : participantes) {
            if (jogador.getVotos() > eliminado.getVotos()) {
                eliminado = jogador;
            }
        }

        return eliminado;
    }
}
