#include<iostream.h>
#include<conio.h>
#include<stdlib.h>
#include<graphics.h>
int i=1,j=1;
long start_std_id=110000;
long start_stf_id=120000;
void student_available_seat(int);
void student_admit_particular_id(int);
class staff
{
protected:
long stf_id;
char name[10];
int  salary;
int  class_name;
public :
void staff_data();
void staff_display();
}stf[10];
void staff::staff_data()
{
//staff_id=stf_id+j;
stf_id=++start_stf_id;

cout<<"enter staff_name:";
cin>>name;
cout<<"enter salary:";
cin>>salary;
cout<<"enter class_name in integer:";
cin>>class_name;
}
void staff::staff_display()
{
cout<<endl<<"staff_id:";
cout<<stf_id<<endl;
cout<<"staff_name:";
cout<<name<<endl;
cout<<"salary:";
cout<<salary<<endl;
cout<<"class_name:";
cout<<class_name<<endl;
}

class fees
{
public:
int fees_status;
int month_num;
int tution_fees;
int exam_fees;
int transport_fees;
}fees_month[12][4];

class student:public fees
{
public:
long std_id;
char student_name[20];
char parent_name[20];
int  class_name;
char address[50];
char  mobile_num[11];
char addmission_date[10];
public:
void student_data();
void student_display();
void student_fees_pay(int );
void student_fees_status(int);
void student_delete();
void student_fees_delete(int);
void student_data_particular_id(int);
void student_upgrade(int);

}std[10];
void student::student_upgrade(int m)
{

if(std[m].student_name[0]!='\0')
std[m].class_name+=1;
}

void student::student_data()
{
int cname;
std_id=++start_std_id;
int m=std_id-110000;
if(std[m].student_name[0]=='\0')
{
cout<<"enter student_name(length[20]):";
cin>>std[m].student_name;

cout<<"enter class_name in integer(0-12):";
cin>>cname;
if(cname>=0&&cname<=12)
std[m].class_name=cname;
else
cout<<"error in class_name"<<endl;


cout<<"enter parent_name(length[20]):";
cin>>std[m].parent_name;
cout<<"enter mobile_number(length[10]):";
cin>>std[m].mobile_num;
cout<<"enter addmission_date(format[dd/mm/yy]):";
cin>>std[m].addmission_date;
cout<<"enter address(length[50]):";
cin>>std[m].address;
}
}
void student::student_display()
{

cout<<endl<<"student_id:";
cout<<std_id<<endl;
cout<<"student_name:";
cout<<student_name<<endl;
cout<<"class_name:";
cout<<class_name<<endl;
cout<<"parent_name(length[20]):";
cout<<parent_name<<endl;
cout<<"mobile_number(length[10]):";
cout<<mobile_num<<endl;
cout<<"addmission_date(format[dd/mm/yy]):";
cout<<addmission_date<<endl;
cout<<"address(length[50]):";
cout<<address<<endl;
}


void student::student_fees_pay(int a)
{
if(std[a].student_name[0]!='\0')
{
cout<<"jan-dec is equivalent to 1-12:"<<endl;
cout<<"enter digit(1-12):";
cin>>month_num;
cout<<"tution_fees:";
cin>>fees_month[month_num][a].tution_fees;
fees_month[month_num][a].fees_status=1;
student_fees_status(a);
}
else
cout<<"student is not admitted at:"<<a+110000<<endl;
}

void student::student_fees_status(int a)
{
for(int m=1;m<=12;m++)
{
if(fees_month[m][a].fees_status==1)
cout<<"fees of month "<<m<<" is paid......"<<endl;
else
cout<<"fees of month "<<m<<" is due"<<endl;
}
}
void student::student_delete()
{
//std_id=NULL;
for(int m=0;m<20;m++)
{
student_name[m]='\0';
parent_name[m]='\0';
}
class_name=NULL;
for(m=0;m<50;m++)
address[i]='\0';
for(m=0;m<11;m++)
mobile_num[m]='\0';
for(m=0;m<10;m++)
addmission_date[m]='\0';
}
void student::student_fees_delete(int a)
{
for(int i=1;i<=12;i++)
{
fees_month[i][a].fees_status=NULL;
fees_month[i][a].tution_fees=NULL;
fees_month[i][a].exam_fees=NULL;
fees_month[i][a].transport_fees=NULL;
}
}
void student_available_seat(int a)
{
for(int m=1;m<=a;m++)
{
if(std[m].student_name[0]=='\0')
cout<<"std_id: "<<m+110000<<endl;
}
}
void student_admit_particular_id(int a)
{
if(std[a].student_name[0]=='\0')
{
std[a].student_data_particular_id(a);
std[a].student_display();
}
else
cout<<"student is already admitted at this std_id"<<endl;
}
void student::student_data_particular_id(int a)
{
int cname;
std_id=110000+a;
cout<<"enter student_name(length[20]):";
cin>>student_name;

cout<<"enter class_name in integer(0-12):";
cin>>cname;
if(cname>=0&&cname<=12)
std[a].class_name=cname;
else
cout<<"error in class name"<<endl;

cout<<"enter parent_name(length[20]):";
cin>>parent_name;
cout<<"enter mobile_number(length[10]):";
cin>>mobile_num;
cout<<"enter addmission_date(format[dd/mm/yy]):";
cin>>addmission_date;
cout<<"enter address(length[50]):";
cin>>address;
}

void main()
{
int gd=DETECT,gm;
long n,std_id,stf_id;
int m;
long id;
initgraph(&gd,&gm,"C:\\TurboC3\\BGI");
setbkcolor(3);
x:
cleardevice();
cout<<"=============================================="<<endl;
cout<<"                  MENU                        "<<endl;
cout<<"=============================================="<<endl;
cout<<"          Made by saurabh_gupta               "<<endl;
cout<<"     enter [1] for adding new student         "<<endl;
cout<<"     enter [2] for staff                      "<<endl;
cout<<"     enter [3] to get information             "<<endl;
cout<<"     enter [4] for fees payment               "<<endl;
cout<<"     enter [5] for fees status                "<<endl;
cout<<"=============================================="<<endl;
cout<<"     enter [-1] for deleting student          "<<endl;
cout<<"     enter [-2] to see available seat         "<<endl;
cout<<"     enter [-3] to admit student at a particular std_id:"<<endl;
cout<<"     enter [-4] to upgrade students in next class:    "<<endl;
cout<<"     enter [0]  to exit                       "<<endl;
cout<<"=============================================="<<endl;
cout<<"     start_std_id:"<<start_std_id+1<<" start_staff_id"<<start_stf_id+1<<endl;
cout<<"==============================================="<<endl<<"::";
cin>>n;

switch(n)
{
case 1:

std[i].student_data();
//cleardevice();
std[i].student_display();
i++;
cout<<"enter [0] to go back:";
cin>>m;
if(m==0)
goto x;
break;


case 2:

stf[j].staff_data();
cleardevice();
stf[j].staff_display();
j++;
cout<<endl<<"enter [0] to go back:";
cin>>m;
if(m==0)
goto x;
break;

case 3:

cout<<"enter id:";
cin>>id;
if(id>110000&&id<120000)
{
m=id-110000;
std[m].student_display();
}
else
{
m=id-120000;
stf[m].staff_display();
}
cout<<endl<<"enter [0] to go back:";
cin>>m;
if(m==0)
goto x;

case 4:

cout<<"enter id:";
cin>>id;
if(id>110000&&id<120000)
{
m=id-110000;
cout<<"student_name:"<<std[m].student_name<<endl;
cout<<"class_name:"<<std[m].class_name<<endl;
cout<<"parent_name:"<<std[m].parent_name<<endl;
std[m].student_fees_pay(m);
}

cout<<endl<<"enter [0] to go back:";
cin>>m;
if(m==0)
goto x;

case 5:

cout<<"enter id:";
cin>>id;
if(id>110000&&id<120000)
{
m=id-110000;
cout<<"student_name:"<<std[m].student_name<<endl;
cout<<"class_name:"<<std[m].class_name<<endl;
cout<<"parent_name:"<<std[m].parent_name<<endl;
std[m].student_fees_status(m);

cout<<endl<<"enter [0] to go back:";
cin>>m;
if(m==0)
goto x;
case -1:

cout<<"enter std_id:";
cin>>id;
if(id>110000&&id<120000)
{
m=id-110000;
std[m].student_delete();
std[m].student_fees_delete(m);
cout<<"student std_id:"<<m+110000<<" is deleted"<<endl;
cout<<"std_id:"<<m+110000<<" is now available for another student"<<endl;
cout<<"student availabel seat is updated:"<<endl;

std[m].student_display();
std[m].student_fees_status(i);
}
cout<<endl<<"enter [0] to go back:";
cin>>m;
if(m==0)
goto x;


case -2:

cout<<"enter number of seats to see availability:";
cin>>m;
student_available_seat(m);

cout<<endl<<"enter [0] to go back:";
cin>>m;
if(m==0)
goto x;

case -3:

cout<<"enter std_id:";
cin>>id;
m=id-110000;
student_admit_particular_id(m);
cout<<endl<<"enter [0] to go back:";
cin>>m;
if(m==0)
goto x;

case -4:

for(m=1;m<400;m++)
std[m].student_upgrade(m);
cout<<endl<<"enter [0] to go back:";
cin>>m;
if(m==0)
goto x;

}
}
getch();
}


