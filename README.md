# push_swap

**push_swap** is an algorithmic project written in C, focused on sorting data in a stack using a limited set of operations. The goal is to sort a stack of integers in as few moves as possible, utilizing specific operations allowed by the project. This project emphasizes problem-solving, algorithm optimization, and stack manipulation.

## Project Overview

This project involves sorting a stack (`a`) of integers with the help of an auxiliary stack (`b`). The challenge is to implement the sorting process efficiently, minimizing the number of operations performed. The following operations are permitted:

- **sa (swap a)**: Swap the first two elements at the top of stack `a`. Does nothing if there are fewer than two elements.
- **sb (swap b)**: Swap the first two elements at the top of stack `b`. Does nothing if there are fewer than two elements.
- **ss**: Perform `sa` and `sb` simultaneously.
- **pa (push a)**: Take the first element at the top of `b` and put it at the top of `a`. Does nothing if `b` is empty.
- **pb (push b)**: Take the first element at the top of `a` and put it at the top of `b`. Does nothing if `a` is empty.
- **ra (rotate a)**: Shift all elements of stack `a` up by one position, moving the first element to the last position.
- **rb (rotate b)**: Shift all elements of stack `b` up by one position, moving the first element to the last position.
- **rr**: Perform `ra` and `rb` simultaneously.
- **rra (reverse rotate a)**: Shift all elements of stack `a` down by one position, moving the last element to the first position.
- **rrb (reverse rotate b)**: Shift all elements of stack `b` down by one position, moving the last element to the first position.
- **rrr**: Perform `rra` and `rrb` simultaneously.

## My Approach

In my implementation, I used a doubly linked list structure to represent the stacks, allowing for efficient insertion and deletion of elements from both ends of the stack. The approach involved:

- **Indexing**: Each element was assigned an index based on its value to facilitate sorting.
- **Binary Representation & Radix Sort**: I sorted the binary representations of these indexes using the Radix sort algorithm. This method is particularly effective for larger datasets, reducing the overall complexity and the number of moves required for sorting.

## Performance and Scoring

My implementation scored 84 points. While it is efficient for sorting larger datasets, there are more optimized algorithms that perform better for smaller datasets (e.g., with 100 or 500 elements). Nevertheless, my approach excels in sorting larger numbers of arguments with fewer moves.

### Strengths:
- Efficient for large datasets, minimizing the number of operations.
- Robust handling of various edge cases.

### Weaknesses:
- Could be optimized further for smaller datasets (100 and 500 elements).

## Project Requirements

- **Language**: The project is written entirely in C.
- **Norm Compliance**: The code adheres to the Norm standard. Any violations, including in bonus files, will result in a 0 score.
- **Error Handling**: Functions must not result in segmentation faults, bus errors, double frees, etc. Any such errors will render the project non-functional.
- **Memory Management**: All dynamically allocated memory must be properly freed. Memory leaks are not tolerated.
- **Makefile**: A Makefile is provided to compile the project. It includes the rules `$(NAME)`, `all`, `clean`, `fclean`, and `re`. The Makefile does not relink files unnecessarily.
- **Libft**: If used, `libft` sources and Makefile are included in a `libft` folder, and the main Makefile compiles the library using its own Makefile.
- **Testing**: While not required, creating test programs is encouraged to verify the correctness and efficiency of your implementation.

## How to Run

To compile and run the project:

make
./push_swap [list_of_numbers]

### Example with a Simple Argument List:

ARG="4 67 3 87 23"; ./push_swap $ARG

### Generating a List of Random Arguments

You can generate a list of random numbers using the following bash command:
```sh
ARG=$(shuf -i 0-999999 -n 100 | tr '\n' ' '); ./push_swap $ARG
```

This command generates 100 random numbers between 0 and 999999, stores them in `ARG`, and runs `push_swap` with those arguments.

### Running with Checker

You can use the checker program to verify that your push_swap solution is correct:
```sh
ARG=$(shuf -i 0-999999 -n 100 | tr '\n' ' '); ./push_swap $ARG | ./checker $ARG
```

This will pass the operations generated by push_swap to checker for validation.

### Running with Valgrind

To check for memory leaks and errors, you can run push_swap with valgrind:

valgrind --leak-check=full ./push_swap $ARG

This command will run push_swap on your list of arguments while monitoring memory usage.

