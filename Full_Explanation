## Steps and Justifications to Code-Building

### Step 1: Choosing the Approach
Although I can output a text-based calculator and wait for the user input (such as moving the player in previous labs), I decided not to go for that as it looses the feeling of a real-time calculator. I'd like to go above and beyond by using something not taught in class -- a python GUI interface. The tk interface is the only one that's built into the standard library. This is necessary as this is an assignment that will be accessed by others. A different library may cause inconvenience in the grading process. Generally, I referenced to [Real Python](https://realpython.com/python-gui-tkinter/) for guides regarding Tk interface.

However, later on I realized that macbook has a system bug that affects the color customization. So, a tkmacosx is added as well. **It is recommended that this code is accessed via a macbook to fully demonstrate the code.**
<br>

### Step 2: Setting Up the Interface
First, the base is created with 400X510 pixels (through test and trial) to fit a 7X3 grid with appropriate size for the buttons and display frame. The colors are based on the Apple calculator shown above. The hex numbers are allocated to color names for easier reference. I decided that resizing is not allowed in case the user messes up the proportions. 

Then, the screen display and the buttons are created. According to the tk interface parameters, the interface is created with a constant format as the buttons do repeat itself. For the buttons, if it is at column 2, the 'padx' is set to 0 so that the spacings between the buttons are equal. Additionally, 'sticky' means which side the object is aligned to. If it's all directions ('wens' represent West,East,North,South), then it fills the grid. This is often used to keep the sizes constant. 

(Note: Although this is the second step, this section is mainly at the end of the code as it calls to the functions in the beginning)
<br>

### Step 3: Basic Button Functions
The code corresponding to each button needs to be formed. Different buttons may have different functions. Generally, the numerals button should add numerals onto the screen, the AC button should clear everything, the $+,-,*,/$ are operators, delete allows the user to change their input by deleting, and finally the equal button outputs an evaluated result. 

An additional 'OVERLINE' button is added for additional novelty for this assignment. It should add an overline to the most recent numeral to times it by 1,000. This raises the maximum capcity of the calculator from 3,999 to 3,999,999. This will be the additional function. 

Rather than multiple functions, I realized that it's a class of button functions that relies on the user's input. Therefore, I formatted it as a class with 2 objects that's constantly used: the screen display (self.text) and the total expression (self.expression). Rather than a string, I used a StringVar() as this allows automatic update for the screen display whenever it is changed. 

Most of the functions are quite straightforward, therefore please refer to the comments for explanations regarding the functions. The only thing worth explaining here is that I generally used the ```eval()``` function to evaluate a string expression. Therefore, the characters of +,-,* and / are added directly. Within the function, another 2 functions are often used: __AtoR__ and __RtoA_string__. These are much more complex which is explained in the next section. 
<br>

### Step 4: Converting between Roman and Arabic Numerals & Overline Function

#### Overline Function
One thing quite confusing is that when Python tries to print 'V\u0305', it outputs $V \bar{  }$ (overline after letter) but when the interface outputs the same string, it shows $\bar{V}$. This is important to keep in mind while testing the functions within Jupyter Notebook. Therefore, the overline function is simply appending the overline command '\u0305' to the input. In that case, this means not all characters in the string are Roman Numerals. This complicates the conversions a lot more. 

#### Roman to Arabic
The general rule is that each letter represents a value. Therefore, a function is built to convert a Roman Numeral letter to an integer. However, keep in mind that an overline character will take up two spaces. Rather than writing a code to differentiate the two, I approached this through the use of an array. The index of the Roman array will correspond to the value of the Arabic array with the same index. This way, Python can find corresponding Arabic numbers based on which Roman letters is called through the relationship of their common index. See the code comment for detailed explanations. 

However, one cannot simply add all of these together as subtraction rule applies. Subtraction applies when a small letter value is before a larger letter. Since subtraction is only limited to one letter, one can examine each pair of letters to check if subtraction rule applies. Different expressions is built based on whether the numer is added or subtracted. When debugging, I found that if only the first letter of the pair is added to the final result string, the last letter won't be included. Therefore, dummy numeral 'N' is added to help the code function. See the code comment for detailed explanations. 

Note that the extra overline complicates things. For example, the input can be (take the underscore as the overline) 'C_L_XI' Which is 150,011. The pairs are 'C_','_L','_X','XI' and 'IN' (dummy numerals added). However, the first three pairs isn't really valid as only 2 comparisons are needed: 'C_L_' and 'L_X'. Therefore, a comprehensive if function is given to assign the appropriate pairs to compare for each pair circumstance. See the code comment for detailed explanations. 
<br>

#### Arabic to Roman
This one is a lot more complicated as depending on the power of 10 and the digit value, different Roman numerals will be used with various format. Therefore, I kept the code simpler and less efficient. First, I make sure that the number is within the 3,999,999 bounds of the calculator. Then I reversed the digits so that the index corresponds to the power of tens. Each digit in the Arabic string then moves on to an if list that outputs the appropriate Roman Numeral and format depending on the index of that digit. The index is correlated to the row of the array (power of tens) while the digit corresponds to the format (for example: IV or VI). If the digit is within a number that's over 3999, the reference array will switch to the appropriate one with overlines to output the appropriate Roman Numerals. This way, the conversion from index to power and digit to letters is a lot more straightforward. See the code comment for detailed explanations. 

## Evaluation
The result of this code is an interactive interface that works similar to can actual calculator app. It contains the common operators of addition, subtraction, multiplication and division. The bounds of the calculator is extended further by a factor of 1,000 by using an overline function. Overall, this is a successful calculator with near-final overall aesthetic, sufficient operators for daily calculations, and usable on larger numbers. This should be sufficient for most situations in need for a calculator. 

However, a few limitations exist that may hinder the performance of this calculator:
1. The overline increased the numerals by a factor of 1,000 but I cannot find a way to add the three-sided box to increase the numeral by a factor of 1,000,000. This would also make the code a lot more difficult which may be unrealistic given the time available for this assignment. This means the potential calculation range of this calculator could be much larger but isn't achieved in this assignment. 
2. Due to the limitations and complications, I did not add the fractions for the Roman Numerals. I believe it is beyond the scope of this assignment. But this also means some division won't be accurate when decimals/fractions are involved. This would hinder the performance of the calculator. And since decimals aren't used by Romans, I cannot simply add a decimal to indicate numbers smaller than 1. 
3. As the romans did not use negative numbers, I didn't add this feature into this calculator. However, in our modern calculations, negatives is a vital function. Therefore, this calculator would also not be able to perform this task.
4. And finally, in order to simplify things, I reset the whole calculator when the user presses equal. Therefore, the user cannot continue the calculations like what common calculators can. This feature was one of the planned functions in the assignment but didn't happen due to limited time. 

In conclusion, this is a useful and well constructed (aesthetically) calculator that performs basic functions on larger numbers, and stayed true to the Roman Numeral rules (ie. no negatives, no decimals) but fractions and continuations of the result after pressing equal can be added next time to further improve the functions. 
