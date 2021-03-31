#include<iostream>
#include<stdio.h>
#include<conio.h>
#include<stdlib.h>
#include<iomanip>
#include<string.h>
#include<windows.h>

using namespace std;

void gotoxy(int x, int y)
{
    COORD c;
    c.X=x;
    c.Y=y;
    SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),c);
}
enum state{menu,loggedin};
enum state currentstate=menu;
int n;
char currentuser[100];

typedef struct user
{
    char username[100];
    char password[100];
    char place[100];
    float price;
    int numtick;
    struct user *next;
}user;

int ShowBrochure();
user* InitializeList(user*);
user* AddUser(user*);
void LoginUser(user*);
void BookTicket(user*);
void CancelTicket(user*);
void ChangePassword(user*);
void LogoutUser();
void CheckTicket(user*);
void DisplayAll(user*);
void WriteToFile(user*);
void ExitProgram();

int main()
{
    system("color 3E");
    system("mode 800");

    string welcome="***  || WELCOME TO ANALLA TRAVELS ||  ***";
    int x;
    gotoxy(68,2);
    for(x=0;x<welcome.length();x++)
    {
        cout<<welcome[x];
        Sleep(10);
    }
    user *h=NULL;
    int ch1,ch2;
    h=InitializeList(h);
    while (1)
    {
        if(currentstate==menu)
        {
            gotoxy(70,10);
            cout<<"\n";
            int i;
            for(i=8;i<23;i++)
            {
                gotoxy(70,i);
                cout<<"=";

            }
            for(i=8;i<23;i++)
            {
                gotoxy(103,i);
                cout<<"=";
            }
            for(i=71;i<103;i++)
            {
                gotoxy(i,8);
                cout<<"=";
            }
            for(i=71;i<103;i++)
            {
                gotoxy(i,22);
                cout<<"=";
            }

            system("color 3E");
            gotoxy(80,11);
             cout<<"1. Sign-up\n";
              gotoxy(80,12);
             cout<<"2. Login\n";
              gotoxy(80,13);
              cout<<"3. Brochure\n";
               gotoxy(80,14);
             cout<<"0. Exit\n";
              gotoxy(80,15);
             string enter="Enter your choice : ";
             gotoxy(75,17);
             for(x=0;x<enter.length();x++)
             {
                 cout<<enter[x];
                 Sleep(20);
             }
             cin>>ch1;
            switch(ch1)
            {
                case 1:
                    system("cls");
                    h=AddUser(h);
                    break;
                case 2:
                    system("cls");
                    LoginUser(h);
                    break;
                case 3:
                    system("cls");
                    ShowBrochure();
                    break;
                case 0:
                    ExitProgram();
                    exit(0);
                    break;
                default:
                    cout<<"Not a valid input at this stage\n";
            }
        }
        else if(currentstate==loggedin)
        {
        system("CLS");
        system("color E5");
        int i;
            for(i=7;i<22;i++)
            {
                gotoxy(70,i);
                cout<<"*";

            }
            for(i=7;i<22;i++)
            {
                gotoxy(103,i);
                cout<<"*";
            }
            for(i=71;i<103;i++)
            {
                gotoxy(i,6);
                cout<<"*";
            }
            for(i=71;i<103;i++)
            {
                gotoxy(i,21);
                cout<<"*";
            }

        gotoxy(71,2);
        cout<<"================================";
        gotoxy(79,3);
		cout<<" OPTIONS AVAILABLE";
		gotoxy(71,4);
		cout<<"================================\n";
		gotoxy(77,8);
            cout<<"Book Package - 1";
            gotoxy(77,9);
            cout<<"Check Ticket - 2";
            gotoxy(77,10);
            cout<<"Cancel Ticket - 3";
            gotoxy(77,11);
            cout<<"Change Password - 4";
            gotoxy(77,12);
           cout<<"Brochure - 5";
            gotoxy(77,13);
             cout<<"Logout User - 6";
            gotoxy(75,15);
                   string choice="Enter your choice : ";
                   int a;
                   for(a=0;a<choice.length();a++)
                   {
                       cout<<choice[a];
                       Sleep(20);
                   }
            cin>>ch2;
            switch(ch2)
            {
                case 1:
                    BookTicket(h);
                    system("PAUSE");
                    system("CLS");
                    break;
                case 2:
                    CheckTicket(h);
                    system("PAUSE");
                    system("CLS");
                    break;
                case 3:
                    CancelTicket(h);
                    system("PAUSE");
                    system("CLS");
                    break;
                case 4:
                    ChangePassword(h);
                    system("PAUSE");
                    system("CLS");
                    break;
                case 5:
                   ShowBrochure();
                    system("PAUSE");
                    system("CLS");
                    break;
                case 6:
                     LogoutUser();
                     system("PAUSE");
                    system("CLS");
                    break;
                default:
                    cout<<"Not a valid input at this stage\n";
            }
        }
    }
    return 0;
}

user* InitializeList(user *h)
{
    user* t,*ptr,temp;
    FILE *fp;
    int cc=0,x;
    float ff;
    fp=fopen("users.txt","r");

    if(fp==NULL)
        return NULL;

    if(fgetc(fp)==EOF)
        return NULL;

    rewind(fp);
	while(fscanf(fp,"%s %s %s %f %d",temp.username,temp.password,temp.place,&temp.price,&temp.numtick)!=EOF)
	{
		ptr=(user*)malloc(sizeof(user));
		strcpy(ptr->username,temp.username);
		strcpy(ptr->password,temp.password);
		strcpy(ptr->place,temp.place);
		ptr->price=temp.price;
		ptr->numtick=temp.numtick;
		ptr->next=NULL;

		if(h==NULL)
            h=t=ptr;
		else
		{
			h->next=ptr;
			h=ptr;
		}
	}
	fclose(fp);
    return t;
}

void WriteToFile(user *h)
{
    FILE *fp;
    fp=fopen("users.txt","w");
    while(h!=NULL)
    {
        fprintf(fp,"%s %s %s %f %d\n",h->username,h->password,h->place,h->price,h->numtick);
        h=h->next;
    }
    fclose(fp);
}
int ShowBrochure()
{
	system("CLS");
	gotoxy(65,3);
	system("color c0");
	cout<<"\"Live with no excuses and travel with no regrets\" - Oscar Wilde";
	cout<<"\n\nWe provide travel to the following countries : \n\n1.Switzerland\n2.Australia\n3.Canada\n4.Japan\n5.Germany";
     cout<<"\n\n\n\n\nPlease enter the number corresponding to the country you are interested in : ";
    cin>>n;
    switch(n)
    {
    case 1:
        system("cls");
        cout<<endl;
        system("color 1E");
        cout<<"\" Wedged neatly between Germany, Austria, France, and Italy, Switzerland melds the best of all worlds — and adds a healthy dose of chocolate, cowbells, and cable cars.\"- Rick Steves";
        cout<<"\n\nCities included in the package are : \n\n->Geneva\n->Lucerne\n->Zurich\n->Bern\n->Lausanne";
        cout<<"\n\n6Days 7Nights...package cost:40,000/-";
        cout<<"\n\nPlace code: SW"<<endl;
        system("pause");
        system("cls");
         break;

    case 2:
        system("cls");
        cout<<endl;
        system("color 1E");
        cout<<"\t\t\"Being lost in Australia gives you a lovely sense of security\"-Bruce Chatwin, The Songlines";
        cout<<"\n\nCities included in the package are : \n\n->Sydney\n->Melbourne\n->Brisbane\n->Gold Coast\n->Darwin";
        cout<<"\n\n7Days 8Nights...package cost:60,000/-";
      cout<<"\n\nPlace code: AUS"<<endl;
      system("pause");
        system("cls");

      break;

    case 3:
        system("cls");
        cout<<endl;
        system("color 1E");
        cout<<"\t\t\"I believe the world needs more Canada\"- Bono,Musician";
        cout<<"\n\nCities included in the package are : \n\n->Toronto\n->Vancouver\n->Montreal\n->Ottawa\n->Quebec City";
        cout<<"\n\n6Days 7Nights...package : 25,000/-";
        cout<<"\n\nPlace code: CAN"<<endl;
        system("pause");
        system("cls");

        break;

    case 4:
        system("cls");
        cout<<endl;
        system("color 1E");
        cout<<"\t\t\"Japan never considers time together as time wasted. Rather, it is time invested.\"- Donald Richie";
        cout<<"\n\nCities included in the package are : \n\n->Osaka\n->Kyoto\n->Tokyo\n->Sapporo\n->Kobe";
        cout<<"\n\n6Days 7Nights...package : 38,000/-";
        cout<<"\n\nPlace code: JAP"<<endl;
        system("pause");
        system("cls");

     break;

    case 5:
        system("cls");
        cout<<endl;
        system("color 1E");
        cout<<"\t\t\"Germany must have her place in the Sun\"- Wilhelm II";
        cout<<"\n\nCities included in the package are : \n\n->Berlin\n->Munich\n->Hamburg\n->Frankfurt\n->Cologne";
        cout<<"\n\n8Days 7Nights...package : 1,20,000/-";
        cout<<"\n\nPlace code: GER"<<endl;
        system("pause");
        system("cls");
         break;
            }
}


user* AddUser(user* h)
{
    user *t;
    t=h;
    user *nw;
    nw=(user*)malloc(sizeof(user));
    fflush(stdin);
    gotoxy(80,10);

    cout<<"WELCOME TO REGISTER ZONE";
    system("color 0B");

   string enter="\n\n\t\t\t\t  ENTER USERNAME: ";
   int y;
   for(y=0;y<25;y++)
   {
       cout<<enter[y];
       Sleep(30);
   }
    cin>>nw->username;
    while(h!=NULL)
    {
        if(!strcmp(h->username,nw->username))
        {
            cout<<"That username already exists\n";
            system("pause");
            system("cls");
            return t;
        }
        h=h->next;
    }
    h=t;
    fflush(stdin);
    string desired="\n\n\t\t\t\t  DESIRED PASSWORD: ";
    for(y=0;y<25;y++)
    {
        cout<<desired[y];
        Sleep(30);
    }
    cin>>nw->password;
    cout<<"\n\n\nYou have been registered successfully ! \n";
    system("pause");
    system("cls");

    nw->next=NULL;
    strcpy(nw->place,"N/A");
    nw->price=0.0;
    nw->numtick=0;

    if(h==NULL)
    {
        h=t=nw;
    }
    else
    {
        while(h->next!=NULL)
        {
            h=h->next;
        }
        h->next=nw;
    }
    WriteToFile(t);
    return t;
}
void LoginUser(user* h=NULL)
{

    char username[100];
    char password[100];
    cout<<"\n\n";
    system("color 47");
     int j;
            for(j=8;j<23;j++)
            {
                gotoxy(60,j);
                cout<<"*";

            }
            for(j=8;j<23;j++)
            {
                gotoxy(103,j);
                cout<<"*";
            }
            for(j=59;j<104;j++)
            {
                gotoxy(j,8);
                cout<<"*";
            }
            for(j=60;j<103;j++)
            {
                gotoxy(j,22);
                cout<<"*";
            }
    gotoxy(65,12);
    cout<<"Enter Email/Username: ";
    cin>>username;
     gotoxy(65,14);
    cout<<"Enter Password: ";
    cin>>password;
       static int temp=0;
    do
    {
        if((!strcmp(h->username,username)) && (!strcmp(h->password,password)))
        {
            currentstate=loggedin;
            strcpy(currentuser,username);
            gotoxy(70,16);
            cout<<"Login successful!\n\n\n";
            gotoxy(60,25);
            system("PAUSE");
            h=h->next;

            return;
        }
        else if((!strcmp(h->username,username)) && (strcmp(h->password,password)))
        {
            cout<<"Password mismatch\n\n\n\n";
            temp++;
            system("pause");
            system("cls");
            LoginUser();
        }
        h=h->next;
    }while(h!=NULL || temp>0);
    cout<<"Sorry, no such user record was found\n";
}

void BookTicket(user *h)
{
    user *t=h;
    char place[100];
    while(h!=NULL)
    {
        if(!strcmp(h->username,currentuser))
            break;
        h=h->next;
    }
    if(h==NULL)
        return;
    if(h->price!=0.0)
    {
        gotoxy(65,25);
        cout<<"You must cancel your previous ticket before buying a new one\n";
        return;
    }
    ShowBrochure();
    float pricelist[5]={40000.0,60000.0,25000.0,38000.0,120000.0};
    gotoxy(2,2);
    cout<<"The place code for following countries are : \ni.Switzerland - SW/sw\nii.Australia - AUS/aus\niii.Canada - CAN/can\niv.Japan - JAP/jap\nv.Germany - GER/ger\n";
    gotoxy(2,8);
    string book="\n\nEnter place code to book your package(eg: sw, ja) : \n";
    int k;
    for(k=0;k<55;k++)
    {
        cout<<book[k];
        Sleep(30);
    }
    cin>>place;
    char choice;
    string confirm="\n\nWould You Like to Confirm Booking?\n[1] - Yes\n[2] - No\n";
    for(k=0;k<confirm.length();k++)
    {
        cout<<confirm[k];
        Sleep(30);
    }
    cin>>choice;
    float price;
    if(choice!='1')
        return;
    if(strcmp(place,"SW")==0 || strcmp(place,"sw")==0)
        price=pricelist[0];
    else if(strcmp(place,"AUS")==0 || strcmp(place,"aus")==0)
        price=pricelist[1];
    else if(strcmp(place,"CAN")==0 || strcmp(place,"can")==0)
        price=pricelist[2];
    else if(strcmp(place,"JAP")==0 || strcmp(place,"jap")==0)
        price=pricelist[3];
    else if(strcmp(place,"GER")==0 || strcmp(place,"ger")==0)
        price=pricelist[4];
     else
    {
        cout<<"That tour code doesn't exist\n";
        return;
    }

    string tickets="\nEnter the number of tickets you want to book\n";
    for(k=0;k<46;k++)
    {
        cout<<tickets[k];
        Sleep(30);
    }
    cin>>h->numtick;
    if(h->numtick==0)
        return;
    strcpy(h->place,place);
    h->price=price;
    WriteToFile(t);\
    string done="\nBookings Done!!\n";
    for(k=0;k<17;k++)
    {
        cout<<done[k];
        Sleep(25);
    }
    system("PAUSE");

}

void CheckTicket(user *h)
{
    system("cls");
    system("color 5F");
    while(h!=NULL)
    {
        if(!strcmp(h->username,currentuser))
            break;
        h=h->next;
    }
    if(!strcmp(h->place,"\0") || h->price==0.0 || h->numtick==0)
    {
        gotoxy(65,8);
        cout<<"You do not have a ticket booked yet\n";
        return;
    }
    float total=0.0;
    total=(h->price)*(h->numtick);
    gotoxy(65,8);
    cout<<"You have booked "<<h->numtick<<" tickets for a sum total of Rs "<<total<<" for tour code "<<h->place<<"\n";
}


void CancelTicket(user *h)
{
    system("cls");
    system("color DF");
    user *t=h;
    while(h!=NULL)
    {
        if(!strcmp(h->username,currentuser))
            break;
        h=h->next;
    }

    int flag=-1;

    if(h==NULL)
    {
        gotoxy(65,10);
        cout<<"No such user\n";
    }


    if(strcmp(h->place,"SW")==0 || strcmp(h->place,"sw")==0)
        flag++;
    else if(strcmp(h->place,"AUS")==0 || strcmp(h->place,"aus")==0 )
        flag++;
    else if(strcmp(h->place,"CAN")==0 || strcmp(h->place,"can")==0)
        flag++;
    else if(strcmp(h->place,"JAP")==0 || strcmp(h->place,"jap")==0)
        flag++;
    else if(strcmp(h->place,"GER")==0 || strcmp(h->place,"ger")==0)
        flag++;
    else
    {
        gotoxy(65,10);
        cout<<"You haven't booked a tour yet\n";
        return;
    }
    if(flag==0)
    {
        gotoxy(65,10);
        cout<<"Your ticket has been successfully cancelled";
        gotoxy(55,11);
        cout<<"A refund of Rs "<<(h->price)*(h->numtick)<<" for Tour Code "<< h->place<<" for "<<h->numtick<<" tickets will soon be made to your original source of purchase\n";
        strcpy(h->place,"N/A");
        h->price=0.0;
        h->numtick=0;
        WriteToFile(t);
    }
}

void ChangePassword(user *h)
{
    user *t=h;
    char passcurr[100];
    fflush(stdin);
    system("cls");
    system("color 0A");
    gotoxy(65,10);
    string current="Enter your current password to continue: ";
    int b;
    for(b=0;b<42;b++)
    {
        cout<<current[b];
        Sleep(30);
    }
    cin>>passcurr;
    while(h!=NULL)
    {
        if(!strcmp(h->username,currentuser))
            break;
        h=h->next;
    }
    if(h==NULL)
        return;
    if(!strcmp(passcurr,h->password))
    {
        gotoxy(65,12);
        string newp="Enter new password: ";
        for(b=0;b<newp.length();b++)
        {
            cout<<newp[b];
            Sleep(30);
        }
        cin>>h->password;
        gotoxy(65,14);
        string change="Password changed successfully\n";
        for(b=0;b<change.length();b++)
        {
            cout<<change[b];
            Sleep(30);
        }

    }
    WriteToFile(t);
}

void LogoutUser()
{
    system("cls");
    system("color 0F");
    if(currentstate==menu || strcmp(currentuser,"\0")==0)
    {
        gotoxy(65,12);
        cout<<"You must be logged in to logout\n";
        return;
    }
    strcpy(currentuser,"\0");
    currentstate=menu;
    gotoxy(65,12);
    cout<<"You have been successfully logged out\n";
}

void ExitProgram()
{
    system("cls");
    system("color 05");
    gotoxy(65,12);
    string thanks="Thank you for choosing Analla Travels\n \t\t\t\t\t\t\t\t\tExiting...\n\t\t\t\t\t\t\t\tProgram developed by Kavya Shah (19IT131)...";
    fflush(stdin);
    int y;
    for(y=0;y<thanks.length();y++)
    {
        cout<<thanks[y];
        Sleep(10);
    }
}
