
NQueens Algorithm:
#include<stdio.h>
#include<conio.h>
void nqueens(int);
int place(int[],int);
void prin(int n,int x[])
{
char c[10][10];
int i,j;
for(i=1;i<=n;i++)
{
for(j=1;j<=n;j++)
{
c[i][j]='X';
}
}
for(i=1;i<=n;i++)
{
c[i][x[i]]='Q';
}
for(i=1;i<=n;i++)
{
for(j=1;j<=n;j++)
{
printf("%c",c[i][j]);
}
printf("\n");
}
}
void main()
{
int n;
printf("\nenter the no of queens:\t");
scanf("%d",&n);
if(n==2 || n==3)
printf("no solution for %d queens\n",n);
else
nqueens(n);
}
void nqueens(int n)
{
int k,x[10],count=0;
k=1;
x[k]=0;
while(k!=0)
{
x[k]++;
while(place(x,k)==1&&x[k]<=n)
{
x[k]++;
}
if(x[k]<=n)
{
if(k==n)
{
printf("\nsolution %d is\n",++count);
for(k=1;k<=n;k++)
printf("%d----->%d\n",k,x[k]);
printf("\n solution in the form of chess board\n");
prin(n,x);
}
else
{
k++;
x[k]=0;
}
}
else
{
k--;
}
}
}
int place(int x[],int k)
{
int i;
for(i=1;i<=k-1;i++)
{
if(i-x[i]==k-x[k]||i+x[i]==k+x[k]||x[i]==x[k])
{
return 1;
}
