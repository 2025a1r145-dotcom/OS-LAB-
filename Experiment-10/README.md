<img width="648" height="162" alt="Screenshot 2026-10-30 at 11 03 02 AM" src="https://github.com/user-attachments/assets/032a9594-5a24-40e0-ab19-16a40a3e21f5" />
<img width="872" height="568" alt="output(2)" src="https://github.com/user-attachments/assets/e93bd060-5af2-4d47-a78a-669984492ec9" />


AIM

To write and execute a C program in Ubuntu Linux that creates a child process using the fork() system call, waits for its termination using the wait() system call, and displays its Process ID (PID).

REQUIREMENTS

Ubuntu Linux operating system

GCC compiler

Bash Shell

Terminal application

C programming language

PROGRAM
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/wait.h>

int main(){
pid_t p = fork();
if(p==0){
printf("Child running with PID: %d\n",getpid());
sleep(2);
printf("Child Exiting....\n");
exit(0);
}
else{
printf("Parent Waiting for child to terminate....\n");
pid_t terminated_pid = wait(NULL);
printf("Parent Terminated Child PID: %d\n", terminated_pid);
}
return 0;
}


PROCEDURE

Open the Ubuntu Linux terminal.

Create a C file named fork_wait.c.

Write the program and save the file.

Compile the program using GCC.

Execute the compiled program in the terminal.

Observe the child process ID and the parent process waiting for its termination.

RESULT

The C program was successfully compiled and executed in Ubuntu Linux. The fork() system call created a child process, and the wait() system call ensured that the parent process waited until the child terminated. The child's Process ID was successfully displayed.
