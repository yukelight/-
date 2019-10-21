# -
#include<iostream>
#include<cmath>
using namespace std;
template<class Elem>
class list{
  bool insert(Elem& e);
  bool isempty();
  bool getvalue();
  bool print();
   
};
template<class Elem>
class llist;
template<class Elem>
class node{
    Elem element;
    node* next;
    public :
       node( Elem &e,node*nnext=NULL){
    element=e;
    next=nnext;
    }
       node(node*nnext=NULL){next=nnext;}
    friend class llist<Elem>;
};
template<class Elem>
class llist :public list<Elem>{
  node<Elem>*head;
  node<Elem>*curr;
  node<Elem>*tail;
  public:
  llist(){
    head=curr=tail=new node<Elem>();
}
  bool insert(Elem &e){
 
    node<Elem>*p=new node<Elem>(e);
    p->next=head->next;
    curr=head->next=p;
    return true;
    }
  bool getvalue(Elem e){
    e=curr->next->element;
    return true;
    }
  bool print(){
curr=head->next;
  while(curr!=NULL){
  Elem e;
  e=curr->element;
  cout << e<< endl;
  curr=curr->next;
}
    return true;
}
  bool isempty(){
  return head->next==NULL;
}
  bool reverse(){
  node<Elem>*u;
  node<Elem>*i;
  node<Elem>*o;
  u=head;
  i=u->next;
  o=i->next;
while(o!=NULL){
  
  i->next=o->next;
  o->next=u->next;
  u->next=o;
u=u->next;
  i=u->next;
  o=i->next;
}
}
};
int main(){
int input;
llist<int> d;
for(int i=0;i<7;i++){
  cin>>input;
  d.insert(input);
}
d.print();
d.reverse();
d.print();
    return 0;
}
