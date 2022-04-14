#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define SIZE 200
struct venda {
  int cod_locacao;
  int data_inicial, data_entrega;
  float valor_aluguel;
  int placa;
  int modelo;
  int ano;
  char nome_carro[100];
};

struct cadastro {
  char nome_cliente[100];
  char endereco[50];
  int numero, telefone;
  char bairro[50];
  char cidade[50];
  char estado[50];
};
int op;
void locacao();

void venda();
void pesquisa();
void lista();

int main(void) {

  do {
    system("clear");
    printf("\n\n*************SISTEMA DE LOCAÇÃO***********\n\n");
    printf("\n--------------MENU--------------\n 1. Para Cadastro \n 2. Para Realizar venda\n 3. Para Listar "
           "todos os cadastros\n 4. Para Pesquisar\nDigite a opção Desejada\n");
    scanf("%d",&op);
    switch(op){
      case 1:
      locacao();
      break;
      case 2:
        venda();
      break;
      case 3:
        lista();
      break;
      case 4:
        pesquisa();
      break;
      case 5:
        system("exit");
      break;
      
      default:
      printf(" Opção invalida\n");
      break;
    }

  } while (op!=5);
  return 0;
}
void lista() {
  struct cadastro a[SIZE];
  struct venda b[SIZE];
  int i;
  for (i = 0; i < SIZE; i++) {
    if (b[i].cod_locacao > 0) {
      printf("nome... %s\n Endereço... %s \n Bairro.... %s \n Estado... %s \n "
             "Telefone... %d\n  Data Inicial ... %d \n Data entrega ... %d \n "
             "Valor... %f  \n Codigo de Locação ... %d",
             a[i].nome_cliente, a[i].endereco, a[i].bairro, a[i].estado,
             a[i].telefone, b[i].data_inicial, b[i].data_entrega,
             b[i].valor_aluguel, b[i].cod_locacao);
    } else {
      break;
    }
  }
}
void locacao() {
  struct cadastro a[SIZE];
  static int linha;
  do {

    printf("\nDigite o nome do Cliente\n");
    scanf("%s", a[linha].nome_cliente);
    printf("\nDigite o Endereço \n");
    scanf("%s", a[linha].endereco);
    fflush(stdin);
    printf("\nCidade... \n");
    scanf("%s", a[linha].cidade);
    printf("\nDigite o Estado...\n");
    scanf("%s", a[linha].estado);
    printf("\nDigite o Bairro.. \n");
    scanf("%s", a[linha].bairro);
    printf("\nDigite numero do Telefone \n");
    scanf("%d", &a[linha].telefone);
    printf("\n Digite 1 para continuar ou qualquer valor para sair\n");
    scanf("%d", &op);
    fflush(stdin);
    linha++;
  } while (op == 1);
};
void venda() {
  static int cont;
  struct venda b[SIZE];
  do {

    printf("\nDigite o Codigo da Locação \n");
    scanf("%d", &b[cont].cod_locacao);
    printf("\n Digite Data inicial dia mes e ano \n");
    scanf("%d", &b[cont].data_inicial);
    printf("\n Digite a Data de entrega dia mês e ano\n");
    scanf("%d", &b[cont].data_entrega);
    printf("\nValor:  ");
    scanf("%f", &b[cont].valor_aluguel);
    printf("Digite 1 para nova venda ou Qualquer Tecla pra Sair");
    scanf("%d", &op);
    cont++;
  } while (op == 1);
};
void pesquisa() {

  do {
    printf("\nDigite 1 para Consulta com codigo de locação\n Digite 2 para "
           "Consulta pela placa\n Digite 3 para consulta Pelo Nome\n");
    scanf("%d", &op);
    switch (op) {
      struct venda b[SIZE];
      struct cadastro a[SIZE];
      int i;
      int codigopesquisa;
      int pesq_placa;
      char pesq_nome[80];
    case 1:
      printf("\nDigite o codigo de locação..");
      scanf("%d", &codigopesquisa);
      for (i = 0; i < SIZE; i++) {
        if (b[i].cod_locacao == codigopesquisa) {
          printf("nome... %s\n Endereço... %s \n Bairro.... %s \n Estado... %s "
                 "\n Telefone... %d\n  Data Inicial ... %d \n Data entrega ... "
                 "%d \n Valor... %f  ",
                 a[i].nome_cliente, a[i].endereco, a[i].bairro, a[i].estado,
                 a[i].telefone, b[i].data_inicial, b[i].data_entrega,
                 b[i].valor_aluguel);
        }
      }
      break;
    case 2:
      printf("\nDigite a Placa... ");
      scanf("%d", &pesq_placa);
      for (i = 0; i < SIZE; i++) {
        if (b[i].placa == pesq_placa) {
          printf("nome... %s\n Endereço... %s \n Bairro.... %s \n Estado... %s "
                 "\n Telefone... %d\n  Data Inicial ... %d \n Data entrega ... "
                 "%d \n Valor... %f  ",
                 a[i].nome_cliente, a[i].endereco, a[i].bairro, a[i].estado,
                 a[i].telefone, b[i].data_inicial, b[i].data_entrega,
                 b[i].valor_aluguel);
        }
      }
      break;
    case 3:
      printf("\nDigite o nome... ");
      fgets(pesq_nome, 80, stdin);
      for (i = 0; i < SIZE; i++) {
        if (strcmp(a[i].nome_cliente, pesq_nome) == 0) {
          printf("nome... %s\n Endereço... %s \n Bairro.... %s \n Estado... %s "
                 "\n Telefone... %d\n  Data Inicial ... %d \n Data entrega ... "
                 "%d \n Valor... %f  ",
                 a[i].nome_cliente, a[i].endereco, a[i].bairro, a[i].estado,
                 a[i].telefone, b[i].data_inicial, b[i].data_entrega,
                 b[i].valor_aluguel);
        }
      }
      break;
    default:
      printf("\nOpção invalida");
    }
    printf("\nDigite 1 para continuar \n");
    scanf("%d", &op);
  } while (op == 1);
}
