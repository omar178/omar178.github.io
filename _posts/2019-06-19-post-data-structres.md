---
layout: post
title: "Post Data structres"
date: 2019-06-19 23:45:50
image: '/assets/img/'
description:
tags:
categories:
twitter_text:
---
# Data Structure:

## primitive type:

Boolean, true or false.
    • Character
    • Floating-point numbers, limited precision approximations of real number values.
        ◦ Including Single precision and Double precision IEEE 754 Floats, among others
    • Fixed-point numbers
    • Integer, integral or fixed-precision values.
    • Reference (also called a pointer or handle), a small value referring to another object's address in memory, possibly a much larger one. Importance: As long as one can access a reference to the data, one can access the data through it, and the data itself need not be moved. They also make sharing of data between different code areas easier; each keeps a reference to it.
    • Enumerated type, a small set of uniquely named values.
## Composite types or non-primitive type:
Composite data types are one which can be created by
    • Array (as an example String which is an array of characters)
    • Record (also called tuple or structure)  collection of fields possibly of different data type,For example, a date could be stored as a record containing a numeric year field, a month field represented as a string, and a numeric day-of-month field. A personnel record might contain a name, a salary, and a rank. A Circle record might contain a center and a radius—in this instance, the center itself might be represented as a point record containing x and y coordinates.
    • Union (Tagged union is a subset, also called variant, variant record, discriminated union, or disjoint union)

## Abstract data type
where a data type is defined by its behavior (semantics) from the point of view of a user of the data, specifically in terms of possible values, possible operations on data of this type, and the behavior of these operations. This contrasts with data structures, which are concrete representations of data, and are the point of view of an implementer, not a user.
### List
sequence of infinite elements. Lists are typically implemented either as linked lists (either singly or doubly linked) or as arrays, usually variable length or dynamic arrays.
Operations
Implementation of the list data structure may provide some of the following operations:
    • a constructor for creating an empty list;
    • an operation for testing whether or not a list is empty;
    • an operation for prepending an entity to a list
    • an operation for appending an entity to a list
    • an operation for determining the first component (or the "head") of a list
    • an operation for referring to the list consisting of all the components of a list except for its first (this is called the "tail" of the list.)
    • an operation for accessing the element at a given index.
### Tuple
A Tuple is a collection of Python objects separated by commas. In someways a tuple is similar to a list in terms of indexing, nested objects and repetition but a tuple is immutable unlike lists which are mutable.
Linked List Data Structure

A linked list is a linear data structure, in which the elements are not stored at contiguous memory locations. The elements in a linked list are linked using pointers as shown in the below image:


In simple words, a linked list consists of nodes where each node contains a data field and a reference(link) to the next node in the list.

Key Differences Between Array and Linked List
1. An array is the data structure that contains a collection of similar type data elements whereas the Linked list is considered as non-primitive data structure contains a collection of unordered linked elements known as nodes.
2. In the array the elements belong to indexes, i.e., if you want to get into the fourth element you have to write the variable name with its index or location within the square bracket.
3. In a linked list though, you have to start from the head and work your way through until you get to the fourth element.
4. Accessing an element in an array is fast, while Linked list takes linear time, so it is quite a bit slower.
5. Operations like insertion and deletion in arrays consume a lot of time. On the other hand, the performance of these operations in Linked lists is fast.
6. Arrays are of fixed size. In contrast, Linked lists are dynamic and flexible and can expand and contract its size.
7. In an array, memory is assigned during compile time while in a Linked list it is allocated during execution or runtime.
9. Elements are stored consecutively in arrays whereas it is stored randomly in Linked lists.
10. The requirement of memory is less due to actual data being stored within the index in the array. As against, there is a need for more memory in Linked Lists due to storage of additional next and previous referencing elements.
11. In addition memory utilization is inefficient in the array. Conversely, memory utilization is efficient in the linked list.

### Stack
Stack is a linear data structure which follows a particular order in which the operations are performed. The order may be LIFO(Last In First Out) or FILO(First In Last Out).

### Queue Data Structure

A Queue is a linear structure which follows a particular order in which the operations are performed. The order is First In First Out (FIFO). A good example of a queue is any queue of consumers for a resource where the consumer that came first is served first. The difference between stacks and queues is in removing. In a stack we remove the item the most recently added; in a queue, we remove the item the least recently added.

### Circular Queue
Circular Queue is a linear data structure in which the operations are performed based on FIFO (First In First Out) principle and the last position is connected back to the first position to make a circle. It is also called ‘Ring Buffer’.

In a normal Queue, we can insert elements until queue becomes full. But once queue becomes full, we can not insert the next element even if there is a space in front of queue.
Operations on Circular Queue:
    • Front: Get the front item from queue.
    • Rear: Get the last item from queue.
    • enQueue(value) This function is used to insert an element into the circular queue. In a circular queue, the new element is always inserted at Rear position.
           Steps:
        1. Check whether queue is Full – Check ((rear == SIZE-1 && front == 0) || (rear == front-1)).
        2. If it is full then display Queue is full. If queue is not full then, check if (rear == SIZE – 1 && front != 0) if it is true then set rear=0 and insert element.
    • deQueue() This function is used to delete an element from the circular queue. In a circular queue, the element is always deleted from front position.
## Trees:
Are the best way to represent hierarchical data that couldn’t be represented linearly
depth of a node = no. Of edges to this node
height of a node = no. Of edges from leaf to the longest road of this node
### Binary Tree Data Structure
A tree whose elements have at most 2 children is called a binary tree. Since each element in a binary tree can have only 2 children, we typically name them the left and right child.

A Binary Tree node contains following parts.
    1. Data
    2. Pointer to left child
    3. Pointer to right child
that a tree has at most 2 childern
tree is called proper binary tree if it has either 2 or 0 children
complete binary tree is filled with node except for the leaf
Decision Trees


In Decision Tree the major challenge is to identification of the attribute for the root node in each level. This process is known as attribute selection. We have two popular attribute selection measures:

### Information Gain
When we use a node in a decision tree to partition the training instances into smaller subsets the entropy changes. Information gain is a measure of this change in entropy.
Definition: Suppose S is a set of instances, A is an attribute, Sv is the subset of S with A = v, and Values (A) is the set of all possible values of A, then

### Entropy
Entropy is the measure of uncertainty of a random variable, it characterizes the impurity of an arbitrary collection of examples. The higher the entropy more the information content.
Definition: Suppose S is a set of instances, A is an attribute, Sv is the subset of S with A = v, and Values (A) is the set of all possible values of A, then

### Gini Index
    • Gini Index is a metric to measure how often a randomly chosen element would be incorrectly identified.
    • It means an attribute with lower Gini index should be preferred.
    • Sklearn supports “Gini” criteria for Gini Index and by default, it takes “gini” value.
    • The Formula for the calculation of the of the Gini Index is given below.

What is Support Vector Machine?
An SVM model is a representation of the examples as points in space, mapped so that the examples of the separate categories are divided by a clear gap that is as wide as possible.
In addition to performing linear classification, SVMs can efficiently perform a non-linear classification, implicitly mapping their inputs into high-dimensional feature spaces
What does SVM do?
Given a set of training examples, each marked as belonging to one or the other of two categories, an SVM training algorithm builds a model that assigns new examples to one category or the other, making it a non-probabilistic binary linear classifier.
What Support vector machines do, is to not only draw a line between two classes here, but consider a region about the line of some given width. Here’s an example of what it can look like:
This is the intuition of support vector machines, which optimize a linear discriminant model representing the perpendicular distance between the datasets.
