# push_swap

A C program that sorts a stack of integers using a limited set of operations and outputs the operations sequence.

## Features
- Sorts numbers using two stacks (`stack_a`, `stack_b`)  
- Only permitted operations:  
  - `sa`, `sb`, `ss` (swap top two elements)  
  - `pa`, `pb` (push between stacks)  
  - `ra`, `rb`, `rr` (rotate up)  
  - `rra`, `rrb`, `rrr` (rotate down)  
- Handles any number of arguments, detects duplicates and invalid inputs  
- Optimized for minimal operation count

## Usage
```sh
./push_swap [numbers…]
```
- Pass space-separated integers as arguments
- The program prints each operation on its own line

## How It Works
- Input Validation:
  - Check that each argument is a valid 32-bit integer
  - Check for duplicate values
- Initialization:
  - Build stack_a from input, stack_b starts empty
- Sorting Algorithm:
  - For small sets (≤5 numbers), use hard-coded optimal sequences
  - For larger sets, use a radix sort on binary representation or a chunk-based strategy:
    - Divide stack_a into value ranges (“chunks”)
    - Push elements chunk by chunk to stack_b in sorted order
    - Push back to stack_a to achieve full sort
- Operation Selection:
  - Compute whether rotate or reverse-rotate is shorter for moving a target element
  - Combine operations (rr, ss, rrr) when beneficial
- Output:
  - Print each operation as it is performed
  - Exit when stack_a is sorted and stack_b is empty
