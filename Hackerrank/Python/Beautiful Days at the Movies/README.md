Beautiful Days at the Movies    https://www.hackerrank.com/challenges/beautiful-days-at-the-movies/problem


Green


```{Python}
def beautifulDays(i, j, k):
    count = 0
    for num in range (i, j+1):
        reverse_num = ""
        reverse = [x for x in str(num)[::-1]]
        for n in reverse:
            reverse_num += n
        if (abs(num - int(reverse_num))) % k == 0:
            count += 1
    return (count)
```

One-liner

```{Python}
def beautifulDays(i, j, k):
    return sum([1 for day in range (i, j+1) if abs(day - int(str(day)[::-1])) % k == 0])
```