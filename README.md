# arq.c
Implemente um programa que grave o nome completo de 5 pessoas em um arquivo binário. Implemente um procedimento para exibir todos os nomes gravados no arquivo.

     #include<stdio.h>
     #include<stdlib.h>
     #include<string.h>


    typedef struct pessoa{
        char nome[30];
    }pessoa;

    int main(){
        FILE *arq1;
        pessoa p[5];
        for(int i=0;i<5;i++){
            printf("Digite um nome completo: ");
            gets(p[i].nome);
        }
        arq1 = fopen("nomesbinario","w");
        if(arq1 == NULL){
          printf("Erro ao abrir o arquivo.");
        }
        for(int i=0;i<5;i++){
           fwrite(&p[i],sizeof(pessoa),1,arq1);
        }
        fclose(arq1);

         //leitura:

         FILE *arq2;
         arq2 = fopen("nomesbinario","w");
         for(int i=0;i<5;i++){ 
            fread(&p,sizeof(pessoa),1,arq2);
            printf("%i)%s\n",i+1,p[i].nome);
         }
         fclose(arq2);
     }
      








