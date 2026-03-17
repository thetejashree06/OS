#include <stdio.h>
struct Process
{
    int pid;
    int arrival_time;
    int burst_time;
    int remaining_time;
    int priority;
    int completion_time;
    int waiting_time;
    int turnaround_time;
};
int main()
{
    int n, time = 0, completed = 0;
    int highest_priority;
    int index = -1;
    printf("Enter number of processes: ");
    scanf("%d", &n);
    struct Process p[n];
    // Input
    for (int i = 0; i < n; i++)
    {
        printf("\nProcess %d\n", i + 1);
        p[i].pid = i + 1;
        printf("Arrival Time: ");
        scanf("%d", &p[i].arrival_time);
        printf("Burst Time: ");
        scanf("%d", &p[i].burst_time);
        printf("Priority (Lower number = Higher priority): ");
        scanf("%d", &p[i].priority);
        p[i].remaining_time = p[i].burst_time;
    }
    // Scheduling Logic
    while (completed != n)
    {
        highest_priority = 9999;
        index = -1;
        for (int i = 0; i < n; i++)
        {
            if (p[i].arrival_time <= time &&
                p[i].remaining_time > 0 &&
                p[i].priority < highest_priority)
            {
                highest_priority = p[i].priority;
                index = i;
            }
        }
        if (index == -1)
        {
            time++;
        }
        else
        {
            p[index].remaining_time--;
            time++;
            if (p[index].remaining_time == 0)
            {
                completed++;
                p[index].completion_time = time;
                p[index].turnaround_time =
                    p[index].completion_time - p[index].arrival_time;
                p[index].waiting_time =
                    p[index].turnaround_time - p[index].burst_time;
            }
        }
    }
    // Output
    float total_wt = 0, total_tat = 0;

    printf("\nPID\tAT\tBT\tPR\tCT\tTAT\tWT\n");

    for (int i = 0; i < n; i++)
    {
        total_wt += p[i].waiting_time;
        total_tat += p[i].turnaround_time;

        printf("%d\t%d\t%d\t%d\t%d\t%d\t%d\n",
               p[i].pid,
               p[i].arrival_time,
               p[i].burst_time,
               p[i].priority,
               p[i].completion_time,
               p[i].turnaround_time,
               p[i].waiting_time);
    }
    printf("\nAverage Turnaround Time = %.2f", total_tat / n);
    printf("\nAverage Waiting Time    = %.2f\n", total_wt / n);
    return 0;
}
