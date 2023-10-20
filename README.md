#include <stdio.h>

char tabuleiro[3][3];

void inicializarTabuleiro() {
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            tabuleiro[i][j] = ' ';
        }
    }
}

void exibirTabuleiro() {
    printf("\nTabuleiro:\n");
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            printf(" %c ", tabuleiro[i][j]);
            if (j < 2)
                printf("|");
        }
        if (i < 2)
            printf("\n---|---|---\n");
            
}
    printf("\n\n");
}

int verificarVitoria(char jogador) {
    // Implemente a lógica de verificação de vitória aqui
    return 0;  // Temporariamente retornando 0 (nenhum vencedor)
}

int main() {
    char jogadorAtual = 'X';
    int linha, coluna;
    int jogadas = 0;

    inicializarTabuleiro();

    printf("Bem-vindo ao Jogo da Velha!\n\n");

    while (jogadas < 9) {
        exibirTabuleiro();

        printf("Jogador %c, informe a linha (0-2) e a coluna (0-2) para a sua jogada: ", jogadorAtual);
        scanf("%d %d", &linha, &coluna);
        if (linha < 0 || linha > 2 || coluna < 0 || coluna > 2 || tabuleiro[linha][coluna] != ' ') {
            printf("Jogada inválida. Tente novamente.\n");
            continue;
        }

        tabuleiro[linha][coluna] = jogadorAtual;
        jogadas++;

        if (verificarVitoria(jogadorAtual)) {
            exibirTabuleiro();
            printf("Parabéns! O jogador %c venceu!\n", jogadorAtual);
            return 0;
        }

        jogadorAtual = (jogadorAtual == 'X') ? 'O' : 'X';
    }

    exibirTabuleiro();
    printf("Empate! O jogo terminou sem vencedores.\n");

    return 0;
}
