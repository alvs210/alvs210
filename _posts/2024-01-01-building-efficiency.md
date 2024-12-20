---
title: "Building Efficiency"
date: 2023-08-10T08:08:50-04:00
---

Achieved 5th most time- and space- efficient algorithm in the Computer Architecture Fall 2023 Course at Duke! 

This is a C program called "BuildEff" (short for Building Efficiency) to identify the most energy efficient Duke building (per square foot) in the input file provided. Converted it into MIPS Assembly language too while mantaining efficiency.

### A snippet of my C code -- sorting algorithm

```
void sorty (struct listitem *head) {
    // int swapped, i;
    int swapped = 0;
    int i = 0;
    struct listitem *temp = NULL;
    struct listitem* lptr = NULL;
    if (head == NULL) {      ////FAUL
        return;
    }
    do {
        swapped = 0;
        temp = head;
        while (temp->next != lptr) {
            if (temp->efficiency < temp->next->efficiency) {
                swappy(temp->next, temp);
                swapped = 1;
            }
            temp = temp->next;
        }
        lptr = temp;
    }
    while(swapped);

}
```

### A snippet of my Assembly code! Just comparing building efficiencies

```
_comparison:    #comparing efficiencies

    lb $t3, ($s2)
    lb $t2, ($s3)

    bgt $t3, $t2, _more
    blt $t3, $t2, _less

    addiu $s2, $s2, 1
    addiu $s3, $s3, 1

    j _comparison

```

Full GitHub Code: [Click Here](https://github.com/alvs210/BuildingEfficiency/tree/main)

Assignment for BuildEff in C: [Click Here](https://people.ee.duke.edu/~jab/ece250/homeworks/homework1.pdf)

Assignment for BuildEff in Assembly: [Click Here](https://people.ee.duke.edu/~jab/ece250/homeworks/homework2.pdf)

# Assignment Details - C and MIPS

Write a C program called BuildEff (short for Building Efficiency) to identify the most energy efficient
building (per square foot) in the input file provided. The tool will take a filename as an input (eg.,
“./BuildEff buildinginfo.txt”). The format of this file is file is a series of
building stats, where each entry is 3 lines long. The first line is the name of a building (a string with no
spaces), the second line is the square footage of the building (an int, which you will need to typecast as a
float later), and the third line is the annual amount of electricity used per year (in KwH – Kilowatt hours))
(a float). After the last building in the list, the last line of the file is the string “DONE”. For example:

```
HudsonAnnex
30000
522000.0
FitzpatrickCIEMAS
332178
4686414.2
DONE
```
My program outputted a number of lines equal to the number of buildings and each line is the
building’s name and energy efficiency in kWh per square foot per year. The lines were sorted in
descending order of kWh per square foot per year (least efficient building first).

I had to write my own sorting function (you can’t just use the qsort library function). Buildings with equal efficiency
were sorted alphabetically (e.g. based on the strcmp function). For example:

```
HudsonAnnex 17.4
FitzCIEMAS 14.10814
FancyHall 12.6
MessyHall 12.6
```
When writing it in Assembly, a few of the rules changed. Because the program is now prompting for input interactively, the program will output
prompts before reading values.

