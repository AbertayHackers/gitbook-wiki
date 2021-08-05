# C Coding

C is a general-purpose programming language. It is closely associated with the UNIX system where it was developed, since the system and most of the programs that run on it are written in C. The language is not explicitly tied to one operating system or machine, and is useful for writing a variety of programs ranging from operating systems and compilers to major programs in many different domains.

All of the features of C are contained in some form within C++ so when working with C++ it can be more efficent to work with C constructs instead of their newer equivilent. One example of this includes the ?: operator which can be used as a far more efficent version of a if statment ~~Which unfortunately looks god awful in code~~

## Basic Examples

### Hello World

```c
#include <stdio.h> // Inclusion for standard Input/Output library

main()
{
    printf("Hello Hackers\n"); //print 'Hello Hackers' with a new line (\n).
    return 0; // Linux returns 0 typically for a successful run, Windows likes the opposite
}
```

### For Loops \(with a bit of int concatenation\)

```c
#include <stdio.h> // Standard input output

int main() {
    int beers; // Initialisation of int for beers

    printf("A fitting example for hackers.\n\n");

    for (beers = 99; beers > 0; beers-- ) // This will loop until beers = 0
    {
        printf("Bottles of beer on the wall, %d Bottles of beer\n", beers);
        printf("Take one down and pass it around, %d bottles of beer on the wall.\n\n", beers);
    }

    printf("No more bottles of beer on the wall, no more bottles of beer.\n");
    printf("Go to the store and buy some more, 99 bottles of beer on the wall.\n");
    printf("\nAnd conditional loops are just that easy");

    return 0;
}
```

### While Loops \(with the `rand` function\)

```c
#include <stdio.h>    // Standard input output
#include <time.h>    // Using time to seed the random function
#include <stdlib.h>    // Standard Library

int main() {

    printf("Lets spin to win\nLooking for Tails\n\n");
    srand(time(NULL));

    while (rand() % 2 == 0) // Heads
    {
        printf("Not yet, it was heads\n");
    }

    printf("Tails");
}
```

### File Creation

```c
#include <stdio.h> // Standard input output (which includes file input output)

main() {
    FILE *filepath;
    char buff[255]; // Liable for buffer overflows if mishandled

    filepath = fopen("./test.txt", "w+"); // Opens a text file for both reading and writing
    fprintf(filepath, "Lorem ipsum dolor sit amet,\n");
    fputs("consectetur adipiscing elit,\n", filepath);
    fclose(filepath);

    filepath = fopen("./test.txt", "r");
    fscanf(filepath, "%s", buff); // fscanf will read until it encounters a space
    fgets(buff, 255, filepath); // fgets will read from current pointer position until it encounters a end of line
    fgets(buff, 255, filepath); // fgets in this instance will read the entire second line
}
```
