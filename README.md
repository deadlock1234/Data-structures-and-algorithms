# Data-structures-and-algorithms
#include <stdio.h>
#include<stdlib.h>
#include<malloc.h>
struct node
{
    int data;
    struct node*next;
};
void insertafter(struct node*head,int pos,int data)
{ int i=1;
    struct node*newnode=(struct node*)malloc(sizeof(struct node));
    newnode->data=data;
    while(i<pos && head->next!=NULL)
    {
        head=head->next;
    }
    struct node*temp=head->next;
    head->next=newnode;
    newnode->next=temp;
}
void append(struct node*head,int data)
{
    struct node*newnode=(struct node*)malloc(sizeof(struct node));
    newnode->data=data;
    newnode->next=NULL;
    while(head->next!=NULL)
    {
        head=head->next;
    }
    head->next=newnode;
    
}
void push(struct node**head_ref,int data)
{
    struct node*newnode=(struct node*)malloc(sizeof(struct node));
    newnode->data=data;
    newnode->next=*head_ref;
    *head_ref=newnode;
}
void print(struct node*head)
{
    while(head!=NULL)
    {
        printf("%d  \t",head->data);
        head=head->next;
    }
    
    
}
void delete(struct node**head_ref,int data)
{   struct node*temp=*head_ref;struct node*head=*head_ref;
    struct node*prev=temp;
    while(head!=NULL )
    { 
      prev=head;
      head=head->next;
      if(prev->data==data)
            break;
    }
    if(head==NULL)
    {
        printf("\nvalue to be deleted not found in the list");
        printf("no \n change in the linked list");
    }
    else
    {
        if(*head_ref==head)
        {
            *head_ref=head->next;
        }
        else
        {
        prev->next=prev->next->next;
      
        printf("\nnew linked list: \n");
        }
        
        
    }
}
int main()
{
    struct node*head=NULL;
    push(&head,10);
    push(&head,20);
    push(&head,30);
   append(head,40);
    append(head,50);
    insertafter(head,2,60);
    insertafter(head,4,80);
    print(head);
    delete(&head,30);
    delete(&head,100);
    
    print(head);
}
    
    
    
    
    
    
    
    
