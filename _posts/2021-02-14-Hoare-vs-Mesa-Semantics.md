Conditon Variables - Hoare vs Mesa semantics.

Condition variables comes in two main flavors - one following the hoare semantics and another following the mesa semantics. In his [paper|https://john.cs.olemiss.edu/~dwilkins/Seminar/S05/Monitors.pdf] Hoare described a conditional variable as below: 

1. "Note that a condition "variable" is neither true nor false; indeed, it does not have any stored value accessible to the program. In practice, a condition variable will be represented by an (initially empty) queue of processes which are currently waiting on the condition"
 
2. "The acquire procedure does not have to retest that busy has gone false when it resumes after its wait, since the release procedure has guaranteed that this is so; and as mentioned before, no other program can intervene between the signal and the continuation of exactly one waiting program."

3. "If more than one program is waiting on a condition, we postulate that the signal operation will reactivate the longest waiting program. This gives a simple neutral queuing discipline which ensures that every waiting program will eventually get its turn."

The Mesa Semantics 

Sempahores sometime fall short in a lot of area. You need a combined API which tells you if you have to be put to sleep and should also relinquish the underlying the synchronization primative, so that when the predicate becomes true, you can be woken-up. A critical question is when the execution of the program comes back to the point in the user-space where the cv.wait() was called, two of the following things can happen. The cv can garuntee the predicate is still valid, or it might not be valid and you would have re-check it. 

Mesa semantics is a case of leaky abstraction - anyone using it needs to be aware of spurious wake-ups and the fact that a predicate associated with it should be covered in a
while loop. 



In the early 90's Richard Gabriel wrote a piece titled "Worse is better". In there, he discusses two different philosophies for software design - the "New Jersey Approach"
and the "MIT/Stanford Approach". He contrast the two design along the following design dimensions - simplicity, correctness, consistency, completeness. 



