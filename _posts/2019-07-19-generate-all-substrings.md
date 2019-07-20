Although we rarely need to generate all substrings of a string in optimal solutions for algorithmic puzzles, knowing how to do so can be a powerful tool to use for brute force solutions.

```
def substr(str):
    result = []
    for i in range(len(str)):
        for j in range(len(str)+1):
            result.append(str[i:j])
    return result
```

The function would have time complexity O(n^2) due to the nested loop, and space complexity O(n) for the array.