#include <iostream>
#include <stdlib.h>
#include <time.h>
#include <conio.h>
using namespace std;
#define r 15
#define c 21
struct plc
{
    int row = -1;
    int col = -1;
};

void print(char page[r][c]);
void meghdar_aval(char page[r][c]);
bool move(char page[r][c], plc p[], char u, int &n);
void gen_food(char page[r][c], plc p[], int n);

int main()
{
    srand(time(0));

    char page[r][c];

    plc p[400];
    int socer = 1;

    meghdar_aval(page);
    page[r / 2][c / 2] = '*';
    p[0].row = r / 2;
    p[0].col = c / 2;

    char buttom, but;
    bool flag1 = 1, flag2;

    gen_food(page, p, socer);

    long unsigned int speed=150;
    /*cout<<"Enter speed who you want between 1 untill 5: ";
    cin>>speed;
    cin.get();

    if(speed==1) speed=500; if(speed==2) speed=300; if(speed==3) speed=200; if(speed==4) speed=80;
    if(speed==5) speed=40;*/

    while (flag1)
    {
        but = buttom;
        system("cls");

        if (kbhit())
        {
            buttom = getch();
            if (but == 'w' && buttom == 's')
                buttom = but;
            else if (but == 's' && buttom == 'w')
                buttom = but;
            else if (but == 'd' && buttom == 'a')
                buttom = but;
            else if (but == 'a' && buttom == 'd')
                buttom = but;
        }

        flag1 = move(page, p, buttom, socer);

        print(page);

        _sleep(speed);
    }

    cout << "\n\n                                                  ~~~ ! GAME OVER ! ~~~";
    cout << "\n\n                                                    your socer is : " << socer << "\n\n";

    system("pause");
}

void gen_food(char page[r][c], plc p[], int n)
{

    bool f = 1, f2 = 1;
    int i, j;

    while (f)
    {
        i = rand() % r + 1;
        j = rand() % c + 1;

        if (i == r || i == r - 1)
            i -= 2;

        if (j == c || j == c - 1)
            j -= 2;

        for (int k = 0; k < n && f2; k++)
        {
            if (p[k].row == i && p[k].col == j)
                f2 = 0;
        }

        if (f2)
            f = 0;
    }

    page[i][j] = '$';
}

bool move(char page[r][c], plc p[], char u, int &socer)
{
    bool f = 1;
    int l1 = 0, l2 = 0;
    plc p2[400];

    for (int i = 0; i < socer; i++)
    {
        p2[i].row = p[i].row;
        p2[i].col = p[i].col;
    }

    if (u == 'w')
        l1 = -1;
    else if (u == 's')
        l1 = 1;
    else if (u == 'd')
        l2 = 1;
    else if (u == 'a')
        l2 = -1;

    if (u == 'w' || u == 's' || u == 'd' || u == 'a')
    {
        if (page[p[0].row + l1][p[0].col + l2] == '#' || page[p[0].row + l1][p[0].col + l2] == 'o')
            f = 0;

        else
        {
            if (page[p[0].row + l1][p[0].col + l2] == '$')
            {
                page[p[0].row + l1][p[0].col + l2] = page[p[0].row][p[0].col];
                p[0].row += l1;
                p[0].col += l2;

                for (int i = 1; i < socer; i++)
                {
                    p[i] = p2[i - 1];
                    page[p[i].row][p[i].col] = 'o';
                    //page[p[i].row][p[i].col] = page[p2[i - 1].row][p2[i - 1].col];
                }
                p[socer] = p2[socer - 1];
                page[p[socer].row][p[socer].col] = 'o';

                socer++;
                gen_food(page, p, socer);
            }

            else
            {
                page[p[0].row + l1][p[0].col + l2] = page[p[0].row][p[0].col];
                p[0].row += l1;
                p[0].col += l2;

                for (int i = 1; i < socer; i++)
                {
                    p[i] = p2[i - 1];
                    page[p[i].row][p[i].col] = 'o';
                    //page[p[i].row][p[i].col] = page[p2[i ].row][p2[i ].col];
                }
                page[p2[socer - 1].row][p2[socer - 1].col] = ' ';
            }
        }
    }

    return f;
}

void meghdar_aval(char page[r][c])
{
    for (int i = 0; i < r; i++) // meghdar dehi avalye
    {
        if (i == 0 || i == r - 1)
        {
            for (int j = 0; j < c; j++)
            {
                page[i][j] = '#';
            }
        }

        else
        {
            page[i][0] = '#';
            for (int j = 1; j < c; j++)
            {
                page[i][j] = ' ';
            }
            page[i][c - 1] = '#';
        }
    }
}

void print(char page[r][c])
{

    for (int i = 0; i < r; i++) // chap
    {
        for (int j = 0; j < c; j++)
        {
            cout << page[i][j] << ' ';
        }

        cout << endl;
    }
}
