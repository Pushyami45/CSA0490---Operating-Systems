#include <stdio.h>

// Structure to represent a process
struct Process {
    int id;
    int burst_time;
    int priority;
    int remaining_time;
};

// Function to perform priority scheduling
void priorityScheduling(struct Process processes[], int n) {
    int currentTime = 0;

    while (1) {
        // Find the process with the highest priority that has arrived
        int highestPriorityProcess = -1;
        for (int i = 0; i < n; i++) {
            if (processes[i].remaining_time > 0 && processes[i].priority > highestPriorityProcess && processes[i].arrival_time <= currentTime) {
                highestPriorityProcess = i;
            }
        }

        // If no process is remaining, break the loop
        if (highestPriorityProcess == -1)
            break;

        // Execute the process for 1 unit of time
        processes[highestPriorityProcess].remaining_time--;
        currentTime++;

        // Print the execution of the process
        printf("Time %d: Process %d\n", currentTime, processes[highestPriorityProcess].id);

        // If the process has completed, update its turnaround time
        if (processes[highestPriorityProcess].remaining_time == 0) {
            processes[highestPriorityProcess].turnaround_time = currentTime - processes[highestPriorityProcess].arrival_time;
        }
    }
}

int main() {
    // Number of processes
    int n;

    printf("Enter the number of processes: ");
    scanf("%d", &n);

    // Array to store processes
    struct Process processes[n];

    // Input process details
    for (int i = 0; i < n; i++) {
        printf("Enter details for Process %d:\n", i + 1);
        processes[i].id = i + 1;
        printf("Burst Time: ");
        scanf("%d", &processes[i].burst_time);
        printf("Priority: ");
        scanf("%d", &processes[i].priority);
        processes[i].remaining_time = processes[i].burst_time;
        processes[i].turnaround_time = 0;
    }

    // Perform priority scheduling
    priorityScheduling(processes, n);

    // Print turnaround time for each process
    printf("\nTurnaround Time for each process:\n");
    for (int i = 0; i < n; i++) {
        printf("Process %d: %d\n", processes[i].id, processes[i].turnaround_time);
    }

    return 0;
}
