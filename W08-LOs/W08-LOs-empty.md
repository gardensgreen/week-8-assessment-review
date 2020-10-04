# Binary Trees, Graphs, and Network Knowledge (Week 8) - Learning Objectives

## Assessment Structure

-   1 hour, 40 minutes
-   Mixture of multiple choice (15-20), free response (1-3) and VSCode (1-3) problems, each with multiple specs.
    -   Free response just requires enough detail to answer the question, 1-3 sentences. As long as you are able to explain the concept and answer all aspects that it asks, you are good.
    -   Coding problems will have specs to run (`npm test`) and check your work against
-   Standard assessment procedures
    -   You will be in an individual breakout room
    -   Use a single monitor and share your screen
    -   Only have open those resources needed to complete the assessment:
        -   Zoom
        -   VSCode
        -   Browser with AAO and Progress Tracker (to ask questions)
        -   Approved Resources for this assessment:
        -   MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript

## Binary Trees (W8D2) - Learning Objectives

### Binary Trees

1.  Explain and implement a Binary Tree.

        - A binary tree is a type of graph with stricter rules. (Collection of nodes and edges between them.)
        - Binary trees cannot have any cycles, which are edges that form a loop between nodes
        - In Computer Science, we only consider rooted trees. Rooted trees are trees that have a root node that is able to access all other nodes.
        - Important tree terminology:
            - root: The single node of a tree that can access every other node through edges.
            - parent node: A node that is connected to lower nodes in the tree. If a tree only has one node, it is not a parent node because there are no children.
            - child node: A nide that is connected to a higher node in the tree. Every node except for the root is a child node of some parent.
            - sibling node: Nodes that have the same parent.
            - leaf node: A node that has no children (at the ends of the branches of the tree)
            - internal node: A non-leaf node (aka Parent)
            - path: A series of nodes that can be traveled through edges.
            - subtree: A smaller portion of the original tree. Any node that is not the root node is itself the root of a subtree.
        - Tree Basics:
            - A non-empty tree has to have a root.
            = A tree doesn't have any parent node's if there are no children.
            - What's the min/max number of parent and leaf nodes for a tree with 5 nodes?
                - Implementing in a chain results in max number of parents and min number of leaves: 4 parents 1 leaf
                - Implementing as a balanced tree results in min number of parents and max number of leaves: 2 parents, 3 leaves
        - Binary Tree Implementation: All that we need in order to implement a binary tree is a TreeNode class that can store a value and references to a left and right child. We can create a tree by assigning the left and right properties to point to other TreeNode instances:

        ```js
        class TreeNode {
          constructor (val){
            this.val = val;
            this.left = null;
            this.right = null;
          }
        }

2.  Identify the three types of tree traversals: pre-order, in-order, and post-order.

        - Pre-order: Values are accessed as soon as the node is reached.
        - In-order: Values are accessed after we have fully explored the left but before we explore the right branch.
        - Post-order: Values are accessed after all of our children have been accessed.
        - *Breadth First: The previous three traversal types are Depth First Traversals. Breadth first accesses values of node by level, left to right, top to bottom.

3.  Explain and implement a Binary Search Tree.

        - A binary search tree is a binary tree with the added stipulation that all values to the left of a node are less than its value and all values to the right are greater than its value.
        - Example of BST with an insert method:

    ```javascript
    class BST {
        constructor() {
            this.root = null;
        }

        insert(val, currentNode = this.root) {
            let newNode = new TreeNode(val);
            if (!this.root) {
                this.root = newNode;
                return;
            }

            if (val < currentNode.val) {
                if (!currentNode.left) {
                    currentNode.left = newNode;
                } else {
                    this.insert(val, currentNode.left);
                }
            } else {
                if (!currentNode.right) {
                    currentNode.right = new TreeNode();
                } else {
                    this.insert(val, currentNode.right);
                }
            }
        }
    }
    ```

## Graphs (W8D3) - Learning Objectives

### Graphs

1. Explain and implement a Graph.

    - A graph is the same as a tree without the strict rules
    - A graph can:
        - Consist of any collection of nodes and edges (no limits on connections)
        - Have cycles
        - Have disconnected portions (a forest, with multiple trees, for example)
        - Be missing a root node (doesn't have to have one node that connects to everything)
    - In a tree, we had an idea of children and parents, in a graph we have neighbors (no hierarchy).
    - Just like how we could represent trees in multiple ways, we can represent graphs many ways as well, with advantages/disadvantages to each:
        - Adjacency Matrix - (2D array):
            - It is visually clear what is happening
            - One axis (outside array) has an entry (inner array) for each node in the graph. If one node is connected to another node in the graph, our entry in the inner array is set to true. Otherwise the entry is set to false
        - Adjacency List - (POJO):
            - Object where every value in the graph has a key.
            - Value for the key is an array with each other node that it is connected to (neighbors)
            - Easy to iterate through
            - Doesn't take up as much space as an Adjacency Matrix or Node
            - Can refer to the entire graph by referencing the object.
        - Nodes:
            - Similar to linked list/tree implementations.
            - Track the value and the neighbors array as instance variables on the node
            - We don't have a reference to the overall graph with this implementation

2. Traverse a graph.
    - We can use recursion or iteration to traverse each node.
    - We generally want to keep track of each node that we've visited already so that we don't get trapped in cycles. Easiest way to to do this is to keep a Set variable that we update as we traverse to each node.
      -3 The main difference between a depth-first search and a breadth-first search is utilizing a stack vs. a queue

## Network Knowledge (W8D4) - Learning Objectives

### Network Models

1. Describe the structure and function of network models from the perspective of a developer.

### IP Suite

1. Identify the correct fields of an IPv6 header.
2. Distinguish an IPv4 packet from an IPv6.
3. Describe the following subjects and how they relate to one another: IP Addresses, Domain Names, and DNS.
4. Identify use cases for the TCP and UDP protocols.
5. Describe the following subjects and how they relate to one another: MAC Address, IP Address, and a port.
6. (Optional) Identify the fields of a TCP segment.

-   This is optional additional information! I've still included it here since it is listed on the AAO platform, but know that this material is more in depth than you need to know.

7. (Optional) Describe how a TCP connection is negotiated.

-   This is optional additional information! I've still included it here since it is listed on the AAO platform, but know that this material is more in depth than you need to know.
-   Starting a Connection

8. Explaining the difference between network devices like a router and a switch.

### Network Tools

-   These are tools to be able to see some of the above topics presented on your own machine. Their use, as in commands that you would run or how to read the output, are not assessable material, they are simply included to provide an opportunity to see the some of the above concepts in action.

1. Use `traceroute` to show routes between your computer and other computers.
2. Use Wireshark to show/inspect network traffic.
