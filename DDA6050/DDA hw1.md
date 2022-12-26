## DDA 6050 Assignment 1



#### 1   Exercise 1 Sorting, growth rates, costs

(a) 

Average time:  O(nlogn)

Space complexity:  O(logn)



(b)

Worst-case time: O(n^2^)

Space complexity:  O(n)

At the worst-case, the array is increasing or decreasing. If the array is increasing, each time we pick the  number which is the smallest number that bigger than the last number we picked, therefore we need to pick n-1 number, and do the comparison n-1 times. 



(c) 

<img src="DDA 作业.assets/image-20221009170840525.png" alt="image-20221009170840525" style="zoom:80%;" />



The worst-case time complexity of the insertion sort  is O(n^2^), happens when these numbers are reversed order. 

Time complexity of the second phase in worst-case:  T(n) = n/10 * T(10) =  n/10 * 10^2^ = 10n = O(n)





#### 2    Exercise 2 

(a)  False.  Heapsort executes in worst-case is still O(nlogn). Because for each node which is not a leaf node,  to make the heap in order, we need to do the  exchange logn times. 

(b)  True. In worst-case, each number need to compare with every number before it. T(n) = 1 + 2 + ... + n-1 = (1 + n-1) * n/2 = n^2^/2 

(c)  False. In worst-case, the array is in reversed order, almost every two numbers will be compared.  Shellsort executes in worst-case O(n^2^).

(d)  False. Insertion sort in best case is O(n).

(e)  False. Access speed for m elements in a splay tree is O(MlogN), and for a linked list is O(mn)



#### 3 Exercise 3 Solve the following recurrence relations using the iteration technique

##### a.

##### Recursion tree

<img src="DDA 作业.assets/image-20221010213326525.png" alt="image-20221010213326525" style="zoom:67%;" />

##### Substitution method

(1) Inductive hypothesis: T(n) ≤ c2^n^

(2) Base case:  IH hold for 0 < n < 3

(3) Inductive step: 

Let k >= 3, Assume that the IH holds for all n such that 1 ≤ n < k 
$$
\begin{align}
T(k) &= T(k - 1) + T (k/2) + k \\
 	 &≤ c2^{k-1} + c2^{k/2} + k \\
 	 &= (c/2 + c/2^{k/2}+k/2^k)*2^k \\
 	 &= [c(1/2 + 1/2^{k/2})+k/2^k]*2^k \\
	 &≤ [c(1/2 + 1/2^{3/2})+3/8]*2^k \\
	 &≤ (0.9c + 0.375)*2^k
 
\end{align}
$$
Set c = 10, 
$$
\begin{align}
T(k) &≤ (0.9c + 0.375)*2^k \\
	 &≤ c2^k
 
\end{align}
$$
(4) Conclusion: By induction, T(n) ≤ c2^n^ for all n > 0



##### b.

##### Recursion tree

<img src="DDA 作业.assets/image-20221010213253511.png" alt="image-20221010213253511" style="zoom:67%;" />



#### 4 Exercise 4

- **a. 𝑇 (𝑛) = 4𝑇 (𝑛/3) + 𝑛 lg 𝑛.** 

​		$a = 4,\ b=3,\ log_ba= log_34 ≈ 1.26,\ f(n) = nlgn < n^{1.26}, f(n) = O(n^{log_ba})$  

​		By case one of general version of Master Theorem:  $T(n) = \Theta(n^d) =\Theta(nlgn)$ 



- **b. 𝑇 (𝑛) = 3𝑇 (𝑛/3) + 𝑛/ lg 𝑛.** 

$$
\begin{align}
&Let\ g(n)=T(n)/n,\\ \\
&n*g(n)=3*(n/3)*g(n/3)+n/logn\\ \\
&g(n)=g(n/3)+1/logn\\
&=1/logn + 1/log(n/3) + 1/log(n/9)+...\\
&=\Theta(1/logn + 1/log(n/2) + 1/log(n/4)+...)\\
&= \Theta(1/ logn + 1/ (logn − 1) + 1/ (logn − 2) + 1/ (logn − 3) + ...)\\
& = \Theta(1+1/2+1/3+...+1/logn)\\
&= \Theta(log log n)\\\\
&T(n)=\Theta(nlog log n)
\end{align}
$$

- **c. 𝑇 (𝑛) = 4𝑇 (𝑛/2) + 𝑛^2^√ 𝑛.** 

​		$a = 4,b=2, d = 5/2, a < b^d  $ 

​		By case two of  Master Theorem :  $T(n) = \Theta(n^d) =\Theta(n^{5/2})$ 



- **d. 𝑇 (𝑛) = 3𝑇 (𝑛/3 − 2) + 𝑛/2.** 

  - For upper bond,  Let  $T(n) <= S(n),\ S(n) = 3S(n/3) + n/2$. 

    $a = 3,\ b=3,\ d = 1, a = b^d  $ 

    By case one of  Master Theorem :  $S(n) = \Theta(nlogn),\ T(n) = O(nlogn)$ 

  - For lower bond,  Let  $T(n) >= U(n), \ U(n)=T(n-3),\ U(n) = 3U(n/3) + (n-3)/2$ 

    $a = 3,\ b=3,\ d = 1, a = b^d  $ 

    By case one of  Master Theorem :  $U(n) = \Theta(nlogn),\ T(n) = \Omega(nlogn)$ 

  - Therefore, $ \ T(n) =\Theta(nlogn)$



- **e. 𝑇 (𝑛) = 2𝑇 (𝑛/2) + 𝑛/ lg 𝑛**

$$
\begin{align}
&Let\ g(n)=T(n)/n,\\ \\
&n*g(n)=2*(n/2)*g(n/2)+n/logn\\ \\
&g(n)=g(n/2)+1/logn\\
&=1/logn + 1/log(n/2) + 1/log(n/4)+……\\
&= \Theta(1/ logn + 1/ (logn − 1) + 1/ (logn − 2) + 1/ (logn − 3) + ...)\\
& = \Theta(1+1/2+1/3+...+1/logn)\\
&= \Theta(log log n)\\\\
&T(n)=\Theta(nlog log n)
\end{align}
$$



#### 5 Exercise 5 Monge Array 

**a**. 

If 2x2 array is a Monge, 𝐴[𝑖, 𝑗] + 𝐴[𝑖 + 1, 𝑗 + 1] ≤ 𝐴[𝑖, 𝑗 + 1] + 𝐴[𝑖 + 1, 𝑗], i = 0, 1, j = 0, 1



For array with 2 rows and m columns,  each adjacent 4 square numbers of it are small Monge array

Suppose we have two Monge array: 𝐴[𝑖, 0], 𝐴[𝑖 + x, 1], 𝐴[𝑖, 1] , 𝐴[𝑖 + x, 0] and 𝐴[𝑖 + x, 0], 𝐴[𝑖 + y, 1], 𝐴[𝑖 + x, 1], 𝐴[𝑖 + y, 0], where 0 < i, x, y  < m, i + y < m,   x ≠ y. Then 𝐴[𝑖, 0] + 𝐴[𝑖 + x, 1] ≤ 𝐴[𝑖, 1] + 𝐴[𝑖 + x, 0] and 𝐴[𝑖 + x, 0] + 𝐴[𝑖 + y, 1] ≤ 𝐴[𝑖 + x, 1] + 𝐴[𝑖 + y, 0]. Plus them together, we can find that A[𝑖, 0] + 𝐴[𝑖 + y, 1]≤ 𝐴[𝑖, 1] + 𝐴[𝑖 + y, 0]. Therefore, for array with 2 rows and n columns, if 𝐴[𝑖, 𝑗] + 𝐴[𝑖 + 1, 𝑗 + 1] ≤ 𝐴[𝑖, 𝑗 + 1] + 𝐴[𝑖 + 1, 𝑗], the array is Monge array. 



Then consider a m x n array, each adjacent 2 rows of it is a Monge array. 

Suppose we have two Monge array,  𝐴[𝑖, 𝑗] , 𝐴[𝑖 + x, 𝑗 + y], 𝐴[𝑖, 𝑗 + y], 𝐴[𝑖 + x, 𝑗]  and  𝐴[𝑖, 𝑗 + z], 𝐴[𝑖 + x, 𝑗 + y], 𝐴[𝑖, 𝑗 + y], 𝐴[𝑖 + x, 𝑗 + z], where 0 < i, x  < m,  0 < j, y, z < n, i + x < m,( j + z, j + y) < n , z ≠ y

We have 𝐴[𝑖, 𝑗] + 𝐴[𝑖 + x, 𝑗 + y] ≤ 𝐴[𝑖, 𝑗 + y] + 𝐴[𝑖 + x, 𝑗]  and  𝐴[𝑖, 𝑗 + y] + 𝐴[𝑖 + x, 𝑗 + z] ≤ 𝐴[𝑖 + x, 𝑗 + y] + 𝐴[𝑖, 𝑗 + z]. 

Plus them together, we can find that  𝐴[𝑖, 𝑗] + 𝐴[𝑖 + x, 𝑗 + z] ≤ 𝐴[𝑖, 𝑗 + z]+ 𝐴[𝑖 + x, 𝑗]

Therefore, the m x n  array is a Monge array.



**b. **Change 22 to 24.

<img src="DDA 作业.assets/image-20221009194342831.png" alt="image-20221009194342831" style="zoom: 67%;" />



**c**.

Suppose f(i + k) < f(i) , where 0 < i, k <= n, i + k <= n 

Because A[i, f(i)] and A[i + k, f(i + k)] are the minimum element of their rows, A[i, f(i + k)] + A[i + k, f(i)]  >  A[i, f(i)] + A[i + k, f(i + k)], which is not a Monge array. Therefore, there must be f(i) <= f(i + k), and 𝑓 (1) ≤ 𝑓 (2) ≤ ⋯ ≤ 𝑓 (𝑚) for any 𝑚 × 𝑛 Monge array.



**d**.

From problem **c** we know that index of the column containing the leftmost minimum element of row i is smaller than the index of row i + 1. Then, for each 1 < i < n/2 - 1, f(2i) <= f(2i + 1) <= f(2i + 2). Because we already know the even rows' answer, we only need to search f(2i + 2) - f(2i) + 1 numbers for f(2i + 1).

T(2n) = (f(2n) - f(2n - 2) + 1) + (f(2n - 2) - f(2n - 4) + 1) ... (f(4) - f(2) + 1) + f(2) = f(2n) - f(1) + 2n

Therefore, T(n) = f(n) - f(1) + n

In worst-case, we must scan all m columns.

T(n) = f(n) - f(1) + n = O(m + n) 



**e**.

T(n) = T(n/2) + O(m + n) 



Assume T(n) = O(m + n log m)

T(n) = T(n/2) + O(m + n) = O(m + n/2 log m) + O(m + n) = O(m + n log m)

 By induction, T(n) =  O(m + n log m)



#### 6 Exercise 6 Longest Zig-Zag Subsequence



```
input: int num[n]

dp[i][0] = maximum length subsequence ending at i such that num[i] > num[i-1]
dp[i][1] = maximum length subsequence ending at i such that num[i] < num[i-1]
```



**recursive formulation**

```
dp[i][0] = dp[i-1][1] + 1 	 if num[i] > num[i-1]
dp[i][0] = 1				 other cases

dp[i][1] = dp[i-1][0] + 1	 if num[i] < num[i-1]
dp[i][1] = 1				 other cases
```



**pseudocode**

```
input: int num[n]

int dp[n][2], set all elements in dp to 1;
int sizeOfLongestSequence = 0;

for(i : from 1 to n){
	if(num[i] > num[i-1]){
		dp[i][0] = dp[i-1][1] + 1;
		sizeOfLongestSequence = max(dp[i][0], sizeOfLongestSequence)
	}
	else if(num[i] < num[i-1]){
		dp[i][1] = dp[i-1][0] + 1;
		sizeOfLongestSequence = max(dp[i][1], sizeOfLongestSequence)
	}
}

output: sizeOfLongestSequence
```



