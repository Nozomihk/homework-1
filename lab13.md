# 令人头大的贪吃蛇
## snake_move
#include<stdio.h>
#include<stdlib.h>           
#include<time.h>

#define SNAKE_MAX_LENGTH 20
#define SNAKE_HEAD 'H'
#define SNAKE_BODY 'X'
#define BLANK_CELL ' '
#define SNAKE_FOOD '$'
#define WALL_CELL '*'

int gameover=0;
char map[12][12]={
    {"***********"},
    {"*XXXXH    *"},
    {"*         *"},
    {"*         *"},
    {"*         *"},
    {"*         *"},
    {"*         *"},
    {"*         *"},
    {"*         *"},
    {"*         *"},
    {"*         *"},
    {"***********"}
};
int snakeLength=5;
int snake_X[SNAKE_MAX_LENGTH] = {1,1,1,1,1};
int snake_Y[SNAKE_MAX_LENGTH] = {1,2,3,4,5};

void output(void){
    int i;
	system("cls");
    for(i=0;i<12;i++){
        printf("%s\n",map[i]);
    }
}

void Gameover(void){
    char map_gameover[12][12]={
        "***********",
        "*         *",
        "*         *",
        "*         *",
        "*   YOU   *",
        "*         *",
        "*   DIED  *",
        "*         *",
        "*         *",
        "*         *",
        "*         *",
        "***********"
    };    
    system("cls");
    int i;
    for(i=0;i<12;i++){
        printf("%s\n",map_gameover[i]);
    }
	system("pause");
}
void BodyMove(int snakelen){
    int i;
    map[snake_X[0]][snake_Y[0]]=' ';
    for(i = 0;i < snakelen - 1;++i){
        snake_X[i]=snake_X[i + 1];
        snake_Y[i]=snake_Y[i + 1];
    }
}
void HeadMove(int dy,int dx,int snakelen){
    snake_X[snakelen - 1] += dx;
    snake_Y[snakelen -1] += dy;
    map[snake_X[snakelen - 2]][snake_Y[snakelen - 2]] = SNAKE_BODY;
    map[snake_X[snakelen - 1]][snake_Y[snakelen - 1]] = SNAKE_HEAD;
}
void Snake_Move(int snakelen){
    char direct=getchar();
    switch(direct){
        case 'a':
        case 'A':if(map[snake_X[snakelen - 1]][snake_Y[snakelen - 1] - 1] == ' '){
            int dy = -1,dx = 0;
			BodyMove(snakelen);
            HeadMove(dy,dx,snakelen);
        }
		else{
			gameover = 1;
		}break;
        case 'w':
        case 'W':if(map[snake_X[snakelen - 1] - 1][snake_Y[snakelen - 1]] == ' '){
            BodyMove(snakelen);
            int dy = 0,dx = -1;
            HeadMove(dy,dx,snakelen);
        }
		else{
			gameover = 1;
		}break;
        case 's':
        case 'S':if(map[snake_X[snakelen - 1] + 1][snake_Y[snakelen - 1]] == ' '){
            BodyMove(snakelen);
            int dy = 0,dx = 1;
            HeadMove(dy,dx,snakelen);
        }
		else{
			gameover = 1;
		}break;
        case 'd':
        case 'D':if(map[snake_X[snakelen - 1]][snake_Y[snakelen - 1] + 1] == ' '){
            BodyMove(snakelen);
            int dy = 1,dx = 0;
            HeadMove(dy,dx,snakelen);
        }
		else{
			gameover = 1;
		}break;
        default:break;
    }
}
int main(void){
    while(gameover != 1){
        output();
        Snake_Move(snakeLength);
    }
    Gameover();
}


## snake_eat
#include<stdio.h>
#include<stdlib.h>           
#include<time.h>

#define SNAKE_MAX_LENGTH 20
#define SNAKE_HEAD 'H'
#define SNAKE_BODY 'X'
#define BLANK_CELL ' '
#define SNAKE_FOOD '$'
#define WALL_CELL '*'


char map[12][12]={
    {"***********"},
    {"*XXXXH    *"},
    {"*         *"},
    {"*         *"},
    {"*         *"},
    {"*         *"},
    {"*         *"},
    {"*         *"},
    {"*         *"},
    {"*         *"},
    {"*         *"},
    {"***********"}
};
int snakeLength=5;
int snake_X[SNAKE_MAX_LENGTH] = {1,1,1,1,1};
int snake_Y[SNAKE_MAX_LENGTH] = {1,2,3,4,5};

int gameover = 0;

void output(void){
    int i;
	system("cls");
    for(i=0;i<12;i++){
        printf("%s\n",map[i]);
    }
}
void putfood(void){
	int x=rand()%10+1;
    int y=rand()%10+1;
    if(map[x][y] == ' '){
    	map[x][y]='$';
	}    
	else{
		putfood();
	}     
};
void Gameover(void){
    char map_gameover[12][12]={
        "***********",
        "*         *",
        "*         *",
        "*         *",
        "*   YOU   *",
        "*         *",
        "*   DIED  *",
        "*         *",
        "*         *",
        "*         *",
        "*         *",
        "***********"
    };
    system("cls");
    int i;
    for(i=0;i<12;i++){
        printf("%s\n",map_gameover[i]);
    }
}
void BodyMove(int snakelen){
	map[snake_X[0]][snake_Y[0]]=' ';
    int i;
    for(i = 0;i < snakelen - 1;++i){
        snake_X[i]=snake_X[i + 1];
        snake_Y[i]=snake_Y[i + 1];
    }
}
void HeadMove(int dy,int dx,int snakelen){
    snake_X[snakelen - 1] += dx;
    snake_Y[snakelen -1] += dy;
    map[snake_X[snakelen - 2]][snake_Y[snakelen - 2]] = SNAKE_BODY;
    map[snake_X[snakelen - 1]][snake_Y[snakelen - 1]] = SNAKE_HEAD;
}
void HeadChange(int dy,int dx,int snakelen){
	snakeLength += 1;
	snake_X[snakelen] = snake_X[snakelen - 1] + dx;
	snake_Y[snakelen] = snake_Y[snakelen - 1] + dy;
	map[snake_X[snakelen - 1]][snake_Y[snakelen - 1]] = SNAKE_BODY;
    map[snake_X[snakelen]][snake_Y[snakelen]] = SNAKE_HEAD;
}
void Snake_Move(int snakelen){
    char direct=getchar();
    switch(direct){
        case 'a':
        case 'A':if(map[snake_X[snakelen - 1]][snake_Y[snakelen - 1] - 1] == ' '){
			BodyMove(snakelen);
			int dy = -1,dx = 0;
            HeadMove(dy,dx,snakelen);
        }
        else if(map[snake_X[snakelen - 1]][snake_Y[snakelen - 1] - 1] == '$'){
			int dy = -1,dx = 0;
            HeadChange(dy,dx,snakelen);
            putfood();
		}
		else{
			gameover = 1;
		}break;
        case 'w':
        case 'W':if(map[snake_X[snakelen - 1] - 1][snake_Y[snakelen - 1]] == ' '){
			BodyMove(snakelen);
            int dy = 0,dx = -1;
            HeadMove(dy,dx,snakelen);
        }
        else if(map[snake_X[snakelen - 1] - 1][snake_Y[snakelen - 1]] == '$'){
			int dy = 0,dx = -1;
            HeadChange(dy,dx,snakelen);
            putfood();
		}
		else{
			gameover = 1;
		}break;
        case 's':
        case 'S':if(map[snake_X[snakelen - 1] + 1][snake_Y[snakelen - 1]] == ' '){
			BodyMove(snakelen);
            int dy = 0,dx = 1;
            HeadMove(dy,dx,snakelen);
        }
        else if(map[snake_X[snakelen - 1] + 1][snake_Y[snakelen - 1]] == '$'){
			int dy = 0,dx = 1;
            HeadChange(dy,dx,snakelen);
            putfood();
		}
		else{
			gameover = 1;
		}break;
        case 'd':
        case 'D':if(map[snake_X[snakelen - 1]][snake_Y[snakelen - 1] + 1] == ' '){ 
		    BodyMove(snakelen);
            int dy = 1,dx = 0;
            HeadMove(dy,dx,snakelen);
        }
        else if(map[snake_X[snakelen - 1]][snake_Y[snakelen - 1] + 1] == '$'){
			int dy = 1,dx = 0;
            HeadChange(dy,dx,snakelen);
            putfood();
		}
		else{
			gameover = 1;
		}break;
        default:break;
    }
}
int main(void){
	putfood();
    while(gameover != 1&&snakeLength <= SNAKE_MAX_LENGTH){
        output();
        Snake_Move(snakeLength);
    }
    Gameover();
}
