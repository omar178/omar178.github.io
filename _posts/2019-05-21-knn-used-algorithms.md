---
layout: post
title: "KNN used Algorithms"
date: 2019-05-21 12:53:24
image: '/assets/img/'
description:
tags:
- Machine learning
- Algorithms
categories:
twitter_text:
---
# K-d tree formation — Speeding up K-NN
One way is to construct a sorted hierarchical data structure called k-d tree or k-dimensional tree. A k-dimensional tree is a binary tree. We illustrate its process of formation below through a working example for easy understanding.

Consider a three dimensional (training) data set shown in Table 0, below left. For convenience of representation we have not shown the fourth column containing class labels for each data record. We have three attributes ‘a’, ‘b’ and ‘c’. Among the three, attribute ‘b’ has the greatest variance. We sort the data set on this attribute (Table 1) and then divide it into two parts at the median.

    Table 0  			    Table 1		
  Unsorted data			 Sort on column b		
a	b	c		a	b	c
22	38	21		6	2	9
4	8	6		4	8	6
2	14	3		2	14	3
8	20	12		8	20	12
10	26	18		10	26	18
12	32	15		12	32	15<---
18	56	33		22	38	21
16	44	27		16	44	27
20	50	24		20	50	24
14	62	30		18	56	33
6	2	9		14	62	30

The median is at (12,32,15). Dividing Table 1 into two parts at the median gives us two tables, Table 2 and Table 3 as below. Next, from among the remaining (two) attributes, we select that dimension that has the greatest variance. This dimension is ‘c’. Again, we sort the two tables on this dimension and then break them at the respective medians.

Break Table 1 on median (12,32,15)						
        >			       <
     Table 2			     Table 3		
a	b	c		a	b	c
22	38	21		6	2	9
16	44	27		4	8	6
20	50	24		2	14	3
18	56	33		8	20	12
14	62	30		10	26	18

Tables sorted on column C are as below.

Sort Table 2 on column c 	Sort Table 3 on column c		
     Table 3			    Table 4		
a	b	c		a	b	c
22	38	21		2	14	3
20	50	24		4	8	6
16	44	27<---		6	2	9<---
14	62	30		8	20	12
18	56	33		10	26	18

Table 3 is next split at median, (16,44,27), and Table 4 is split at median, (6,2,9), as below.

        Break Table 3 on median  (16,44,27)						
         >				<
14	62	30		22	38	21
18	56	33		20	50	24
             Break Table 4 on median (6,2,9)
        >				<		
8	20	12		2	14	3
10	26	18		4	8	6

We have now four tables here. If we decide to end the splitting process then these four tables are tree-leaves. Else, next we would split by sorting column ‘a’ (and next split on ‘b’, ‘c’…).

Once this data structure is created, it is easy to find out the (approx) neighborhood of any point. For example, to find the neighborhood of a point (9,25,16), we move down the hierarchy left or right. First, at root node, we compare 25, with the value at the root (from column b) then at the next node we compare, 16 (from column c) and lastly 9. The data at the leaf are possible (but not necessarily) nearest points. Generally distances from the points in the table on the other side of this node are also calculated in order to discover nearest points. One may also move a step up the tree to discover nearest points. Incidentally, the median points (12,32,15, for example) are also made a part of either left or right sub-tree.
