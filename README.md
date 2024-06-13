# Task5.1-GUI-
Task 5.1P RPi - Making GUI
import tkinter as tk
from tkinter import Radiobutton
import RPi.GPIO as GPIO

GPIO.setmode(GPIO.BOARD)
red_pin = 11
green_pin = 13
blue_pin = 15
GPIO.setup(red_pin, GPIO.OUT)
GPIO.setup(green_pin, GPIO.OUT)
GPIO.setup(blue_pin, GPIO.OUT)

def all_off():
	GPIO.output(red_pin, GPIO.LOW)
	GPIO.output(green_pin, GPIO.LOW)
	GPIO.output(blue_pin, GPIO.LOW)
	
def led_selection():
	all_off()
	if var.get() == 1:
		GPIO.output(red_pin,GPIO.HIGH)
	elif var.get()==2:
		GPIO.output(green_pin, GPIO.HIGH)
	elif var.get() == 3:
		GPIO.output(blue_pin, GPIO.HIGH)
		
def on_exit():
	all_off()
	GPIO.cleanup()
	root.destroy()
	
root = tk.Tk()
root.title("LED Control")

var = tk.IntVar()

radio_red = Radiobutton(root, text="RED LED", variable=var, value=1, command=led_selection)
radio_red.pack(anchor=tk.W)
radio_green = Radiobutton(root, text="GREEN LED", variable=var, value=2, command=led_selection)
radio_green.pack(anchor=tk.W)
radio_blue = Radiobutton(root, text="BLUE LED", variable=var, value=3, command=led_selection)
radio_blue.pack(anchor=tk.W)

exit_button = tk.Button(root, text="Exit", command=on_exit)
exit_button.pack()

root.mainloop()
