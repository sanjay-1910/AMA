### Slicing in Python

Slicing is used to take a part of a string or list.  
For example, from the word **"Python"**, we can take **"Pyth"** by choosing the start and end positions.
example
```
s = "sanjay"
print(s[1:3])
#output : an 
```

### Rollback

Rollback is used to cancel the changes made in a transaction.  
For example, if money is deducted from one account but not added to another, rollback cancels the deduction.

----------

### Isolation

Isolation means one transaction should not disturb another transaction.  
For example, if two users update the same data at the same time, their changes should not mix.


### Composite Key

A composite key is created using two or more columns together.  
For example, student ID and course ID together can uniquely identify a student’s course record.



### Extract Keys and Values in Dictionary
To extract both keys and values together from a dictionary, we use  `.items()`.  
It returns key and value pairs as tuples, which we can loop through or convert into a list if needed.

----------

### O(log n) Time Complexity

O(log n) means the number of steps increases very slowly as the input size increases.  
For example, in binary search, we reduce the data to half in each step instead of checking every element one by one.


### GROUP BY

GROUP BY is used to collect rows that have the same values.  
For example, grouping employees by department to find the total salary in each department.



### ORDER BY

ORDER BY is used to arrange the result in sorted order.  
For example, sorting students based on marks from highest to lowest.

----------

### Append and Extend
Append is a list method used to add one element to the end of a list.  
For example, if we have a list `[1, 2]` and append `3`, the list becomes `[1, 2, 3]`.

Extend is a list method used to add multiple elements from another list to the end of a list.  
For example, if we have `[1, 2]` and extend it with `[3, 4]`, the list becomes `[1, 2, 3, 4]`.



### Drop, Delete, Truncate

Drop removes the entire table completely along with its structure.  
For example, Delete removes only selected rows, and Truncate removes all rows but keeps the table structure.



### TOP command

The **top** command in Linux is used to see the current running processes in the system.  
It shows details like CPU usage, memory usage, running tasks, and system load in real time, and it automatically refreshes the information every few seconds (usually every 2 seconds)



### Grep Command

Grep is used to search for a word or pattern inside a file.  
For example, searching for the word "error" inside a log file.



### Transaction

A transaction is a group of operations treated as one unit.  
For example, transferring money from one bank account to another.



### Savepoint

A savepoint is a small checkpoint inside a transaction.  
For example, if multiple updates are made, we can go back to a particular step instead of cancelling everything.



### What happens if we try to remove element from the list which is not in the list?

ValueError happens when we give a wrong value to remove from a python list
if we want to remove the element from the list that is not present in the list it will give value error.

