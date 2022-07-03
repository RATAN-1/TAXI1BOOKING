#include<stdio.h>
#include<string.h>
#include<time.h>
#include<math.h>
#include<stdlib.h>
#define c 23
#define b 11
int i,x,u,otp;
char ch;
struct user
{
    int start,e;
    long int num;
    long long int phn;
    char n[20],location[50],name[100],lname[100],destination[150];
}a;
struct taxi
{
    float km,co,tc,tax;
}t;
int inputotp()
{
    srand(time(0));
    otp=rand()%9999;
    return otp;

}
void input()
{
    printf("Enter your first name :");
    fflush(stdin);
    gets(a.name);
    printf("\nEnter last name : ");
    fflush(stdin);
    gets(a.lname);
    printf("\nEnter phone number : ");
    scanf("%lld",&a.phn);
    printf("\nEnter pickup location : ");
    fflush(stdin);
    gets(a.location);
    printf("\nEnter the destination : ");
    fflush(stdin);
    gets(a.destination);
}
void display()
{
    for(i=1;i<=20;i++) printf("x");
    printf("BILL DETAILS");
    for(i=1;i<=20;i++) printf("x");

    printf("\nNAME\t\t:\t%s",strcat(strcat(a.lname," "),a.name));
    printf("\nPhone Number\t:\t%lld",a.phn);
    printf("\nLocation\t:\t%s",a.location);
    printf("\nDestination\t:\t%s\n",a.destination);
    for(i=1;i<=52;i++) printf("x");
    printf("\nBase Fare\t:\t%.3f",t.co);
    printf("\nTax\t\t:\t%.3f",t.tax);
    printf("\nTotal Payable\t:\t%.3f",t.tc);
}
int main()
{
    input();
    do
    {printf("\nPress '1' to book a car/ '2' to book a bike : ");
     scanf("%d",&a.num);
     if(a.num==1)
     {
        printf("\nCost per km is RS.23");

     }
     else if (a.num==2)
     {
        printf("\nCost per km is RS.11");
     }
     else
     {
        printf("\ninvalid");
     }
      if(a.num==1 || a.num==2) break;
    }while(1);

    if(a.num==1)
    {
        printf("\nYour Car taxi AP39LP8143 Reaches you in 5 mins");
    }
    else printf("\nYour Bike taxi AP39LP8141 Reaches you in 5 mins");

    x=inputotp();
     printf("\n End ride otp: %d",x);
    do
    {

     printf("\tEnter End ride otp to terminate the the ride : ");
     scanf("%d",&a.e);
     if(a.e==x&&a.num==1)
     {
        printf("\nRide completed successfully");
        printf("\nEnter no.of Kilometers travelled : ");
        scanf("%f",&t.km);
        t.co=t.km*c;
        t.tax=t.co*5/100;
        t.tc=t.co+t.tax;
     }
     else if(a.e==x&&a.num==2)
     {
        printf("\nRide completed successfully");
        printf("\nEnter no.of Kilometers travelled :");
        scanf("%f",&t.km);
        t.co=t.km*b;
        t.tax=t.co*5/100;
        t.tc=t.co+t.tax;
     }
     else printf("invalid");
     if(a.e==x) break;
    } while(1);
    display();


}

