# CIS129_Lab11_BrendaCeja
# Code for IPython to write grades to grades.txt
#9.1 of Lab 11
grades = []
print("Enter grades one by one. Type 'done' to finish.")

while True:
    grade = input("Enter grade: ")
    if grade.lower() == 'done':
        break
    try:
        grades.append(int(grade))
    except ValueError:
        print("Invalid input. Please enter a valid integer grade.")

with open('grades.txt', 'w') as file:
    for grade in grades:
        file.write(f"{grade}\n")

print("Grades written to grades.txt.")



# Code to read grades from grades.txt and display each grade, their total, count and average.
#9.2 of Lab 11
try:
    with open('grades.txt', 'r') as file:
        grades = [int(line.strip()) for line in file]  # Read and convert grades from the file

    print("Grades:")
    for grade in grades:
        print(grade)

    total = sum(grades)  # Calculate the total of grades
    count = len(grades)  # Count the number of grades
    average = total / count if count != 0 else 0  # Calculate the average, avoid division by zero

    print(f"\nTotal of grades: {total}")  # Print total of grades
    print(f"Count of grades: {count}")  # Print count of grades
    print(f"Average grade: {average:.2f}")  # Print average of grades

except FileNotFoundError:
    print("File 'grades.txt' not found. Please make sure the file exists in the current directory.")



    #9.3 of Lab 11
import csv

# Open the grades.csv file in append mode
with open('grades.csv', 'a', newline='') as file:
    writer = csv.writer(file)
    print("Enter student data. Type 'exit' as first name to stop.")

    while True:
        first_name = input("Enter the student's first name: ")
        if first_name.lower() == 'exit':
            break
        last_name = input("Enter the student's last name: ")
        try:
            exam1_grade = int(input("Enter grade for exam 1: "))
            exam2_grade = int(input("Enter grade for exam 2: "))
            exam3_grade = int(input("Enter grade for exam 3: "))
            writer.writerow([first_name, last_name, exam1_grade, exam2_grade, exam3_grade])
            print("Student's grades recorded.")
        except ValueError:
            print("Invalid input; please enter integer grades.")

print("Exiting and saving file.")
