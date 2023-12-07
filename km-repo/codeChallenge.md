# [TOPIC] 

# Summary:	
Coding interviews are challenging, it’s always recommended to study the fundamentals: Data structures, algorithms, dynamic programming, etc. even before you start to resolve problems in coding interview platforms.

The purpose of this article is to draft some recommendations on how to approach a coding challenge. You can use these recommendations during your practice or during your actual coding interview.

So, let’s start with an example problem:

Given an array of integers, and an integer representing a target sum. Write a Java program that can read the array and display a pair of numbers that sum up to the target sum.Example:
Input:
[2,7,11,15], target =18
Expected output
7,11

There are many ways to solve the above problem. In this article, we will walk you through the different phases on how to solve a coding problem:

Write test cases
Make a brute force-solution
Refine
Code
Test
 
# Related Topics	
 Lorem ipsum... 
 
# Success Story	
Write test cases (A.K.A understand the problem)
Before writing a single line of code, you must be sure you understand the problem. One common mistake is that people skip the analysis phase to save time. However, wrong inputs lead to wrong solutions.

It’s essential to understand the problems at their basic level: Inputs, outputs and constraints. A good strategy to cope with this is to ask your interviewer as many questions as needed and write test cases to validate your understanding.

TIP: Always let your interviewer know what you’re thinking.

These are some examples of questions and test cases for the above code challenge:

Questions:
Does this array includes negative numbers? No.
What if there is no solution? Return null.
“Display a pair of numbers” means printing the values? No, you need to return an array with those numbers.
What is the expected output if there are more than one possible solution? Display the first solution you find.
What If I receive and empty or negative inputs? Return null.
Test Cases:

TC 1: Happy path
Input:	[2,7,11,15], target =18
Expected output:	7,11
TC 2: There is no pair to achieve the target sum
Input:	[2,7,11,15], target =11
Expected output:	null
TC 3: 2 possible solutions
Input:	[2,7,11,15,3], target =18
Expected output:	7,11
TC 4: negative case,
Input:	[], target =0
Expected output:
 
# Use Cases	
Make a Brute-force solution
Now you have a good understanding of the problem; you need to find a solution ASAP.

A brute-force solution is naïve, you don’t need to worry for efficiency at this point. How would you solve the problem by hand with pen and paper?

For example:

Use two loops (nested) to compare all possible combinations of pairs until we find a pair that sum up to the target sum.
Some interviewers could accept a brute-force solution like this. If that is the case, go for it and start to code. It will be something like this:

code img

But in most cases, interviewers will reject solutions like that because O(n^2) is highly inefficient.

The question now is: How can we improve to O(n) or faster?

So, this brings end to the first part of the article. The answer for that question will be covered in part 2, where I will explain how to refine and how we will get to final solution for this problem.
 
# Sample	
Refine
To find a better solution, it’s critical to identify where the bottleneck is. In the above example, we need to find a way to use a single loop instead of nested loops.

The problem with nested loops is that we repeat operations we already made. But what if we could use a data structure to store the results of those operations instead?

Let’s take this test case:

Refine test case

Maps are often an excellent alternative to nested loops, and they help us to respond to the question “Have I seen this value?”.

At this point, we can say we have another alternative, and this is one is faster: O(n)

Declare a map.
Use a loop to iterate the input array.
Per each element we will calculate the complement to the target sum.
complement =targetSum – current element.
If the complement exists in the map then we found a solution: The current element, and the complement are the solution we are looking for.
If not, we store the current element in the map and continue looping.
The code will look something like this:



But what if the interviewer asks us to improve our solution? Is it possible?
Sometimes it will be possible to improve, or will be beyond our knowledge. But what does improve mean? Improving only sometimes means getting a faster algorithm. Sometimes you need to make tradeoffs, such as sacrificing speed to save storage.

However, in our problem we can go faster by using another common strategy: Use a sorting algorithm first, and then use two pointers:



The pseudo code will be:

Sort the input array.
Start left index at zero and right at the last element of the array.
Loop until left < right/.
Calculate the sum of a[left] + a [right] if it matches the target sum then we have a solution.
If not, we need to adjust indices for bigger or smaller values, and continue with the iterations.
Code
Finally, we found a good solution: We have O(n log n) in time and O(1) in space (since we are not creating new data structures). So, our final code will look something like this:

Good solution

Of course, if this were a real-world scenario, you would have already made many modifications to your code because you realized some errors as you progressed through the different phases.

However, detecting and fixing those errors is part of the development cycle. Whether this is a coding interview or an actual project, you will want to catch and fix as many errors as possible before the delivery.

Test it!

It’s time to get back to the test cases we define at the beginning and use them to validate our solution:

Test it

Output

A better way to test your code is by using Junit with TDD. The funny thing is that if you already grasped this article and didn’t know what TDD is, then you already know TDD, but no one has told you. So let’s discuss it in the following article.
 
# References
 Lorem ipsum... 


This is how you can make a reference

[This is a reference to another link](https://www.terraform.io/docs/providers/azurerm/guides/service_principal_client_secret.html)
