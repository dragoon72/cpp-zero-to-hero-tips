# 1.cerr
### the Basics of std::cerr

In C++, std::cerr is used to output error messages or diagnostic information. Unlike std::cout, which is buffered 
(it waits to fill up a memory "bucket" before printing), std::cerr is unbuffered. 
This means it prints the message to the screen immediately, ensuring you see the error even if the program crashes a millisecond later.

Example:
    
    
    #include<iostream>
    int main(){
    int x = 10;
    int y = 0;
    if (y == 0) {
        // Using cerr to report the issue immediately
        std::cerr << "Error: Attempted to divide by zero!" << std::endl;
    } else {
        std::cout << "Result: " << x / y << std::endl;
    }
    return 0;
    }

Use:

Safety: If your program hits a "Segmentation Fault" and dies, std::cout might still
be holding your last message in the buffer, so it never gets printed. std::cerr sends it out the door the moment you call it.

# 2. push_back()

Its job is simple: it removes the very last element of the container.

### How it Works 

When you call pop_back(), the container reduces its size by one and destroys the element that was at the end.

#### Important Rules

No Return Value: Unlike some other languages, pop_back() in C++ returns void. It does not return the value it just removed. 
If you need that value, you must grab it using .back() before popping.

Empty Containers: Calling pop_back() on an empty container causes undefined behavior (usually a crash). Always check if the container is .empty() first!

Efficiency: For std::vector, this is an $O(1)$ operation (constant time) because it doesn't require shifting any other elements.

    #include <iostream>
    #include <vector>

    int main() {
    std::vector<int> numbers = {10, 20, 30};

    if (!numbers.empty()) {
        // 1. Get the value if you need it
        int lastVal = numbers.back(); 
        std::cout << "Removing: " << lastVal << std::endl;

        // 2. Remove the element
        numbers.pop_back(); 
    }

    std::cout << "New size: " << numbers.size() << std::endl; // Prints 2
    return 0;
    }


.back()-> Accesses the last element (returns a reference).

.pop_back()-> Removes the last element (returns nothing).

.clear()->Removes all elements at once.

