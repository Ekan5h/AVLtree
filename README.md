# AVL Tree
AVL Tree implementation in C++ using classes and templates.  
This tree is a special case of augmented BST which is a self-balancing tree, ie it prevents skewness while the insertion and deletion operation. Height of each subtree rooted at the current node is stored with the current node.  
For each node:  

>*height = 1 + max( height( left\_child ), height( right\_node ) )*

### Basic Operation
AVL tree always maintains a loose balance ie the heights of the subtrees on both sides of a node can differ by atmost one.  
The balance in the tree heights is achieved by the following two operations:

#### Right Rotation
            y                              x
           / \      Right Rotation        / \
          x   C     -------------->      A   y
         / \                                / \
        A   B                              B   C
Here, x and y are nodes while A, B and C are AVL trees.  
It can be observed that the right height increases by one while the left length may or may not decrease by one for an AVL tree.

#### Left Rotation
            x                              y
           / \       Left Rotation        / \
          A   y      ------------->      x   C
             / \                        / \
            B   C                      A   B
Here, x and y are nodes while A, B and C are AVL trees.  
It can be observed that the left height increases by one while the right length may or may not decrease by one for an AVL tree.  

## Balancing
Following are the states of nodes and the way to balance the tree. Notice that the height difference at the root node is 2 (loose balance is maintained).  
Here x and y are nodes while h,h+1 denote the height of tree.

### Case I
            y                              x
           / \      Right Rotation        / \
          x   h     -------------->     h+1  y
         / \             on y               / \
       h+1 h/h+1                         h/h+1 h
### Case II
            y                              y
           / \       Left Rotation        / \
          x   h      ------------->      z   h
         / \             on x           / \
        h  h/h+1                      h+1 h/h+1

Then,

            y                              z
           / \      Right Rotation        / \
          z   h     -------------->     h+1  y
         / \             on y               / \
       h+1 h/h+1                         h/h+1 h
### Case III
            x                              y
           / \       Left Rotation        / \
          h   y      ------------->      x   h+1
             / \         on x           / \
         h/h+1 h+1                     h h/h+1
### Case IV
            y                              y
           / \      Right Rotation        / \
          h   x     -------------->      h   z
             / \        on x                / \
          h/h+1 h                       h/h+1 h+1

Then,

            y                              z
           / \       Left Rotation        / \
          h   z      ------------->      y  h+1
             / \         on y           / \
          h/h+1 h+1                    h h/h+1
