

    import random
    
    def randarr(total):
        arr = []
        for i in range(0, total):
            arr.append(random.randint(0, 10000))
        return arr
        

# Quicksort

Sorts an array of items by picking a `pivot` element in the array and sorting items into a left and right subarrays


    arr = randarr(10)
    def quicksort(arr):
        if(len(arr) > 0):
            pivot = arr[len(arr) - 1]
            left = []
            right = []
            for i in arr:
                if i < pivot:
                    left.append(i)
                elif i > pivot:
                    right.append(i)
            return quicksort(left) + [pivot] + quicksort(right)
        return []
    
    print "Original Array: {0}".format(arr) 
    print "Sorted Array: {0}".format(quicksort(arr))

    Original Array: [6106, 1073, 1460, 3474, 8774, 4459, 2286, 4917, 2610, 6184]
    Sorted Array: [1073, 1460, 2286, 2610, 3474, 4459, 4917, 6106, 6184, 8774]


# Bubblesort

Sort an array by swapping positions. Requires multiple passes through the array to ensure the lowest value has bubbled to the top


    arr = randarr(10)
    def bubblesort(arr):
        changed = False
        for i in range(0, len(arr)):
            if i + 1 < len(arr):
                if arr[i + 1] < arr[i]:
                    temp = arr[i]
                    arr[i] = arr[i + 1]
                    arr[i + 1] = temp
                    changed = True
        if changed:
            return bubblesort(arr)
        else:
            return arr
            
    print "Original Array: {0}".format(arr) 
    print "Sorted Array: {0}".format(bubblesort(arr))

    Original Array: [8494, 2650, 5303, 4745, 6318, 9649, 3332, 5389, 7907, 5045]
    Sorted Array: [2650, 3332, 4745, 5045, 5303, 5389, 6318, 7907, 8494, 9649]


# Fizzbuzz
Write a program that prints the integers from 1 to 100. But for multiples of three print "Fizz" instead of the number, and for the multiples of five print "Buzz". 
For numbers which are multiples of both three and five print "FizzBuzz".


    for i in range(1, 100):
        s = ""
        if i % 3 == 0:
            s += "Fizz"
        if i % 5 == 0:
            s += "Buzz"
        if s == '':
            s = i
        print s

    1
    2
    Fizz
    4
    Buzz
    Fizz
    7
    8
    Fizz
    Buzz
    11
    Fizz
    13
    14
    FizzBuzz
    16
    17
    Fizz
    19
    Buzz
    Fizz
    22
    23
    Fizz
    Buzz
    26
    Fizz
    28
    29
    FizzBuzz
    31
    32
    Fizz
    34
    Buzz
    Fizz
    37
    38
    Fizz
    Buzz
    41
    Fizz
    43
    44
    FizzBuzz
    46
    47
    Fizz
    49
    Buzz
    Fizz
    52
    53
    Fizz
    Buzz
    56
    Fizz
    58
    59
    FizzBuzz
    61
    62
    Fizz
    64
    Buzz
    Fizz
    67
    68
    Fizz
    Buzz
    71
    Fizz
    73
    74
    FizzBuzz
    76
    77
    Fizz
    79
    Buzz
    Fizz
    82
    83
    Fizz
    Buzz
    86
    Fizz
    88
    89
    FizzBuzz
    91
    92
    Fizz
    94
    Buzz
    Fizz
    97
    98
    Fizz


# B-Tree
Given a b-tree structure, compare the left to the right to ensure the structure is a mirror
```
        7
       / \
      3   3
     / \ / \
    4  5 5  4
```


    class Node:
        
        def __init__(self, data, left=None, right=None):
            self.data = data
            self.left = left
            self.right = right
            
    tree = Node(7, left=Node(3, left=Node(4), right=Node(5)), right=Node(3, left=Node(5), right=Node(4)))
    
    
    def compare(left, right):
        if(left and right and left.data == right.data):
            return True and compare(left.right, right.left) and compare(left.left, right.right)
        elif left is None and right is None:
            return True
        else:
            return False
    
        
        
    print "Left and right branches of tree are equal: {0}".format(compare(tree.left, tree.right))

    Left and right branches of tree are equal: True


# B-Tree Level Navigation
Navigate a b-tree by level and print out the data for each node

For example:
```
        7
       / \
      3   3
     / \ / \
    4  5 5  4
```
Should yield: 7, 3, 3, 4, 5, 5, 4



    from Queue import Queue
    
    class Node:
        
        def __init__(self, data, left=None, right=None):
            self.data = data
            self.left = left
            self.right = right
            
    tree = Node(7, left=Node(3, left=Node(4), right=Node(5)), right=Node(3, left=Node(5), right=Node(4)))
    
    
    def level(node, more = None):
        if node is not None:
            if more is None:
                more = []
            more += [node.left, node.right]
            print node.data
        if more:
            level(more[0], more[1:])
    
    level(tree)


    7
    3
    3
    4
    5
    5
    4



    
