# student-ranking-system-in-c
```
#include <stdio.h>
#include <stdlib.h>

struct student
{
    char name[100];
    int id;
    int mark;
};
void sortrank(struct student s[], int n);
int sortid(struct student s[], int n);
int main()
{
    struct student s[100];
    int choice,n,i,j;
    printf("ENTER NUMBER OF STUDENT : ");
    scanf("%d",&n);
    for (i=0;i<n;i++)
    {
        printf("\nENTER STUDENT ID: ");
        scanf("%d", &s[i].id);
        printf("ENTER STUDENT NAME: ");
        scanf(" %[^\n]", s[i].name);
        printf("ENTER STUDENT MARK: ");
        scanf("%d", &s[i].mark);
    }
    while (1)
    {
        printf("======STUDENT REMARK=====\n");
        printf("1) DISPLAY RANK LIST\n");
        printf("2) Search Student by Register Number\n");
        printf("0) EXIT\n");
        printf("ENTER CHOICE : ");
        scanf("%d",&choice);
        switch (choice)
        {
            case 1: 
                sortrank(s,n);
                break;
           case 2 :
                i=sortid(s,n);
                if (i!=-1)
                {
                    printf("STUDENT FOUND\n");
                    printf("NAME : %s\n", s[i].name);
                    printf("MARK : %d\n",s[i].mark);
                }
                else 
                    printf("STUDENT NOT FOUND");
                break; 
           case 0: 
                printf("=====PROGRAM EXIT=====\n");
                exit(0);
           default :
                printf("ENTER VALID NUMBER\n");
                break;
        }
    }
}
void sortrank(struct student s[], int n)
{
    struct student temp;
    int i,j;
    for (i=1;i<n;i++)
    {
        temp=s[i];
        j=i-1;
        while (j>=0 && s[j].mark>temp.mark)
        {
            s[j+1]=s[j];
            j--;
        }
        s[j+1]=temp;
    }
    printf("NAME\tID\tMARK\n");
    for (i=0;i<n;i++)
    {
        printf("%s\t%d\t%d\n",s[i].name,s[i].id,s[i].mark);
    }
}
int sortid(struct student s[],int n)
{
    struct student temp;
    int i,j,min;
    for (i=0;i<n-1;i++)
    {
        min=i;
        for (j=i+1;j<n;j++)
        {
            if (s[j].id<s[min].id)
                min=j;
        }
        if (min!=i)
        {
            temp = s[i];
            s[i]= s[min];
            s[min] = temp;
        }
    }
    int id,mid;
    printf("ENTER STUDENT ID : ");
    scanf("%d",&id);
    int l=0,r=n-1;
    while (l<=r)
    {
        mid=(l+r)/2;
        if (id==s[mid].id)
            return mid;
        else if (id>s[mid].id)
            l=mid+1;
        else 
            r=mid-1;
    }
    return -1;
    
}
```
### OUTPUT

<img width="1867" height="927" alt="1 output" src="https://github.com/user-attachments/assets/b7154832-00be-4416-82ef-daae2113c312" />
