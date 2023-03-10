# Strings-in-Binary-Search-Tree-BST
Implement a C++ program to store Strings in Binary Search tree. Your program should have following functions: • Insert • Display • Search 
Implement a C++ program to store Strings in Binary Search tree. Your program should have following functions: • Insert • Display • Search 
#include<iostream>
using namespace std;
struct node 
{
    string data;
    node *left;
    node *right;
};
node *createnode(string d)
{
    node *nn=new node;
    nn->data=d;
    nn->left=NULL;
    nn->right=NULL;
    return nn;
}
    node *insert(node *r,string d)
    {
    
        if(r==NULL)
        {
           return createnode(d);
        }
        if(d<r->data)
        {
            r->left=insert(r->left,d);
        }
        if(d>r->data)
        {
            r->right=insert(r->right,d);
        }
        
        return r;
    }
    void printinorder(node *r)
    {
        if(r==NULL)
        {
            return;
        }
        printinorder(r->left);
        cout<<r->data;
         cout<<endl;
        printinorder(r->right);
       
    }
    
      void printpostorder(node *r)
    {
        if(r==NULL)
        {
            return;
        }
        printpostorder(r->left);
        printpostorder(r->right);
         cout<<r->data;
         cout<<endl;
       
    }
    

    void printpreorder(node *r)
    {
        if(r==NULL)
        {
            return;
        }
        cout<<r->data;
         cout<<endl;
        printpreorder(r->left);
        printpreorder(r->right);
         
       
    }
    
bool search(node *r,string d)
{
    if(r==NULL)
    {
     return false;
    }
    if(r->data==d)
    {
      return true;
    }
    if(d<r->data)
    {
        return search(r->left,d);
    }
    else
    return search(r->right,d);
}
int main()
{
    node *root=new node;
    root=NULL;
    int c;
    do 
    {
       cout<<"Enter 1 for inserting data \n Enter 2 to search the data \n Enter 3 to print data in inorder \n Enter -100 to exit"<<endl;
       cin>>c;
    if(c==1)
    {
        string k;
        cout<<"enter the data you want to insert"<<endl;
        cin>>k;
        root=insert(root,k);
    }
    if(c==2)
    {
    string k;
    cout<<"enter the data you want to search"<<endl;
    cin>>k;
    cout<<search(root,k)<<endl;
    }
   if(c==3)
   { 
    cout<<"Printing the data in inorder"<<endl;
    printinorder(root);
    }
  
    }
    while(c!=-100);
}
