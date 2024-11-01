<h1 align="center">Python Lists</h1>

- [Appending item to end of a list](#appending-item-to-end-of-a-list)


# Appending item to end of a list
Example:
```python
old_list = ['car', 'b', 'lens']
item = 'sushi'
```  

### 1. Append a single item to end of list with `append()`:
```python
old_list.append(item)
# old_list = ['car', 'b', 'lens', 'sushi']
```
*runtime* = O(1)  
*space* = O(1)

### 2. Concatinate another list onto the end of the old list with `extend()`:
```python
old_list.extend([item])
# old_list = ['car', 'b', 'lens', 'sushi']
```
The operator `+=` is semantically similar to `extend()` when working with lists:
```python
old_list += [item]
# old_list = ['car', 'b', 'lens', 'sushi']
```
*runtime* = O(n), where n = size of the list being added.  
*space* = O(1), but more expensive than `append()` if only 1 item is added because another list `[item]` has to be created.


> [!Note]  
> `+=` modifies the `old_list` in-place by reassigning `old_list + [item]` to itself, so this reassignment does not work if the old list is an immutable object, such as an element in a tuple, `tup[0]`.
```python
tup = ([1, 3], [6, 5])
tup[0].extend([2, 4])
tup = ([1, 3, 2, 4], [6, 5])
tup[0] += [2, 4]    #invalid operation
```  
> Note that although tuples are immutable, `+=` will appear to work:
```python
tup += [2, 4]
# tup = ([1, 3], [6, 5], [2, 4])
```
> This is because under the hood, another new tuple object is created and the pointer of `tup` is updated to point to the new tuple. The reassignment is not done in-place.

### 3. Create a new list with `+`:
```python
new_list = old_list + [item]
# new_list = ['car', 'b', 'lens', 'sushi']
```
*runtime* = O(n)  
*space* = O(n)  
where n = length of old list + length of the list being added

### 4. Create a new list by unpacking old list with `*`-operator:
```python
new_list = [*old_list, item]
# new_list = ['car', 'b', 'lens', 'sushi']
```
*runtime* = O(n)  
*space* = O(n), slightly better than method #3 when adding a single item because `item` doesn't need to be in a list, `[item]` to be added to the `old_list`.  
where n = size of old list + item