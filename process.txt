#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <stdlib.h>

int main()
{
    int sayi = 0;
    int pid,status;
 
    printf("Bir sayı girin \n");
    scanf("%d", &sayi);
 
       if(sayi < 0)
    {
          printf("Lutfen pozitif bir sayı girin \n");
      scanf("%d", &sayi);
    }
 
    pid = fork();
 
  
 
     if(pid == 0)  //Child process
    {
             do
        {
        if(sayi%2 != 0)
        {
          sayi = (sayi*3)+1;
                }
         
        else if(sayi%2 == 0)
        {
          sayi = sayi/2;
        }
 
        printf("%d \n",sayi); // önce child process lar yazdırılıyor
        }while(sayi != 1);
    }
 
    else  //Parentprocess
    {
 
        printf("pid %d \n",pid);
    printf("Child görevi bitmesi bekleniyor. \n"); // wait fonk yardımı ile
      wait(&status);
      }     
     
     
return 0;   
}
