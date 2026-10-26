# Project-Password-Generator
import secrets
import string

print("===== PASSWORD GENERATOR =====")
length = int(input("Enter the password length:"))


while length <= 0:
    print("Please enter a positive length!")
    length = int(input("Enter the password length:"))
i1 = input("Include digits? (yes/no):")
i2 = input("Include symbols? (yes/no):")


def password_(length):
    password = []
    characters = string.ascii_letters
    if i1.lower() == "yes":
        characters += string.digits

    if i2.lower() == "yes":
        characters += string.punctuation

    for i in range(length):
        a = secrets.choice(characters)
        password.append(a)

    return "".join(password)


result = password_(length)
print("Generated password:", result)

with open("passwords.txt", "a") as file:
    file.write(f"Length: {length} | Password: {result}\n")
