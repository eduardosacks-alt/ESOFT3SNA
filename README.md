# ESOFT3SNA
Nome: eduardo bersch sacks

ativ1: #include <stdio.h>

int main() {
    char p1[50], p2[50], p3[50];
    printf("Digite três palavras: ");
    scanf("%s %s %s", p1, p2, p3);
    printf("Inverso: %s %s %s\n", p3, p2, p1);
    return 0;
}

ativ2:  #include <stdio.h>

int main() {
    int v[5];
    for(int i = 0; i < 5; i++) scanf("%d", &v[i]);
    for(int i = 4; i >= 0; i--) printf("%d ", v[i]);
    return 0;
}

ativ3:  #include <stdio.h>

int main() {
    int m[3][3];
    for(int i = 0; i < 3; i++)
        for(int j = 0; j < 3; j++) {
            scanf("%d", &m[i][j]);
            m[i][j] *= 5;
        }
    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) printf("%d ", m[i][j]);
        printf("\n");
    }
    return 0;
}


ativ4:  #include <stdio.h>

int main() {
    int A[3][3], I[3][3] = {0}, R[3][3] = {0};
    // Criar Identidade e ler A
    for(int i = 0; i < 3; i++) {
        I[i][i] = 1;
        for(int j = 0; j < 3; j++) scanf("%d", &A[i][j]);
    }
    // Multiplicação A * I
    for(int i = 0; i < 3; i++)
        for(int j = 0; j < 3; j++)
            for(int k = 0; k < 3; k++)
                R[i][j] += A[i][k] * I[k][j];
                
    printf("Resultado da multiplicacao (deve ser igual a original):\n");
    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) printf("%d ", R[i][j]);
        printf("\n");
    }
    return 0;
}

ativ5:  #include <stdio.h>

int main() {
    int v[3], m[3][3], res[3] = {0};
    for(int i = 0; i < 3; i++) scanf("%d", &v[i]);
    for(int i = 0; i < 3; i++)
        for(int j = 0; j < 3; j++) scanf("%d", &m[i][j]);

    for(int j = 0; j < 3; j++) // Colunas
        for(int i = 0; i < 3; i++) // Linhas
            res[j] += v[i] * m[i][j];

    for(int i = 0; i < 3; i++) printf("Res[%d]: %d\n", i, res[i]);
    return 0;
}

ativ6:  #include <stdio.h>

typedef struct {
    char nome[50];
    int matricula;
    float media;
} Aluno;

int main() {
    Aluno todos[10], aprovados[10], reprovados[10];
    int ca = 0, cr = 0;

    for(int i = 0; i < 10; i++) {
        scanf("%s %d %f", todos[i].nome, &todos[i].matricula, &todos[i].media);
        if(todos[i].media >= 5.0) aprovados[ca++] = todos[i];
        else reprovados[cr++] = todos[i];
    }

    printf("\nAprovados:\n");
    for(int i = 0; i < ca; i++) printf("%s\n", aprovados[i].nome);
    printf("\nReprovados:\n");
    for(int i = 0; i < cr; i++) printf("%s\n", reprovados[i].nome);
    return 0;
}

ativ7:  #include <stdio.h>
#include <string.h>

typedef struct {
    char titulo[31], autor[16];
    int ano;
} Livro;

int main() {
    Livro livros[5];
    char busca[31];
    for(int i = 0; i < 5; i++) 
        scanf(" %30[^\n] %15[^\n] %d", livros[i].titulo, livros[i].autor, &livros[i].ano);

    printf("Buscar titulo: ");
    scanf(" %30[^\n]", busca);

    for(int i = 0; i < 5; i++) {
        if(strcmp(livros[i].titulo, busca) == 0)
            printf("Achado: %s, Autor: %s, Ano: %d\n", livros[i].titulo, livros[i].autor, livros[i].ano);
    }
    return 0;
}

ativ8:  #include <stdio.h>

int main() {
    int v[5];
    for(int i = 0; i < 5; i++) scanf("%d", (v + i));
    for(int i = 0; i < 5; i++) printf("%d ", *(v + i) * 2);
    return 0;
}

ativ9:  #include <stdio.h>

int ordena(int *a, int *b, int *c) {
    int temp;
    if (*a > *b) { temp = *a; *a = *b; *b = temp; }
    if (*a > *c) { temp = *a; *a = *c; *c = temp; }
    if (*b > *c) { temp = *b; *b = *c; *c = temp; }
    return (*a == *b && *b == *c);
}

int main() {
    int x, y, z;
    scanf("%d %d %d", &x, &y, &z);
    ordena(&x, &y, &z);
    printf("%d %d %d\n", x, y, z);
    return 0;
}

ativ10: #include <stdio.h>
#include <stdlib.h>

typedef struct {
    char nome[50];
    float nota;
} Aluno;

Aluno* maiorNota(Aluno *ptr, int n) {
    Aluno *maior = ptr;
    for(int i = 1; i < n; i++) {
        if((ptr + i)->nota > maior->nota) maior = (ptr + i);
    }
    return maior;
}

int main() {
    int n;
    printf("Quantidade de alunos: ");
    scanf("%d", &n);

    Aluno *turma = (Aluno*) malloc(n * sizeof(Aluno));

    for(int i = 0; i < n; i++) {
        scanf("%s %f", (turma + i)->nome, &(turma + i)->nota);
    }

    Aluno *melhor = maiorNota(turma, n);
    printf("Melhor aluno: %s com nota %.2f\n", melhor->nome, melhor->nota);

    free(turma);
    return 0;
}

