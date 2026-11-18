# Linux Bonus Labs

## Grep

### Create the Lab File

Run the following commands:

```sh
mkdir grep-lab
cd grep-lab

nano staff.txt

# Add the following to the file

Alice Smith,IT Support,London
Bob Jones,Cyber Security,Manchester
Charlie Brown,Cloud Engineer,London
Diana Prince,IT Support,Birmingham
Ethan Hunt,DevOps Engineer,London
Fatima Khan,Cyber Security,Leeds
George Wilson,Cloud Engineer,Manchester
Hannah Davis,IT Support,Leeds
```

### Task 1: Find a Specific Name

Display the line containing Alice.

<details><summary>Answer:</summary>

`grep "Alice" staff.txt`

</details>

### Task 2: Find All IT Support Staff

Display all staff working in IT Support.

<details><summary>Answer:</summary>

`grep "IT Support" staff.txt`

</details>

### Task 3: Count Matches

Count how many staff work in London.

<details><summary>Answer:</summary>

`grep -c "London" staff.txt`

</details>

### Task 4: Case-Insensitive Search

Create another file:

```sh
nano systems.txt

# Add the following to the file

Linux
linux
LINUX
Windows
macOS
```

Find all occurrences of "linux" regardless of case.

<details><summary>Answer:</summary>

`grep -i "linux" systems.txt`

</details>

### Task 5: Show Line Numbers

Display all Cloud Engineers and include line numbers.

<details><summary>Answer:</summary>

`grep -n "Cloud Engineer" staff.txt`

</details>

### Task 6: Invert a Match

Show all staff who are not in London.

<details><summary>Answer:</summary>

`grep -v "London" staff.txt`

</details>

### Task 7: Match Multiple Patterns

Show all lines containing either London or Leeds.

<details><summary>Answer:</summary>

`grep -E "London|Leeds" staff.txt`

</details>

### Challenge Questions:

1. How many staff work in Cyber Security?
2. Which line number contains Hannah Davis?
3. Which cities have IT Support staff?
4. How many staff do not work in London?
5. Display only the Manchester staff.

<details><summary>Answer:</summary>

1. 2
2. Line 8
3. London, Birmingham, Leeds
4. 4
5. `grep "Manchester" staff.txt`

</details>

## Sed

Use the previous `staff.txt` file

### Task 1: Replace Text

Replace London with Leeds (output only, don't modify the file).

<details><summary>Answer:</summary>

`sed 's/London/Leeds/' staff.txt`

</details>

### Task 2: Replace All Occurrences

Create a file with repeated text: `echo "London London London" > cities.txt`

Replace all occurrences of London with Leeds.

<details><summary>Answer:</summary>

`sed 's/London/Leeds/g' cities.txt`

</details>

### Task 3: Display a Specific Line

Display only line 3.

<details><summary>Answer:</summary>

`sed -n '3p' staff.txt`

</details>

### Task 4: Display a Range of Lines

Display lines 2 to 4.

<details><summary>Answer:</summary>

`sed -n '2,4p' staff.txt`

</details>

### Task 5: Delete a Line

Display the file without line 2.

<details><summary>Answer:</summary>

`sed '2d' staff.txt`

</details>

### Task 6: Delete Blank Lines

Create a file:

```sh
nano notes.txt

# Add the following text, include the empty lines

Linux

AWS

Azure
```

Remove blank lines.

<details><summary>Answer:</summary>

`sed '/^$/d' notes.txt`

</details>

### Task 7: Modify the File In-Place

Replace "IT Support" with "Technical Support" and save the changes.

<details><summary>Answer:</summary>

`sed -i 's/IT Support/Technical Support/g' staff.txt`

</details>

Verify

<details><summary>Answer:</summary>

`cat staff.txt`

</details>

### Challenge Questions

1. Display only the first line of staff.txt.
2. Display only the last line of staff.txt.
3. Delete line 4 from the output.
4. Replace "Engineer" with "Specialist" in the output.
5. Display only lines containing "IT Support".

<details><summary>Answer:</summary>

```sh
# 1
sed -n '1p' staff.txt

# 2
sed -n '$p' staff.txt

# 3
sed '4d' staff.txt

# 4
sed 's/Engineer/Specialist/g' staff.txt

# 5
sed -n '/IT Support/p' staff.txt
```

</details>

### Bonus

Combine grep and sed:

Show only Cloud Engineers and replace "London" with "REMOTE":

<details><summary>Answer:</summary>

`grep "Cloud Engineer" staff.txt | sed 's/London/REMOTE/'`

</details>

## Linux awk Lab

Use the previous `staff.txt` file

### Task 1: Print the Entire File

<details><summary>Answer:</summary>

`awk '{print}' staff.txt`

</details>

### Task 2: Print the First Column

Display only employee names.

<details><summary>Answer:</summary>

`awk -F, '{print $1}' staff.txt`

</details>

Expected output:

```text
Alice Smith
Bob Jones
Charlie Brown
Diana Prince
Ethan Hunt
```

### Task 3: Print the Job Roles

Display only the second column.

<details><summary>Answer:</summary>

`awk -F, '{print $2}' staff.txt`

</details>

### Task 4: Print Names and Cities

Display the first and third columns.

<details><summary>Answer:</summary>

`awk -F, '{print $1, $3}' staff.txt`

</details>

### Task 5: Find Staff in London

Display employees whose city is London.

<details><summary>Answer:</summary>

`awk -F, '$3=="London" {print $1}' staff.txt`

</details>

### Task 6: Count Records

Count the number of employees.

<details><summary>Answer:</summary>

`awk 'END {print NR}' staff.txt`

</details>

### Task 7: Add Labels to Output

Display names with a label.

<details><summary>Answer:</summary>

`awk -F, '{print "Employee:", $1}' staff.txt`

</details>

Expected output:

```text
Employee: Alice Smith
Employee: Bob Jones
Employee: Charlie Brown
Employee: Diana Prince
Employee: Ethan Hunt
```

### Task 8: Print Line Numbers

<details><summary>Answer:</summary>

`awk '{print NR, $0}' staff.txt`

</details>

### Task 9: Count London Employees

<details><summary>Answer:</summary>

`awk -F, '$3=="London" {count++} END {print count}' staff.txt`

</details>
