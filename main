import tkinter
from cryptography.fernet import Fernet

master_key = ""

# create window
window = tkinter.Tk()
window.config(pady=20,padx=20)
window.title("Secret Notes")
window.minsize(400,500)

# title label

title_label = tkinter.Label(text="Enter the title")
title_label.pack()

# title entry

title_entry = tkinter.Entry()
title_entry.focus()
title_entry.pack()

# note label

note_label = tkinter.Label(text="Enter the secret note")
note_label.pack()

# note text box

text_box = tkinter.Text(width=20,height=15)
text_box.pack()

# key label

key_label = tkinter.Label(text="Enter the key")
key_label.pack()

# key entry

key_entry = tkinter.Entry()
key_entry.pack()

# save and encrypt button
def keycreator():
    key1 = str(Fernet.generate_key())
def save_encrypt():
    global master_key
    notes_file = open("notes.txt", "a")
    title = title_entry.get()
    notes_file.write(title)
    notes_file.write("\n")

    key1 = 'u8RAvUKIPE3w3VLklEqXv4466uCeEvlKxCvdvEjxDUs='
    f = Fernet(key1)
    message = text_box.get("1.0",tkinter.END)
    x = message.encode()
    encryption = f.encrypt(x)
    notes_file.write(encryption.decode('utf-8'))
    notes_file.write("\n")
    notes_file.close()

    master_key = key_entry.get()

    title_entry.delete(0,tkinter.END)
    text_box.delete("1.0",tkinter.END)
    key_entry.delete(0,tkinter.END)



save_button = tkinter.Button(text="Save & Encrypt",command=save_encrypt)
save_button.pack()

# decrypt button

def decrypt():
    global master_key
    global title_entry
    title_entry.delete(0,tkinter.END)

    if master_key == key_entry.get() and master_key!="":
        key_entry.delete(0,tkinter.END)
        key1 = 'u8RAvUKIPE3w3VLklEqXv4466uCeEvlKxCvdvEjxDUs='
        f = Fernet(key1)
        message2 = text_box.get("1.0",tkinter.END)
        decryption = f.decrypt(message2)
        text_box.delete("1.0",tkinter.END)
        text_box.insert("1.0",decryption)
    else:
        error_window = tkinter.Tk()
        error_window.title("Error")
        error_window.minsize(150,150)
        error_label = tkinter.Label(error_window,text="Please enter a valid key",font=('Arial',17,'bold'))
        error_label.pack()

        error_button = tkinter.Button(error_window,text="OK",command=error_window.destroy)
        error_button.pack()
        error_window.mainloop()


decrypt_button = tkinter.Button(text="Decrypt",command=decrypt)
decrypt_button.pack()


window.mainloop()
