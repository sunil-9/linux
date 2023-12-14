### Q1: Displaying Car List with Numbers
You have a file named `cars.txt` with the following content:

```bash
$ nano cars.txt
Audi
BMW
Bentley
Maserati
Volvo
```

Write a script to generate the following output using the above file:

```bash
1. Audi
2. BMW
3. Bentley
4. Maserati
5. Volvo
```

### Q2: Calculating Factorial

Write a script to generate the factorial of a given number. For example, if the number is 4, the script should calculate and display the result as 4! = 4 * 3 * 2 * 1 = 24.

### Q3: Displaying Server Information

Write a script to display server information, including Date, Uptime, Memory, and Network details.

### Q4: Displaying Script Arguments

Write a script to print all the arguments given with the script. For example:

```bash
./script.sh this is a test
this
is
a
test
count: 4
```

### Q5: Matching IP Address Pairs with Roll Number

Write a script to find out your IP address, remove dots (.), make pairs of 2 digits serially, and check if your roll number matches any of the pairs of IP addresses. If the roll number is less than 10, multiply it by 10. 
For example, if your IP address is `192.167.1.1` then the pairs will be `19`, `21`, `67`, `11`. If your roll number is 5, then multiply it by 10, i.e., 50. Now, check if 50 matches any of the pairs. If it matches, print "Found", otherwise print "Not Found".