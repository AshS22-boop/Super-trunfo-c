#include <stdio.h>

#define MAX_NOME_CIDADE 50

typedef struct {
    char estado;
    char codigo[4];
    char nomeCidade[MAX_NOME_CIDADE];
    unsigned long int populacao;
    float area;
    float pib;
    int pontosTuristicos;
    float densidadePopulacional;
    float pibPerCapita;
    float superPoder;
} Carta;

void lerCarta(Carta *carta) {
    printf("Estado (A-H): ");
    scanf(" %c", &carta->estado);
    printf("Código da Carta (ex: A01): ");
    scanf("%s", carta->codigo);
    printf("Nome da Cidade: ");
    scanf("%49s", carta->nomeCidade);
    printf("População: ");
    scanf("%lu", &carta->populacao);
    printf("Área (km²): ");
    scanf("%f", &carta->area);
    printf("PIB (bilhões de reais): ");
    scanf("%f", &carta->pib);
    printf("Número de Pontos Turísticos: ");
    scanf("%d", &carta->pontosTuristicos);
}

void calcularAtributos(Carta *carta) {
    carta->densidadePopulacional = (float)carta->populacao / carta->area;
    carta->pibPerCapita = carta->pib * 1000000000 / carta->populacao;
    carta->superPoder = (float)carta->populacao + carta->area + carta->pib + carta->pontosTuristicos + carta->pibPerCapita + (1 / carta->densidadePopulacional);
}

void compararCartas(Carta carta1, Carta carta2) {
    printf("Comparação de Cartas:\n");
    printf("População: Carta %d venceu (%d)\n", (carta1.populacao > carta2.populacao) ? 1 : 2, (carta1.populacao > carta2.populacao));
    printf("Área: Carta %d venceu (%d)\n", (carta1.area > carta2.area) ? 1 : 2, (carta1.area > carta2.area));
    printf("PIB: Carta %d venceu (%d)\n", (carta1.pib > carta2.pib) ? 1 : 2, (carta1.pib > carta2.pib));
    printf("Pontos Turísticos: Carta %d venceu (%d)\n", (carta1.pontosTuristicos > carta2.pontosTuristicos) ? 1 : 2, (carta1.pontosTuristicos > carta2.pontosTuristicos));
    printf("Densidade Populacional: Carta %d venceu (%d)\n", (carta1.densidadePopulacional < carta2.densidadePopulacional) ? 1 : 2, (carta1.densidadePopulacional < carta2.densidadePopulacional));
    printf("PIB per Capita: Carta %d venceu (%d)\n", (carta1.pibPerCapita > carta2.pibPerCapita) ? 1 : 2, (carta1.pibPerCapita > carta2.pibPerCapita));
    printf("Super Poder: Carta %d venceu (%d)\n", (carta1.superPoder > carta2.superPoder) ? 1 : 2, (carta1.superPoder > carta2.superPoder));
}

void imprimirCarta(Carta carta, int numeroCarta) {
    printf("Carta %d:\n", numeroCarta);
    printf("Estado: %c\n", carta.estado);
    printf("Código: %s\n", carta.codigo);
    printf("Nome da Cidade: %s\n", carta.nomeCidade);
    printf("População: %lu\n", carta.populacao);
    printf("Área: %.2f km²\n", carta.area);
    printf("PIB: %.2f bilhões de reais\n", carta.pib);
    printf("Número de Pontos Turísticos: %d\n", carta.pontosTuristicos);
    printf("Densidade Populacional: %.2f hab/km²\n", carta.densidadePopulacional);
    printf("PIB per Capita: %.2f reais\n", carta.pibPerCapita);
    printf("Super Poder: %.2f\n", carta.superPoder);
}

int main() {
    Carta carta1, carta2;

    printf("Insira os dados da Carta 1:\n");
    lerCarta(&carta1);
    calcularAtributos(&carta1);
