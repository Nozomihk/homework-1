<<<<<<< HEAD
# 智能蛇
=======
#智能蛇
>>>>>>> ab8fb0fe4a514826feb760b7c51968598fd6938a
```
# include <stdio.h>
# include <string.h>
# include <windows.h>
# include <stdlib.h>
# include <conio.h>
# include <time.h>
# include <math.h>

# define MAP_ROW 40
# define MAP_LINE 100
# define LENTH 5
int head_x = MAP_ROW / 2, head_y = MAP_LINE / 2, tail_x, tail_y;
char map[MAP_ROW][MAP_LINE];
int snake[MAP_ROW][MAP_LINE];
char direct = 'a';
int food_x, food_y;

void Map();
void Snake();
void gotoxy(int , int );
int Judgewall();
int Judgefood();
int judgeself=1;
int score = 0;
void Food();
void Key();
void Run();
int main()
{
    int a;
    gotoxy(MAP_LINE / 3, MAP_ROW / 2);
    printf("Please choose the speed");
    gotoxy(MAP_LINE / 3, MAP_ROW / 2 + 1);
    printf("5 is easy and 1 is hard");
    scanf("%d", &a);
    getchar();
    gotoxy(0, 0);
    memset(snake, 0, sizeof(snake));
    Map();
    Snake();
    Food();
    while (1)
    {
        Key();
        Sleep(a*50);
        Run();
        if (Judgewall() == 0 || judgeself == 0)
            break;
    }
    gotoxy(MAP_LINE / 3, MAP_ROW / 2);
    printf("Game over ！");
    gotoxy(MAP_LINE / 3, MAP_ROW /2 +1);
    printf("Your score is %d", score);
    return 0;
}
void Map()
{
    int i, j;
    for (i = 0; i < MAP_ROW; ++i)
        map[i][0] = '#';
    for (j = 1; j < MAP_LINE; ++j)
        map[0][j] = '#';
    for (i = MAP_ROW - 1, j = 1; j < MAP_LINE; ++j)
        map[i][j] = '#';
    for (j = MAP_LINE - 1, i = 1; i < MAP_ROW; ++i)
        map[i][j] = '#';
    for (i = 0; i < MAP_ROW; i++)
    {
        for (j = 0; j < MAP_LINE; j++)
        {
            if (map[i][j] == '#')
            {
                //gotoxy(i, j);
                printf("#");
            }
            else
            {
                //gotoxy(i, j);
                printf(" ");
            }
        }
        printf("\n");
    }
}
void Snake()
{
    gotoxy( MAP_LINE / 2,MAP_ROW / 2 );
    printf("Q");
    snake[head_x][head_y] = LENTH;
    int a;
    for (a = 1; a < LENTH; a++)
    {
        gotoxy( a + MAP_LINE / 2,MAP_ROW / 2);
        printf("a");
        snake[head_x][head_y + a] = LENTH - a;
    }
    tail_x = MAP_ROW / 2;
   tail_y = a + MAP_LINE / 2;
}
void gotoxy(int x, int y)
{
    CONSOLE_SCREEN_BUFFER_INFO    csbiInfo;
    HANDLE    hConsoleOut;
    hConsoleOut = GetStdHandle(STD_OUTPUT_HANDLE);
    GetConsoleScreenBufferInfo(hConsoleOut, &csbiInfo);
    csbiInfo.dwCursorPosition.X = x;
    csbiInfo.dwCursorPosition.Y = y;
    SetConsoleCursorPosition(hConsoleOut, csbiInfo.dwCursorPosition);
}
void Food()
{
    srand(time(NULL));
        food_x = rand() % (MAP_ROW-10)+5;
        food_y = rand() % (MAP_LINE-10)+5;
    gotoxy( food_y,food_x);
        printf("@");
}
void Key()
{
    char sh, ch;
    if (_kbhit())
    {
        ch = _getch();
        if (ch == -32)
        {
            sh = _getch();
            switch (sh)
            {
            case 72:
                if (direct == 's')
                    ;
                else
                    direct = 'w';
                break;
            case 80:
                if (direct == 'w')
                    ;
                else
                    direct = 's';
                break;
            case 75:
                if (direct == 'd')
                    ;
                else
                    direct = 'a';
                break;
            case 77: 
                if (direct == 'a')
                    ;
                else
                    direct = 'd';
                break;
            }
        }
        else
        {
            switch (ch)
            {
            case 'w':case 'W':
                if (direct == 's')
                    ;
                else
                    direct = 'w';
                break;
            case 's':case 'S':
                if (direct == 'w')
                    ;
                else
                    direct = 's';
                break;
            case 'a':case 'A':
                if (direct == 'd')
                    ;
                else
                     direct = 'a';
                break;
                            case 'd':case 'D':
                if (direct == 'a')
                    ;
                else
                    direct = 'd';
                break;
            }
        }
    }
}void Run()
{
    switch(direct)
    {
    case 'a':
        gotoxy(head_y, head_x);
        printf("a");
        if (snake[head_x][head_y - 1] == 0)
            snake[head_x][head_y - 1] = snake[head_x][head_y] + 1;
        else
            judgeself = 0;
        head_y--;
        break;
    case 'd':
        gotoxy(head_y, head_x);
        printf("a");
        if (snake[head_x][head_y + 1] == 0)
            snake[head_x][head_y + 1] = snake[head_x][head_y] + 1;
        else
            judgeself = 0;
        head_y++;
        break;
    case 's':
    	        gotoxy(head_y, head_x);
        printf("a");
        if (snake[head_x + 1][head_y] == 0)
            snake[head_x + 1][head_y] = snake[head_x][head_y] + 1;
        else
            judgeself = 0;
        head_x++;
        break;
    case 'w':
        gotoxy(head_y, head_x);
        printf("a");
        if(snake[head_x - 1][head_y] == 0)
            snake[head_x - 1][head_y] = snake[head_x][head_y] + 1;
        else 
            judgeself = 0;
        head_x--;
    }
    gotoxy(head_y, head_x);
    printf("Q");
    if (Judgefood())
    {
        score++;
        Food();
    }
    else
    {
        if (snake[tail_x][tail_y] + 1 == snake[tail_x - 1][tail_y])
        {
            snake[tail_x][tail_y] = 0;
            gotoxy(tail_y, tail_x);
            printf(" ");
            tail_x--;
                    }
        else if (snake[tail_x][tail_y] + 1 == snake[tail_x + 1][tail_y])
        {
            snake[tail_x][tail_y] = 0;
            gotoxy(tail_y, tail_x);
            printf(" ");
            tail_x++;
        }
        else if (snake[tail_x][tail_y] + 1 == snake[tail_x][tail_y - 1])
        {
            snake[tail_x][tail_y] = 0;
            gotoxy(tail_y, tail_x);
            printf(" ");
            tail_y--;
        }
        else
        {
            snake[tail_x][tail_y] = 0;
            gotoxy(tail_y, tail_x);
            printf(" ");
            tail_y++;
        }
    }

}
int Judgewall()
{
    if (map[head_x][head_y] == '#')
        return 0;
    return 1;
}
int Judgefood()
{
    if (head_x==food_x&&head_y == food_y)
        return 1;
    return 0;
}
<<<<<<< HEAD
```
=======
```
>>>>>>> ab8fb0fe4a514826feb760b7c51968598fd6938a
