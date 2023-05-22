# Concrete Mathematics
## Chapter 1 Recurrent Problems
### 1.1 The tower of Hanoi
The problem is to move all the plates in one peg to another without breaking the rule that smaller plates are always put on larger ones. We are asked to calculate the minimum number of steps needed to do that. It is obvious that we need 0 step for 0 plate, 1 for 1 plate and 3 for 2 plates **(SMALL CASES MATTER)**.  
To solve this problem, one should agree that without moving the largest plate at the bottom to the target peg, the mission is impossible.  
Only when the smaller plates have been moved to and put well on the third peg can one move the largest plate to the target peg. If we denote the minimum of steps needed to move $n$ plates from one peg to another as $T_n$, then  
$$T_{n} \le 2\cdot T_n + 1 \tag{1.1.1}$$  
The righthand side of the inequality is the number of steps that suffice the move. Is that necessary, we may ask? To get the answer, we should first focus on where extra steps may be counted. Moving the upper $(n-1)$ plates from one peg to another takes no less than $T_{n-1}$ steps, as we assumed, and those plates have to be moved twice: one for making the largest bottom plate be moved, the other for moving themselves. Therefore, $2\cdot T_{n-1}$ is a necessary part of $T_n$.  
We cannot move the largest bottom peg to the target peg without paying anything, while we can do that in more than two steps. This indicates that 1 is the minimum for moving the largest plate.  
So, putting both considerations together, we have  
$$T_{n} \ge 2\cdot T_n + 1 \tag{1.1.2}$$
Thus, 
$$T_{n} = 2\cdot T_n + 1 \tag{1.1.3}$$
With a little more effort, We can get the closed form of $T_n$:
$$T_{n} + 1 = 2\cdot T_n + 2 = 2\cdot (T_{n-1} + 1), T_0 = 0 \tag{1.1.4-a}$$
$$T_{n} + 1 = 2^n + T_0 = 2^n\tag{1.1.4-b}$$
$$T_{n} = 2^n - 1 \tag{1.1.4-c}$$  
We can easily see the result works with cases of 0, 1 and 2 plates. By substituting (1.1.3) with (1.1.4-c), we are more convinced that (1.1.4-c) is the correct answer.

### 1.2 Lines dividing the plane
What is the maximum number of regions defined by $n$ lines in a plane?  
To solve this problem, consider the facts:  
1. **(SMALL CASES DO MATTER)** 1 line can define 2 regions and 2 lines can define 4.  
2. One region can be divided to at most 2 region when a new line is added to the plane.
3. The $n$-th line (for $n \lt 0$) increases the number of regions by $k$ if and only if it splits $k$ of the old regions. 
4. The $n$-th line splits $k$ old regions if and only if it hits the previous lines at $(k-1)$ different places.
5. Two lines can intersect in at most one point.

Thus, we make $L_n$ be the maximum number of regions $n$ lines can define in a plane, and we have:  
$$L_n \le L_{n-1} + n \tag{1.2.1}$$
If every time we add a new line in such a way that it is not parallel to any of the other $k$ lines, and it does not go through any of the intersect points, we can have $(k+1)$ more regions, which is to say:  
$$L_n \ge L_{n-1} + n \tag{1.2.2}$$
Thus,  
$$L_n = L_{n-1} + n \tag{1.2.3}$$
The closed form of the result is: 
$$L_n = 1 + \frac{n\cdot (n + 1)}{2} \tag{1.2.4}$$
