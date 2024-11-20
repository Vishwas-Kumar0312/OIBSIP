import tkinter as tk
from tkinter import messagebox

# Function to calculate BMI
def calculate_bmi():
    try:
        weight = float(weight_entry.get())
        height = float(height_entry.get()) / 100  # Convert cm to meters
        bmi = weight / (height ** 2)
        bmi_result.set(f"Your BMI is: {bmi:.2f}")
        classify_bmi(bmi)
    except ValueError:
        messagebox.showerror("Input Error", "Please enter valid numbers for weight and height.")

# Function to classify BMI
def classify_bmi(bmi):
    if bmi < 18.5:
        classification = "Underweight"
    elif 18.5 <= bmi < 24.9:
        classification = "Normal weight"
    elif 25 <= bmi < 29.9:
        classification = "Overweight"
    else:
        classification = "Obese"
    classification_label.config(text=f"Classification: {classification}")

# Tkinter window
root = tk.Tk()
root.title("BMI Calculator")

# GUI layout
tk.Label(root, text="Enter your weight (kg):").pack(pady=5)
weight_entry = tk.Entry(root)
weight_entry.pack(pady=5)

tk.Label(root, text="Enter your height (cm):").pack(pady=5)
height_entry = tk.Entry(root)
height_entry.pack(pady=5)

bmi_result = tk.StringVar()
tk.Label(root, textvariable=bmi_result).pack(pady=10)

classification_label = tk.Label(root, text="")
classification_label.pack(pady=5)

tk.Button(root, text="Calculate BMI", command=calculate_bmi).pack(pady=10)

root.mainloop()
