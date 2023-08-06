```
#include<iostream>
#include <cstring>
using namespace std;
class Node
{
public:
	int data;
	Node* left, * right;
	Node(int value)
	{
		data = value;
		right = left = NULL;
	}

};
class BST {
public:

   Node* root;
   
   BST()
   {
	   root = NULL;
   }

   Node* insert(Node* r, int item)
   {
	   if (r == NULL)
	   {
		   Node* newnode = new Node(item);
		   r = newnode;
	   }
	   else if (item < r->data)

		   r->left = insert(r->left, item);

	   else

		   r->right = insert(r->right, item);
	   return r;
		   
   }
   void insert(int item)
   {
	   root = insert(root, item);
   }

   void preorder(Node* r)
   {
	   if (r == NULL)
		   return;
		   cout << r->data << "          ";
		   preorder(r->left);
		   preorder(r->right);
   }

   void inorder(Node* r)
   {
	   if (r == NULL)
		   return;
		   inorder(r->left);
		   cout << r->data << "          ";
		   inorder(r->right);
	   
   }


   void postorder(Node* r)
   {
	   if (r == NULL)
		   return;
		   postorder(r->left);
		   postorder(r->right);
		   cout << r->data << "          ";

   }
Node* search(Node* r, int key)
{
	if (r == NULL)
		return NULL;
	else if (r->data == key)
		return r;
	else if (key < r->data)
		return search(r->left, key);
	else
		return search(r->right, key);
}


bool search(int key)
{
	Node* result = search(root, key);
	if (result == NULL)
		return false;
	else
		return true;

}

Node* MinElement(Node* r)
{
	if (r == NULL)
		return NULL;
	else if (r->left == NULL)
		return r->right;
	else
		return r->left;
}
Node* MaxElement(Node* r)
{
	if (r->right == NULL)
		return r;
	else if (r == NULL)
		return NULL;
	else
		return MaxElement(r->right);
}

Node* Delete(Node* r, int key)
{
	if (r == NULL)
		return NULL;
	if (key < r->data)
		 r->left = Delete(r->left, key);
	else if (key > r->data)
		 r->right = Delete(r->right, key);

	else
	{
		if (r->left == NULL && r->right == NULL)
			r = NULL;

		else if (r->left != NULL && r->right == NULL)
		{
			r->data = r->left->data;
			delete r->left;
			r->left == NULL;
		}
		else if (r->left == NULL && r->right != NULL)
		{
			r->data = r->right->data;
			delete r->right;
			r->right == NULL;
		}
		else
		{
			Node* max = MaxElement(r->left);
			r->data = max->data;
			r->left = Delete(r->left, max->data);
		}
   	}
	return r;
  }
};
int main()
{
	//insert

	BST btree;
	btree.insert(45);
	btree.insert(15);
	btree.insert(79);
	btree.insert(90);
	btree.insert(10);
	btree.insert(55);
	btree.insert(12);
	btree.insert(20);
	btree.insert(50);

	//end insert
	
	cout << "Element a BST" << endl;

	cout << "elment of tree preorder\n";
	btree.preorder(btree.root);
	
	cout << "\n================================================================================================\n" ;
	cout << "elment of tree inorder\n" ;
	btree.postorder(btree.root);

	cout << "\n=================================================================================================\n";
	cout << "elment of tree postorder\n" ;
	btree.inorder(btree.root);
	
	cout << "\n=================================================================================================\n";

	//search 
	int key;
	cout << "Enter Key As Search" << endl;
	cin >> key;
	if (btree.search(key))
		cout << "Item Found";
	else
		cout << "Item Not Found" << endl;
	
	cout << "----------------------------------------"<< endl;
	//end search

	//find min and max

	cout << "find Min  " << endl;

	Node* min = btree.MinElement(btree.root);

	if (min == 0)
		cout << "No number found" << endl;
	else
		cout << "Min Element = " << min->data << endl;
	
	cout << "----------------------------------------" << endl;


	cout << "find Max" << endl;

	Node* Max = btree.MaxElement(btree.root);

	if (min == 0)
		cout << "No number found" << endl;
	else
		cout << "Max Element = " << Max->data << endl;
	//end find min and max 

	cout << "----------------------------------------" << endl;
	
	//Delete 
	
	cout << "Delete  Element ??" << endl;
	int D_key;cin >> D_key;
	Node *result = btree.Delete(btree.root, D_key);
	cout << "preoreder After Delete "<<D_key << endl;
	btree.preorder(result);
	cout << endl;

	cout << "Delete Any Element ??" << endl;
	
	int D_key2; cin >> D_key2;
	result = btree.Delete(btree.root, D_key2);
	cout << "preoreder After Delete "<<D_key2 << endl;
	btree.preorder(result);

}
```
