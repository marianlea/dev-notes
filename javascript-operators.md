## XOR (Exclusive OR)

- XOR is a bitwise operator which compares two bits and returns 1 if they are different, returns 0 if they are the same
- Common use case: **Finding the number that appears odd number of times in an array**

### Truth Table

| A   | B   | A ^ B |
| --- | --- | ----- |
| 0   | 0   | 0     |
| 0   | 1   | 1     |
| 1   | 0   | 1     |
| 1   | 1   | 0     |

### Example: Finding Odd-One-Out

```js
const arr = [1, 2, 3, 2, 3, 1, 4];
let result = 0;
for (const num of arr) {
  result ^= num;
}
console.log(result); // ➝ 4
```

```js
function findOdd(arr) {
  return arr.reduce((acc, num) => acc ^ num, 0);
}
console.log(result); // ➝ 4
```

- This works because XOR pairs of the same number and cancel each other ( because n ^ n = 0)
- As a result you are left with the number that appears odd number of times
