# Base64 Encoding Decoding

Base64 is a group of binary-text conversion algorithms, which helps transform binary data into a sequence of human understandable/printable characters. For Base64, the set of characters is 64.

The basic algorithm is - convert chunk of **6 bits** data into a unique character in the conversion table.



This allows, easy storage and transmission of binary data - example files, data over the internet.

*How can files be binary? It can be a text file, can be an image. Well lets think in terms of perspective. End of day everything is a 1 or 0. How we interpret it matter. When we use the term **binary** files, we are referring to the data format in the file which is meant for machines to make sense of, not humans*/

## Base64 table from RFC 4648

The conversion table - 6bits of chunk mapped to a character is defined in [RFC 4648](https://datatracker.ietf.org/doc/html/rfc4648#section-4).
- The first 26 patterns are mapped to `A-Z`
- The next 26 patterns are mapped to `a-z`
- The next 10 patterns are mapped to `0-9`
- The 63rd pattern is mapped to `+`
- The 64th pattern is mapped to `/`
- When padding is done to make sure we have 6 bits of chunks, append `=` at the end


## The Base 64 Alphabet

Depending on the variants of implementation, the 63rd and 64th mappings do change, and padding becomes optional.

| Value | Encoding |
| :---: | -------- |
|   0   | A        |
|   1   | B        |
|   2   | C        |
|   3   | D        |
|   4   | E        |
|   5   | F        |
|   6   | G        |
|   7   | H        |
|   8   | I        |
|   9   | J        |
|  10   | K        |
|  11   | L        |
|  12   | M        |
|  13   | N        |
|  14   | O        |
|  15   | P        |
|  16   | Q        |
|  17   | R        |
|  18   | S        |
|  19   | T        |
|  20   | U        |
|  21   | V        |
|  22   | W        |
|  23   | X        |
|  24   | Y        |
|  25   | Z        |
|  26   | a        |
|  27   | b        |
|  28   | c        |
|  29   | d        |
|  30   | e        |
|  31   | f        |
|  32   | g        |
|  33   | h        |
|  34   | i        |
|  35   | j        |
|  36   | k        |
|  37   | l        |
|  38   | m        |
|  39   | n        |
|  40   | o        |
|  41   | p        |
|  42   | q        |
|  43   | r        |
|  44   | s        |
|  45   | t        |
|  46   | u        |
|  47   | v        |
|  48   | w        |
|  49   | x        |
|  50   | y        |
|  51   | z        |
|  52   | 0        |
|  53   | 1        |
|  54   | 2        |
|  55   | 3        |
|  56   | 4        |
|  57   | 5        |
|  58   | 6        |
|  59   | 7        |
|  60   | 8        |
|  61   | 9        |
|  62   | +        |
|  63   | /        |
|  pad  | =        |
For [Base64URL](https://datatracker.ietf.org/doc/html/rfc4648#section-5) encoding, the `+` changes to `-` and `/` changes to `_`.  
The pad character "=" is typically percent-encoded when used in an URI , but if the data length is known implicitly, this can be avoided by skipping the padding.
## Algorithm

- Take `n` bytes of input which will spit out 
	- `((n + 2) / 3) * 4` characters with padding
	- `(n * 8 + 5) / 6` without padding
- Read 3 bytes at a time - 24 bits.
- Split 24 bits into 4 chunk of 6 bits each.
- Map each 6 bits to the above table.
- If any chunk is less in size (pad zeroes to make it 6 bits)
- If input length is not divisible by 3, add padding with `=`.
	- `n % 3 == 0` -> no padding
	- `n % 3 == 1` -> append `==`
	- `n % 3 == 2` -> append `=`

So we take 3 bytes each = 24 bits, and then divide into 4 chunks. So for 3 bytes we will get 4 encoded characters. So the final result will be divisible by 4. If not divisible, we add those many `=` to make it.



