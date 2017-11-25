C programming basics
======


#### Header Files

* #include directive tells preprocessor to include the header (.h) file into the source code
* if the header file is enclosed in < > tags the preprocessor will search in the standard libraries
* if the header file uses " " tags then the preprocessor will search the same directory as the source file

#### Functions

* the expected return value type prepends the function

``` c
int main() {
    ...
    return 0
}

```

#### Arguments

    int argc     # number of arguments passed to main(), is automatically calculated. 
    char **argv  # array of character strings
    car *argv[]  # array of character strings

#### Standard Library Functions

    printf("hello world\n");   # prints the string to the screen


#### Loops

* index 0 will always be the name of the program
* argc is the auto calculated size of the array (including index 0)