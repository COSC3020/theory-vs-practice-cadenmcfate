[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/FgMJElkj)
# Theory vs. Practice

- List 3 reasons why asymptotic analysis may be misleading with respect to
  actual performance in practice.
  

- Suppose finding a particular element in a binary search tree with 1,000
  elements takes 5 seconds. Given what you know about the asymptotic complexity
  of search in a binary search tree, how long would you guess finding the same
  element in a search tree with 10,000 elements takes? Explain your reasoning.

- You measure the time with 10,000 elements and it takes 100 seconds! List 3
  reasons why this could be the case, given that reasoning with the asymptotic
  complexity suggests a different time.

## 1:
1a) Low order terms and constants get ignored in asymptotic analysis. It is possible for algorithms with the same $\Theta (n)$ average time complexity to perform wildly different if there are heaps of constant and low order terms being ignored.

  2a) Asymptotic analysis also doesn't account for the data set. Algorithms will have different performance with different data sets. As we saw with insertion sort, it beats all the other given algorithms when given a sorted data set, even though the median time is the worst.
  
  3a) Performance often depends on the implimentation. You might trade memory for runtime, or runtime for stability, or something to that effect, depending on what you are specifically trying to impliment.

## 2:

We know the average case of search in a binary search tree is $\Theta (logn)$. Since 1,000 elements correlates to 5 seconds of runtime, we can extrapolate that finding the same element in a tree of 10,000 elements will take roughly 1 more second:
  
  $5 \text{ seconds}=c*\text{log}_2 (1000) \approx c*9.97\Rightarrow c\approx0.5$
  
  $0.5\text{log}_2(10000)\approx6.64$ seconds.

## 3:
1) It could be the case that this binary search tree is not balanced. If the first data set of 1000 elements was random, the tree could've been close to balanced, and the desired element could luckily be near the root of the tree. If this new data set of 10000 elements is sorted and the element is unluckily located near the bottom of the tree, this could account for such a drastic runtime increase.
2) It's possible that this data set is too large for our system and performance is being severely throttled. We could be operating on a system like a Pi where RAM is very limited and it is having trouble handling this larger data set in an efficient manner.
3) The times could've been measured inaccurately. Perhaps the search operations weren't local but rather through the internet. Or perhaps the timing included the amount of time it took to take in the data and balance the tree. An inefficient tree-balancing algorithm could slow things down severely with a large data set.

