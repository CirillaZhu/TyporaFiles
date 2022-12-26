##### DDA A3 zhu yulin 116020372



#### 1 Exercise 1

This is an improvement to the method since it eliminates the requirement to compare P[q]+q] with T[i], when P[q+1]!= T[i] and then if P[[q]+q]=P[q+1]T[i]. 



#### 2 Exercise 2


$$
F(i, j)=max\left\{
\begin{aligned}
F(i - 1, j - 1) + z \\
F(i - 1, j) + x \\
F(i, j - 1) + y\\
\end{aligned}
\right.
$$


##### b 

Yes.



#### 3 Exercise 3

```c++
class TrieNode {
public:
    char data; 
    TrieNode* children[26];
    int is_leaf;
    
    TrieNode(char data) {
        TrieNode* node = (TrieNode*)calloc(1, sizeof(TrieNode));
        for (int i = 0; i < 26; i++)
            node->children[i] = NULL;
        node->is_leaf = 0;
        node->data = data;
    }

    void insert(TrieNode* root, char* word) {
        TrieNode* temp = root;

        for (int i = 0; word[i] != '\0'; i++) {
            int idx = (int)word[i] - 'a';

            if (temp->children[idx] == NULL)
                temp->children[idx] = &TrieNode(word[i]);

            temp = temp->children[idx];
        }
        temp->is_leaf = 1;
    }

    int search(TrieNode* root, char* word)
    {
        TrieNode* temp = root;

        for (int i = 0; word[i] != '\0'; i++)
        {
            int position = word[i] - 'a';
            if (temp->children[position] == NULL)
                return 0;
            temp = temp->children[position];
        }
        if (temp != NULL && temp->is_leaf == 1)
            return 1;
        return 0;
    }
};
```

#### 4 Exercise 4



##### b

This is not possible. Because for each node, we have to check all nodes connected to it, which takes at least O(mn) time.





#### 5 Exercise 5

The names of all the tree's elements will be kept track of in a linked list, whose set object contains a single tail pointer. In addition, we will store a pointer x.l in each node, which indicating the place of that element in the list.  

MAKE-SET(x) function will creates a new linked list, and adds the label of x to the list, and sets pointer x.l point to that label.  Everything is done in O(1). 

UNION(x,y) has the extra constraint that we union the linked lists of x and y. Since we don't need to change pointers to the head, we can link up the lists in constant time, maintaining UNION's runtime. 
PRINT-SET(x) function  set s=FIND-SET(x).  The linked list's items will then be printed, beginning with the one that x is pointing at, which will start the list as the first element. Since printing takes O(1) and the list has the same number of items as the set, this operation requires a time investment that is linear to the number of set members. 



#### 6 Exercise 6

##### a

Put the residual graph together using the initial flow. A positive 1 capacity should be added to the edge that has been widened. Search for an augmenting path using BFS, if a path is found, the flow can be updated. Otherwise, it remains the same. Since if the augmenting path exists, the flow rased by 1, which is the greatest increase allowed, therefore we only need to execute this once. 

##### b

Put the residual graph together using the initial flow. If the lowered edge had a positive residual capacity and was not at capacity, we could reduce the edge capacity by one without impacting the maximum flow. If not, we add one to the edge's negative capacity and search for an augmenting path that goes from t to s rather than from s to t and includes the lowered edge. 