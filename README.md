# batalla-naval
#include<stdio.h>
#include<stdlib.h>
#include<time.h>//crear biblioteca para el tiempo



int menu()
{
    int p;
    printf("\n\n");
    printf("BENEMERITA UNIVERSIDAD AUTONOMA DE PUEBLA\n");
    printf("Faculdad De Ciencias De La Computacion\n");
    printf("Poyecto Final:  \n");
    printf("\n\n");
    printf("------------------- Juego de Batalla Naval----------------------------\n");
    printf("----------------------------------------------------------------------\n");
    printf("                                   |>                                 \n");
    printf("                                  *|                                  \n");
    printf("                                  *|*                                 \n");
    printf("                                  *|**                                \n");
    printf("                                  *|***                               \n");
    printf("                                  *|****                              \n");
    printf("                         ***********************                      \n");
    printf("                           -------------------                        \n");
    printf("                           *******************                        \n");
    printf("                            *****************                         \n");
    printf("                             ***************                           \n");
    printf("                               ************                           \n");
    printf("----------------------------------------------------------------------\n");
        printf("\n\n");
    printf("porfavor de poner su teclado en masyuculas\n");
    printf("1. Jugar\n");
    printf("2. Salir\n");
    printf("Por favor ingrese una opcion: \n");
    scanf("%i",&p);
    fflush(stdin);//dispositivo de salida sin buffer su utilidad es nula// buffer son arrays en los cuales se aÃ±aden datos
    return p;
}

int menu2(){
    printf("eres demasiado joven para jugar \n");
    printf("intentalo cuando tengas mas de 18 aÃ±os \n");
}

int tabla()
{
    int fallo = 10;
    int aste = 40;
    int cari = 1;
    printf("%c: barco , %c: barco undido , %c: no dio en el blanco \n\n",aste,cari,fallo);
}




void matriz(char mu[5][5],char apuntador[3])
{
    int i,j,asignacion_a=65;
    for (i=0; i<5; i++)
    {
        for (j=0; j<5; j++)
        {
            mu[i][j]=asignacion_a++;
            if (apuntador[0]==mu[i][j]) mu[i][j]=42;
            if (apuntador[1]==mu[i][j]) mu[i][j]=42;
            if (apuntador[2]==mu[i][j]) mu[i][j]=42;
        }
    }
}


void Virtual(char mv[5][5])
{
    int i,j,asignacion_a=65;
    for (i=0; i<5; i++)
    {
        for (j=0; j<5; j++)
        {
            mv[i][j]=asignacion_a++;
        }
    }

}


void nombre(char name[100])
{
    char nombre1;
    printf("ingresa tu nombre: ");
 gets(name);//escanear
    system("cls");
    printf("\nNOMBRE: %s \n",name);
}

void edad(int years[20])
{
    char name[100];
    int year;
    printf("menores de 18 anos no podran jugar \n");
    printf("ingresa tu edad: ");
    scanf("%d",&year);
   system("cls");
   if (year>=18){
    printf(" Bienvenido al juego de BATALLA NAVAL\n");
     printf("\n EDAD: %d \n\n\n",year);
   }
   else{
    printf("no se puede jugar es menor de edad \n");
    printf("vuelve cuando tengas 18 years o mas por favor :)\n");
         printf("\n EDAD: %d \n\n\n",year);
   }
}


void imprime(char mu[5][5])
{
    int i,j;

    for (i=0; i<5; i++)
    {
        for (j=0; j<5; j++)
        {
            printf("|%c|\t",mu[i][j]);


        }
        printf("\n\n");
    }
}


void letras(char m_p[5][5])
{
    int i,j,asignacion_a=65;
    for (i=0; i<5; i++)
    {
        for (j=0; j<5; j++)
        {
            m_p[i][j]=asignacion_a++;
        }
    }

}


void barcos(char b[5])
{
    int i,anterior,a=1;
    for(i=0; i<5;)
    {
        printf("la unbicacion del barco %i: ",a);
        scanf("%c",&b[i]);
        fflush(stdin);//dispositivo de salida sin buffer su utilidad es nula
        if (b[i]>=65 && b[i]<=84)
        {
            if(b[i]>= 65 && b[i]<=90);
            else b[i]=b[i]-32;
            if (b[i]!=anterior)
            {
                anterior=b[i];
                i++;
                a++;
            }
            else printf("barco en otra posicion \n");
        }
        else printf("incotrrecta ingre una letra dada por el tablero \n");
    }
}



void Maquinaaleatorio(char mu[5][5],int *x, int *j)
{
    int i,y;
    srand (time(NULL));//punto inicial para generar una serie de enteros
    do
    {
        *x=rand ()  %  5;
        *j=rand () %  5;
    }
    while(  mu[*x][*j] == 5 || mu[*x][*j] == 1 );

}




void aleatorio(char ale[5])
{
    int i,numero;
    srand (time(NULL));//punto inicial para generar una serie de enteros 
    do
    {
        i=0;
        for (; i<5; i++)
        {
            numero = rand () % 20 + 65;
            ale[i]=numero;
        }
    }
    while(ale[0]==ale[1] || ale[0]==ale[2] || ale[1] == ale[2]);
}




void lanzamiento_usuario(char mv[5][5],char mu[5][5],char m_op[5][5],char name[100],char ale[5], int years[20])
{
    char k,t,m,i,anterior;
    int p=0,c=0,x=0,j=0,C=0,ne=0;
    do
    {
        if (p==0 )
        {
            printf("punto donde desea atacar?:  ");
            scanf("%s",&k);
            if (k>=65 && k<=84)
            {
                if(k==ale[0] || k==ale[1] || k==ale[2] )
                {
                    if(k!=anterior)
                    {
                        printf("BARCO HUNDIDO!!!\n");
                        C++;
                        anterior=k;
                        system("pause");
                        system("cls");
                        printf("\nNOMBRE: %s \n",name);
                        imprime(mu);
                        tabla();
                        for (i=0; i<5; i++)
                        {
                            for (m=0; m<5; m++)
                            {
                                if(k==mv[i][m]) mv[i][m]=1;
                                printf("|%c|\t",mv[i][m]);
                            }
                            printf("\n\n");
                        }
                        printf("\nMAQUINA\n");
                    }
                    else printf("ya esta,esta cordenada  \n");
                }

                else
                {

                    if(k!=anterior)
                    {
                        printf("No dio en el blanco\n");
                        p++;
                        anterior=k;
                        system("pause");
                        system("cls");
                        printf("\nNOMBRE: %s \n",name);
                        imprime(mu);
                        tabla();
                        for (i=0; i<5; i++)
                        {
                            for (m=0; m<5; m++)
                            {
                                if (k==mv[i][m]) mv[i][m]=5;
                                printf("|%c|\t",mv[i][m]);
                            }
                            printf("\n\n");
                        }
                        printf("\nMAQUINA\n");
                    }
                    else printf("ya esta esta cordenada \n");
                }
            } else printf("incorrecto ingrese una letra del tablero\n");
        }
        if(p==1)
        {
            Maquinaaleatorio(mu,&x,&j);
            printf("maquina Ataco en posicion: %c\n",m_op[x][j]);
            t=mu[x][j];
            if(t=='*')
            {
                printf("Dio en el blanco\n");
                c++;
                system("pause");
                system("cls");
                printf("\nNOMBRE: %s \n",name);
                printf("\n EDAD: %d \n\n\n",years);
                for (i=0; i<5; i++)
                {
                    for (m=0; m<5; m++)
                    {
                        if (t==mu[i][m]) mu[x][j]=1;
                        printf("|%c|\t",mu[i][m]);
                    }
                    printf("\n\n");
                }
                tabla();
                imprime(mv);
                printf("\nMAQUINA\n");
            }
            else
            {
                printf("No dio en el blanco\n");
                p=0;
                system("pause");
                system("cls");
                printf("\nNOMBRE: %s \n",name);
                 printf("\n EDAD: %d \n\n\n",years);
                for (i=0; i<5; i++)
                {
                    for (m=0; m<5; m++)
                    {
                        if (mu[i][m]==mu[x][j]) mu[i][m]=5;
                        printf("|%c|\t",mu[i][m]);
                    }
                    printf("\n\n");
                }
                tabla();
                imprime(mv);
                printf("\nMAQUINA\n");
            }
        }

        while (c==3)
        {
            for (i=0; i<5; i++)
            {
                printf("suerte para la proxima \n");
            }
            printf("GAME OVER!!\n");
            c=0;
            p=3;
        }
        while (C==3)
        {
            for (i=0; i<5; i++)
            {
                printf("FELICIDADES JUSTO EN EL BLANCO!!! \n");

            }
            printf("retate a ver si puedes ganar una vez mas \n");
            C=0;
            p=3;
        }

    }
    while(p !=3 );
    system("pause");
    system("cls");
}

int main()
{
    char mu[5][5],mv[5][5],name[100],m_op[5][5],barc[5],ale[5];
    int years[20];
    int op;
    nombre(name);
    edad(years);
    
    do
    {
        op=menu();
        if (op==1)
        {
            printf("\nComenzamos\n");
            system("pause");
            system("cls");
            printf("\n\nNOMBRE: %s \n \n\n",name);
           
            letras(mu);
            imprime(mu);
            matriz(mu,barc);
            tabla();

            Virtual(mv);
            imprime(mv);
            printf("\nMAQUINA\n\n\n");

            barcos(barc);
            system("pause");
            system("cls");
            aleatorio(ale);
            printf("\n\nNOMBRE: %s \n \n\n",name);
             printf("\n EDAD: %d \n\n\n",years);

            matriz(mu,barc);
            imprime(mu);
            tabla();

            Virtual(mv);
            imprime(mv);
            printf("\nMAQUINA\n\n\n");

           letras(m_op);
            lanzamiento_usuario(mv,mu,m_op,name,ale,years);
        }
