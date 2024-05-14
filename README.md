# religious-times-with-python
In this project, I programmed by calling apis and the tkinter library to show the religious times of my city.
import requests
import json
import tkinter as tk
from tkinter import messagebox
from time import strftime

def jprint(Obj):
    text = json.dumps(Obj, sort_keys = True, indent = 8)
    return text

def showMsg():  
    messagebox.showinfo("Message", jprint(responseJson))

#token = {"808212:65c433677d637", "{token}"}
#city = {"تهران", "{city}"}
#en_num = {"true", "{en_num}"}
path1 = r"E:\programming\some coding\GraphicyAppWithPython\oghatsharee.png"
URL1 ="https://one-api.ir/owghat/?token=808212:65c433677d637&city=تهران&en_num=true"
URL2 = "https://one-api.ir/DigitalCurrency/?token=808212:65c433677d637"
URL3 = "https://api.open-notify.org/astros.json"

window = tk.Tk()
window.title("GraphicyApp")
window.size()
window.geometry("400x400")
window.minsize(width=300, height=300)
window.maxsize(width=800, height=800)

response = requests.get(URL1)
responseJson = response.json()

photo = tk.PhotoImage(file = path1)
photoimage = photo.subsample(3, 3)

button1 = tk.Button(window, command = showMsg, text = "نشان بده", font = ("Nazanin",12), image = photoimage, compound = tk.LEFT)
#button1.pack(side = tk.TOP, padx = 100, pady = 100)
#button1.place(x=325, y=125)
button1.place(relx=.5, rely=.5, anchor= "center")

tk.Label(window, text = "اوقات شرعی", font = ("Nazanin",14)).pack(side = tk.TOP, pady = 30)

window.mainloop()
