# YILAN-OYUNU-BASLANGIC-KISMI
#include <stdio.h>
#include <stdlib.h>


#define PLAYER_NUM 2


      struct oyuncu
	  {
      	char Ad[50];
      	int id;
	  };

    int satir=10,sutun=20;
    char alan[20][40];
	int score=0;
	 
    void degerler_isteme(struct oyuncu *oy_1);
    void duvar(char dizi[20][40]);
    void ciz(char dizi[20][40]);

    int main() {
    	
    	FILE *pgiris,*prekor;
    	pgiris= fopen("yilan.txt","w");
    	
    	
    	struct oyuncu player[PLAYER_NUM];
    	int i;
    	 	
    	for(i=0;i<PLAYER_NUM;i++)
    	{
    		degerler_isteme(&player[i]);
		}
        
        fprintf(pgiris,"************** YILAN OYUNU **************\n\n");
    	fprintf(pgiris,"\t    Id \t\t  AD\n");
    	fprintf(pgiris,"\t ---------\t-------- \n");
    	
    	for(i=0;i<PLAYER_NUM;i++)
    	{
    	fprintf(pgiris,"Oyuncu %d: [%d]         [%s] \n",i+1,player[i].id,player[i].Ad);	
		}
		
		fclose(pgiris);
		
		duvar(alan);
		ciz(alan);
		
		getch();	
	return 0;
}

  void degerler_isteme(struct oyuncu *oy_1)
  {
  	printf("Lutfen id'nizi girin:  ");
  	scanf("%d",&(oy_1->id));
  	
  	printf("Lutfen adinizi girin:  ");
  	scanf(" %s",&(oy_1->Ad));
  	
  	printf("\n\n");
  }
  
  void duvar(char dizi[20][40])
  { 
       int i,j; 
       for(i=0;i<20;i++){ 
          if(i==0||i==19){ 
              for(j=0;j<40;j++){ 
                  dizi[i][j]='='; 
              } 
          } 
          else{ 
               dizi[i][0]='|'; 
               for(j=1;j<39;j++){ 
                   dizi[i][j]=' '; 
               } 
               dizi[i][39]='|'; 
          } 
           
       } 
       alan[satir][sutun]='#'; 
  }
   
  void ciz(char dizi[20][40])
  { 
       system("CLS"); 
       printf("Score: %d\n",score); 
       int i,j; 
       
       for(i=0;i<20;i++)
	   { 
          for(j=0;j<40;j++)
		  { 
              printf("%c",dizi[i][j]); 
          } 
          printf("\n"); 
       }       
  }
