---
description: 'Author: @wingkwong'
---

# Sorting

Sorting refers to rearranging elements in a specific order. The most common order is either ascending or descending. There are a lot of algorithms to sort the array with different time complexity.&#x20;

In C++, if define a static array of N elements of type int such as $$a[4]$$ you can sort like as below where $$N$$ is the number of elements to be sorted.&#x20;

```cpp
sort(a, a + N);
```

If you want to sort for a specific range $$[x, y)$$,  then use&#x20;

```cpp
sort(a + x, a + y);
```

For dynamic array, we do in such way

```cpp
sort(a.begin(), a.end());
```

If you want to sort for a specific range $$[x, y)$$,  then use&#x20;

```cpp
sort(a.begin() + x, a.begin() + y);
```

To sort in an decreasing order,&#x20;

```cpp
sort(a.begin(), a.end(), greater<int>());
```

By default, `sort()` sorts the elements in the range $$[x, y)$$ into ascending order. If the container includes pairs, tuples or array\<int, N>, it first sorts the first element, then the second element if there is a tie and so on. For example, the following comparator is same as `sort(a.begin(), a.end());`.

```cpp
sort(a.begin(), a.end(), [&](const array<int, 3>& x, const array<int, 3>& y) {
    return (
        (x[0] < y[0]) || 
        (x[0] == y[0] && x[1] < y[1]) ||
        (x[0] == y[0] && x[1] == y[1] || x[2] < y[2])
    );
});
```

### Suggested Problems

* [0912 - Sort an Array (Medium)](../../solutions/0900-0999/0921-sort-an-array-medium.md)
