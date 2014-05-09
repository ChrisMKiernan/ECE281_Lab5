# Lab 5 Assembly Programming in PRISM

Better late than never? I understand the implications/consequences of this README being very late, and I must accept them. I did, however, assume that having something to be graded is better than nothing.

## Part 1: PRISM setup

The first part of this assignment was to upload a working PRISM code to the FPGA using the ALU from Lab 4. The rest of the components for the PRISM module was provided. Coding this involved nothing more than a few component declarations. In the PRISM module, it was required that we add the ALU and declare the component; basically just hooking up the right wires to the working ALU module. The next step was to declare the whole PRISM module in the Nexys top module from Lab 3, in order that the output of the PRISM program would run on the 7-segment displays. Once again, basically just putting a few wires in the right places. 

The program ran, fully functional on the FPGA on M33, 18 April. 

## Part 2: Assembly Programming

The purpose of this assignment was to create an assembly program that counted up from the current number. If the input was switched to a negative number (8-F), the program should count down from the current number correctly. Requirements for functionality included overflow, that is, when the number got to 99, it should roll over to 00, and vice versa when counting down to 00. My first attempt at this was unsuccessful. I was a little behind my classmates that were working on the Lab, and I decided to jumo into the program without a clear program flow, despite what was suggested in the lab handout. For the first working day of the lab, I was unsuccessful. 

On the second working day, I decided to start from scratch and create a flowchart of the code. This made coding the program much easier, as all conditions were already thought through before I began writing. Using the flowchart I created, coding was much faster, and I completed the entirety of the code in about 30 min. However, when I was done and was testing my code, I ran into a problem: I was attempting to access the wrong memory module at one point in the program, causing the number to get "stuck" every time it needed to pass a "ten" (e.g., from 19-20). While attempting to switch to the programming wizard to solve this, I accidentally closed the program without saving, causing all of my work thus far to be lost. Luckily, with the code written down and having already programed it once, programing it the second time was much easier, and took about 10 min. The code was successful, and was demonstrated on M35, 24 April.

The previous leads me to a suggestion for the PRISM simulator: include a warning before closing the program if the current work is not saved. Granted, the loss of code was nobody's fault but mine, but accidentally closing the program can be very frustrating if you have not saved recently. Unless it is meant to be a lesson in "save early, save often," in which case I suppose I learned my lesson. 

#### Code Flow

![alt text](http://i.imgur.com/1vrppAQ.jpg "The aforementioned flowchart of the assembly code")

This is the flowchart of the code. B1 is considered the LSB and B2 is considered the MSB (least- and most-significant "digit" may be more appropriate here). The code is broken into two main components: add and subtract. To test if I needed to move to the MSB, I added 6 to the digit. This is becasue the code needed to move to the next bit if the digit was "A" (or -6 in binary). That way, I could add 6 and use a "jump if zero" command if the number got to "A." In the case of subtraction, I could simply test if the digit was 0, in which case I would reassign it the value of 9 and most to the MSB, as you can see in the flowchart. 
