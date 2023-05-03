Download Link: https://assignmentchef.com/product/solved-cs061-assignment-2-further-familiarization-with-the-basic-lc-3-instructions
<br>
To further familiarize you with the basic LC-3 instructions;

to understand the difference between numeric characters and actual numbers; to handle two’s complement conversions; and to perform basic input/output.




<h1>High Level Description</h1>

Prompt the user to input two single digit numbers.

The second will then be subtracted from the first, and the operation reported in the console:

&lt;first number&gt; – &lt;second number&gt; = &lt;difference&gt;

SO if the user enters 8 and 4, these two numbers will first be echoed to the console on separate lines, then the subtraction operation will be displayed:

<strong>LC-3 I/O</strong>

First, read this <a href="https://docs.google.com/document/d/14vaOKv7-IpuY8VWcoQnq8opl5CpcLHay7sTZG4BzoY4/edit?usp=sharing">brief intro to the LC-3 BIO</a><u>​ </u><a href="https://docs.google.com/document/d/14vaOKv7-IpuY8VWcoQnq8opl5CpcLHay7sTZG4BzoY4/edit?usp=sharing">S</a> <u>​ </u>(Basic Input Output System)

<h1>Low Level Breakdown</h1>

This assignment comprises five tasks:

<ol>

 <li>Prompt the user, and read two numeric characters <em>(</em>​ <em>‘0’ … ‘9’)</em>​ from the user using Trap x20 (GETC). Echo the characters to the console <u>as they are input</u>​ (OUT), and store them as ​      <strong>character</strong>​ data in separate registers.</li>

 <li>Output to the console the operation being performed e.g.</li>

</ol>

5 – 7 =

<em>(how will you print the operation ” – “? How will you print the ” = “? Note the double quotes!!) </em>

<ol start="3">

 <li>Once the setup is printed, convert the numeric characters into the actual numbers they represent (e.g. convert the ASCII code for ‘7’ into the binary representation of the number 7).</li>

 <li>Perform the subtraction operation <em>(</em>​ <em>by taking the two’s complement of the second operand and adding)</em>​, and determine the sign (+/-) of the result; if it is negative, determine the <em><u>magnitude</u></em>​      ​ of the result (i.e. take 2’s complement to turn it back into a positive number).</li>

 <li>Convert resulting number back to a printable character and print it, together with minus sign if necessary.</li>

</ol>

Remember, the number -4 when converted to text is actually two separate and distinct ascii characters, ‘-‘ and ‘4’.

<strong><u>Reminder</u>:</strong><u>​</u><strong> Make sure you <u>always</u></strong>​     <strong> have your Text Window open when you run simpl – this is the only</strong><u>​ </u><strong> way to catch run-time (mostly i/o) errors!  </strong>

<strong>Example, with detailed algorithm </strong>​<strong><em>(we won’t always give you this!) </em></strong>● Program prompts for user input (two characters):

<ul>

 <li>user enters ‘5’, which is echoed to console and copied to a register.</li>

 <li>user enters ‘7’, which is echoed to console and copied to a different register. Program outputs</li>

</ul>

5 – 7 =

<em>(this will actually require at least 4 distinct output steps using OUT and PUTS) </em>

<ul>

 <li>Program converts ‘5’ (ascii code) into 5 (number) and stores it back in the same register.</li>

 <li>Program converts ‘7’ into 7 and stores it back in the same register.</li>

 <li>Program takes 2’s complement of 7, and stores the result back into the same register.</li>

 <li>Program adds the contents of the two registers – i.e. it performs the operation (5-7) and stores the result (-2) in a third register.</li>

 <li>Program recognizes that result is negative, obtains the magnitude of -2 (= 2), and outputs <strong>‘-‘</strong>​ (minus sign).</li>

 <li>Program converts 2 (number) into ‘2’ (ascii code), and stores it back in same register.</li>

 <li>Program outputs ​<strong><em>‘2’</em></strong>​ ​<u>followed by a newline</u>​.</li>

</ul>

<h1>Expected/ Sample output</h1>

In this assignment, your output must ​<strong><em>exactly</em></strong>​ match the following, including:

<ul>

 <li>the prompt, ​<em><u>followed by newline</u> </em></li>

 <li>Each digit input “echoed” and ​<em><u>followed by a newline</u> </em></li>

 <li>the subtraction operation, including spaces as shown, also <u>​<em>followed by a newline</em></u>​:</li>

</ul>

(Difference is Positive)

(Difference is Zero)

(Difference is Negative)

Your code will obviously be tested with a range of different operands giving all possible results. Make sure you test your code likewise!

<strong>NOTES</strong>:​

<ul>

 <li>All console output must be <strong>NEWLINE terminated.</strong>​</li>

</ul>

<h1>          ● We will test only with positive single digit numeric inputs​</h1>

<ul>

 <li><strong>NO </strong>error message is needed for invalid input (i.e. we will not test with non-numeric inputs)​ <strong>Uh</strong><u>…</u><strong>help? </strong></li>

 <li>Trap x20 (GETC) will <em>always</em>​ ​ store the input character into R0.</li>

</ul>

You cannot specify any other register to receive the keyboard input.

<ul>

 <li>Trap x21 (OUT) will ​<em>always</em>​ print whatever ASCII code is stored in R0. You cannot specify any other register to output to screen.</li>

 <li>If the user enters ‘7’, the value stored into R0 is the <u>ASCII code</u>​ ​ b0000 0000 0011 0111</li>

</ul>

( = x0037 = ‘7’ ), <strong><em><u>not</u></em></strong><u>​ </u>​  the <u>number​ </u> 7 = b0000 0000 0000 0111 (= #7).​

Go to ​ <a href="https://www.asciitable.com/">w</a>​ <a href="https://www.asciitable.com/">ww.asciitable.com</a> and see why.​

<em>(conversion between a character and the number it represents will be used repeatedly in this course, so make sure you understand how to do it now!!) </em>

<ul>

 <li>To take the two’s complement of a number ​<em>(i.e. to make a positive number negative or vice versa)</em>​:</li>

</ul>

– Invert the bits ​<em>(what assembly instruction does this?)</em>  – Add one

<ul>

 <li>A neat trick in LC3 to copy the value of one register directly to another:</li>

</ul>

ADD R5, R6, #0   ; R5 ← (R6) + 0,  i.e.  R5 ← (R6)

<ul>

 <li>If the result is negative, remember that you will have to print ​<em><u>two</u></em>​ characters, not one ​<em>(there is no ASCII code for ‘-1’, right?) </em></li>

 <li>If you are struggling with writing LC-3 code from scratch, try writing the program out in pseudo-code or even C++ first. Then, your only task is to convert the logic/code into LC-3.</li>

</ul>

<strong> </strong>

<strong> </strong>