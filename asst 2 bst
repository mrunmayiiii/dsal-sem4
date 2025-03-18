#include <iostream>
#include <bits/stdc++.h>
using namespace std;

class Node {
public:
    Node *left;
    Node *right;
    int data;

    Node(int d) {
        data = d;
        left = NULL;
        right = NULL;
    }
};

class Binarytree {
public:
    Node *root;

    Binarytree() {
        root = NULL;
    }

    Node* buildTree() {
        cout << "Enter element to be added (-1 for NULL): ";
        int ele;
        cin >> ele;
        
        if (ele == -1) {
            return NULL;
        }

        Node* newNode = new Node(ele);

        cout << "Enter left child of " << ele << endl;
        newNode->left = buildTree();
        
        cout << "Enter right child of " << ele << endl;
        newNode->right = buildTree();

        return newNode;
    }

    void initializeTree() {
        root = buildTree();
    }

    Binarytree(const Binarytree &other) {
        root = copyTree(other.root);
    }

    Binarytree &operator=(const Binarytree &other) {
        if (this == &other) {
            return *this;
        }
        eraseAllNodes();
        root = copyTree(other.root);
        return *this;
    }

    Node *copyTree(Node *node) {
        if (!node) return NULL;

        Node *newNode = new Node(node->data);
        newNode->left = copyTree(node->left);
        newNode->right = copyTree(node->right);
        return newNode;
    }

    void inorderRec(Node *node) {
        if (!node) return;
        inorderRec(node->left);
        cout << node->data << " ";
        inorderRec(node->right);
    }

    void inorderRecursive() {
        inorderRec(root);
        cout << endl;
    }

    void preorderRec(Node *node) {
        if (!node) return;
        cout << node->data << " ";
        preorderRec(node->left);
        preorderRec(node->right);
    }

    void preorderRecursive() {
        preorderRec(root);
        cout << endl;
    }

    void postorderRec(Node *node) {
        if (!node) return;
        postorderRec(node->left);
        postorderRec(node->right);
        cout << node->data << " ";
    }

    void postorderRecursive() {
        postorderRec(root);
        cout << endl;
    }

    int height(Node *node) {
        if (!node) return 0;
        return max(height(node->left), height(node->right)) + 1;
    }

    int getHeight() {
        return height(root) - 1;
    }

    int countLeaves(Node *node) {
        if (!node) return 0;
        if (!node->left && !node->right) return 1;
        return countLeaves(node->left) + countLeaves(node->right);
    }

    int getLeafCount() {
        return countLeaves(root);
    }

    int countInternalNodes(Node *node) {
        if (!node || (!node->left && !node->right)) return 0;
        return 1 + countInternalNodes(node->left) + countInternalNodes(node->right);
    }

    int getInternalNodeCount() {
        return countInternalNodes(root);
    }

    void erase(Node *node) {
        if (!node) return;
        erase(node->left);
        erase(node->right);
        delete node;
    }

    void eraseAllNodes() {
        erase(root);
        root = nullptr;
    }

    void swapChildren(Node *node) {
        if (!node) return;
        swap(node->left, node->right);
        swapChildren(node->left);
        swapChildren(node->right);
    }

    void swapTree() {
        swapChildren(root);
    }

    void mirrorRec(Node *node) {
        if (!node) return;
        swap(node->left, node->right);
        mirrorRec(node->left);
        mirrorRec(node->right);
    }

    void mirror() {
        mirrorRec(root);
    }
};

int main() {
    Binarytree tree;
    tree.initializeTree();

    cout << "\nIn-order traversal: ";
    tree.inorderRecursive();

    cout << "Pre-order traversal: ";
    tree.preorderRecursive();

    cout << "Post-order traversal: ";
    tree.postorderRecursive();

    cout << "Height of the tree: " << tree.getHeight() << endl;
    cout << "Number of leaf nodes: " << tree.getLeafCount() << endl;
    cout << "Number of internal nodes: " << tree.getInternalNodeCount() << endl;

    cout << "In-order before swapping children: ";
    tree.inorderRecursive();
    tree.swapTree();
    cout << "In-order after swapping children: ";
    tree.inorderRecursive();

    cout << "In-order before mirroring: ";
    tree.inorderRecursive();
    tree.mirror();
    cout << "In-order after mirroring: ";
    tree.inorderRecursive();

    Binarytree copyTree = tree;
    cout << "In-order of copied tree: ";
    copyTree.inorderRecursive();

    Binarytree assignedTree;
    assignedTree = tree;
    cout << "In-order of assigned tree: ";
    assignedTree.inorderRecursive();

    tree.eraseAllNodes();
    cout << "In-order after erasing all nodes: ";
    tree.inorderRecursive();

    return 0;
}
