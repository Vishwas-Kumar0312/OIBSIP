import tkinter as tk
from tkinter import messagebox
import secrets
import string

# Password Generation Logic
def generate_password():
    length = int(length_entry.get())  # Get the length from user input
    use_upper = upper_var.get()  # Check if uppercase letters should be included
    use_lower = lower_var.get()  # Check if lowercase letters should be included
    use_digits = digits_var.get()  # Check if digits should be included
    use_special = special_var.get()  # Check if special characters should be included

    if not any([use_upper, use_lower, use_digits, use_special]):
        messagebox.showwarning("Input Error", "Please select at least one character type.")
        return

    # Construct the character pool based on user selection
    char_pool = ""
    if use_upper:
        char_pool += string.ascii_uppercase
    if use_lower:
        char_pool += string.ascii_lowercase
    if use_digits:
        char_pool += string.digits
    if use_special:
        char_pool += string.punctuation

    # Securely generate password
    password = ''.join(secrets.choice(char_pool) for _ in range(length))
    password_var.set(password)  # Set the password in the label for user to see

# Clipboard integration
def copy_to_clipboard():
    generated_password = password_var.get()
    if generated_password:
        root.clipboard_clear()  # Clear clipboard
        root.clipboard_append(generated_password)  # Append password to clipboard
        messagebox.showinfo("Clipboard", "Password copied to clipboard!")
    else:
        messagebox.showwarning("Copy Error", "No password to copy.")

# Tkinter window setup
root = tk.Tk()
root.title("Advanced Password Generator")
root.geometry("400x400")
root.resizable(False, False)

# Variables
password_var = tk.StringVar()
length_var = tk.IntVar(value=12)  # Default password length is 12
upper_var = tk.BooleanVar(value=True)
lower_var = tk.BooleanVar(value=True)
digits_var = tk.BooleanVar(value=True)
special_var = tk.BooleanVar(value=False)

# Labels and Entries
tk.Label(root, text="Password Length:").pack(pady=5)
length_entry = tk.Entry(root, textvariable=length_var)
length_entry.pack(pady=5)

# Checkbox for password options
tk.Checkbutton(root, text="Include Uppercase Letters", variable=upper_var).pack(anchor="w", padx=20)
tk.Checkbutton(root, text="Include Lowercase Letters", variable=lower_var).pack(anchor="w", padx=20)
tk.Checkbutton(root, text="Include Digits", variable=digits_var).pack(anchor="w", padx=20)
tk.Checkbutton(root, text="Include Special Characters", variable=special_var).pack(anchor="w", padx=20)

# Button to generate password
generate_btn = tk.Button(root, text="Generate Password", command=generate_password)
generate_btn.pack(pady=20)

# Password Display
tk.Label(root, text="Generated Password:").pack(pady=5)
password_display = tk.Entry(root, textvariable=password_var, state="readonly", width=35)
password_display.pack(pady=5)

# Clipboard Button
copy_btn = tk.Button(root, text="Copy to Clipboard", command=copy_to_clipboard)
copy_btn.pack(pady=10)

root.mainloop()
