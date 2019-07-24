#include <stdio.h>
#include <stdbool.h>
#include<string.h>

#define MATRIX_SIZE 4
int printWords(char Matrix1[MATRIX_SIZE][MATRIX_SIZE]){//this function print all the possible words in the matrix.
char xadd[18];
int Matrix[MATRIX_SIZE][MATRIX_SIZE];
int countwords=0;
for(int i=0;i<=3;i++){
    for (int j=0;j<=3;j++){
    int ezer=0;
    while (xadd[ezer]!= '\0') {
        xadd[ezer]='\0';
         ezer=ezer+1;
}
    countwords+=recursivestringsnake(xadd,0,Matrix1,Matrix,i,j);
        for(int k=0;k<MATRIX_SIZE;k++){
    for (int p=0;p<MATRIX_SIZE;p++){
    Matrix[k][p]=0;}
            
        }
    }
}
return countwords;
}

void duplicatearray(int array[MATRIX_SIZE][MATRIX_SIZE],int copyarray[MATRIX_SIZE][MATRIX_SIZE]){//this function copy array to other array
    for(int i=0;i<MATRIX_SIZE;i++){
    for (int j=0;j<MATRIX_SIZE;j++){
    array[i][j]=copyarray[i][j];
}
}
}

bool isWord(char* s){//this function sends all the correct words that we need to find in the matrix
      return (!strcmp(s,"CAT") |
   !strcmp(s,"CATS") |
   !strcmp(s,"TRAM") |
   !strcmp(s,"TRAMS") |
   !strcmp(s,"TAME") |
   !strcmp(s,"CAR") |
   !strcmp(s,"CARS") |
   !strcmp(s,"RAT") |
   !strcmp(s,"RATS") |
   !strcmp(s,"RAMP") |
   !strcmp(s,"ART") |
   !strcmp(s,"CART") |
   !strcmp(s,"STAMP") |
      !strcmp(s,"TAKEN") |
   !strcmp(s,"MEN") |
   !strcmp(s,"MAKE") |
   !strcmp(s,"TAKE") |
   !strcmp(s,"ATE") |
   !strcmp(s,"SELL") |
   !strcmp(s,"STEEL") |
   !strcmp(s,"ME") |
   !strcmp(s,"TRACE") |
   !strcmp(s,"RAKE") );
}

int recursivestringsnake(char xadd[18],int countwords,char Matrix1[MATRIX_SIZE][MATRIX_SIZE],int Matrix[MATRIX_SIZE][MATRIX_SIZE],int Xaxis,int Yaxis){//this function use in recursion to find the words that we got from the function "isWord"

if(Xaxis<0||Yaxis<0||Xaxis>=MATRIX_SIZE||Yaxis>=MATRIX_SIZE||Matrix[Xaxis][Yaxis]==1){//gg
    return countwords;
}
xadd[strlen(xadd)]=Matrix1[Xaxis][Yaxis];
Matrix[Xaxis][Yaxis]=1;
if(isWord(xadd)==1){
    countwords++;
    printf("%s\n",xadd);
}
char xadd1[16];
char xadd2[16];
char xadd3[16];
char xadd4[16];
int fill[MATRIX_SIZE][MATRIX_SIZE],fill2[MATRIX_SIZE][MATRIX_SIZE],fill3[MATRIX_SIZE][MATRIX_SIZE],fill4[MATRIX_SIZE][MATRIX_SIZE];
duplicatearray(fill,Matrix),duplicatearray(fill2,Matrix),duplicatearray(fill3,Matrix),duplicatearray(fill4,Matrix);
strncpy(xadd1,xadd,16),strncpy(xadd2,xadd,16),strncpy(xadd3,xadd,16),strncpy(xadd4,xadd,16);
int ans1=recursivestringsnake(xadd4,0,Matrix1,fill,Xaxis,Yaxis-1), ans2=recursivestringsnake(xadd2,0,Matrix1,fill4,Xaxis-1,Yaxis),ans3=recursivestringsnake(xadd1,0,Matrix1,fill3,Xaxis+1,Yaxis), ans4=recursivestringsnake(xadd3,0,Matrix1,fill2,Xaxis,Yaxis+1);
return countwords +ans1+ans2+ans3+ans4;
}
int main(){
    char Matrix1[MATRIX_SIZE][MATRIX_SIZE]=
{{'C','A','R','T'},
{'E','T','A','K'},
{'E','S','M','E'},
{'L','L','P','N'}};

    printf("the number of words in the program is: %d words \n",printWords(Matrix1));
}