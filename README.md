[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=11681493&assignment_repo_type=AssignmentRepo)

# CMPS 2200 Recitation 01

**Name (Team Member 1):\*\***\*\*\*\***\*\***\_\***\*\*\*\*\*\*\***  
**Name (Team Member 2):\*\***\*\*\*\***\*\***\_\***\*\*\*\*\*\*\***

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`.

## Install Python Dependency

We need Python library of "tabulate" to visualize the results in a good shape. Please install it by running 'pip install tabulate' or 'pip install -r requirements.txt' in Shell Tab of Repl.

## Running and testing your code

- To run tests, from the command-line shell, you can run
  - `pytest test_main.py` will run all tests
  - `pytest test_main.py::test_one` will just run `test_one`
  - We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Git" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`.

- [ ] 2. Test that your function is correct by calling from the command-line `pytest main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`?

**The worst case input value of 'key' for 'linear_search' is a key that is not in mylist because the algorithm has to iterate through all of mylist and then return -1 after going through the last index of mylist showing that it does not exist in mylist. The worst case input for 'linear_search' also has a runtime of O(n) with n being the length of mylist. The same is for 'binary_search' however, its runtime is O(log2(n))as explained in class by the divide and conquer algorithm.**

- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`?

**The best case input value 'key' for 'linear_search' is the index 0 of the list aka the first element of the list because it yields a runtime of O(1). The best case input value 'key' for 'binary_search' is the middle element of the list aka the element at the index of the length of the mylist mod 2.**

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

**TODO: add your timing results here**
| n | linear | binary |
|--------------|----------|----------|
| 10.000 | 0.001 | 0.002 |
| 100.000 | 0.004 | 0.002 |
| 1000.000 | 0.040 | 0.004 |
| 10000.000 | 0.403 | 0.004 |
| 100000.000 | 4.035 | 0.006 |
| 1000000.000 | 42.957 | 0.026 |
| 10000000.000 | 429.429 | 0.028 |

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

**The theoretical running times do indeed match my empirical results. In the linear search, the time increases dramatically as the number of 0s in n increase. In binary search the time still increases which makes sense, but not nearly to the same dramatic effect. The difference is the most extreme in the example n = 10000000.000 where it takes the linear function 429.429 and the binary 0.028. For this example the binary function is over 15000 times faster.**

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times.
  - What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? **If the list isn't sorted and you sort a list of n elements k times using $\Theta(n^2)$, the worst-case time complexity for linear search is $\Theta(n^2+nk)$ which is O(nk).**
  - For binary search? **For binary search the worst-case time complexity is $\Theta(log_2(n))$ for each search. If you search the list k times, you need to first sort the list which takes $\Theta(n^2)$ time, so the worst-case time complexity is $\Theta(k log_2 n + n^2)$ which is O(klog_2 n).**
  - For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? **When it is more efficient to first sort and then use binary search can be represented by when k log_2 n + n^2 < nk. Dividing both sides by k results in log_2 n + (n^2/k) < n. So when k > n^2/(n - log_2 n) it is more efficient to first sort and then use binary search.**
    \*\*\*\*
