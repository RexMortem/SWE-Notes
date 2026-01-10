
## Bit Shifts and Powers of 2

Doing a bit shift (`num << shift`) multiplies num by $2^{\text{shift}}$ (this is because it shifts num in binary to the left by `shift` places).


> [!note]- Power of 2
> Since $2^{0} = 1$, we have `1 << shift` equal to $2^{\text{shift}}$. So whenever you need $2^{n}$:
> ```python
> n = 5
> print(1 << n) # 2^5
> ```

## Setting, Clearing, Toggling, and Checking nth bit

> [!note]- Setting nth bit to 1
> We can generate a number where everything is 0 except the nth bit with `(1 << n)` where the digits are 0-indexed. Then we can OR it with the number to set the nth bit to 1.
>```python
>n = 11 # 1011 in binary - let's set 2nd (3rd if 1-indexed) bit to 1
print(n | (1 << 2)) # 15 which is 1111 in binary
>```

> [!note]- Setting nth bit to 0
>We can generate a number where the nth bit is 1 and everything else is 0 with `(1 << n)` where digits are 0-indexed, and we can flip this to generate a number where the nth bit is 0 and everything else is 1 with `~(1 << n)`. Then we can AND it with the number to set the nth bit to 0.
>```python
>n = 15 # 1111 in binary - let's set 2nd (3rd if 1-indexed) bit to 0
print(n & ~(1 << 2)) # 11 which is 1011 in binary
>```

> [!note]- Toggling nth bit
>We can generate a number where the nth bit is 1 and everything else is 0 with `(1 << n)` where digits are 0-indexed. Then we can XOR it with the number to toggle the nth bit.
>
>This is because where there is a 0 and it is XORed with the original bits, it leaves them unchanged. Where there is a 1 and it is XORed, the original bit is flipped.
>```python
>n = 15 # 1111 in binary - let's toggle 2nd (3rd if 1-indexed) bit
n ^= 1 << 2
print(n) # 11 which is 1011 in binary
n ^= 1 << 2
print(n) # 15
>```

> [!note]- Checking nth bit
>We can generate a number where the nth bit is 1 and everything else is 0 with `(1 << n)` where digits are 0-indexed. Then we can AND it to retrieve the value represented by the bit - if this is positive then the bit will have been set (1) and if it is 0 then the bit will not have been set (0).
>
>```python
>n = 11 # 1011 in binary
print(n & (1 << 2) > 0) # checking 2nd (3rd if 1-indexed) bit - False
print(n & (1 << 1) > 0) # checking 1st (2nd if 1-indexed) bit - True
>```


## Sources

- https://www.geeksforgeeks.org/competitive-programming/bit-tricks-competitive-programming/
- https://www.geeksforgeeks.org/competitive-programming/bitwise-hacks-for-competitive-programming/