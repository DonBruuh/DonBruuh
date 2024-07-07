def calculate_bmi(weight, height):
    """
    Calculates Body Mass Index (BMI) given weight in kilograms and height in meters.
    Formula: weight / (height ** 2)
    """
    return weight / (height ** 2)

def get_valid_input(prompt, input_type):
    """
    Function to get valid input from the user with type checking.
    """
    while True:
        user_input = input(prompt)
        if user_input.strip() == '':
            print("Input cannot be empty. Please try again.")
        else:
            try:
                if input_type == 'int':
                    value = int(user_input)
                elif input_type == 'float':
                    value = float(user_input)
                else:
                    value = user_input  # for string inputs
                return value
            except ValueError:
                print("Invalid input. Please enter a valid number.")

# Get user inputs
first_name = input("Nombre: ")
parental_last_name = input("Apellido Paterno: ")
maternal_last_name = input("Apellido Materno: ")

age = get_valid_input("Edad: ", 'int')
weight = get_valid_input("Peso: ", 'float')
height = get_valid_input("Altura: ", 'float')

# Calculate BMI
bmi = calculate_bmi(weight, height)

# Display gathered information and BMI
print("\nPersonal Information:")
print(f"First Name: {first_name}")
print(f"Parental Last Name: {parental_last_name}")
print(f"Maternal Last Name: {maternal_last_name}")
print(f"Age: {age} years")
print(f"Weight: {weight} kg")
print(f"Height: {height} meters")
print(f"BMI: {bmi:.2f}")

# Interpret BMI
if bmi < 18.5:
    print("BMI Category: Bajo Peso")
elif 18.5 <= bmi < 25:
    print("BMI Category: Peso Normal")
elif 25 <= bmi < 30:
    print("BMI Category: Sobre Peso")
else:
    print("BMI Category: Obesidad")
