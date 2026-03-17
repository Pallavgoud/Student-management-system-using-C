# Student-management-system-using-C
#include <stdio.h>
#include <stdlib.h>

struct student {
    int id;
    char name[50];
};

void addStudent() {
    FILE *fp = fopen("students.txt", "a");
    struct student s;

    printf("Enter ID: ");
    scanf("%d", &s.id);
    printf("Enter Name: ");
    scanf("%s", s.name);

    fprintf(fp, "%d %s\n", s.id, s.name);
    fclose(fp);

    printf("Student Added!\n");
}

void viewStudents() {
    FILE *fp = fopen("students.txt", "r");
    struct student s;

    while (fscanf(fp, "%d %s", &s.id, s.name) != EOF) {
        printf("ID: %d | Name: %s\n", s.id, s.name);
    }

    fclose(fp);
}

int main() {
    int choice;

    while (1) {
        printf("\n1. Add Student\n2. View Students\n3. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addStudent();
                break;
            case 2:
                viewStudents();
                break;
            case 3:
                exit(0);
            default:
                printf("Invalid choice\n");
        }
    }

    return 0;
}
