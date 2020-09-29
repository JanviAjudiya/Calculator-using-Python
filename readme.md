#  calculator
#### 5 files --> view.py, main.py, model.py, controller.py and test.py
#  Library
#  Python GUI using PyQt

## Installation

##### PIP install PyQt5

## Test installation of PyQt5
#### import module
     
import sys  

from PyQt5.QtWidgets import QApplication
from PyQt5.QtWidgets import QLabel
from PyQt5.QtWidgets import QWidget
    
#### Create GUI

app = QApplication(sys.argv)  
window = QWidget()  
window.setWindowTitle('PyQt5 App')  
window.setGeometry(100, 100, 280, 80)  
window.move(600, 15) 

####  This is to label as test 
helloMsg = QLabel('This is Test', parent=window)   
helloMsg.move(60, 30)  
window.show()  
    
    
#### Retain GUI Window


sys.exit(app.exec_())
  


# Calculator Using PyQt5 

## View of application
  
      
#### 1. Create view.py
     
#### 2. Importing following modules

from PyQt5.QtCore import Qt  
from PyQt5.QtWidgets import QMainWindow      
from PyQt5.QtWidgets import QWidget    
from PyQt5.QtWidgets import QGridLayout    
from PyQt5.QtWidgets import QLineEdit    
from PyQt5.QtWidgets import QPushButton     
from PyQt5.QtWidgets import QVBoxLayout 

    
#### 3. Create GUI class and extend QMainWindow class

class GUI(QMainWindow):

 - ##### Add constructor and Parameter

    - Initialzing view constructor i.e. superclass contructor  
    - Setting window titile by  using setWindowTitle  
    - setFixedSize  
    - set central widget and generalLayout by using property generalLayout  
    - centralWidget  
    - createDisplayLED  
    - createButtons  

 - ##### Define Methods
   ##### (Which will create method for Display Panel, Buttons layout and method for set/get/clear display)

    - createDisplayLED()  
    - create buttons by createButtons() and also using grid layout for buttons 
    - display some text by using setDisplayText()  
    - getting display text by using getDisplayText()  
    - clearing display for reusage by clearDisplay()  


## Model of application
      
#### 1. Create model.py
     
#### 2. Create function for calculator's operation

#### 3. Generating errot meassage by exception to handle exception

ERROR_MSG = 'ERROR'  
def evaluateExpression(expression):  
    try:  
        result = str(eval(expression, {}, {}))  
    except Exception:  
        result = ERROR_MSG  
    return result  



## Controller of application
     
#### 1. Create controller.py
     
#### 2. Import following module


from functools import partial

#### Create error meassge

ERROR_MSG = 'ERROR'
    
#### 3. Create Controller class

class Controller:
 - ##### Add constructor

    def _init_(self, model, view):  
        self._evaluate = model  
        self._view = view  
        self._connectSignals()  

 - ##### Define Methods
   ##### (Which will create method for CalculateResult Build expression Connect signals and slots.)Which means evaluate exression.

    - calculateResult()  
    - buildExpression() ## (build expression) 
    - connectSignals() ## (connect signals and slots)


## Main Class
     
#### 1. Create main.py
     
#### 2. Import following module

import sys  

from PyQt5.QtWidgets import QApplication    
from view import GUI  
from model import evaluateExpression  
from controller import Controller  
    
#### 3. Create Main Function
# Client code

def main():  
"""Main function."""
    # Create an instance of QApplication
pycalc = QApplication(sys.argv)  
# Show the calculator's GUI
view = GUI()  
view.show()  
model = evaluateExpression  
Controller(model=model, view=view)  
sys.exit(pycalc.exec_()) 
 
if _name_ == "_main_":  
main()