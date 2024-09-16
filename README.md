
# Push-Swap Project

## Overview

Push-Swap is a simple project that implements a non-comparative sorting algorithm using two stacks (`a` and `b`) and a set of specific instructions. The goal is to sort the integers in stack `a` using the least number of operations. The project consists of two programs:

1. **Push-Swap**: Generates the smallest possible list of instructions to sort a given list of integers.
2. **Checker**: Verifies if a given list of instructions correctly sorts the integers.

## Features

- Implements two stacks (`a` and `b`) and a variety of operations (`pa`, `pb`, `sa`, `sb`, etc.).
- Calculates the smallest sequence of instructions to sort stack `a`.
- Verifies whether a sequence of operations sorts stack `a` and leaves stack `b` empty.

## Instructions

### Operations

- `pa`: Push the top element from stack `b` to stack `a`.
- `pb`: Push the top element from stack `a` to stack `b`.
- `sa`: Swap the first two elements of stack `a`.
- `sb`: Swap the first two elements of stack `b`.
- `ss`: Execute `sa` and `sb`.
- `ra`: Rotate stack `a` (shift elements up, the first element becomes the last one).
- `rb`: Rotate stack `b`.
- `rr`: Execute `ra` and `rb`.
- `rra`: Reverse rotate stack `a` (shift elements down, the last element becomes the first one).
- `rrb`: Reverse rotate stack `b`.
- `rrr`: Execute `rra` and `rrb`.

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/antmusumba/push-swap.git
    ```

2. Navigate to the project directory:

    ```bash
    cd push-swap
    ```

3. Install dependencies (if any) or ensure Go is installed:

    ```bash
    go mod tidy
    ```

## Usage

### Push-Swap

The `push-swap` program calculates the smallest number of instructions to sort a stack.

```bash
go run cmd/pushswap/main.go "2 1 3 6 5 8"
```

Output:
```
pb
pb
ra
sa
rrr
pa
pa
```

#### Error Handling:
- If there is an invalid argument (non-integer or duplicate), the program will display `Error`.
  
```bash
go run cmd/pushswap/main.go "2 1 one 3"
Error
```

### Checker

The `checker` program takes the stack `a` as input and reads instructions from standard input. It executes the instructions and checks if the stack is sorted and stack `b` is empty.

```bash
go run cmd/checker/main.go "2 1 3"
```

Enter instructions:
```
pb
pb
ra
pa
pa
```

Output:
```
OK
```

If the stack isn't sorted correctly, it will return `KO`.

```bash
go run cmd/checker/main.go "3 2 1"
```

Enter instructions:
```
sa
pb
KO
```

## Examples

### Push-Swap Example

```bash
$ go run cmd/pushswap/main.go "4 3 2 1"
pb
pb
sa
ra
pa
pa
```

### Checker Example

```bash
$ echo -e "sa\npb\npa\n" | go run cmd/checker/main.go "2 1"
OK
```

## Running Tests

To ensure everything works properly, you can run the tests:

```bash
go test ./internal/...
```

## Error Handling

The programs will output `Error` if:
- The input contains non-integer values.
- There are duplicate integers in the stack.
- An invalid instruction is provided (in checker).
  
## Roadmap

- [x] Implement stack operations (`Push`, `Pop`, `Swap`, `Rotate`).
- [x] Implement the push-swap algorithm to minimize operations.
- [x] Implement the checker program to validate sorting.
- [ ] Optimize the sorting algorithm for larger sets of integers.
- [ ] Improve performance with advanced sorting heuristics.

## Contributing

Contributions are welcome! Feel free to submit pull requests, report issues, or suggest improvements.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.


