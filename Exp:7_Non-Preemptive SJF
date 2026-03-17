#include <stdio.h>
int main() {
    int n, i, j;
    printf("Enter number of processes: ");
    scanf("%d", &n);
    int pid[n], bt[n], wt[n], tat[n];
    // Input
    for(i = 0; i < n; i++) {
        pid[i] = i + 1;
        printf("Enter Burst Time for Process %d: ", pid[i]);
        scanf("%d", &bt[i]);
    }
    // Sort based on Burst Time (SJF)
    for(i = 0; i < n - 1; i++) {
        for(j = i + 1; j < n; j++) {
            if(bt[i] > bt[j]) {
                int temp;
                temp = bt[i];
                bt[i] = bt[j];
                bt[j] = temp;
                temp = pid[i];
                pid[i] = pid[j];
                pid[j] = temp;
            }
        }
    }
    // Waiting Time
    wt[0] = 0;
    for(i = 1; i < n; i++) {
        wt[i] = wt[i - 1] + bt[i - 1];
    }
    // Turnaround Time
    for(i = 0; i < n; i++) {
        tat[i] = wt[i] + bt[i];
    }
    // Display Table Format
    printf("\n------------------------------------------------------------\n");
    printf("%-10s %-12s %-15s %-18s\n", 
           "Process", "Burst Time", "Waiting Time", "Turnaround Time");
    printf("------------------------------------------------------------\n");
    float total_wt = 0, total_tat = 0;
    for(i = 0; i < n; i++) {
        total_wt += wt[i];
        total_tat += tat[i];

        printf("%-10d %-12d %-15d %-18d\n", 
               pid[i], bt[i], wt[i], tat[i]);
    }
    printf("------------------------------------------------------------\n");
    printf("Average Waiting Time    : %.2f\n", total_wt / n);
    printf("Average Turnaround Time : %.2f\n", total_tat / n);
    return 0;
}
