# XORed
## Problem
I was given the following equations. Can you help me decode the flag?

XORed.txt:
```
I was given the following equations. Can you help me decode the flag?
Key 1 = 5dcec311ab1a88ff66b69ef46d4aba1aee814fe00a4342055c146533
Key 1 ^ Key 3 = 9a13ea39f27a12000e083a860f1bd26e4a126e68965cc48bee3fa11b
Key 2 ^ Key 3 ^ Key 5 = 557ce6335808f3b812ce31c7230ddea9fb32bbaeaf8f0d4a540b4f05
Key 1 ^ Key 4 ^ Key 5 = 7b33428eb14e4b54f2f4a3acaeab1c2733e4ab6bebc68436177128eb
Key 3 ^ Key 4 = 996e59a867c171397fc8342b5f9a61d90bda51403ff6326303cb865a
Flag ^ Key 1 ^ Key 2 ^ Key 3 ^ Key 4 ^ Key 5 = 306d34c5b6dda0f53c7a0f5a2ce4596cfea5ecb676169dd7d5931139
```

Author: AC

## Solution
XOR or ^ is the [exclusive or](https://en.wikipedia.org/wiki/Exclusive_or) operator.
A property of XOR is that `(a ^ b) ^ b = a`.

For example, take `(35 ^ 17) ^ 17`.  
```
35 ^ 17 = 50
50 ^ 17 = 35

so, (35 ^ 17) ^ 17 = 35
```
[Here](https://www.youtube.com/watch?v=vzyM_PRaZuc)'s a 7 minute video that goes more in depth.

In the puzzle, the flag is XORed with all 5 keys. So to get the flag, you want to XOR the XORed flag with other XOR keys until you get rid of all the other keys.
`(F^1^2^3^4^5) ^ (2^3^5) ^ (1^3) ^ (3^4)` clears every key except F, giving you the flag.

```
(F^1^2^3^4^5) ^ (2^3^5) = F^1^4 	(keys 2, 3, 5 are removed)
(F^1^4) ^ (1^3) = F^3^4 	        (key 1 is removed, key 3 is reintroduced)
(F^1^4) ^ (1^4) = F	                (keys 1, 4 are removed, leaving the flag)
```

Flag: `flag{n0t_t00_h4rD_h0p3fully}`