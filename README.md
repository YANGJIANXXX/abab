#include<stdio.h>
#include<conio.h>
#include<windows.h>
#define X 10
#define Y 20
int main()
{
	void MAP(char map[X][Y]);
	void move(char map[X][Y],int ox,int oy,int nx,int ny);
	char map[X][Y]={
		{'~','~',' ','#','#',' ','#','#','#',' ','#','#','#','#','#','#',' ','~','~','~'},
		{'~','@',' ',' ',' ',' ',' ',' ',' ',' ','#',' ',' ','#',' ',' ','#',' ','~','~'},
		{'~',' ',' ',' ','#',' ','#',' ','#',' ',' ','#',' ',' ',' ','#','#','#',' ','~'},
		{'~',' ','#',' ','#',' ','#',' ',' ','#',' ','#',' ','#',' ',' ',' ','#',' ','~'},
		{'~',' ','#',' ','#',' ',' ',' ',' ','#',' ','#',' ','#',' ','#',' ','#',' ','~'},
		{'~',' ',' ',' ','#',' ','#','#',' ',' ',' ','#','#','#',' ','#','#','#',' ','~'},
		{'~','~',' ',' ','#',' ',' ',' ',' ','~',' ',' ','#','#',' ',' ',' ','#',' ','E'},
		{'~','~',' ','#','#',' ','#',' ','#','~','#',' ',' ',' ',' ','#',' ',' ',' ','~'},
		{'~',' ',' ',' ',' ',' ',' ',' ','~','~','#','#','#','#','#','#',' ','#','~','~'},
		{'#','#','#',' ','#','#','#','~','~',' ',' ','#','#','#','#','#',' ','~','~','~'},
	};
	char shuru;
	int x=1,y=1;
	char ok=' ';
	printf("上w,下s,左a,右d，退出q\n");
	MAP(map);
	while(1){
		shuru=getch();
		switch(shuru){
		case'w':
		case'W':
			if(map[x-1][y]==ok||map[x-1][y]=='E'){
			move(map,x,y,x-1,y);
			x--;
				}
			break;
		case's':
		case'S':
			if(map[x+1][y]==ok||map[x+1][y]=='E'){
			move(map,x,y,x+1,y);
			x++;
				}
			break;
		case'a':
		case'A':
			if(map[x][y-1]==ok||map[x][y-1]=='E'){
			move(map,x,y,x,y-1);
			y--;
				}
			break;
		case'd':
		case'D':
			if(map[x][y+1]==ok||map[x][y+1]=='E'){
			move(map,x,y,x,y+1);
			y++;
				}
			break;
		case'q':
		case'Q':
			return 0;
			break;
		default:
			break;
		}
	system("cls");
		MAP(map);
		if(y==Y-1){
			system("cls");
			printf("出去了！\n");
			break;
		}
	}
	return 0;
}
void MAP(char map[X][Y]){
	for(int i=0;i<X;i++){
		for(int j=0;j<Y;j++){
			printf("%c",map[i][j]);
		}
		printf("\n");
	}
}
void move(char map[X][Y],int ox,int oy,int nx,int ny){
	char tmap;
	tmap=map[ox][oy];
	map[ox][oy]=map[nx][ny];
	map[nx][ny]=tmap;
}

