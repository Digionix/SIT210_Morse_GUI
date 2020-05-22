import Tkinter as Tk
import tkFont
from gpiozero import LED
import RPi.GPIO 
from time import sleep

RPi.GPIO.setmode(RPi.GPIO.BCM)


# Hardware

led = LED(18) # Blue LED  


# GUI 

window = Tk.Tk()
window.title("Morse Code Blinker")
myFont = tkFont.Font(family = "Helvetica", size = 12, weight = "bold")


# Event Function
	
def dot():
    led.on()
    sleep(0.50)
    led.off()
    sleep(1)


def dash():
    led.on()
    sleep(1.50)
    led.off()
    sleep(1)
   
   
def split(word):
	return [char for char in word]
	



def Convert_To_Morse():
    result = TextBox.get()
    result = result.upper()
    
    if (len(result) <= 12):
	
		letters = split(result)
        for input in letters:
                       
            if (input == 'A'):
                dot()
                dash()
    
            elif (input == 'B'):
                dash()
                dot()
                dot()
                dot()
    
            elif (input == 'C'):
                dash()
                dot()
                dash()
                dot()
      
            elif (input == 'D'):
                dash()
                dot()
                dot()

            elif (input == 'E'):
                dot()
    
            elif (input == 'F'):
                dot()
                dot()
                dot()
                dash()

            elif (input == 'G'):
                dash()
                dot()
                dot()

            elif (input == 'H'):
                dot()
                dot()
                dot()
                dot()

            elif (input == 'I'):
                dot()
                dot()

            elif (input == 'J'):
                dot()
                dash()
                dash()
                dash()

            elif (input == 'K'):
                dash()
                dot()
                dash()

            elif (input == 'L'):
                dot()
                dash()
                dot()
                dot()

            elif (input == 'M'):
                dash()
                dash()

            elif (input == 'N'):
                dash()
                dot()

            elif (input == 'O'):
                dash()
                dash()
                dash()

            elif (input == 'P'):
                dot()
                dash()
                dash()
                dot()

            elif (input == 'Q'):   
                dash()
                dash()
                dot()
                dash()

            elif (input == 'R'):
                dot()
                dash()
                dot()

            elif (input == 'S'):
                dot()
                dot()
                dot()

            elif (input == 'T'):
                dash()

            elif (input == 'U'):
                dot()
                dot()
                dash()

            elif (input == 'V'):
                dot()
                dot()
                dot()
                dash()

            elif (input == 'W'):
                dot()
                dash()
                dash()

            elif (input == 'X'):
                dash()
                dot()
                dot()
                dash()

            elif (input == 'Y'):
                dash()
                dot()
                dash()
                dash()
    
            elif (input == 'Z'):
                dash()
                dash()
                dot()
                dot()

            elif (input == '1'):
                dot()
                dash()
                dash()
                dash()
                dash()

            elif (input == '2'):
                dot()
                dot()
                dash()
                dash()
                dash()

            elif (input == '3'):
                dot()
                dot()
                dot()
                dash()
                dash()

            elif (input == '4'):
                dot()
                dot()
                dot()
                dot()
                dash()

            elif (input == '5'):
                dot()
                dot()
                dot()
                dot()
                dot()

            elif (input == '6'):
                dash()
                dot()
                dot()
                dot()
                dot()

            elif (input == '7'):
                dash()
                dash()
                dot()
                dot()
                dot()

            elif (input == '8'):
                dash()
                dash()
                dash()
                dot()
                dot()

            elif (input == '9'):
                dash()
                dash()
                dash()
                dash()
                dot()

            elif (input == '0'):
                dash()
                dash()
                dash()
                dash()
                dash()

            elif (input == ' '):
                sleep(1.50)
			
            elif (input == '.'):
              dot()
              dash()
              dot()
              dash()
              dot()
              dash()
				
            elif (input == ','):
              dash()
              dash()
              dot()
              dot()
              dash()
              dash()

            elif (input == '?'):
              dot()
              dot()
              dash()
              dash()
              dot()
              dot()

            elif (input == '/'):
              dash()
              dot()
              dot()
              dash()
              dot()
			
            else:
                print('Unknown Input detected')
    

def close():
    RPi.GPIO.cleanup()
    window.destroy()

# Input box

Tk.Label(window, text="Enter Text (Max 12 Char) ").grid(row=0)

TextBox = Tk.Entry(window)

TextBox.grid(row=0, column=1)


# Converter	

convertButton = Tk.Button(window, text = "Convert", font = myFont, command = Convert_To_Morse, bg = "red", height = 1, width = 24)
convertButton.grid(row = 0, column = 2)



# Big Exit Button

exitButton = Tk.Button(window, text = "Exit", font = myFont, command = close, bg = "purple", height = 1, width = 24)
exitButton.grid(row = 1, column = 1)

window.protocol("WM_DELETE_WINDOW", close) # for clean exit

window.mainloop()




