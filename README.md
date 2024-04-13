IMPLEMENTATION OF SJF SCHEDULING ALGORITHM 
AIM
To write a C program to implement shortest job first (non-pre-emptive) scheduling algorithm.
DESCRIPTION:
For SJF scheduling algorithm, read the number of processes/jobs in the system, their CPU burst times. Arrange all the jobs in order with respect to their burst times. There may be two jobs in queue with the same execution time, and then FCFS approach is to be performed. Each process will be executed according to the length of its burst time. Then calculate the waiting time and turnaround time of each of the processes accordingly.
ALGORITHM:
Step 1: Start the program.
Step 2: Get the input process and their burst time. Step 3: Sort the processes based on burst time.
Step 4: Compute the waiting time and turnaround time for each process. Step 5: Calculate the average waiting time and average turnaround time. Step 6: Print the details about all the processes.
Step 7: Stop the program.
PROGRAM:
#include<stdio.h> void main()
{
int i,j,n,bt[30],at[30],st[30],ft[30],wat[30],wt[30],temp,temp1,tot,tt[30]; float awt, att;
int p[15];
wat[1]=0;
printf("ENTER THE NO.OF PROCESS");
scanf("%d",&n);
printf("\nENTER THE PROCESS NUMBER,BURST TIME AND ARRIVAL TIME");
for(i=1;i<=n;i++)
{
scanf("%d\t %d\t %d",&p[i],&bt[i],&at[i]);
}
printf("\nPROCESS\tBURSTTIME\tARRIVALTIME");
for(i=1;i<=n;i++)
{
printf("\np%d\t%d\t\t%d",p[i],bt[i],at[i]);
}
for(i=1;i<=n;i++)
{
for(j=i+1;j<=n;j++)
{
if(bt[i]>bt[j])
{
temp=bt[i]; bt[i]=bt[j]; bt[j]=temp; temp1=p[i]; p[i]=p[j]; p[j]=temp1;
}
}
if(i==1)
{
 }
else
{st[1]=0;
ft[1]=bt[1]; wt[1]=0;
st[i]=ft[i-1];
ft[i]=st[i]+bt[i];
wt[i]=st[i];
}
}
printf("\n\n\t\t\tGANTT CHART\n"); printf("\n	\n");
for(i=1;i<=n;i++)
printf("|\tp%d\t",p[i]); printf("|\t\n");
printf("\n	\n");
printf("\n"); for(i=1;i<=n;i++)
printf("%d \t\t",wt[i]);
printf("%d",wt[n]+bt[n]); printf("\n	\n"); for(i=2;i<=n;i++)
wat[i]=wt[i]-at[i]; for(i=1;i<=n;i++)
tt[i]=wat[i]+bt[i]-at[i]; printf("\nPROCESS\tBURSTTIME\tARRIVALTIME\tWAITINGTIME\tT URNAROUNDTI ME\n");
for(i=1;i<=n;i++)
{
printf("\np%d %5d %15d %15d %15d",p[i],bt[i],at[i],wat[i],tt[i]);
}
for(i=1,tot=0;i<=n;i++) tot+=wt[i];
awt=(float)tot/n;
printf("\n\n\n AVERAGE WAITING TIME=%f",awt); for(i=1,tot=0;i<=n;i++)
tot+=tt[i]; att=(float)tot/n;
printf("\n\n AVERAGE TURNAROUND TIME=%f",att);
}


OUTPUT:
enter the no.of process3
enter the process number,burst time and arrival time 1 8 1
2 5 1
3 3 1

PROCESS	BURSTTIME	ARRIVALTIME	WAITINGTIME	TURNAROUNDTIME
p3	3	1	0	2
p2	5	1	2	6
p1	8	1	7	14
AVERAGE WAITING TIME=3.666667 AVERAGE TURNAROUND TIME=7.333333
RESULT:
The SJF scheduling algorithm has been implemented in C.
