# Digital-Clock-using-Python
# DIGITAL_CLOCK USING PYTHON
import tkinter as tk
from time import strftime

def update_time():
    current_time = strftime('%H:%M:%S')
    clock_label.config(text=current_time)
    if not stop_flag:
        clock_label.after(1000, update_time)

def stop_clock():
    global stop_flag
    stop_flag = True

def restart_clock():
    global stop_flag
    stop_flag = False
    update_time()

#Create the main window
window = tk.Tk()
window.title("Digital Clock")
window.geometry("300x200")
window.resizable(False, False)

#Create a label for displaying the time
clock_label = tk.Label(window, font=("Helvetica", 48), fg="cyan", bg="black")
clock_label.pack(pady=20)

#Create a button to stop the clock
stop_button = tk.Button(window, text="Stop Clock", command=stop_clock)
stop_button.pack()

#Create a button to restart the clock
restart_button = tk.Button(window, text="Restart Clock", command=restart_clock)
restart_button.pack()

#Initialize the stop flag
stop_flag = False

#Start updating the time
update_time()

#Run the main event loop
window.mainloop()
