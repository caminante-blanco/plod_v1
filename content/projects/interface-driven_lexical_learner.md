+++
date = '2025-12-27T20:32:14-08:00'
title = 'Interface-Driven Lexical Learner (Draft)'
tags = ['linguistics', 'drafts'] 
+++
## The Author's apology for his draft
This post is currently in draft form. This means that you should take nothing in the following paragraphs as true, verified, original, intentional, or edifying. This blog post is provided 'as is', without warranty of any kind, expressed or implied. Please put no more faith in it than you would an essay produced by a typewriter-wielding monkey. I **will** eventually finish this post properly, and once that happens, I will stand behind my words fully.

I am publishing this post now because having something publicly accessible helps to keep me honest, and provides some much-needed encouragement to actually see the work to completion. Citations, verifications, and elucidations to follow.

## Never solve a deterministic problem probablistically
XOR is one of the standard bitwise operators, and is probably one of the first logic gates you will learn in any CS class. It is so important that it's been part of Intel's instruction sets since the 8008. In just about any programming language, you can express it with just one operator:

```python
#binary 0
a = 0b0

#binary 1
b = 0b1

#Prints 1
print(a ^ b)

#Prints 0
print(a ^ a)
print(b ^ b)
```
XOR is easy to understand, and completely deterministic (0 ^ 0 will always be 0, and 0 ^ 1 will always be 1). But imagine someone put the XOR gate in a black box, so that you could only see the inputs and outputs, and they asked you to model its effects. You might implement something like this:

```python
import numpy as np

w1 = np.array([[1, 1], [1, 1]])
b1 = np.array([0, -1])

w2 = np.array([[1], [-2]])
b2 = np.array([0])


def relu(z1):
    return np.maximum(0, z1)


def xor(x):
    x = np.array(x)
    y = relu(x @ w1 + b1) @ w2 + b2
    return y[0]

#Prints 0
print(xor([1, 1]))

#Prints 1
print(xor([0, 1]))
```
That is a multi-layer perceptron (MLP), a very simple neural network. XOR is deterministic so we can expect that over enough training passes, our MLP will eventually look something like the model above. This model perfectly approximates XOR, but it is obviously inferior. We have replaced a simple logic gate with over a dozen floating point operations, and traded `0 ^ 0 = 0` for `0 ^ 0 ≈ 0`. In this case the unknown nature of the modeled function made that tradeoff necessary, but in any other situation it would be a ridiculous exercise in overengineering. 


## What is this project?
The *Interface-Driven Lexical Learner* (IDLL) is an attempt to 

---
**For now that's all folks!**
