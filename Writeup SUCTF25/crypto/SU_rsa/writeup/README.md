### SU_rsa

应该算是比较容易分析的简单rsa

由于给的是d的高位，直接可以用得到k
$$
k=(e*d_m-1)//n + 1
$$
由标准关系得到
$$
k*(n-p-q+1)+1==e*d\\
(p+q) =(n+1+k^{-1})\mod e
$$
相当于给出了p%e或者q%e的值，e为256bits，显然small_roots求解一下就行。