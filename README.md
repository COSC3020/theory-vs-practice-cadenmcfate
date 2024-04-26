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
1a) Low order terms and constants get ignored in asymptotic analysis. It is possible for algorithms with the same $\Theta (n)$ average time complexity to perform wildly different if there are heaps of constant and low order terms being ignored. $n^2+1000n = n^2$ as far as asymptotic analysis is concerned. 

  2a) Asymptotic analysis doesn't pay attention to small data sets. The analysis of an algorithm as $n\rightarrow\inf$ could be misleading when it comes to smaller, more realistically sized data sets. This is shown on the average case runtime graph on slide 37 where, for example, the Mergesort line is well below the line for Mergesort in-place for smaller lists, but they become indistinguishable at $n=1,000,000$. 
  
  3a) Big Oh notation is not strict. An algorithm of $O(n)$ is also an element of $O(n^2)$, $O(n!)$, etc. Same goes for Big Omega notation, just in the other direction. Using loose bounds to describe the runtime of an algorithm can lead to an innacurate picture of its runtime. 
  
## 2:

We know the average case of search in a binary search tree is $\Theta (logn)$. Since 1,000 elements correlates to 5 seconds of runtime, we can extrapolate that finding the same element in a tree of 10,000 elements will take roughly 1 more second:
  
  $5 \text{ seconds}=c*\text{log}_2 (1000) \approx c*9.97\Rightarrow c\approx0.5$
  
  $0.5\text{log}_2(10000)\approx6.64$ seconds.

## 3:
1) It could be the case that this implimentation of a binary search tree has an atypical implimentation of search with a polynomial or exponential runtime complexity. In this case, increasing the size of the data set ten-fold could lead to an increase in runtime twenty-fold.
2) It's possible that this data set is too large for our system and performance is being severely throttled. We could be operating on a system like a Pi where RAM is very limited and it is having trouble handling this larger data set in an efficient manner. Lots of time spent swapping memory, less time spent actually searching.
3) If the runtime for the second search operation was measured innacurately, or the timing included the time that it took to execute the insertion and balancing operations when those times were ignored for the first data set, then this could account for the drastic time increase.

