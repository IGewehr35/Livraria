#include <stdio.h>
#include <stdlib.h>
#include <windows.h>
#include <locale.h>
#include <string.h>
#include <conio.h>
#include <time.h>

typedef struct
{
    int codigo;
    char titulo[100];
    float preco;

} LIVRO;

typedef struct
{
    int cod_venda;
    int cod_livro;
    char data[11];
    int quantidade;
    float valor_total;

} VENDA;

void mostravendas()
{
    setlocale(LC_ALL, "Portuguese");

    VENDA vendas;
    int quantidade = 0;

    FILE *pontv;
    pontv = fopen("vendas.txt", "r");

    if (pontv == NULL)
    {
        system("cls");
        printf("\n-----------------------------------------------------");
        printf("\n|            ERRO: NENHUMA VENDA REGISTRADA         |");
        printf("\n-----------------------------------------------------");
        getch();
    }
    else
    {
        system("cls");
        printf("\n-----------------------------------------------------");
        printf("\n|                 EXIBIÇÃO DAS VENDAS               |");
        printf("\n-----------------------------------------------------");

        fread(&vendas, sizeof(VENDA), 1, pontv);
        while(!feof(pontv))
        {
            printf("\nCÓDIGO DA VENDA: %0.5d", vendas.cod_venda);
            printf("\nCÓDIGO DO LIVRO: %0.5d", vendas.cod_livro);
            printf("\nQUANTIDADE: %d", vendas.quantidade);
            printf("\nDATA DA VENDA: %s", vendas.data);
            printf("\nVALOR DA VENDA: R$%.2f", vendas.valor_total);

            printf("\n-----------------------------------------------------");

            fread(&vendas, sizeof(VENDA), 1, pontv);
            quantidade += 1;
        }
        printf("\nATUALMENTE O SISTEMA CONTA COM %d VENDAS REALIZADAS.", quantidade);
        printf("\n-----------------------------------------------------");
        getch();
    }
    fclose(pontv);
}
void pesquisatitulovenda()
{
    setlocale(LC_ALL, "Portuguese");
    char titulobusca[100];
    int n = 0;
    int quantidade = 0;
    int codigoset = 0;
    float totallivro = 0;

    LIVRO livros;
    FILE *pontlivro;

    VENDA vendas;
    FILE *pontvenda;

    system("cls");
    printf("\n-----------------------------------------------------");
    printf("\n|                      PESQUISA                     |");
    printf("\n-----------------------------------------------------");

    pontvenda = fopen("vendas.txt", "r");
    if (pontvenda != NULL)
    {
        printf("\nDIGITE O TÍTULO DO LIVRO: ");
        gets(titulobusca);
        fflush(stdin);

        pontlivro = fopen("livros.txt", "r");
        fread(&livros, sizeof(LIVRO), 1, pontlivro);
        while(!feof(pontlivro))
        {
            if (strcmp(livros.titulo, titulobusca) != 0)
            {
                fread(&livros, sizeof(LIVRO), 1, pontlivro);
                if(feof(pontlivro))
                {
                    system("cls");
                    printf("\n-----------------------------------------------------");
                    printf("\n|                LIVRO NÃO ENCONTRADO               |");
                    printf("\n-----------------------------------------------------");
                    getch();
                }
            }
            else
            {
                n = livros.codigo;
                fread(&vendas, sizeof(VENDA), 1, pontvenda);
                while(!feof(pontvenda))
                {
                    if (n != vendas.cod_livro)
                    {
                        fread(&vendas, sizeof(VENDA), 1, pontvenda);

                        if(feof(pontvenda))
                        {
                            system("cls");
                            printf("\n-----------------------------------------------------");
                            printf("\n|              NENHUMA VENDA ENCONTRADA             |");
                            printf("\n-----------------------------------------------------");
                            getch();
                            return;
                        }
                    }
                    else
                    {
                        system("cls");
                        printf("\n-----------------------------------------------------");
                        printf("\n|                 EXIBIÇÃO DOS LIVROS               |");
                        printf("\n-----------------------------------------------------");

                        while((!feof(pontvenda))&&(n==vendas.cod_livro))
                        {
                            printf("\nCÓDIGO DA VENDA: %0.5d", vendas.cod_venda);
                            printf("\nCÓDIGO DO LIVRO: %0.5d", vendas.cod_livro);
                            printf("\nQUANTIDADE: %d", vendas.quantidade);
                            printf("\nDATA DA VENDA: %s", vendas.data);
                            printf("\nVALOR DA VENDA: R$%.2f", vendas.valor_total);
                            printf("\n-----------------------------------------------------");
                            quantidade += 1;
                            totallivro += vendas.valor_total;
                            fread(&vendas, sizeof(VENDA), 1, pontvenda);
                        }
                        printf("\nESTE LIVRO POSSUI %d VENDAS REALIZADAS TOTALIZANDO R$%.2f", quantidade, totallivro);
                        printf("\n-----------------------------------------------------");
                        getch();
                        return;
                    }
                }
            }
        }
    }
    else
    {
        system("cls");
        printf("\n-----------------------------------------------------");
        printf("\n|            ERRO: NENHUMA VENDA REGISTRADA         |");
        printf("\n-----------------------------------------------------");
        getch();
        return 0;
    }

    fclose(pontlivro);
    fclose(pontvenda);
}
void pesquisatitulo()
{
    setlocale(LC_ALL, "Portuguese");
    char titulobusca[100];
    LIVRO livros;
    FILE *pontlivro;

    system("cls");
    printf("\n-----------------------------------------------------");
    printf("\n|                      PESQUISA                     |");
    printf("\n-----------------------------------------------------");

    pontlivro = fopen("livros.txt", "r");
    if (pontlivro != NULL)
    {
        printf("\nDIGITE O TÍTULO DO LIVRO: ");
        gets(titulobusca);
        fflush(stdin);

        fread(&livros, sizeof(LIVRO), 1, pontlivro);
        while(!feof(pontlivro))
        {
            if (strcmp(livros.titulo, titulobusca) != 0)
            {
                fread(&livros, sizeof(LIVRO), 1, pontlivro);
                if(feof(pontlivro))
                {
                    system("cls");
                    printf("\n-----------------------------------------------------");
                    printf("\n|                LIVRO NÃO ENCONTRADO               |");
                    printf("\n-----------------------------------------------------");
                    getch();
                }
            }
            else
            {
                system("cls");
                printf("\n-----------------------------------------------------");
                printf("\n|                 EXIBIÇÃO DOS LIVROS               |");
                printf("\n-----------------------------------------------------");

                printf("\nCÓDIGO: %06d\n", livros.codigo);
                printf("TÍTULO: %s\n", livros.titulo);
                printf("PREÇO:  R$%.2f", livros.preco);
                printf("\n-----------------------------------------------------");
                getch();
                break;
            }
        }
    }

    else
    {
        system("cls");
        printf("\n-----------------------------------------------------");
        printf("\n|           ERRO: NENHUM ARQUIVO ENCONTRADO         |");
        printf("\n-----------------------------------------------------");
        getch();
    }
    fclose(pontlivro);
    getch();
}
void registro_vendas()
{
    FILE *pontvenda;
    VENDA vendas;
    pontvenda = fopen("vendas.txt", "a");

    LIVRO livros;
    FILE *pontlivro;

    struct tm * tm;
    time_t t;

    setlocale(LC_ALL, "Portuguese");

    int n = 0;
    float preco = 0;
    int opcao = 0;

    system("cls");
    printf("\n-----------------------------------------------------");
    printf("\n|               REGISTRO DE VENDA                   |");
    printf("\n-----------------------------------------------------");

    pontlivro = fopen("livros.txt", "r");
    if (pontlivro != NULL)
    {
        vendas.cod_venda = buscacodigovenda()+1;
        printf("\nCÓDIGO DE VENDA: %0.5d", vendas.cod_venda);
        printf("\nCÓDIGO DO LIVRO: ");
        scanf("%d", &vendas.cod_livro);
        n = vendas.cod_livro;

        fread(&livros, sizeof(LIVRO), 1, pontlivro);
        while(!feof(pontlivro))
        {
            if (n != livros.codigo)
            {
                fread(&livros, sizeof(LIVRO), 1, pontlivro);
                if(feof(pontlivro))
                {
                    system("cls");
                    printf("\n-----------------------------------------------------");
                    printf("\n|                LIVRO NÃO ENCONTRADO               |");
                    printf("\n-----------------------------------------------------");
                    getch();
                    fclose(pontvenda);
                    fclose(pontlivro);
                    return;
                }
            }
            else
            {
                system("cls");
                preco = livros.preco;
                printf("\n-----------------------------------------------------");
                printf("\n|               REGISTRO DE VENDA                   |");
                printf("\n-----------------------------------------------------");
                printf("\nCÓDIGO DE VENDA: %0.5d", vendas.cod_venda);
                printf("\nCÓDIGO DO LIVRO: %0.5d", vendas.cod_livro);
                printf("\nPREÇO DO LIVRO: R$%.2f", livros.preco);
                printf("\nQUANTIDADE: ");
                scanf("%d", &vendas.quantidade);
                fflush(stdin);

                time(&t);
                tm = localtime(&t);
                strftime(vendas.data, 20, "%d/%m/%y", tm);

                printf("DATA: %s", vendas.data);

                vendas.valor_total = preco * vendas.quantidade;
                printf("\nVALOR TOTAL:  R$%.2f\n", vendas.valor_total);
                printf("\nVOCÊ DESEJA COMPRAR ESTE LIVRO?\n1-SIM\n2-NÃO\n\n");
                scanf("%d", &opcao);
                switch(opcao)
                {
                case 1:
                    printf("\nVENDA CONCLUÍDA!");
                    fwrite(&vendas, sizeof(VENDA), 1, pontvenda);
                    getch();
                    fclose(pontvenda);
                    fclose(pontlivro);
                    return;
                default:
                    printf("\nVENDA CANCELADA!");
                    getch();
                    fclose(pontvenda);
                    fclose(pontlivro);
                    return;
                }

            }
        }
    }
    else
    {
        system("cls");
        printf("\n-----------------------------------------------------");
        printf("\n|           ERRO: NENHUM ARQUIVO ENCONTRADO         |");
        printf("\n-----------------------------------------------------");
    }
    fclose(pontvenda);
    fclose(pontlivro);
    getch();
}


void cadastro_livro()
{
    FILE *pontlivro;
    pontlivro = fopen("livros.txt", "a");

    setlocale(LC_ALL, "Portuguese");

    LIVRO livros;
    int opcao = 0;

    system("cls");
    printf("\n-----------------------------------------------------");
    printf("\n|                      CADASTRO                     |");
    printf("\n-----------------------------------------------------");

    livros.codigo = buscacodigo()+1;
    printf("\nCÓDIGO DO LIVRO: %0.5d", livros.codigo);
    fflush(stdin);
    printf("\nDIGITE O TÍTULO DO LIVRO: ");
    gets(livros.titulo);
    printf("DIGITE O PREÇO DO LIVRO: ");
    scanf("%f", &livros.preco);

    printf("\nVOCÊ DESEJA CADASTRAR O LIVRO?\n1-SIM\n2-NÃO\n\n");
    scanf("%d", &opcao);
    switch(opcao)
    {
    case 1:
        printf("\nCADASTRO CONCLUÍDO!");
        fwrite(&livros, sizeof(LIVRO), 1, pontlivro);
        getch();
        fclose(pontlivro);
        return;
    default:
        printf("\nREGISTRO APAGADO");
        fclose(pontlivro);
        getch();
        return;
    }
}


int buscacodigo()
{
    LIVRO livros;
    int q = 0;

    FILE *pontlivro;
    pontlivro = fopen("livros.txt", "r");

    fread(&livros, sizeof(LIVRO), 1, pontlivro);
    while(!feof(pontlivro))
    {
        fread(&livros, sizeof(LIVRO), 1, pontlivro);
        q += 1;
    }
    fclose(pontlivro);
    return q;
}
int buscacodigovenda()
{
    VENDA vendas;
    int q = 0;

    FILE *pontv;
    pontv = fopen("vendas.txt", "r");

    fread(&vendas, sizeof(VENDA), 1, pontv);
    while(!feof(pontv))

    {
        fread(&vendas, sizeof(VENDA), 1, pontv);
        q += 1;
    }

    fclose(pontv);
    return q;
}
void mostramenu()
{
    setlocale(LC_ALL, "Portuguese");

    system("cls");
    printf("\n-----------------------------------------------------");
    printf("\n|                        MENU                       |");
    printf("\n-----------------------------------------------------");
    printf("\n1 - CADASTRAR");
    printf("\n2 - MOSTRAR LIVROS");
    printf("\n3 - PESQUISA POR TÍTULO");
    printf("\n4 - REGISTRAR VENDA");
    printf("\n5 - MOSTRAR VENDAS");
    printf("\n6 - PESQUISA VENDA POR TÍTULO");
    printf("\n7 - PESQUISAR VENDAS POR DATA");
    printf("\nESC - SAIR\n");
}
void pesquisadata()
{
    FILE *pontv;
    VENDA vendas;

    LIVRO livros;
    FILE *pontlivro;

    int dia;
    int mes;
    int ano;
    char data[11];
    float totaldata = 0;
    int quantidade = 0;

    setlocale(LC_ALL, "Portuguese");

    pontv = fopen("vendas.txt", "r");
    if (pontv == NULL)
    {
        system("cls");
        printf("\n-----------------------------------------------------");
        printf("\n|            ERRO: NENHUMA VENDA REGISTRADA         |");
        printf("\n-----------------------------------------------------");
        getch();
    }
    else
    {

        system("cls");
        printf("\n-----------------------------------------------------");
        printf("\n|                      PESQUISA                     |");
        printf("\n-----------------------------------------------------");
        printf("\nDigite o dia: ");
        scanf("%d", &dia);

        if(dia>31)
        {

            system("cls");
            printf("\n-----------------------------------------------------");
            printf("\n|                   DATA INVÁLIDA                    |");
            printf("\n-----------------------------------------------------");

            getch();
            return;

        }
        else
        {

            system("cls");
            printf("\n-----------------------------------------------------");
            printf("\n|                      PESQUISA                     |");
            printf("\n-----------------------------------------------------");
            printf("\nDigite o mes: %0.2d/", dia);
            scanf("%d", &mes);

            if (mes>12)
            {

                system("cls");
                printf("\n-----------------------------------------------------");
                printf("\n|                   DATA INVÁLIDA                    |");
                printf("\n-----------------------------------------------------");

                getch();
                return;

            }

            else
            {

                system("cls");
                printf("\n-----------------------------------------------------");
                printf("\n|                      PESQUISA                     |");
                printf("\n-----------------------------------------------------");
                printf("\nDigite o ano: %0.2d/%0.2d/", dia, mes);
                scanf("%d", &ano);
                if(ano>99)
                {
                    system("cls");
                    printf("\n-----------------------------------------------------");
                    printf("\n|                   DATA INVÁLIDA                    |");
                    printf("\n-----------------------------------------------------");

                    getch();
                    return;
                }
                else
                {
                    snprintf(data, 20, "%0.2d/%0.2d/%0.2d", dia, mes, ano);

                    system("cls");
                    printf("\n-----------------------------------------------------");
                    printf("\n|                      PESQUISA                     |");
                    printf("\n-----------------------------------------------------");
                    printf("\n%s", data);

                    fread(&vendas, sizeof(VENDA), 1, pontv);
                    while(!feof(pontv))
                    {
                        if (strcmp(data, vendas.data) != 0)
                        {
                            fread(&vendas, sizeof(VENDA), 1, pontv);
                            if(feof(pontv))
                            {
                                system("cls");
                                printf("\n-----------------------------------------------------");
                                printf("\n|              NENHUMA VENDA ENCONTRADA             |");
                                printf("\n-----------------------------------------------------");
                                getch();
                            }
                        }
                        else
                        {
                            system("cls");
                            printf("\n-----------------------------------------------------");
                            printf("\n|                 EXIBIÇÃO DAS VENDAS               |");
                            printf("\n-----------------------------------------------------");

                            while(!feof(pontv)&&(strcmp(data, vendas.data) == 0))
                            {
                                printf("\nCÓDIGO DA VENDA: %0.5d", vendas.cod_venda);
                                printf("\nCÓDIGO DO LIVRO: %0.5d", vendas.cod_livro);
                                printf("\nQUANTIDADE: %d", vendas.quantidade);
                                printf("\nDATA DA VENDA: %s", vendas.data);
                                printf("\nVALOR DA VENDA: R$%.2f", vendas.valor_total);
                                printf("\n-----------------------------------------------------");
                                fread(&vendas, sizeof(VENDA), 1, pontv);
                                quantidade += 1;
                                totaldata = totaldata + vendas.valor_total;
                            }
                            printf("\nESTE DIA POSSUI %d VENDAS REALIZADAS E UM VALOR TOTAL DE R$%.2f.", quantidade, totaldata);
                            printf("\n-----------------------------------------------------");
                            getch();

                        }

                    }
                }
            }

        }
        fclose(pontv);
    }
}
void mostrarlivros()
{
    setlocale(LC_ALL, "Portuguese");

    LIVRO livros;
    int quantidade = 0;

    FILE *pontlivro;
    pontlivro = fopen("livros.txt", "r");

    if (pontlivro == NULL)
    {
        system("cls");
        printf("\n-----------------------------------------------------");
        printf("\n|           ERRO: NENHUM ARQUIVO ENCONTRADO         |");
        printf("\n-----------------------------------------------------");
        getch();
    }
    else
    {

        system("cls");
        printf("\n-----------------------------------------------------");
        printf("\n|                 EXIBIÇÃO DOS LIVROS               |");
        printf("\n-----------------------------------------------------");

        fread(&livros, sizeof(LIVRO), 1, pontlivro);
        while(!feof(pontlivro))
        {
            printf("\nCÓDIGO: %0.5d\n", livros.codigo);
            printf("TÍTULO: %s\n", livros.titulo);
            printf("PREÇO:  R$%.2f", livros.preco);
            printf("\n-----------------------------------------------------");

            fread(&livros, sizeof(LIVRO), 1, pontlivro);
            quantidade += 1;
        }
        printf("\nATUALMENTE O SISTEMA CONTA COM %d LIVROS CADASTRADOS.", quantidade);
        printf("\n-----------------------------------------------------");
        getch();
    }
    fclose(pontlivro);
}
int main()
{

    setlocale(LC_ALL, "Portuguese");
    system("color 0c");
    char tecla = 0;
    mostramenu();

    while (tecla!=27)
    {
        if (kbhit())
        {
            tecla = getch();
            printf("\n%c", tecla);

            switch(tecla)
            {
            case 13:
                mostramenu();
                break;
            case 27:
                exit(0);
                break;
            case 49:
                cadastro_livro();
                mostramenu();
                break;
            case 50:
                mostrarlivros();
                mostramenu();
                break;
            case 51:
                pesquisatitulo();
                mostramenu();
                break;
            case 52:
                registro_vendas();
                mostramenu();
                break;
            case 53:
                mostravendas();
                mostramenu();
                break;
            case 54:
                pesquisatitulovenda();
                mostramenu();
                break;
            case 55:
                pesquisadata();
                mostramenu();
            default:
                printf(" <- Opção inválida!\nPressione qualquer botão.");
                getch();
                mostramenu();
                break;
            }
        }
    }
}
