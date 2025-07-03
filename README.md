# Calculator
My first project using python.


from tkinter import *

def click(event):
    text = event.widget.cget("text")
    if text == "=":
        try:
            value = eval(scvalue.get())
            scvalue.set(value)
        except Exception:
            scvalue.set("Error")
    elif text == "C":
        scvalue.set("")
    else:
        scvalue.set(scvalue.get() + text)

root = Tk()
root.geometry("480x650")  
root.title("Created by Rohit")

scvalue = StringVar()
scvalue.set("")
screen = Entry(root, textvar=scvalue, font="lucida 30 bold", justify=RIGHT)
screen.grid(row=0, column=0, columnspan=4, ipadx=8, ipady=15, padx=10, pady=20)

buttons = [
    ["9", "8", "7", "+"],
    ["6", "5", "4", "-"],
    ["3", "2", "1", "*"],
    ["0", "C", "=", "/"],
]

for i in range(4):
    for j in range(4):
        b = Button(root, text=buttons[i][j], font="lucida 20 bold", padx=20, pady=20)
        b.grid(row=i+1, column=j, padx=10, pady=10)
        b.bind("<Button-1>", click)

Button(root, text="Close", command=root.destroy, font="lucida 15").grid(row=5, column=0, columnspan=4, pady=20)

root.mainloop()

