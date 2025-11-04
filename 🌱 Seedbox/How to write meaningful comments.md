---
created: 2023-08-11
last updated: 2025-11-04
---
up::
tags:: #state/seedling #on/programming/clean_code

# How to write meaningful comments

## What not to comment
Do not make comments that are worthless for the sake of having comments in the code. Some examples:
```
// the class definition of an Action
class Action
{
...
};

// Find node in the given subtree, with the given name and using the given depth
Node* FindNodeInSubtree(Node* subtree, string name, int depth);
```

In general, ==don't comment facts that can be derived quickly from the code itselt==. Quickly is the key word here. If it takes more than a couple of seconds to read the code, you might have to comment it.


## Don't comment bad names, fix them
If you have to explain through a comment that a function/class/variable does something different that what can be expected from its name. The problem is not the lack of comment, it's the name itself.

## Record your thoughts
Most of the time while we work on our code (whether it is writing, testing, reading, fixing, etc.), lots of thoughts and reflections can come to our mind and this insight can be useful. Instead of letting them rest in your memory, write a comment.

For example if there is a known small issue in the coded that does not need a fix. If other solutions have been explored but were not effective. If you have come to a conclusion while working on the code. All these insights are valuable and can be useful for the next person working on the code. Some examples:

```
// Surprisingly, a binary tree was 40% faster than a hash table for 
// this data. The cost of computing a hash was more than the 
// left/right comparisons.

// This heuristic might miss a few words. That's OK; solving this 100% 
// is hard.

// This class is getting messy. Maybe we should create a 
// 'ResourceNode' subclass to  help organize things.
```

## Comment your constants
Sometimes constants are easily recognized by their name(`PI`, `RAD_TO_DEGREE`, `SECONDS_PER_DAY`). However, most of the time they perform a highly specific function and may have values that are not intuitive to a newcomer. ==Write explanatory comments for constants with very specific values or whose function is not very clear==.

```
// Impose a reasonable limit - no human can read that much anyway. const int MAX_RSS_SUBSCRIPTIONS = 1000;

const float image_quality = 0.72f; // users thought 0.72 gave the best size/quality tradeoff

const float heuristic_weight = 0.33f: // value that yielded the best results in multiple experiments
```

## Advertise likely pitfalls
If you are aware that some function has specific pitfalls, comment them so that anyone using it is aware.

## Add "Big Picture" comments
High-level comments that explain abstract information are very rare in codebases. When you have a really big codebase with multiple systems interacting and hundred of classes, having a very high-level explanation on how does systems work and how they are related is very useful for people who do not know or work directly with that code.

## Use summary comments
Summary comments can be used to structure big functions so that they are more easy to read. they also give a quick look of the function's inner doings without having to look at every line of code.

```
void GenerateUserReport()
{
	# Acquire a lock for this user 
	... 
	
	# Read user's info from the database 
	... 
	
	# Write info to a file 
	... 
	
	# Release the lock for this user
	...
}
```