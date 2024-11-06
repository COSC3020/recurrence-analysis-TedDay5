# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

Recurrence relation: T(n) = 3T(n/3) + $n^5$ and i = $log_3$ n.
I found this recurrence relation from n/3 happening 3 times, the 3 for loops, and 2 having $n^2$ time and one having n time.

```math
T(n) = 3[3T(n/3^2) + (n/3)^5] + n^5
```
```math
T(n) = 3^2T(n/3^2) + (n/3^4)^5 + n^5
```
```math
T(n) = 3^3T(n/3^3) + (n/3^8)^5 + (n/3^4)^5 + n^5
```
This pattern is produced:

```math
3^iT(n/3^i) + \sum_{i = 0}^n n^5/3^{4^i}, and i = log_3 n
```
```math
3^{log_3 n}T(n/3^{log_3 n}) + n^5 * (1/3)^{4^{log_3 n}}
```
```math
n * T(1) + n^5 * 1/(1 - 1/3)
```
```math
n^5 ∈ O(n^5)
```

“I certify that I have listed all sources used to complete this exercise, including the use
of any Large Language Models. All of the work is my own, except where stated
otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is
suspected, charges may be filed against me without prior notice.”
