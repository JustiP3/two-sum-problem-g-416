## The Two Sum Problem.

### Intro

In this section, we ask that you approach the problem the same way that you would in an interview.  So that means that you should think about your process, as much as you think about getting to the correct answer.  Try to approach this readme as you would a mock interview.  You want to use these guides to practice the correct habits now, so that your approach becomes second nature by the time you interview.

### The Problem

Given an array of numbers, return every pair of numbers that can be added up to a given target.

### Step 1: Clarify the problem.

In clarifying the problem stage, you determining the scope of the problem, and are trying to determine where to focus your energy before beginning to solve the problem.  Are there points of ambiguity here?  Edge cases that we may need to consider?

> Even if in your consideration, you end up dismissing something, it's generally good to tell your interviewer that you have made the consideration.  An interviewer wants to see that you are going through this process, even if you had the correct understanding all along.  
>
 
**Why this is critical** As a developer, you will be given an assignment and then work will be checked later.  You can waste a lot of time by working towards the wrong problem, or not doing the upfront work of considering the scope of what you are being asked to solve.  
   
**Now, what questions would you ask about this problem?**

Take a minute, and think about it. 

There does not seem to be a lot of ambiguity in this problem, but we can still go through this procedure.

1. *Repeat the question:* 	 "Ok, so you'll provide me an array of numbers, and a sum, and I will need to determine which two numbers add up to the provided sum."  
2. *Determine the scope:* "It sounds like these numbers can be positive or negative.  Although, I'm not sure that will make this problem more complicated.  Also, it sounds like the array can be empty." 

> Here, the interviewee making sure he fully understands the problem.  He searches for ambiguity, and goes to a couple of potential edge cases like handling an empty array or negative numbers.  These are typical edge cases that can generally be leaned on.
> 
> He cannot see whether this changes the problem at all, but still let's the interviewer aware that he is trying to cast a wide net, and consider the scope of the problem.  He also gives the interviewer an opportunity to focus his energy in certain areas.  If the interviewer wants him to skip over this phase and get straight toward solving the problem, the interviewer will point him in that direction.

3. *Give an example of the problem and solution*: 
Ok, so let's say we are given an array of numbers, [5, -2, 4, 9, 1] and need to see which numbers add up to 6.  Here, the pair of integers would be 5, and 1.

> If the interviewer provided us with an example, we would have leaned on the provided example - as the interviewer may have chosen it for a reason.  Here, instead we come up with our own.
> 
> In this step, the interviewee moves into the first stage of problem solving, by choosing an example and providing a solution.  He does not come up with an algorithm at this point, but rather just makes the goal concrete.  When choosing an example, it's a good idea to choose something complicated enough that it solves the meat of the problem, yet easy enough that one does not get distracted.  Generally, choosing three to six elements in a collection is fine.  Edge cases can be delayed to solve later on.  

### Problem Solving

Now that we feel comfortable in understanding the problem, we move onto the problem solving stage. 

1. Break down what your brain is doing

	Take another look at our example.
	
	```javascript
	let sum = 6
	let a = [5, -2, 4, 9, 1]
	
	function twoSum(sum, a){
	
	}
	
	twoSum()
	[
		[5, 1]
	]
	```
	
	Ok, so your brain is able to determine that given the above array, the two elements that add up to 6 are 5 and 1.  So how is brain accomplishing that task?  If you slow down, and try to move methodically, are you able to interpret what your brain is doing?
	
	```text 
	This is your thinking space.
	
	
	
	
	
	
	Some thinking.
	
	
	And some more.
	
	Ok, here is some thinking.
	
	
	```
	

2. Lean on the brute force solution

	Ok, so one option that is generally available to you is the brute force solution.  By brute force, we mean try every permutation to find all of the answers.  So what does this mean here?
	
	Here, it means that we potentially can arrive at a sum of six with any two numbers in the array.  So we can simply loop through all of the elements in the array, and then examine every other element in the array to determine if there is a sum that matches 6.  If the sum matches six we push the pair of numbers into an array.
	
	After offering this up as a solution, we should then want to consider what the big o of this operation is.  Give it a shot.
	  
  ```text 
	Think about big O.
	
	
	O
	
	Oh man
	
	What kinda Oh?
	
	A big O.
	
	
	And some more.
	
	Yeppers.
	
	
	```

3. Consider other data structures 

	So essentially, what we are employing is a nested loop.  For each element, go through every other element and see if it matches.  So the cost of this is n, n times, or O(n^2).  That is not a great time efficiency, so let's see if we can do better.  Any ideas?

```javascript
let sum = 6
let a = [5, -2, 4, 9, 1]
```

Ok, so with each element, we are then going through every other element to see if the one that matches to six.  So start with the number five, then go through every other number to see if it matches six.  But wait, how many numbers can add up to 6 given the number 5?  Only one number, 1.  Ok, then we spend the rest of the time going through the array until we hit the number one.

Any ideas of how we can do better?

What if we sort the array?  How does that help?  

```text 
This is your thinking space.
	
	
	
	
	
	
Some thinking.
	
	
And some more.
	
Ok, here is some thinking.	
```

Then once we sort the array, we can employ binary search to see if the matching element exists.  So what is the cost of this.  Well we have the up front cost of sorting the array.  You can employ merge sort, for a cost of  O(n log n).  Then for every element in the array, we employ binary search.

Run through the our example, and make sure this technique works.

As an activity in this lab, we'll let you translate that process into code.

3. Can we do better?

Ok, so now we are employing binary search, to see if a number is in an array.  Every time we see ourselves doing binary search, we should consider a better alternative.  

What is that alternative?  

A hash.  Hashes are good at seeing if a number exists.  This problem is one of repeated lookup.  For every element in an array, we ask we try to see if six minus that number exists?  This is repeated lookup.

Run through the our example, and make sure this technique works.  Once you have confirmed that this works, consider the cost of this function.

What is the cost?

Well there are really two steps.  The first is to place each element into a hash.  And then the second step is to go through each element and see if the matching element exists.  So n times, find something in a hash, which costs O(1).  So the cost of this is O(n) + O(n) which reduces O(n).


### Translate to code

At this point it seems like we have a working solution.  Now, we need to translate it into code. 

Here, you will have the benefits of tests, but in a coding interview, you likely will not have it.  So break your problem into multiple methods, and upon solving each one, have the discipline to test it out on an example.  

Then you want to check edge cases: does your code handle an array that is null?  What should be returned if there are no matches?  

Finally, if time permits, see if there are any shortcuts you can employ.  For example, if you know that our array does not accept negative numbers, then we can eliminate any number greater than our sum as a potential candidate as a solution to the two-sum problem.

### Get to it

We will ask you to implement each of the implementations covered by the two sum problem.     