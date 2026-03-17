#include <stdio.h>
int main() {
    int n, tq;
    printf("Enter number of processes: ");
    scanf("%d", &n);
    int pid[n], bt[n], rt[n], wt[n], tat[n];
    // Input Burst Time
    for(int i = 0; i < n; i++) {
        pid[i] = i + 1;
        printf("Enter Burst Time for Process %d: ", pid[i]);
        scanf("%d", &bt[i]);
        rt[i] = bt[i];   // Remaining time initially equals burst time
    }
    printf("Enter Time Quantum: ");
    scanf("%d", &tq);
    int time = 0, done;
    // Round Robin Logic
    do {
        done = 1;
        for(int i = 0; i < n; i++) {
            if(rt[i] > 0) {
                done = 0;
                if(rt[i] > tq) {
                    time += tq;
                    rt[i] -= tq;
                }
                else {
                    time += rt[i];
                    wt[i] = time - bt[i];  // Waiting time
                    rt[i] = 0;
                }
            }
        }
    } while(!done);
    // Turnaround Time
    for(int i = 0; i < n; i++) {
        tat[i] = bt[i] + wt[i];
    }
    // Display Table
    printf("\n-----------------------------------------------------------------\n");
    printf("%-10s %-12s %-15s %-18s\n",
           "Process", "Burst Time", "Waiting Time", "Turnaround Time");
    printf("-----------------------------------------------------------------\n");
    float total_wt = 0, total_tat = 0;
    for(int i = 0; i < n; i++) {
        total_wt += wt[i];
        total_tat += tat[i];
        printf("%-10d %-12d %-15d %-18d\n",
               pid[i], bt[i], wt[i], tat[i]);
    }
    printf("-----------------------------------------------------------------\n");
    printf("Average Waiting Time    : %.2f\n", total_wt / n);
    printf("Average Turnaround Time : %.2f\n", total_tat / n);
    return 0;
}
