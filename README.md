//# Trabalho
//Trabalho Tannus

#include<stdio.h>
#include<stdlib.h>
#include<locale.h>
#include<string.h>
#include<math.h>
#include<iostream>

typedef struct mode Mode;

struct mode{
	int pid;
	int fila;
	char nome[60];
	Mode *prox;
	
};

Mode *inicioListac;
Mode *finalListac;
Mode *inicioListap;
Mode *finalListap;

void inserir();
void executar();
void imprimirLista();
void Menu();

int main()
{
	setlocale(LC_ALL,"portuguese");
	int escolha = 0;
	
	while (escolha !=4){
		Menu();
		scanf("%d",&escolha);
		system("cls");
		
		switch(escolha)
		{
			case 1:
				inserir();
			break;
			
			case 2:
				executar();
			break;
			
			case 3:
				imprimirLista();
			break;
			
			case 4:
				system("cls");
				printf("Obrigado!");
							
		}
		if(escolha > 4 && escolha<1){
			printf("\nOpção inválida");
		}
	}
}

void inserir(){
	int filains;
	Mode *novop;
	Mode *novoc;
	
	printf("insira a fila \n1-Presencial \n2-Comum\n");
	scanf("%i",&filains);
	
	if(filains ==1){
		novop = (Mode*)malloc(sizeof(Mode));
	
		printf("\nInsira o nome:\n");
		scanf("%s",&novop->nome);
	
		printf("\nInsira o ID:\n");
		scanf("%i",&novop->pid);
	
		novop->fila = filains;
	
		if(inicioListap == NULL && finalListap ==NULL){
		
			inicioListap = novop;
			finalListap = novop;
			finalListap ->prox = NULL;
		}
		else{
			
			if(inicioListap == finalListap){
				finalListap = novop;
				inicioListap->prox = finalListap;
				finalListap->prox = NULL;
			}
			
			else{
				finalListap -> prox = novop;
				finalListap = novop;
				finalListap ->prox = NULL;
				
			}
		}
}

 
	if(filains ==2)
	{
		novoc = (Mode*)malloc(sizeof(Mode));
		
		printf("\nInserção");
		
		printf("\nInsira o nome:");
		scanf("%s", &novoc->nome);
		
		printf("\nInsira o ID:");
		scanf("%i",&novoc->pid);
		
		novoc->fila = filains;
		
			if(inicioListac == NULL && finalListac == NULL){
				inicioListac = novoc;
				finalListac = novoc;
				finalListac->prox = NULL;
			}
			
			else{
				
				if(inicioListac == finalListac){
					finalListac = novoc;
					inicioListac -> prox = NULL;
				
				}
				
				else{
					finalListac -> prox = novoc;
					finalListac = novoc;
					finalListac -> prox = NULL;
				
			}
		}
	}
}

void executar(){
	Mode *aux;
	if(inicioListap != NULL && finalListap != NULL){
		if(inicioListap == finalListap){
			aux - inicioListap;
			inicioListap = NULL;
			finalListap = NULL;
			free(aux);
			
		}
		else{
			aux = inicioListap;
			inicioListap = inicioListap->prox;
			free(aux);
			
		}
	}
	
	else if(inicioListac != NULL && finalListac != NULL){
		if(inicioListac == finalListac){
			aux = inicioListac;
			inicioListac = NULL;
			finalListac = NULL;
			free(aux);
		
		}
		else{
			aux=inicioListac;
			inicioListac = inicioListac->prox;
			free(aux);
		}
				
	}
	else if (inicioListap == NULL && inicioListac == NULL){
		printf("\nListas Vazias");
		
	}
}

void imprimirLista(){
	Mode *auxInserir;
	
	printf("\n Lista Preferencial");
	if(inicioListap != NULL){
		auxInserir = inicioListap;
		while (auxInserir != NULL){
			printf("\n PID: &d | processo %s\n", auxInserir ->pid, auxInserir ->nome);
			auxInserir = auxInserir ->prox;
		}
		
	}
	else
		 printf("Lista Vazia");
	
}
 void Menu(){
 	printf("\n ***Menu de gerenciamento***");
 	printf("\n1-Inserir");
 	printf("\n2-Executar");
 	printf("\n3-Imprimir Fila");
 	printf("\n4-Sair");
 	printf("\nEscolha:");
 	
 	
 }

