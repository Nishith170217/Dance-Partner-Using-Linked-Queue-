#include<stdio.h>
#include<stdlib.h>
#define OK 1

typedef struct{
char name[20];
int sex;
}person;

typedef struct Lnode{
person data;
struct Lnode *next;
}Lnode,*mQ;

typedef struct{
    mQ front;
    mQ rear;
}LinkQueue;

LinkQueue Mdancers,Fdancers;

int InitQueue(LinkQueue *q)
{
    q->front=q->rear=(mQ)malloc(sizeof(Lnode));
    q->front->next=NULL;
    return OK;
}
int EnQueue(LinkQueue *q,person e)
{
    mQ p;
    p=(mQ)malloc(sizeof(Lnode));
    p->data=e;
    p->next=NULL;
    q->rear->next=p;
    q->rear->next=p;
    q->rear=p;

    return OK;
}

int DeQueue(LinkQueue *q,person *e)
{
    mQ p;
    if(q->front==q->rear)
    {
        printf("\nQueue is empty!!\n");
        return 0;
    }
    p=q->front->next;
    *e=p->data;
    q->front->next=p->next;
    if(q->rear==p)
        q->rear=q->front;
    free(p);
    return OK;

}

person top(LinkQueue q)
{
    if(q.front!=q.rear)
        return q.front->next->data;
}

int QueueEmpty(LinkQueue q)
{
    if(q.front==q.rear)
        return OK;
    else
        return 0;

}
void PartnerChoice(mQ q)
{
    Lnode *p;
    person *e=(person*)malloc(sizeof(person));
    InitQueue(&Mdancers);
    InitQueue(&Fdancers);
    p=q->next;
    while(p)
    {
        if(p->data.sex==2)
        {
            EnQueue(&Fdancers,p->data);
            p=p->next;
        }
        else{
            EnQueue(&Mdancers,p->data);
            p=p->next;
        }
    }
    printf("\n\n\t\t\t******************************");
    printf("\n\t\t\t   The dancing Partners are: \n");
    printf("\t\t\t******************************\n");

    while(!QueueEmpty(Fdancers)&&!QueueEmpty(Mdancers))
    {
        if(DeQueue(&Mdancers,e))
            printf("\t\t\t      %s  &  ",e->name);
        if(DeQueue(&Fdancers,e))
            printf("%s\n",e->name);
            printf("\t\t\t******************************\n");
    }
    if(!QueueEmpty(Fdancers))
    {
        *e=top(Fdancers);
        printf("____________________________________________________________________________________\n");
        printf("\n\t\tThe first Woman waiting for partner is : %s\n",e->name);
        printf("____________________________________________________________________________________\n\n");
    }
    else if(!QueueEmpty(Mdancers))
    {
        *e=top(Mdancers);
        printf("____________________________________________________________________________________\n");
        printf("\n\t\tThe first Man waiting for partner is : %s\n",e->name);
        printf("____________________________________________________________________________________\n\n");
    }
}
int dancePair(Lnode *k,int n)
{
    int i,sex;
    Lnode *p;
    for(i=1;i<=n;i++)
    {
        p=(Lnode *)malloc(sizeof(Lnode));
        printf("  Please Enter the information of dancer no %d (For Male Enter 1 For Female Enter 2). \n",i);
        printf("  Name: ");
        scanf("%s",p->data.name);
        printf("  Sex : ",i);
        scanf("%d",&sex);
        while(sex!=1&&sex!=2)
        {
            printf("\n  Input must be 1 For Male and 2 for Female");
            break;
        }
        p->data.sex=sex;
        p->next=k->next;
        k->next=p;
        printf("  Dancer No.%d is %s & Gender Code is: %d\n",i,p->data.name,p->data.sex);
        printf("\n____________________________________________________________________________________");
        printf("\n____________________________________________________________________________________\n\n");
    }

  return OK;
}
void main()
{
    mQ k=NULL,p;
    int x;
    k=(Lnode *)malloc(sizeof(Lnode));
    if(k)
    {
        k->next=NULL;
        printf("____________________________________________________________________________________\n");
        printf("\n-------------------------LAB #3 by Nisith (10460348058)-----------------------------");
        printf("\n____________________________________________________________________________________\n");
        printf("\n  Please Enter the number of total Dancers: ");
        scanf("%d",&x);
        printf("\n____________________________________________________________________________________\n\n");
        if(dancePair(k,x))
        {
            p=k->next;
            printf("\n\t\t\t_______Listed Dancers:_______ \n");
            printf("\t\t\t_____________________________");
            printf("\n\t\t\t      Name         Sex    ");
            printf("\n\t\t\t______________|______________");
            while(p)
            {
                printf("\n\t\t\t%10s%10d",p->data.name,p->data.sex);
                printf("\n\t\t\t______________|______________");
                p=p->next;
            }
        }

        PartnerChoice(k);
    }
}
