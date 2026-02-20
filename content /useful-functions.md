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
