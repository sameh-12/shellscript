
SHELL LAB PROGRAMS

QUESTIONS:













    1. Write programs using the following system calls of UNIX operating system: fork, exec, getpid, exit, wait, close, stat, opendir, readdir

AIM: 
To write programs using the following system calls of UNIX operating system: fork, exec, getpid, exit, wait, close, stat, opendir, readdir

ALGORITHM:
STEP 1: Start Shell Online Compiler
STEP 2: Include necessary header files 
STEP 3: Create main() class and declare the required variables
STEP 4: Use fork() system call to create process and getpid() to get the current process ID
STEP 5: If ‘a’ is 0 then display the particular content, if ‘a’ is not equal to 0 then display the particular content or display Error
STEP 6: Output will be displayed and stop the program

PROGRAM:
#include <stdio.h>
int main()
{
    int a;
    a=fork();
    printf("\n\n\nParent is %d",getpid());
    if(a==0)
    {
        printf("\n\tHELLO FROM CHILD PROCESS \n\t");
        printf("CHILD ID is %d",getpid());
    }
    else if(a!=0)
    {
        printf("\n\tHELLO FROM PARENT PROCESS %d",getpid());
        printf("\n\tHELLO FROM CHILD PROCESS %d\n",a);
    }
    else
    {
        printf("ERROR IN CREATION");
    }
}

OUTPUT:



    2. Write programs using the I/O system calls of UNIX operating system (open, read, write, etc) 

AIM: 
To write programs using the I/O system calls of UNIX operating system (open, read, write, etc) 

ALGORITHM:
STEP 1: Start Shell Online Compiler
STEP 2: Include necessary header files
STEP 3: Create main() class and declare the required variables
STEP 4: Create a file having some values and open the file using the path of the file
STEP 5: Using write() the content in the file can be altered 
STEP 6: Search the word ‘Hello World’ within the file
STEP 7: Display ‘Hello World’ and close the file using close()

PROGRAM:
#include<stdio.h> 
#include<string.h> 
#include<unistd.h> 
#include<fcntl.h> 
  
int main (void) 
{ 
    int fd[2]; 
    char buf1[12] = "hello world"; 
    char buf2[12]; 
  
    fd[0] = open("D:\Lab Prgms\foobar.txt", O_RDWR);         
    fd[1] = open("D:\Lab Prgms\foobar.txt", O_RDWR); 
      
    write(fd[0], buf1, strlen(buf1));         
    write(1, buf2, read(fd[1], buf2, 12)); 
  
    close(fd[0]); 
    close(fd[1]); 
  
    return 0; 
}

OUTPUT:





    3. Write C programs to simulate UNIX commands like ls, grep, etc

AIM: 
To write C programs to simulate UNIX commands like ls, grep, etc

ALGORITHM:
STEP 1: Start Shell Online Compiler
STEP 2: Include necessary header files
STEP 3: Create main() class and declare the required variables
STEP 4: Using the grep() filter the given file for particular pattern of characters
STEP 5: All the lines that contain that pattern will be displayed
STEP 6: The command is() is used to list the names of files in a particular Unix dictionary
STEP 7: Output will be displayed and stop the program

PROGRAM:
#include <iostream>
int main() {
$ cc -o grep.out grep.c;
$ ./grep.out printf cat.c
printf("\nArgument not matched\n");
printf("\n\nFILE CONTENTS ARE: ");
printf("\n-----------------------------\n");
printf("\n");
$ cc -o ls.out ls.c
$ ./ls.out
    return 0;
}

OUTPUT:

    4. Given the list of processes, their CPU burst times and arrival times, display/print the Gantt chart for FCFS and SJF. For each of the scheduling policies, compute and print the average waiting time and average turnaround time. 

AIM: 
To find in the given list of processes, their CPU burst times and arrival times, display/print the Gantt chart for FCFS and SJF. For each of the scheduling policies, compute and print the average waiting time and average turnaround time

ALGORITHM:
STEP 1: Start Shell Online Compiler
STEP 2: Include necessary header files and declare the array size
STEP 3: Create main() class and declare the required variables
STEP 4: Get the number of processes to be inserted and get the value
STEP 5: Start with the first process from its initial position 
STEP 6: Let the other process be in a queue
STEP 7: Output will be displayed and stop the program

PROGRAM:
#include <iostream>
using namespace std;
void findWaitingTime(int processes[], int n,
	int bt[], int wt[])
{
	wt[0] = 0;

	for (int i = 1; i < n ; i++ )
		wt[i] = bt[i-1] + wt[i-1] ;
}
void findTurnAroundTime( int processes[], int n,
	int bt[], int wt[], int tat[])
{
	for (int i = 0; i < n ; i++)
		tat[i] = bt[i] + wt[i];
}

void findavgTime( int processes[], int n, int bt[])
{
	int wt[n], tat[n], total_wt = 0, total_tat = 0;

	findWaitingTime(processes, n, bt, wt);
	findTurnAroundTime(processes, n, bt, wt, tat);
	cout << "Processes "<< " Burst time "
		<< " Waiting time " << " Turn around time\n";
	for (int i=0; i<n; i++)
	{
		total_wt = total_wt + wt[i];
		total_tat = total_tat + tat[i];
		cout << " " << i+1 << "\t\t" << bt[i] <<"\t "
			<< wt[i] <<"\t\t " << tat[i] <<endl;
	}

	cout << "Average waiting time = "
		<< (float)total_wt / (float)n;
	cout << "\nAverage turn around time = "
		<< (float)total_tat / (float)n;
}
int main()
{
	int processes[] = { 1, 2, 3};
	int n = sizeof processes / sizeof processes[0];
	int burst_time[] = {10, 5, 8};
	findavgTime(processes, n, burst_time);
	return 0;
}

OUTPUT:


    5. Given the list of processes, their CPU burst times and arrival times, display/print the Gantt chart for Priority and Round robin. For each of the scheduling policies, compute and print the average waiting time and average turnaround time.

AIM: 
To find in the given list of processes, their CPU burst times and arrival times, display/print the Gantt chart for Priority and Round robin. For each of the scheduling policies, compute and print the average waiting time and average turnaround time

ALGORITHM:
STEP 1: Start Shell Online Compiler
STEP 2: Include necessary header files and declare the array size
STEP 3: Create main() class and declare the required variables
STEP 4: Get the number of processes to be inserted and get the value
STEP 5: Start the first process from its initial position
STEP 6: Let other process in circle in queue (Round Robin & Priority Method)
STEP 7: Calculate the total number of burst time
STEP 8: Output will be displayed and stop the program

PROGRAM:
#include <iostream>
using namespace std;
void findWaitingTime(int processes[], int n,
int bt[], int wt[], int quantum)
{
	int rem_bt[n];
	for (int i = 0 ; i < n ; i++)
		rem_bt[i] = bt[i];
	int t = 0; // Current time
	while (1)
	{
		bool done = true;
		for (int i = 0 ; i < n; i++)
		{
	        if (rem_bt[i] > 0)
			{
				done = false; // There is a pending process
				if (rem_bt[i] > quantum)
				{
				t += quantum;
					rem_bt[i] -= quantum;
				}
				else
				{
					t = t + rem_bt[i];
					wt[i] = t - bt[i];
					rem_bt[i] = 0;
				}
			}
		}
		if (done == true)
		break;
	}
}
void findTurnAroundTime(int processes[], int n,
int bt[], int wt[], int tat[])
{
	for (int i = 0; i < n ; i++)
		tat[i] = bt[i] + wt[i];
}
void findavgTime(int processes[], int n, int bt[],
int quantum)
{
	int wt[n], tat[n], total_wt = 0, total_tat = 0;
	findWaitingTime(processes, n, bt, wt, quantum);
	findTurnAroundTime(processes, n, bt, wt, tat);
	cout << "Processes "<< " Burst time "
	<< " Waiting time " << " Turn around time\n";
	for (int i=0; i<n; i++)
	{
		total_wt = total_wt + wt[i];
		total_tat = total_tat + tat[i];
		cout << " " << i+1 << "\t\t" << bt[i] <<"\t "
		<< wt[i] <<"\t\t " << tat[i] <<endl;
	}

	cout << "Average waiting time = "
	<< (float)total_wt / (float)n;
	cout << "\nAverage turn around time = "
	<< (float)total_tat / (float)n;
}
int main()
{
	int processes[] = { 1, 2, 3};
	int n = sizeof processes / sizeof processes[0];
	int burst_time[] = {10, 5, 8};
	int quantum = 2;
	findavgTime(processes, n, burst_time, quantum);
	return 0;
}
OUTPUT:

 
    6. Developing Application using Inter Process communication (using shared memory, pipes or message queues) 

AIM: 
To find the developing Application using Inter Process communication (using shared memory, pipes or message queues)

ALGORITHM:
STEP 1: Start Shell Online Compiler
STEP 2: Include necessary header files
STEP 3: Create main() class and declare the required variables
STEP 4: Create the message queue using the msgget() system call
STEP 5: Output will be displayed and stop the program

PROGRAM:
#include <stdio.h>
#include <sys/ipc.h>
#include <sys/msg.h>
#define MAX 10
struct mesg_buffer {
	long mesg_type;
	char mesg_text[100];
} message;
int main()
{
	key_t key;
	int msgid;
	key = ftok("progfile", 65);
	msgid = msgget(key, 0666 | IPC_CREAT);
	message.mesg_type = 1;
	printf("Write Data : ");
	fgets(message.mesg_text,MAX,stdin);
	msgsnd(msgid, &message, sizeof(message), 0);
	printf("Data send is : %s \n", message.mesg_text);
	return 0;
}

OUTPUT:


    7. Implement the Producer – Consumer problem using semaphores (using UNIX system calls). 

AIM: 
To Implement the Producer – Consumer problem using semaphores (using UNIX system calls). 

ALGORITHM:
STEP 1: Start Shell Online Compiler
STEP 2: Include necessary header files
STEP 3: Create main() class and declare the required variables
STEP 4: The producer has to generate a piece of data and included it into the buffer and start again 
STEP 5: The same processor at the same time the data will be removed from the buffer, one piece at a time
STEP 6: Output will be displayed and stop the program 

PROGRAM:
#include<stdio.h>
int mutex=1,full=0,empty=3,x=0;
main()
{
   int n;
   void producer();
   void consumer();
   int wait(int);
   int signal(int);
   printf("\n1.Producer\n2.Consumer\n3.Exit");
   while(1)
   {
      printf("\n Enter your choice:");
      scanf("%d",&n);
      switch(n)
      {
         case 1:
                 if((mutex==1)&&(empty!=0))
                    producer();
                 else
                    printf("Buffer is full");
     break;
         case 2:
             if((mutex==1)&&(full!=0))
    consumer();
    else
        printf("Buffer is empty");
       break;
         case 3:
    exit(0);
    break;
      }
   }
}
int wait(int s)
{
   return (--s);
}
int signal(int s)
{
   return(++s);
}
void producer()
{
   mutex=wait(mutex);
   full=signal(full);
   empty=wait(empty);
   x++;
   printf("\n Producer produces the item %d",x);
   mutex=signal(mutex);
}
void consumer()
{
   mutex=wait(mutex);
   full=wait(full);
   empty=signal(empty);
   printf("\n Consumer consumes item %d",x);
   x--;
   mutex=signal(mutex);
}

OUTPUT:


    8. Implement some memory management schemes – I 

AIM: 
To implement some memory management schemes – I 

ALGORITHM:
STEP 1: Start Shell Online Compiler
STEP 2: Include necessary header files
STEP 3: Create main() class and declare the required variables
STEP 4: Get the input from the user 
STEP 5: If the values are invalid, it will display “Invalid Page”
STEP 6: Output will be displayed
STEP 7: Stop the program

PROGRAM:
#include <stdio.h>
#include <unistd.h>
void main()
{
	int b[20],n,i,pa,p,a,d,pg;
    	printf("\nProgram For Paging");
    	printf("\nEnter the number of pages: ");
   	scanf("%d",&n);
   	printf("\nEnter the base address: ");
    	for(i=0;i<n;i++)
    	{
	    	scanf("%d",&b[i]);
    	}
    	printf("\nEnter the logical address:");
    	scanf("%d",&p);
   	printf("\nEnter the page number: ");
    	scanf("%d",&pg);
    	for(i=0;i<n;i++)
    	{
	    if(i==p)
	    {
pa=b[i]+d;
		a=b[i];
		printf("\n\t%dPageNo.\n\t%dBaseAdd.\n\t%dPhysicalAdd.",p,a,pa);
	    }
    }
    printf("\nInvalid Page");
}

OUTPUT:


    9. Implement some memory management schemes – II 

AIM: 
To Implement some memory management schemes – II 

ALGORITHM:
STEP 1: Start Shell Online Compiler
STEP 2: Include necessary header files
STEP 3: Create main() class and declare the required variables
STEP 4: Get the input from the user 
STEP 5: If the values are invalid, it will display “Invalid Page”
STEP 6: Output will be displayed
STEP 7: Stop the program

PROGRAM:
#include<stdio.h>
#include<unistd.h>
#include<stdlib.h>
int main()
{
int b[20],l[20],n,i,pa,s,a,d;
printf("\nProgram for segmentation");
printf("\nEnter the number of segments:");
scanf("%d",&n);
printf("\nEnter the base address and limit register:");
for(i=1;i<=n;i++)
{
scanf("%d",&b[i]);
scanf("%d",&l[i]);
}
printf("\nEnter the logical address:");
scanf("%d",&d);
printf("\nEnter segment number:");
scanf("%d",&s);
for(i=1;i<=n;i++)
{
    if(i==s)
{
if(d<l[i])
{
    pa=b[i]+d;
a=b[i];
printf("\nPageNo.\t BaseAdd. PhysicalAdd. \n %d \t %d \t %d\n",s,a,pa);
exit(0);
}
else
{
printf("\nPage size exceeds");
exit(0);
}
}
}
printf("\nInvalid segment");
return 0;
}

OUTPUT:

10.Implement any file allocation technique (Linked, Indexed or Contiguous)

AIM: 
To Implement any file allocation technique (Linked, Indexed or Contiguous)

ALGORITHM:
STEP 1: Start Shell Online Compiler
STEP 2: Include necessary header files
STEP 3: Create main() class and declare the required variables
STEP 4: Get the input from the user
STEP 5: It will display if the block is already displayed or not
STEP 6: If enter 1 more file can be added and if entered 0 files will not be added
STEP 7: Output will be displayed and stop the program

PROGRAM:
#include <stdio.h>
#include <stdlib.h>

void recursivePart(int pages[]){
    int st, len, k, c, j;
    printf("Enter the index of the starting block and its length: ");
    scanf("%d%d", &st, &len);
    k = len;
    if (pages[st] == 0){
        for (j = st; j < (st + k); j++){
            if (pages[j] == 0){
                pages[j] = 1;
                printf("%d------>%d\n", j, pages[j]);
            }
            else {
                printf("The block %d is already allocated \n", j);
                k++;
            }
        }
    }
    else
        printf("The block %d is already allocated \n", st);
    printf("Do you want to enter more files? \n");
    printf("Enter 1 for Yes, Enter 0 for No: ");
    scanf("%d", &c);
    if (c==1)
        recursivePart(pages);
    else
        exit(0);
    return;
}

int main(){
    int pages[50], p, a;

    for (int i = 0; i < 50; i++)
        pages[i] = 0;
    printf("Enter the number of blocks already allocated: ");
    scanf("%d", &p);
    printf("Enter the blocks already allocated: ");
    for (int i = 0; i < p; i++){
        scanf("%d", &a);
        pages[a] = 1;
    }

    recursivePart(pages);
  
    return 0;
}

OUTPUT:


