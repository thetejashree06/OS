#include <stdio.h>
#include <stdlib.h>

struct Employee {
    int id;
    char name[20];
    float salary;
};

int main() {
    FILE *fp;
    struct Employee emp;
    int choice, id;

    fp = fopen("employee.dat", "rb+");
    if (fp == NULL)
        fp = fopen("employee.dat", "wb+");

    while (1) {
        printf("\n1.Add  2.Search  3.Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch (choice) {

        case 1: // Add Record
            printf("Enter ID: ");
            scanf("%d", &emp.id);
            printf("Enter Name: ");
            scanf("%s", emp.name);
            printf("Enter Salary: ");
            scanf("%f", &emp.salary);

            fseek(fp, (emp.id - 1) * sizeof(emp), SEEK_SET);
            fwrite(&emp, sizeof(emp), 1, fp);

            printf("\n+---------+----------------+-------------+\n");
            printf("| %-7s | %-14s | %-11s |\n", "ID", "Name", "Salary");
            printf("+---------+----------------+-------------+\n");
            printf("| %-7d | %-14s | %-11.2f |\n",
                   emp.id, emp.name, emp.salary);
            printf("+---------+----------------+-------------+\n");
            break;

        case 2: // Search Record
            printf("Enter ID to search: ");
            scanf("%d", &id);

            fseek(fp, (id - 1) * sizeof(emp), SEEK_SET);
            fread(&emp, sizeof(emp), 1, fp);

            if (emp.id == id) {
                printf("\n+---------+----------------+-------------+\n");
                printf("| %-7s | %-14s | %-11s |\n", "ID", "Name", "Salary");
                printf("+---------+----------------+-------------+\n");
                printf("| %-7d | %-14s | %-11.2f |\n",
                       emp.id, emp.name, emp.salary);
                printf("+---------+----------------+-------------+\n");
            } else {
                printf("Record Not Found!\n");
            }
            break;

        case 3:
            fclose(fp);
            return 0;

        default:
            printf("Invalid Choice!\n");
        }
    }

    return 0;
}
