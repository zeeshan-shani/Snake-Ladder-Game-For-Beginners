
//SNAKE LADDER GAME FOR BEGINNERS
#include<iostream>
#include<cstdlib> //library for generating numbers randomly
#include<ctime>
using namespace std;
bool p1_6 = false;//IT WILL BECOME TRUE WHEN A PLAYER 1 GOT 6 ON DICE
bool p2_6 = false;//IT WILL BEFOME TRUE WHEN PLAYER 2 GOT 6 ON DICE
bool end = false ;//IT WILL BECOME TRUE WHEN ANY ONE PLAYER REACHES TO 100
int p1pos = 0;//POSITION WILL BE STARTED FROM 1 AND WE WILL ADD RANDOM N.O TO 0
int p2pos = 0;//POSITION WILL BE STARTED FROM 1 AND WE WILL ADD RANDOM N.O TO 0
int SH[9];//snake head
int ST[9];//snake tail
int LS[9];//ladder head
int LE[9];//ladder tail

void player1()    //THIS IS FUNCTION OF PLAYER ONE WHICH WILL BE CALLED IN MAIN FUNCTION

{
char a;
 if	(p1_6==false)//AS YOU DOES'NT GOT 6 YOU WILL REMAIN IN THIS CHUNK EVERY TIME 
 {
	cout<<"PLYER 1 ROLL YOUR DICE BY PRESSING 'key' "<<endl;
	cin>>a;
	srand(time(0));  // Initialize random number generator.
	int r = (rand() % 6) + 1;
	cout<<"player 1 YOU ROLLED THE DICE AND YOU GOT="<<r<<endl;
	if(r == 6)//NOW IF YOU GOT 6 YOU WILL NOT ENTER IN THIS STATEMENT AGAIN BECAUSE P1_6==TRUE 
	{
			p1_6 = true;
			cout<<" player 1 YOU ARE IN THE GAME"<<endl;
			cout<<"player 1 you are on 1st number of the board"<<endl;
			p1pos = 1;
	}
	
	return ;//when player one do its turn than there will be turn of player 2 
	        //function will exit from here
 }

	cout<<"PLAYER 1 ROLL THE DICE TO REACH TOO NEW POSITION"<<endl;//now WHEN P1_1==TRUE THIS CHUNK OF CODE WILL RUN
	cin>>a;      //PLAYER 1 IS NOW ENTERED IN THE BOARD
	srand(time(0));
	int r=(rand()%6)+1;
	if((p1pos+r)<100)//PLAYER CAN PLAY GAME UNTILL HE REACHES 100;
	                 //if player is 0n 99 ;and he got random n.o 6 so he will be now on 105 ,
	                 //which does not satisfies condion so his position will not be updated
	{
		p1pos = p1pos + r;//HIS RANDOM N.O POSITION WILL BE ADDED TO HIS NEW POSITION IF IT IS <100
		for(int i = 0; i<9; i++ )
		{
			if(SH[i] == p1pos)//IF PLAYER 1 REACHES TOO SNAKE MOUTH
			{
				cout<<"OPPS!Player 1 is on Snake";
				cout<<"It got you from "<<p1pos<<" to "<<p1pos-(SH[i]-ST[i])<<endl;//SUBTRACTING YOUR POSITION FROM (SNAKE HEAD POSITION - SNAKE TAIL POSITION) 
				p1pos = p1pos-(SH[i]-ST[i]);//updaiting new position
			}
			
			else if(LS[i] == p1pos)//IF BY MISTAKE YOU REACH TOO *LADDER START* NOW YOU WILL CLIMB THROUGH IT
			{
		
				cout<<"Great!Player 1 on the Ladder";
				cout<<"It got you from "<<p1pos<<" to "<<p1pos+(LE[i]-LS[i]);//ADDITION  YOUR POSITION FROM (SNAKE HEAD POSITION - SNAKE TAIL POSITION)
				p1pos = p1pos+(LE[i]-LS[i]);//updaiting new position
			}
		}
	}
	cout<<"PLAYER 1 now you are on board n.o="<<p1pos<<endl;//displaying current position of player
	if(p1pos==100)//if player reaches the 100
	{
		cout<<"Player 1 wins";
		end = true;//to end the game
	}
}


void player2()   //THIS IS FUNCTION OF PLAYER 2:
{
char a;
 if	(!p2_6) //AS YOU DOES'NT GOT 6 YOU WILL REMAIN IN THIS CHUNK EVERY TIME
 {
 
	
	cout<<"PLAYER 2  ROLL YOUR DICE BY PRESSING 'key' "<<endl;
	cin>>a;
	srand(time(0));  // Initialize random number generator.
	int r = (rand() % 6) + 1;
	cout<<"PALYER 2 YOU ROLLED THE DICE AND YOU GOT="<<r<<endl;
	if(r == 6)//NOW IF YOU GOT 6 YOU WILL NOT ENTER IN THIS STATEMENT AGAIN BECAUSE P2_6==TRUE
	{
			p2_6 = true;
			cout<<" player 2 YOU ARE IN THE GAME"<<endl;
			cout<<"player 2 you are on 1st number of the board"<<endl;
			p2pos = 1;
	}
	
	return ;//when player one do its turn than there will be turn of player 1
	        //function will exit from here
 }

	cout<<"PLAYER 2 ROLL THE DICE TO REACH TO NEW POSITION"<<endl;//now WHEN P2_1==TRUE THIS CHUNK OF CODE WILL RUN 
	cin>>a;
	srand(time(0));
	int r=(rand()%6)+1;
	if((p2pos+r)<100)
	{
		p2pos = p2pos + r;
		for(int i = 0; i<9; i++ )
		{
			if(SH[i] == p1pos)
			{
				cout<<"OPPS!Player 2 is on Snake";
				cout<<"It got you from "<<p2pos<<" to "<<p2pos-(SH[i]-ST[i])<<endl;
				p2pos = p2pos-(SH[i]-ST[i]);
			}
			else if(LS[i] == p1pos)
			{
				cout<<"Great!Player 2 on the Ladder";
				cout<<"It got you from "<<p2pos<<" to "<<p2pos+(LE[i]-LS[i]);
				p2pos = p2pos+(LE[i]-LS[i]);
			}
		}
	}
	cout<<"PLAYER 2 now you are on board n.o="<<p2pos<<endl;
	if(p2pos==100)
	{
		cout<<"Player 2 wins";
		end = true;
	}	
}
void board()//FUNCTION DEFINED FOR A BOARD
{           //TWO DIMENSIONAL ARRAY IS MADE HERE
	int arr[10][10]={
	                 {100,99,98,97,96,95,94,93,92,91},
	                 {81,82,83,84,85,86,87,88,89,90},
	                 {80,79,78,77,76,75,74,73,72,71},
	                 {61,62,63,64,65,66,67,68,69,70},
	                 {60,59,58,57,56,55,54,53,52,51},
	                 {41,42,43,44,45,46,47,48,49,50},
	                 {40,39,38,37,36,35,34,33,32,31},
	                 {21,22,23,24,25,26,27,28,29,30},
	                 {20,19,18,17,16,15,14,13,12,11},
	                 {01,02,03,04,05,06,07,8,9,10}
				    };	
				    cout<< "THE TWO PLAYER THE SNAKE LADDER GAME "<<endl;
   //TO MAKE BOUNDARIES OF BOARD IHAVE DONE THIS DOWN HERE
cout<<"----------------------------------------------------"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<arr[0][0]<<" |"<<arr[0][1]<<"  |"<<arr[0][2]<<"  |"<<arr[0][3]<<"  |"<<arr[0][4]<<"  |"<<arr[0][5]<<"  |"<<arr[0][6]<<"  |"<<arr[0][7]<<"  |"<<arr[0][8]<<"  |"<<arr[0][9]<<"   |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;	
cout<<"----------------------------------------------------"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<arr[1][0]<<"  |"<<arr[1][1]<<"  |"<<arr[1][2]<<"  |"<<arr[1][3]<<"  |"<<arr[1][4]<<"  |"<<arr[1][5]<<"  |"<<arr[1][6]<<"  |"<<arr[1][7]<<"  |"<<arr[1][8]<<"  |"<<arr[1][9]<<"   |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"----------------------------------------------------"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<arr[2][0]<<"  |"<<arr[2][1]<<"  |"<<arr[2][2]<<"  |"<<arr[2][3]<<"  |"<<arr[2][4]<<"  |"<<arr[2][5]<<"  |"<<arr[2][6]<<"  |"<<arr[2][7]<<"  |"<<arr[2][8]<<"  |"<<arr[2][9]<<"   |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"----------------------------------------------------"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<arr[3][0]<<"  |"<<arr[3][1]<<"  |"<<arr[3][2]<<"  |"<<arr[3][3]<<"  |"<<arr[3][4]<<"  |"<<arr[3][5]<<"  |"<<arr[3][6]<<"  |"<<arr[3][7]<<"  |"<<arr[3][8]<<"  |"<<arr[3][9]<<"   |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"----------------------------------------------------"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<arr[4][0]<<"  |"<<arr[4][1]<<"  |"<<arr[4][2]<<"  |"<<arr[4][3]<<"  |"<<arr[4][4]<<"  |"<<arr[4][5]<<"  |"<<arr[4][6]<<"  |"<<arr[4][7]<<"  |"<<arr[4][8]<<"  |"<<arr[4][9]<<"   |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"----------------------------------------------------"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<arr[5][0]<<"  |"<<arr[5][1]<<"  |"<<arr[5][2]<<"  |"<<arr[5][3]<<"  |"<<arr[5][4]<<"  |"<<arr[5][5]<<"  |"<<arr[5][6]<<"  |"<<arr[5][7]<<"  |"<<arr[5][8]<<"  |"<<arr[5][9]<<"   |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"----------------------------------------------------"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<arr[6][0]<<"  |"<<arr[6][1]<<"  |"<<arr[6][2]<<"  |"<<arr[6][3]<<"  |"<<arr[6][4]<<"  |"<<arr[6][5]<<"  |"<<arr[6][6]<<"  |"<<arr[6][7]<<"  |"<<arr[6][8]<<"  |"<<arr[6][9]<<"   |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;

cout<<"----------------------------------------------------"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<arr[7][0]<<"  |"<<arr[7][1]<<"  |"<<arr[7][2]<<"  |"<<arr[7][3]<<"  |"<<arr[7][4]<<"  |"<<arr[7][5]<<"  |"<<arr[7][6]<<"  |"<<arr[7][7]<<"  |"<<arr[7][8]<<"  |"<<arr[7][9]<<"   |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"----------------------------------------------------"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<arr[8][0]<<"  |"<<arr[8][1]<<"  |"<<arr[8][2]<<"  |"<<arr[8][3]<<"  |"<<arr[8][4]<<"  |"<<arr[8][5]<<"  |"<<arr[8][6]<<"  |"<<arr[8][7]<<"  |"<<arr[8][8]<<"  |"<<arr[8][9]<<"   |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"----------------------------------------------------"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl;
cout<<"|"<<arr[9][0]<<"   |"<<arr[9][1]<<"   |"<<arr[9][2]<<"   |"<<arr[9][3]<<"   |"<<arr[9][4]<<"   |"<<arr[9][5]<<"   |"<<arr[9][6]<<"   |"<<arr[9][7]<<"   |"<<arr[9][8]<<"   |"<<arr[9][9]<<"   |"<<endl;
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl; 
cout<<"|"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"    |"<<"     |"<<endl; 
cout<<"----------------------------------------------------"<<endl;	
}

int main()
{
 board();//FUNCTION OF BOARD IS CALLED
 int d = 0;
 srand(time(0)); // Initialize random number generator.
 for(int i = 0; i<9; i++)
 {
 	//cout<<"setting snake"<<i<<endl;
 	
	SH[i] = (rand() % 100) + 1;//GENERATING RANDOM N.O TOO ADJUST SNAKE HEAD 
	//cout<<SH[i]<<endl;//DISPLAYING SNAKE HEAD
	ST[i] = (rand() % 100) + 1;//GENERATING RANDOM N.O TOO ADJUST SNAKE TAIL
	//cout<<ST[i]<<endl;//DISPLAYING SNAKE TAIL
	for (int j = 0; j<i; i++)
	{   //if FOLLOWING CONDITIONS will happen snake will not set :
	  //1st condition(two snake head will be on the same spot);2nd condition(if snake head is less than tail);3rd condition(snake head and snake tail is at the same row)}
		if ((SH[i] == SH[j])   || (((SH[i]<ST[i]) || ((SH[i]-SH[i]%10)/10)== ((ST[i]-ST[i]%10)/10))))
		{
			i--;  //IF ANY OF ABOVE CONDITION BECOMES TRUE Current Snake is not set
			break;
		}
	}
			
 }
 
  int flag1 = 0;
  for(int i = 0; i<9; i++)
 {
 	flag1 = 0;
 	//cout<<"setting Ladder"<<i<<endl;
	
	LS[i] = (rand() % 100) + 1;
	LE[i] = (rand() % 100) + 1;
	
	for(int k = 0; k<9; k++)
	{
		if (LS[i] == SH[k])
		{
			flag1 = 1;
			break;
		}
	}
	for (int j = 0; j<i; i++)
	{
		if (((LS[i] == LS[j])   || ((LE[i]<LS[i]) || ((LS[i]-(LS[i]%10))/10)== ((LE[i]-(LE[i]%10))/10) || flag1==1)))
		{
			i--;
			break;
		}
	}	
 }

	
 
 for(int i = 0; i<9; i++)
 {
 	cout<< "Snake\t"<<i<<" Head is at "<<SH[i]<<endl;
 	cout<< "Snake\t"<<i<<" Tail is at "<<ST[i]<<endl;
 	cout<< "Ladder\t"<<i<<" Start is at "<<LS[i]<<endl;
 	cout<< "Ladder\t"<<i<<" End is at "<<LE[i]<<endl;
 }

 while (end == false)
 {
	player1();
	player2();
 }
 
 
	return 0;
}
