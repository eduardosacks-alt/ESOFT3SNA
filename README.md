# ESOFT3SNA
Nome: eduardo bersch sacks

Atv1
#include <stdio.h>

int main() {
    char p1[50], p2[50], p3[50];
    printf("Digite três palavras: ");
    scanf("%s %s %s", p1, p2, p3);
    printf("Inverso: %s %s %s\n", p3, p2, p1);
    return 0;
}

atv2
 #include <stdio.h>

int main() {
    int v[5];
    for(int i = 0; i < 5; i++) scanf("%d", &v[i]);
    for(int i = 4; i >= 0; i--) printf("%d ", v[i]);
    return 0;
}

at3
 #include <stdio.h>

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

atv4
 #include <stdio.h>

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

atv5
  #include <stdio.h>

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

 atv6
 #include <stdio.h>

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

 atv7
 #include <stdio.h>
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

atv8
#include <stdio.h>

int main() {
    int v[5];
    for(int i = 0; i < 5; i++) scanf("%d", (v + i));
    for(int i = 0; i < 5; i++) printf("%d ", *(v + i) * 2);
    return 0;
}

 atv9
 #include <stdio.h>

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


at10
#include <stdio.h>
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

    
ATIVIDADE2
desafio1
    
#include <stdio.h>
#include <stdlib.h>


typedef struct No {
    char dado;
    struct No *proximo;
} No;


void push(No **topo, char valor) {
    No *novo = (No*) malloc(sizeof(No));
    if (novo) {
        novo->dado = valor;
        novo->proximo = *topo;
        *topo = novo;
    }
}

char pop(No **topo) {
    if (*topo == NULL) return '\0';
    No *temp = *topo;
    char valor = temp->dado;
    *topo = temp->proximo;
    free(temp);
    return valor;
}

int isEmpty(No *topo) {
    return topo == NULL;
}

int correspondente(char abrindo, char fechando) {
    if (abrindo == '(' && fechando == ')') return 1;
    if (abrindo == '[' && fechando == ']') return 1;
    if (abrindo == '{' && fechando == '}') return 1;
    return 0;
}

int main() {
    char expressao[100];
    No *pilha = NULL;
    int valida = 1;

printf("Digite a expressão: ");
    scanf("%s", expressao);

char *p = expressao;
    while (*p != '\0') {
        if (*p == '(' || *p == '[' || *p == '{') {
            push(&pilha, *p);
        } else if (*p == ')' || *p == ']' || *p == '}') {
            if (isEmpty(pilha) || !correspondente(pop(&pilha), *p)) {
                valida = 0;
                break;
            }
        }
        p++;
    }

if (valida && isEmpty(pilha)) {
        printf("Expressão Válida!\n");
    } else {
        printf("Expressão Inválida!\n");
        
while (!isEmpty(pilha)) pop(&pilha);
    }

    return 0;
}
    free(turma);
    return 0;
}


desafio2:


#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    char caracter;
    struct No *prox;
} No;

void push(No **topo, char c) {
    No *novo = (No*) malloc(sizeof(No));
    if (novo) {
        novo->caracter = c;
        novo->prox = *topo;
        *topo = novo;
    }
}

char pop(No **topo) {
    if (*topo == NULL) return '\0';
    No *aux = *topo;
    char c = aux->caracter;
    *topo = aux->prox;
    free(aux);
    return c;
}

int main() {
    char str[100];
    No *pilha = NULL;

printf("Digite uma string: ");
    scanf(" %[^\n]", str); // Lê inclusive espaços

     1. Inserir cada caractere na pilha
char *ptr = str;
    while (*ptr != '\0') {
        push(&pilha, *ptr);
        ptr++;
    }

    
ptr = str;
    while (pilha != NULL) {
        *ptr = pop(&pilha);
        ptr++;
    }
    

    printf("String invertida: %s\n", str);

return 0;
}



ATIVIDADE3
desafio1

#include <stdio.h>
#include <stdlib.h>

typedef struct Cliente {
    int id;
    int tempoAtendimento;
    struct Cliente *proximo;
} Cliente;

typedef struct {
    Cliente *frente;
    Cliente *tras;
} Fila;

void enfileirar(Fila *f, int id, int tempo) {
    Cliente *novo = (Cliente*) malloc(sizeof(Cliente));
    novo->id = id;
    novo->tempoAtendimento = tempo;
    novo->proximo = NULL;

if (f->tras == NULL) {
        f->frente = f->tras = novo;
    } else {
        f->tras->proximo = novo;
        f->tras = novo;
    }
}

void atender(Fila *f) {
    int tempoEsperaTotal = 0;
    Cliente *atual = f->frente;

printf("\n--- Relatório de Atendimento ---\n");
    while (atual != NULL) {
        printf("Cliente ID: %d | Espera: %d min | Atendimento: %d min\n", 
                atual->id, tempoEsperaTotal, atual->tempoAtendimento);
        
        tempoEsperaTotal += atual->tempoAtendimento;
        
        
 Cliente *temp = atual;
        atual = atual->proximo;
        free(temp);
    }
f->frente = f->tras = NULL;
}

int main() {
    Fila filaAtendimento = {NULL, NULL};
    int n, t;

printf("Quantos clientes serão atendidos? ");
    scanf("%d", &n);

for (int i = 1; i <= n; i++) {
        printf("Tempo de atendimento do cliente %d: ", i);
        scanf("%d", &t);
        enfileirar(&filaAtendimento, i, t);
    }

atender(&filaAtendimento);
    return 0;
}


desafio2:

#include <stdio.h>
#include <stdlib.h>

typedef struct Documento {
    int id;
    int paginas;
    int prioridade;
    struct Documento *proximo;
} Documento;


void inserirComPrioridade(Documento **frente, int id, int pag, int prio) {
    Documento *novo = (Documento*) malloc(sizeof(Documento));
    novo->id = id;
    novo->paginas = pag;
    novo->prioridade = prio;
    novo->proximo = NULL;

    
if (*frente == NULL || prio < (*frente)->prioridade) {
        novo->proximo = *frente;
        *frente = novo;
    } 
else {

Documento *atual = *frente;
        while (atual->proximo != NULL && atual->proximo->prioridade <= prio) {
            atual = atual->proximo;
        }
        novo->proximo = atual->proximo;
        atual->proximo = novo;
    }
}

void imprimirFila(Documento **frente) {
    printf("\n--- Ordem de Impressão ---\n");
    while (*frente != NULL) {
        Documento *temp = *frente;
        printf("[Prioridade: %d] Doc ID: %d | Páginas: %d\n", 
                temp->prioridade, temp->id, temp->paginas);
        
*frente = (*frente)->proximo;
        free(temp);
    }
}

int main() {
    Documento *filaImpressao = NULL;
    int n, id, pag, prio;

printf("Quantidade de documentos para impressão: ");
    scanf("%d", &n);

for (int i = 0; i < n; i++) {
        printf("\nDoc %d - ID, Páginas e Prioridade (ex: 101 5 1): ", i + 1);
        scanf("%d %d %d", &id, &pag, &prio);
        inserirComPrioridade(&filaImpressao, id, pag, prio);
    }

imprimirFila(&filaImpressao);
    return 0;
}

