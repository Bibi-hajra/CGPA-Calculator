# CGPA-Calculator
def calculate_cgpa():
    clear_screen()
    print_header("CGPA Calculation")

    try:
        num_semesters = int(input_validation("Enter the number of semesters: "))
        sum_gpa = 0

        for i in range(num_semesters):
            prompt = f"Enter GPA for semester {i + 1}: "
            sum_gpa += input_validation(prompt)

        cgpa = round(sum_gpa / num_semesters, 2)
        print(f"Your CGPA is: {cgpa}")
    except ValueError:
        print("Invalid input. Please enter numeric values.")

def display_method():
    clear_screen()
    print_header("Calculation Method")
    print("GPA is calculated as the sum of (credit hours * grade points) for all subjects, divided by the total credit hours.")
    print("CGPA is the average of GPA calculated across all semesters.\n")

def exit_application():
    clear_screen()
    print("Thank you for using the GPA & CGPA Calculator. Goodbye!")

def input_validation(prompt=""):
    while True:
        try:
            value = float(input(prompt))
            if value < 0:
                raise ValueError
            return value
        except ValueError:
            print("Invalid input. Please enter a positive number.")

def clear_screen():
    # Clear the console (cross-platform)
    import os
    os.system("cls" if os.name == "nt" else "clear")

def print_header(title):
    print("=" * len(title))
    print(title)
    print("=" * len(title))

# Main function for testing
if __name__ == "__main__":
    while True:
        print("\nMenu:")
        print("1. Calculate CGPA")
        print("2. Display Method")
        print("3. Exit")

        choice = input_validation("Enter your choice (1-3): ")
        if choice == 1:
            calculate_cgpa()
        elif choice == 2:
            display_method()
        elif choice == 3:
            exit_application()
            break
        else:
            print("Invalid choice. Please select a valid option.")
