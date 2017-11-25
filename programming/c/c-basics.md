C programming basics
======


#### Header Files

* #include directive tells preprocessor to include the header (.h) file into the source code
* if the header file is enclosed in < > tags the preprocessor will search in the standard libraries
* if the header file uses " " tags then the preprocessor will search the same directory as the source file


#### Commenting

Single line

``` c

// this is a single line comment

```

Multi Line Comment

``` c

/*  This is a Multie Line 
 *  Comment 
 *  Another Line
 */ 

```



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

#### String Functions

    printf("hello world\n");   # prints the string to the screen
    puts("hello world\n");     # prints a simple string to the screen

Format Specifiers

* using a decimal formatter for a string or vice versa will cause a segmentation fault
* forgetting a formatter value will return (null)

    %d   # decimal 
    %s   # string
    %f   # float
    %e   # double 

    %.2f\n   # limits the output of a float to two decimal places
    %.10f\n  # limits the output of a float to ten decimal places

    printf("there are %d tires on a  %s ", 4, "car");

#### Loops

* index 0 will always be the name of the program
* argc is the auto calculated size of the array (including index 0)


#### Variables

* variables are declared by specifying the type and then the variable name
* int, float, double (double precision floating point), char, void 
* variables can be assigned a value at the same time they are declared, but not good practice

variable assignment

``` c

    double weekly_check
    double monthly_payment

```

or

``` c

    double weekly_check, monthly_payment

```

#### Constants

``` c

    const double AGE = 50;   // cannot be redfined, true constant
    #define NAME "tomcat";   // can be redefined, not a true constant

```