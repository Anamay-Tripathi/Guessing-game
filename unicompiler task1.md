# UNICOMPILER TASK1


```python
#Anubhuti Srivastava #Rajkiya Engineering College
```

NUMBER GUESSING GAME

Prequities


```python
from tkinter import*
from tkinter import messagebox
```


```python
import random
```


```python
target = 0
score = 10
guess=0
```

Making functions for clues


```python

def add():
   return "The sum of target and guess is " + str(guess+target)
 
def sub():
   return "The difference of target and guess is " + str(target-guess)
 
def multiplication():
   return "The product of target and guess is " + str(guess*target)
 
def division():
   return "The division of target by guess is " + str(target/guess)
 
def greater_lesser():
   if target < guess:
       return 'Target is less than the guess'
   elif target > guess:
       return 'Target is greater than the guess'

```


```python

def clues():
   switcher = {
       0: add(),
       1: sub(),
       2: multiplication(),
       3: division(),
       4: greater_lesser()
       }
   return switcher.get(random.randint(0,4))
        

        
```


```python

def generate_target_number():  
   global target
   target = random.randint(1,10)
   messagebox.showinfo(message="Random Number Generated; Start Guessing!! STARTING SCORE=10")
   #Disable the random number button until game ends   
   random_number_button['state'] = DISABLED 
   #Activate the guessing button
   guess_button['state'] = NORMAL
```


```python

def guess_and_score():
   #Make variables global for access across functions
   global score
   global guess
   try:
       guess =0
       #Read if user submitted an input
       guess = int(guess_entry.get())
   except:
       messagebox.showerror(message="Enter a number to guess and play")
       return
   #If target and guess are the same, print score and prompt to user
   if guess == target:
       messagebox.showinfo(message="Congratulations!!! You guessed the number correct. Your score is "+str(score))
       #Enable random number button to play a new game and disable guessing button
       random_number_button['state'] = NORMAL
       guess_button['state'] = DISABLED 
       return
   #If the user runs out of guesses
   elif score == 0:
       messagebox.showwarning(message="Out of Guesses Buddy! Better luck next time );")
       return
   #Call the guessing functions to give the clues
   else:
       score -= 1
       message=clues()
       messagebox.showinfo(message=message)
```


```python
#Creating User interface
```


```python

window  = Tk()
window.geometry("1000x1000")
window.title("UNICOMPILER PYTHON TASK")
 
#Mention the title of the app
title_label = Label(window, text="UNICOMPILER's Number Guessing Game\nGuess a number between 1 to 10\n\n", font=('Ubuntu Mono',12))
title_label.pack()
 
#Generate random number
random_number_button = Button(window, text="Generate Random Number\n\n", command=generate_target_number)
random_number_button.pack()
#Read User input
guess_label = Label(window, text="\n\nEnter your guess\n\n: ")
guess_label.pack()
guess_entry = Entry(window, width=3)
guess_entry.pack()
#Start guessing
guess_button = Button(window, text="\n\nGuess Me\n\n", command=guess_and_score, state=DISABLED)
guess_button.pack()
#Exit and close the app
window.mainloop()
```


```python

    #end of program
```


```python
#thank  you
```


```python

```
