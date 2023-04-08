#include<stdio.h>
#include<stdlib.h>
#include<string.h>
#include<windows.h>
#include<conio.h>
struct phone_book
{ char name[30];
  char sex;
  char Fathername[30];
  char phone_number[20];
  char citizenship_number[20];
  char email[30];
  char address[30];
};
typedef struct phone_book pb;
pb p[100];
int test;
void Create(int i);
void DisplayAll();
void Modify();
void Delete();
void Search_by_Name();
void Search_by_Gender();
void Search_by_FatherName();
void Search_by_phoneNumber();
void Search_by_citizenship_number();
void Search_by_Address();
void Search_by_Email();
void sort();
void gotoxy(int,int);
void boxout(int l,int b,int x,int y);


void boxout(int l,int b,int x,int y)
{
  int i;
  for(i=0;i<l;i=i+2)
  {
    
    gotoxy(x+i,y); 
    printf("");
    gotoxy(x+i,y+b);
    printf("");
  }
  for(i=0;i<b;i++)
  {
    gotoxy(x,y+i);
    printf("|");
    gotoxy(x+l,y+i);
    printf("|");
  }
  gotoxy(x+l,y);
  printf(" ");
  gotoxy(x+l,y+b);
  printf("|");
  gotoxy(x,y);
  printf(" ");
  gotoxy(x,y+b);
  printf("|");
}
void linebox(int l,int b,int x,int y)
{
  int i;
  for(i=0;i<l;i++)
  {
    gotoxy(x+i,y);
    printf("%c",196);
    gotoxy(x+i,y+b);
    printf("%c",196);
  }
  for(i=0;i<b;i++)
  {
    gotoxy(x,y+i);
    printf("%c",179);
    gotoxy(x+l,y+i);
    printf("%c",179);
  }
  gotoxy(x+l,y);
  printf("%c",191);
  gotoxy(x+l,y+b);
  printf("%c",217);
  gotoxy(x,y);
  printf("%c",218);
  gotoxy(x,y+b);
  printf("%c",192);
}
void gotoxy(int x , int y)
{
    COORD c;
    c.X=x;
    c.Y=y;
    SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),c);
}



int main()
{ 
  int ch,x,y;
   static int i=0;
   int k;
   FILE  *fp;
   
     linebox(42,17,90,2);
    boxout(42,17,90,2);
     gotoxy(91,5);
     printf("\tWelcome to PhoneBook Project ");
      gotoxy(91,6);
      printf("-----------------------------------------");
      gotoxy(91,7);
      printf("\t\tTEAM MEMBERS");
        gotoxy(91,8);
          printf("-----------------------------------------");
       gotoxy(91,9);
       printf("2110030031  -  Sumeet Sharma");
       gotoxy(91,11);
       printf("2110030345  - Akshaya");
        gotoxy(91,13);
       printf("2110030037  - Sushma Reddy");
       gotoxy(91,15);
       printf("210030214  - Sri Harsha");
              gotoxy(91,17);
             printf("-----------------------------------------");
            
            linebox(35,3,1,50);
               boxout(35,3,1,50);
                gotoxy(2,52);
                printf("Enter any Number to Continue :");
                scanf(" %d",&k);
          if(k==1)
            system("cls");
            else
            system("cls");

do{ 
  linebox(28,12,90,2);
    boxout(28,12,90,2);
         gotoxy(91,5);
        printf("Enter");
         gotoxy(91,6);
        printf("1.Create Contact");
         gotoxy(91,7);
        printf("2.Display List of Contacts");
      gotoxy(91,8);
        printf("3.Modify Contact");
       gotoxy(91,9);
        printf("4.Search Contact");
       gotoxy(91,10);
        printf("5.Delete Contact");
       gotoxy(91,11);
        printf("6.Exit");
     gotoxy(91,12);
    scanf("%d",&ch);
      system("cls");
    switch(ch)
    {
      case 1:  fp=fopen("Record.txt","a");
      test=0;
          linebox(80,30,90,2);
              boxout(80,30,90,2);
              Create(i);
              if(test==0)
              {fwrite(&p[i],sizeof(pb),1,fp);                //Writing the Data in the file 
              if(fwrite!=0)
              printf("Written Successfully !!\n");
              else
              printf("Error in Writing File\n");
              i++;
              printf("Contact Created Successfully !!!");
              }
              fclose(fp);
              break;
        case 2: sort();
              DisplayAll();
                break;
        case 3: Modify();
                break;
        case 4: 
              do{
               linebox(32,15,90,2);
               boxout(32,15,90,2);  
               gotoxy(91,5);
               printf("Enter");
               gotoxy(91,6);
               printf("1.Search by Name");
               gotoxy(91,7);
               printf("2. Search by Gender");
               gotoxy(91,8);
               printf("3. Search by Father Name");
               gotoxy(91,9);
               printf("4.Search by Phone Number");
               gotoxy(91,10);
               printf("5.Search by Citizenship Number");
           gotoxy(91,11);
               printf("6. Search by Email");
           gotoxy(91,12);
               printf("7.Serch by Address");
           gotoxy(91,13);
               printf("8. Exit");
               gotoxy(91,14);
                 scanf("%d",&y);
                 gotoxy(1,1);
                 switch(y)
                 {  case 1:Search_by_Name();break;
                   case 2:Search_by_Gender();break;
                   case 3:Search_by_FatherName();break;
                   case 4:Search_by_phoneNumber();break;
                   case 5:Search_by_citizenship_number();break;
                   case 6:Search_by_Email();break;
                   case 7:Search_by_Address();break;

                   default: if(y>8)
                    printf("Invalid Choice !!");
                }
                linebox(35,3,1,50);
               boxout(35,3,1,50);
                gotoxy(2,52);
                printf("Enter any Number to Continue :");
                scanf(" %d",&k);
          if(k==1)
            system("cls");
            else
            system("cls");
          }while(y!=8);
          
          break;
       case 5: Delete();
                   break;      
      
        case 6: exit(1);
    }            linebox(35,3,1,50);
               boxout(35,3,1,50);
                gotoxy(2,52);
                printf("Enter any Number to Continue :");
                scanf(" %d",&k);
          if(k==1)
            system("cls");
            else
            system("cls");

    
  }while(1);

  
}

int Verify_by_Name(char s1[])               //Searching for Contact By Name if it alredy exists
{ 
int f=0;
 pb s;
    FILE *op;
   op=fopen("Record.txt","r");
     
    while(fread(&s, sizeof(pb), 1, op))
    {  if(strcmp(s1,s.name)==0)
    f=1;
}
    fclose (op);
return f;
}


int Verify_by_phoneNumber(char s1[])          // Searching for Contact from Contact List By PhoneNumber
{ 
int f=0;
 pb s;
    FILE *op;
   op=fopen("Record.txt","r");
     
    while(fread(&s, sizeof(pb), 1, op))
    {  if(strcmp(s.phone_number,s1)==0)
{
f=1;
}

}
    fclose (op);
    return f;
}

void Create(int i)                           //Creating Contact in Contact List 
{  int x,j,n,k=5;
 char b[12];
    gotoxy(91,k++);
  printf("Enter the Persons Details:");
  gotoxy(91,k++);
  printf("Name :");
  scanf(" %[^\n]s",p[i].name);
  if(Verify_by_Name(p[i].name))                                  // Checking name in ContactList
{  gotoxy(91,k++);
    printf("___Contact Alredy Exists with this Name___");
    test=1;
  }  
  
  else
  {
  do
  { x=0;
  gotoxy(91,k++);
  printf("Phone Number :");
  scanf(" %s",p[i].phone_number);
  n=strlen(p[i].phone_number);
    if(n!=10)
    {x=1;
     gotoxy(91,k++);
     printf("Enter 10 Digits Number!!");
  }
  else
  {
  for(j=0;j<strlen(p[i].phone_number);j++)
  {x=0;
   b[j]=p[i].phone_number[j];
   if(isdigit(b[j]))
   {
   }
   else
   {
     gotoxy(91,k++);
     printf("Enter only Numbers");
     x=1;
     break;
   }
  
  }
  }
  if(x==0)
  if(Verify_by_phoneNumber(p[i].phone_number))                         //Checking Phone Number in Contactlist
  {gotoxy(91,k++);
   printf("___Contact Alredy Exists with this Phone Number___");
   gotoxy(91,k++);
   printf("--Do you want to Continue--    Enter 1 to continue 0 to stop");
   gotoxy(91,k++);
   scanf("%d",&x);
   if(x==0)
  test=1;
  }
}while(x!=0);


 if(test!=1)                                                        //Validation for M or F
    { 
   do
  {gotoxy(91,k++);
  printf("Enter M or F");
  gotoxy(91,k++);
    printf("sex :");
  scanf(" %c",&p[i].sex);
  if(p[i].sex=='M'||p[i].sex=='F')
   x=0;
   else
   x=1;
   
  }while(x==1);
  gotoxy(91,k++);
  printf("Fathername :");                                      //Accepting Father Name 
  scanf(" %[^\n]s",p[i].Fathername);
  
  do{x=0;
  gotoxy(91,k++);
  printf("citizenship_number :");                             
  scanf(" %s",p[i].citizenship_number);
  n=strlen(p[i].citizenship_number);
  if(n!=12)                                                      //Validation to Enter 12 Digits 
  {x=1;
   gotoxy(91,k++);
   printf("Enter 12 Digits Number!!");
  }
  else
  {
  for(j=0;j<strlen(p[i].citizenship_number);j++)               
  {x=0;
    b[j]=p[i].citizenship_number[j];
    if(isdigit(b[j]))                                           //Validation to Enter only Number in Citizenship Number
    {
    }
    else
    {gotoxy(91,k++);
     printf("Enter only Numbers");
     x=1;
     break;
    }
  }}
}while(x!=0);

    gotoxy(91,k++);
  printf("email :");                                             //Accepting Email 
  scanf(" %s",p[i].email);
  
  gotoxy(91,k++);
  printf("address :");                                          //Accepting Address  
  scanf(" %[^\n]s",p[i].address);
}
}
}


void DisplayAll()                        // Displaying   All the Conatcts in the Contact List 
{   pb s;
    FILE *op;
   op=fopen("Record.txt","r");
     
    while(fread(&s, sizeof(pb), 1, op))             //Reading the Data From the file 
    {

    printf("\nName :\t%s",s.name);
      printf("\nPhone Number :\t%s",s.phone_number);
      printf("\nsex :\t%c",s.sex);
      printf("\nFathername :\t%s",s.Fathername);
      printf("\ncitizenship_number :\t%s",s.citizenship_number);
      printf("\nemail :\t%s",s.email);
      printf("\naddress :\t%s",s.address);
      printf("\n\n");
}
    fclose (op);
  
}
void Search_by_Name()                       //Searching for Contact By Name
{ char s1[30];
int f=0;
printf("Enter the Person to Search\nName :");
scanf(" %[^\n]s",s1);
 pb s;
    FILE *op;
   op=fopen("Record.txt","r");
     
    while(fread(&s, sizeof(pb), 1, op))
    {  if(strcmp(s1,s.name)==0)
{
    printf("\nName :\t%s",s.name);
      printf("\nPhone Number :\t%s",s.phone_number);
      printf("\nsex :\t%c",s.sex);
      printf("\nFathername :\t%s",s.Fathername);
      printf("\ncitizenship_number :\t%s",s.citizenship_number);
      printf("\nemail :\t%s",s.email);
      printf("\naddress :\t%s",s.address);
      printf("\n\n");
f=1;
}


}
if(f==0)
printf("\n___Person Not Found in Contacts___\n");
    fclose (op);

}
  
void Modify()                                     // Modifying Contact in the Conatct List
{ char s1[30],b[20];
int  f=0,x,n,j,ch;
printf("Enter the Contact Name to Modify");
scanf(" %[^\n]s",s1);
 pb s;
    FILE *op,*op1;
   op=fopen("Record.txt","r");
   op1=fopen("Temp.txt","w"); 
    while(fread(&s, sizeof(pb), 1, op))
    {  if(strcmp(s1,s.name)==0)
    { printf("\nName :\t%s",s.name);
      printf("\nPhone Number :\t%s",s.phone_number);
      printf("\nsex :\t%c",s.sex);
      printf("\nFathername :\t%s",s.Fathername);
      printf("\ncitizenship_number :\t%s",s.citizenship_number);
      printf("\nemail :\t%s",s.email);
      printf("\naddress :\t%s",s.address);
      printf("\n\n");
    
    
  do{
  printf("Enter\n1.To Modify Name\n2.To Modify PhoneNumber\n3. To modify Gender\n4.To Modify FatherName\n5.To Modify CiteZenship Number\n6.To Modify Email \n7.To Modify Address\n8.Save and Exit");
    scanf("%d",&ch);
  fflush(stdin);
     printf("\nEnter the Persons Details: \n");
     switch(ch)
     {
     
     case 1:
  printf("Name :");
  scanf(" %[^\n]s",s.name);
  break;
  case 2:
  do
  { x=0;
  printf("Phone Number :");
  scanf(" %s",s.phone_number);
  n=strlen(s.phone_number);
    if(n!=10)
    {x=1;
     printf("\n__Enter 10 Digits Number!!__\n");
  }
  else
  {
  for(j=0;j<strlen(s.phone_number);j++)
  {x=0;
   b[j]=s.phone_number[j];
   if(isdigit(b[j]))
   {
   }
   else
   {
     printf("\n__Enter only Numbers__\n");
     x=1;
     break;
   }
  
  }
  }
}while(x!=0);
break;
case 3:
  do
  { x=0;
    printf("\nsex :");
  scanf(" %c",&s.sex);
    if(s.sex=='M'||s.sex=='F')
    {
   x=0;
  }
  else
  {printf("\n__Enter M or F!!__\n");
  x=1;
  }
}while(x==1);
break;
case 4:
  printf("\nFathername :");
  scanf(" %[^\n]s""%s",s.Fathername);
  break;
  case 5:
do
{
  printf("\ncitizenship_number :");
  scanf(" %s",s.citizenship_number);
  n=strlen(s.citizenship_number);
  if(n!=12)
  {printf("\nEnter 12 Digits Number !!__\n");
  x=1;
  }
  else
  {
  for(j=0;j<n;j++)               
  {x=0;
    b[j]=s.citizenship_number[j];
    if(isdigit(b[j]))                                           //Validation to Enter only Number in Citizenship Number
    {
    }
    else
    {
     printf("\n__Enter only Numbers__\n");
     x=1;
     break;
    }
  }}
}while(x==1);
break;
case 6:
  printf("\nemail :");
  scanf(" %s",s.email);
  break;
case 7:
  printf("\naddress :");
  scanf(" %[^\n]s",s.address);
  f=1;
  break;
  case 8: exit(1);
}
}while(ch<=8);
  }
fwrite(&s,sizeof(pb),1,op1);
}  
fclose(op);
fclose(op1);
if(f==1)
{op1=fopen("Temp.txt","r");
 op=fopen("Record.txt","w");
 
 while(fread(&s,sizeof(pb),1,op1))
 {fwrite(&s,sizeof(pb),1,op);
   
 }
 
 fclose(op);
fclose(op1); 
printf("Contact Modified Successfully !!!");
}
else
printf("\n___Person Not Found in Contacts___\n");
}


void Delete()                                            // Deleting Contact From Conatct List 
{ char s1[30];
int  f=0;
printf("Enter the Contact Name to Delete\nName:");
scanf(" %[^\n]s",s1);
 pb s;
    FILE *op,*op1;
   op=fopen("Record.txt","r");
   op1=fopen("Temp.txt","w"); 
    while(fread(&s, sizeof(pb), 1, op))
    {  if(strcmp(s1,s.name)==0)
    { 
  f=1;
  }
  else
  {
fwrite(&s,sizeof(pb),1,op1);
}
}  
fclose(op);
fclose(op1);
if(f==1)
{op1=fopen("Temp.txt","r");
 op=fopen("Record.txt","w");
 
 while(fread(&s,sizeof(pb),1,op1))
 {fwrite(&s,sizeof(pb),1,op);
   
 }
 
 fclose(op);
fclose(op1); 
  printf("Contact Deleted Successfully !!!");
}
else
printf("\n___Person Not Found in Contacts___\n");
}

void Search_by_Gender()                     // Searching Contact from Contact List By Gender 
{ char s1;
printf("Enter the M (Male) or F (Female) \nsex :\n");
scanf(" %c",&s1);
int f=0;
 pb s;
    FILE *op;
   op=fopen("Record.txt","r");
     
    while(fread(&s, sizeof(pb), 1, op))
    {  if(s.sex==s1)
{
    printf("\nName :\t%s",s.name);
      printf("\nPhone Number :\t%s",s.phone_number);
      printf("\nsex :\t%c",s.sex);
      printf("\nFathername :\t%s",s.Fathername);
      printf("\ncitizenship_number :\t%s",s.citizenship_number);
      printf("\nemail :\t%s",s.email);
      printf("\naddress :\t%s",s.address);
      printf("\n\n");
f=1;
}

}
if(f==0)
printf("\n___Person Not Found in Contacts___\n");
    fclose (op);

}

void Search_by_FatherName()              // Searching For Contact from Contact List By Father Name 
{ char s1[30];
printf("Enter Father's Name \nFathername :");
scanf(" %[^\n]s",s1);
int f=0;
 pb s;
    FILE *op;
   op=fopen("Record.txt","r");
     
    while(fread(&s, sizeof(pb), 1, op))
    {  if(strcmp(s1,s.Fathername)==0)
{
    printf("\nName :\t%s",s.name);
      printf("\nPhone Number :\t%s",s.phone_number);
      printf("\nsex :\t%c",s.sex);
      printf("\nFathername :\t%s",s.Fathername);
      printf("\ncitizenship_number :\t%s",s.citizenship_number);
      printf("\nemail :\t%s",s.email);
      printf("\naddress :\t%s",s.address);
      printf("\n\n");
f=1;
}

}
if(f==0)
printf("\n___Person Not Found in Contacts___\n");
    fclose (op);
}

void Search_by_phoneNumber()             // Searching for Contact from Contact List By PhoneNumber
{ 
char s1[20];
printf("Enter the Phone Number \nPhone Number :");
scanf(" %s",&s1);
int f=0;
 pb s;
    FILE *op;
   op=fopen("Record.txt","r");
     
    while(fread(&s, sizeof(pb), 1, op))
    {  if(strcmp(s.phone_number,s1)==0)
{
    printf("\nName :\t%s",s.name);
      printf("\nPhone Number :\t%s",s.phone_number);
      printf("\nsex :\t%c",s.sex);
      printf("\nFathername :\t%s",s.Fathername);
      printf("\ncitizenship_number :\t%s",s.citizenship_number);
      printf("\nemail :\t%s",s.email);
      printf("\naddress :\t%s",s.address);
      printf("\n\n");
f=1;
}

}
if(f==0)
printf("\n___Person Not Found in Contacts___\n");
    fclose (op);
}

void Search_by_citizenship_number()             // Searching for Contact from Contact List by Citizenship Number 
{ 
char s1[20];
printf("Enter the Citizenship Number \ncitizenship_number :");
scanf(" %s",&s1);
int f=0;
 pb s;
    FILE *op;
   op=fopen("Record.txt","r");
     
    while(fread(&s, sizeof(pb), 1, op))
    {  if(strcmp(s.citizenship_number,s1)==0)
{
    printf("\nName :\t%s",s.name);
      printf("\nPhone Number :\t%s",s.phone_number);
      printf("\nsex :\t%c",s.sex);
      printf("\nFathername :\t%s",s.Fathername);
      printf("\ncitizenship_number :\t%s",s.citizenship_number);
      printf("\nemail :\t%s",s.email);
      printf("\naddress :\t%s",s.address);
      printf("\n\n");
f=1;
}

}
if(f==0)
printf("\n___Person Not Found in Contacts___\n");
    fclose (op);
}

void Search_by_Address()                  //Searching for Contact from Contact List By Address
{ char s1[30];
printf("Enter the Address ");
scanf(" %[^\n]s",&s1);
int f=0;
 pb s;
    FILE *op;
   op=fopen("Record.txt","r");
     
    while(fread(&s, sizeof(pb), 1, op))
    {  if(strcmp(s1,s.address)==0)
{
    printf("\nName :\t%s",s.name);
      printf("\nPhone Number :\t%s",s.phone_number);
      printf("\nsex :\t%c",s.sex);
      printf("\nFathername :\t%s",s.Fathername);
      printf("\ncitizenship_number :\t%s",s.citizenship_number);
      printf("\nemail :\t%s",s.email);
      printf("\naddress :\t%s",s.address);
      printf("\n\n");
f=1;
}

}
if(f==0)
printf("\n___Person Not Found in Contacts___\n");
    fclose (op);
}

void Search_by_Email()                      // Searching for Contact from Contact List By Email
{ char s1[30];
printf("Enter the  Email ");
scanf(" %[^\n]s",&s1);
int f=0;
 pb s;
    FILE *op;
   op=fopen("Record.txt","r");
     
    while(fread(&s, sizeof(pb), 1, op))
    {  if(strcmp(s1,s.email)==0)
{
    printf("\nName :\t%s",s.name);
      printf("\nPhone Number :\t%s",s.phone_number);
      printf("\nsex :\t%c",s.sex);
      printf("\nFathername :\t%s",s.Fathername);
      printf("\ncitizenship_number :\t%s",s.citizenship_number);
      printf("\nemail :\t%s",s.email);
      printf("\naddress :\t%s",s.address);
      printf("\n\n");
f=1;
}

}
if(f==0)
printf("\n___Person Not Found in Contacts___\n");
    fclose (op);
}

void sort()                            // Code for Sorting Data in File 
{ int i,j;
pb *s,s1;
FILE *fp;
fp=fopen("Record.txt","r");      
fseek(fp,0,SEEK_END);                  //fseek() used to move file pointer associated with a given file to a specific position.
int n=ftell(fp)/sizeof(pb);          //ftell() returns the current file position  
s=(pb*)calloc(n,sizeof(pb));        //used to allocate a specified amount of memory and then initialize it to zero
rewind(fp);                          //sets the file position to the beginning of the file 
for(i=0;i<n;i++)
fread(&s[i],sizeof(pb),1,fp);
fclose(fp);

for(i=1;i<n;i++)
{for(j=0;j<n-i;j++)
{
 if(strcmp(s[j].name,s[j+1].name)>0)
   {
       s1=s[j];
       s[j]=s[j+1];
       s[j+1]=s1;
   }
}
}
fp=fopen("Record.txt","w");

for(i=0;i<n;i++)
{
      fwrite(&s[i],sizeof(pb),1,fp);
}
fclose(fp);
}
