Conditon Variables 

Hoare vs mesa semantics.

Condition variables comes in two main flavors - one following the hoare semantics and another following the mesa semantics. Before we define the two styles of the semantics and how they differ, let me talk a bit about their history and how they evolved over time.

Condition variables were successors to generic sempahores as synchronization primitives. 

Imagine the following problem - you have a connection pool manager and the current maximum number .. continue to describe the problem. 

In his paper (which I partially skimmed) Hoare described a conditional variable as below: 

Sempahores sometime fall short in a lot of area. You need a combined API which tells you if you have to be put to sleep and should also relinquish the underlying the synchronization
primative, so that when the predicate becomes true, you can be woken-up. A critical question is when the execution of the program comes back to the point in the user-space where the
cv.wait() was called, two of the following things can happen. The cv can garuntee the predicate is still valid, or it might not be valid and you would have re-check it. 

Mesa semantics is a case of leaky abstraction - anyone using it needs to be aware of spurious wake-ups and the fact that a predicate associated with it should be covered in a
while loop. 

In the early 90's Richard Gabriel wrote a piece titled "Worse is better". In there, he discusses two different philosophies for software design - the "New Jersey Approach"
and the "MIT/Stanford Approach". He contrast the two design along the following design dimensions - simplicity, correctness, consistency, completeness. 



