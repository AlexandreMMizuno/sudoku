#include <stdio.h>
#include <stdlib.h>

typedef struct Matriz
{
    int linha;
    int coluna;
    int **matriz;
}VetorBi;

VetorBi *matriz(int linha, int coluna ){
    
   int j=0;
    
   VetorBi *matriz = malloc( sizeof(VetorBi));

   matriz->linha = linha;
   matriz->coluna = coluna;
        
   matriz->matriz = malloc( sizeof(int) * matriz->coluna );
             
   for ( j = 0; j < matriz->linha; j++ )
   {    
      matriz->matriz[j] = malloc( sizeof(int) * matriz->linha );              
   }
   
   return matriz;
}

void desalocar(VetorBi *matriz){
     int c, x;
     
     for(x=0; x<matriz->coluna; x++ )
         free(matriz->matriz[x]);
     
     free(matriz->matriz);
     free(matriz);
     
}

void embaralharNumeros(int *vetor){
     
     int k;
     
     for (k = 0; k < 9; k++)
     {
          size_t num = k + rand() / (RAND_MAX / (9 - k) + 1);
          int t = vetor[num];
          vetor[num] = vetor[k];
          vetor[k] = t+1;
     }     
}

void iniciarMatriz(VetorBi *matriz, int *vetor){

     int i,j;
     
     for ( i = 0; i < 9; i++ )
     {                   
       for ( j = 0; j < 9; j++ )
       {                                  
          matriz->matriz[i][j] = 0;        
       }            
     }
     
     for (i = 0; i < 9; i++)
     {
        vetor[i] = i;  
     }   
}

int verificaLinha(VetorBi *matriz, int iFinal, int jFinal, int addNum){
     int i,j, resp=1;
                     
       for ( j = 0; j < jFinal; j++ )
       {                                  
          if(addNum == matriz->matriz[iFinal][j]){
             resp = 1; 
             break;
          } 
          
          else resp = 0;     
       } 
     
     return resp;           
}

int verificaColuna(VetorBi *matriz, int jFinal, int addNum){
     int j, resp=1;
                     
       for ( j = 0; j < jFinal; j++ )
       {                                  
          if(addNum == matriz->matriz[j][jFinal]){
             resp = 1; 
             break;
          } 
          
          else resp = 0;     
       }
     
     return resp;           
}

int verificatresPorTres(VetorBi *matriz, int iInicial, int jInicial, int iFinal, int jFinal, int addNum){
     int i,j, resp=0;
      
      if(jFinal > jInicial)
      {
       for ( i = iInicial; i <= iFinal; i++ )
       {              
           for ( j = jInicial; j <= jFinal; j++ )
           {                              
              if(addNum == matriz->matriz[i][j]){
                 resp = 1; 
                 break;
              } 
              
              else if(addNum != matriz->matriz[i][j] && (jInicial+1) == jFinal) resp = 0;  
           }
       }
     }
     return resp;           
}

int trocarValor(VetorBi *matriz, int iInicial, int jInicial, int iFinal, int jFinal){
    int verifLinha=0, verifColuna=0, verifRegiao=0, aux, terminou=0,i,j;
    
     for ( i = iInicial; i <= iFinal; i++ )
       {                   
          for ( j = jInicial; j <= jFinal; j++ )
          {
            
            aux = matriz->matriz[i][j];
            matriz->matriz[i][j] = matriz->matriz[iFinal][jFinal];
            matriz->matriz[iFinal][jFinal] = aux;
                          
            if(j>2)verifLinha = verificaLinha(matriz, i, j, matriz->matriz[iFinal][jFinal]);
            if(j>0)verifColuna = verificaColuna(matriz, j, matriz->matriz[iFinal][jFinal]);
            else verifColuna = verificaColuna(matriz, i, matriz->matriz[iFinal][jFinal]);
            verifRegiao = verificatresPorTres(matriz, iInicial, jInicial, i, jFinal, matriz->matriz[iFinal][jFinal]);
                   
            if(verifLinha == 0 && verifColuna == 0 && verifRegiao == 0 ){
               terminou = 1;
               break;
            }
                                
            else{
               aux = matriz->matriz[iFinal][jFinal];
               matriz->matriz[iFinal][jFinal] = matriz->matriz[i][j];
               matriz->matriz[i][j] = aux; 
               terminou = 0;  
            }                      
          }
          verifLinha=0;
          verifColuna=0;
          verifRegiao=0;
       }
       
       return terminou;
}

void atribuirValores(VetorBi *matriz){
   int i,j, iInicial, iFinal, jInicial, jFinal, num, cont=0, addNum=1, terminou =0,acabou=0, aux;
   int verifLinha=0, verifColuna=0, verifRegiao=0; 
   
   iInicial = 0;
   iFinal = 2;
   jInicial = 0;
   jFinal = 2; 
   int vetor[9];   
    
   srand( time(NULL) );
   
   iniciarMatriz(matriz, vetor);      
   embaralharNumeros(vetor);      
       
   do 
   {
       for ( i = iInicial; i <= iFinal; i++ )
       {                   
              for ( j = jInicial; j <= jFinal; j++ )
              {
                  if(iFinal <=2 && jFinal <= 2){                                 
                      matriz->matriz[i][j] = vetor[cont];  
                      cont++;
                  }                 
                  else{
                       
                       terminou = 0;  
                       do{
                           if(j>2)verifLinha = verificaLinha(matriz, i, j, addNum);
                           if(j>0)verifColuna = verificaColuna(matriz, j, addNum);
                           else verifColuna = verificaColuna(matriz, i, addNum);
                           
                           verifRegiao = verificatresPorTres(matriz, iInicial, jInicial, i, jFinal, addNum);
                           
                           if(verifLinha == 0 && verifColuna == 0 && verifRegiao == 0){
                             matriz->matriz[i][j] = addNum;
                             terminou = 1;
                           }

                         /* if(i == iFinal && j == jFinal && terminou ==0 && addNum !=0){
                              matriz->matriz[i][j] = addNum;
                              do{                                 
                                   acabou = trocarValor(matriz, iInicial, jInicial, iFinal, jFinal);                                                                        
                              }while(acabou != 1);
                          }*/
                          addNum++;
                         
                       }while(terminou != 1);
                       addNum = 1; 
                  }
                  verifLinha=0;
                  verifColuna=0;
                  verifRegiao=0; 
                  
              }                
       }
       
       cont = 0;
       embaralharNumeros(vetor);
       jInicial = jFinal + 1;
       jFinal = jFinal + 3;
       
       if(jFinal > 8){
          iInicial = iFinal + 1;
          iFinal = iFinal + 3; 
          jInicial = 0;
          jFinal = 2;         
       }

   }while(iFinal <9);
}

void imprimirMatriz(VetorBi *matriz){
   int i,j, iInicial, iFinal, jInicial, jFinal; 
   
   iInicial = 0;
   iFinal = 2;
   jInicial = 0;
   jFinal = 2;
   
   do 
   {
       for ( i = iInicial; i <= iFinal; i++ )
       {                   
              for ( j = jInicial; j <= jFinal; j++ )
              {   
              printf("[%d,%d]=%d ",i,j,matriz->matriz[i][j]);            
              }
              printf("\n");
       }
       printf("\n");
       printf("\n");
       jInicial = jFinal + 1;
       jFinal = jFinal + 3;
       
       if(jFinal > 8){
          iInicial = iFinal + 1;
          iFinal = iFinal + 3;  
          jInicial = 0;
          jFinal = 2;        
       }

   }while(iFinal <9);
}

int main(){
    VetorBi *m= matriz(9,9); 
    
    int i,j; 
    
    atribuirValores(m);
    
    printf("Sudoku\n\n");
    imprimirMatriz(m);

    desalocar(m); 
    system("pause");
    return 0; 
}
