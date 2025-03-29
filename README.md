##8
 
 import java.util.Scanner;
 public class TSP
 {
public static void main(String[] args)
{
int c[][]=new int[10][10], tour[]=new int[10];
Scanner in = new Scanner(System.in);
int i, j,cost;
System.out.println("**** TSP DYNAMIC PROGRAMMING*****");
System.out.println("Enter the number of cities: ");
int n = in.nextInt();
if(n==1)
{
System.out.println("Path is not possible");
System.exit(0);
}
System.out.println("Enter the cost matrix");
for(i=1;i<=n;i++)
for(j=1;j<=n;j++)
c[i][j] = in.nextInt();
System.out.println("The entered cost matrix is");
for(i=1;i<=n;i++)
{
for(j=1;j<=n;j++)
{
System.out.print(c[i][j]+"\t");
}
System.out.println();
}
for(i=1;i<=n;i++)
tour[i]=i;
cost = tspdp(c, tour, 1, n);
System.out.println("The accurate path is");
for(i=1;i<=n;i++)
System.out.print(tour[i]+"->");
System.out.println("1");
System.out.println("The accurate mincost is "+cost);
System.out.println("******* ************* ***************");
}
static int tspdp(int c[][], int tour[], int start, int n)
{
int mintour[]=new int[10], temp[]=new int[10], mincost=999, ccost, i, j, k;
if(start == n-1)
{
return (c[tour[n-1]][tour[n]] + c[tour[n]][1]);
}
for(i=start+1; i<=n; i++)
{
for(j=1; j<=n; j++)
temp[j] = tour[j];
temp[start+1] = tour[i];
temp[i] = tour[start+1];
if((c[tour[start]][tour[i]]+(ccost=tspdp(c,temp,start+1,n)))<mincost)
{
mincost = c[tour[start]][tour[i]] + ccost;
for(k=1; k<=n; k++)
 mintour[k] = temp[k];
}
}
for(i=1; i<=n; i++)
tour[i] = mintour[i];
return mincost;
}
}



##9
import java.util.Scanner;
 import java.io.*;
 class operation
 {
int x[]=new int[20];
int count=0;
public boolean place(int row,int column)
{
int i;
for(i=1;i<=row-1;i++)
{
if(x[i] == column)
return false;
else
if (Math.abs(x[i]-column)== Math.abs(i-row))
return false;
}
return true;
}
public void Queen(int row,int n)
{
int column;
for(column=1;column<=n;column++)
{
if(place(row,column))
{
x[row] = column;
if(row==n)
{
print_board(n);
}
else
Queen(row+1,n);
}
}
}
public void print_board(int n)
{
int i;
System.out.println("\n\nSolution :"+(++count));
for(i=1;i<=n;i++)
{
System.out.print(" " +i);
}
for(i=1;i<=n;i++)
{
System.out.print("\n\n"+i);
for(int j=1;j<=n;j++)
{
if(x[i]==j)
System.out.print(" Q");
else
System.out.print(" -");
}
}
}
}
class NQueens
{
public static void main (String args[] )throws IOException
{
 Scanner scanner = new Scanner(System.in);
 System.out.print("Enter the size of the chessboard (N): ");
 int n = scanner.nextInt();
 if(n==2 || n==3)
 {
 System.out.print("Not Possible");
}
scanner.close();
 operation op=new operation();
 op.Queen(1,n);
}
}
