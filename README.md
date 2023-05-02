Download Link: https://assignmentchef.com/product/solved-cosc117-homework-5-loops-and-decisions
<br>
For each of the following create a new project with an appropriate name and then write a program that solves the given problem. Remember to use Shift+Ctrl+F to format the program, or Shift+Command+F on the Mac. For each program, you will be submitting the java code file through MyClasses, along with either a Microsoft Word docx file, LibreOffice Writer odt, or a text file (which you can create with NotePad++) which contains the output of at least three runs of each program on different data inputs.

<h1>1             Programming Exercises</h1>

<ol>

 <li>Write a program that will take as input a length (such as 23.4 in) and a conversion unit (such as ft) and output the converted length. Units are to be input by their abbreviations without a . at the end, for example, 23.4 in or 17.98 mi or 56.9 km . The units the program is to convert from and to are in, ft, yd, mi, mm, cm, m, km. A run of the program is below. Have the program print out brief instructions, as below. Also have the program print out an error if either the input units or the conversion units are invalid. The final output should be a simple conversion equation with 5 decimal place accuracy for both the input and output. In the run below, the user typed in 2 mi after the program asked for the length and the km after the program asked for new units. This was the only input from the user.</li>

</ol>

Input a length as &lt;length&gt; &lt;units&gt;, for example, 23.4 ft The &lt;units&gt; can be: in, ft, yd, mi, mm, cm, m, or km.

Do not use a . at the end of the units, so 23.4 feet is 23.4 ft

Length: 26.2 mi

Input the units to be converted to: in, ft, yd, mi, mm, cm, m, or km.

New Units: km

26.20000 mi = 42.16481 km

<strong>Hints:</strong>

<ul>

 <li>Your first input line contains two inputs, the first is a double and the second is a string.</li>

 <li>You may want to trim the input strings in case the user types in some extra spaces.</li>

 <li>It may make the program logic easier if you take the input length and convert it to one unit (inches for example) and then convert that to the desired output unit.</li>

</ul>

<ol start="2">

 <li>This exercise is to implement a method to find a root, or a zero, of a function. In your mathematics classes you have, for many different reasons, needed to solve <em>f</em>(<em>x</em>) = 0 for <em>x</em>. For example, to solve <em>x</em><sup>2 </sup>− 3<em>x </em>+ 1 = 0 you would have used the quadratic formula. Not all functions are as easy to solve as a quadratic, in fact many are so difficult that they cannot be solved exactly but need to be approximated. For example, what about solving sin(<em>x</em>) + cos(<em>x</em>) = 0?</li>

</ol>

1

One method to finding a solution to <em>f</em>(<em>x</em>) = 0 is as follows. In this method you start with a function to find the root of, <em>f</em>(<em>x</em>), a lower bound <em>a </em>and upper bound <em>b </em>values. We choose <em>a </em>and <em>b </em>so that we know there is a solution between them, that is we choose <em>a </em>and <em>b </em>so that <em>f</em>(<em>a</em>) and <em>f</em>(<em>b</em>) have different signs, i.e. one is positive and one is negative. First, make sure that <em>f</em>(<em>a</em>) and <em>f</em>(<em>b</em>) have different signs. If not then print out that there is not a root between these two values and end the program. If they do differ in sign then find the midpoint between <em>a </em>and <em>b</em>, call it <em>m</em>, that is . Evaluate the function at the midpoint, <em>f</em>(<em>m</em>). If <em>f</em>(<em>a</em>) and <em>f</em>(<em>m</em>) have different signs then reset the upper bound <em>b </em>to <em>m</em>. If <em>f</em>(<em>m</em>) and <em>f</em>(<em>b</em>) have different signs then reset the lower bound <em>a </em>to <em>m</em>. Then continue the process with finding the midpoint of the new values of <em>a </em>and <em>b</em>. Keep going until the difference between <em>a </em>and <em>b </em>is less than the input tolerance. Once that happens return the midpoint value. Three runs of the program are below.

Input Initial Lower Bound: 1

Input Initial Upper Bound: 4

Input Tolerance on Approximation: 0.0000001

Approximation to a root at: 2.3561945259571075

Input Initial Lower Bound: 1

Input Initial Upper Bound: 2

Input Tolerance on Approximation: 0.0001 There is no root between 1.0 and 2.0.

Input Initial Lower Bound: 7

Input Initial Upper Bound: 9

Input Tolerance on Approximation: 0.000001

Approximation to a root at: 8.63938045501709

For this one we are going to introduce a simple “method” so that you can evaluate <em>f</em>(<em>x</em>) more easily throughout the program. Below is a start to the program, notice on line 21 we have the code double lbval = f(a). This of course declares the variable lbval and initializes it to the value of the right hand side of the expression. The right hand side of the expression is f(a). What happens here is that the value of <em>a </em>is sent to the value of <em>x </em>in the code on line 31. Then val is given the value of sin(<em>x</em>)+cos(<em>x</em>), that is sin(<em>a</em>)+cos(<em>a</em>). This <em>f</em>(<em>a</em>) value is then returned to line 21 and stored in lbval. The same thing happens but with the value of <em>b </em>on line 22.

1 <strong>import </strong>java.util.Scanner;

2

3 <strong>public class </strong>HW05_Prob1 {

4

<ul>

 <li><strong>public static void </strong>main(String[] args) {</li>

 <li>Scanner keyboard = <strong>new </strong>Scanner(System.in);</li>

</ul>

7

<ul>

 <li>out.print(“Input Initial Lower Bound: “);</li>

 <li><strong>double </strong>a = keyboard.nextDouble();</li>

</ul>

10

<ul>

 <li>out.print(“Input Initial Upper Bound: “);</li>

 <li><strong>double </strong>b = keyboard.nextDouble();</li>

</ul>

13

<ul>

 <li>out.print(“Input Tolerance on Approximation: “);</li>

 <li><strong>double </strong>tolerance = keyboard.nextDouble();</li>

</ul>

16

<ul>

 <li>// This next block is just to show how you will get</li>

</ul>

2

<ul>

 <li>// function values using the f method below. It can be removed 19 // when you submit the program.</li>

</ul>

20

<ul>

 <li><strong>double </strong>lbval = f(a);</li>

 <li><strong>double </strong>ubval = f(b);</li>

</ul>

23

<table width="349">

 <tbody>

  <tr>

   <td width="48">24</td>

   <td width="29"> </td>

   <td width="273">System.out.println(“f(a) = ” + lbval);</td>

  </tr>

  <tr>

   <td width="48">2526</td>

   <td width="29"> </td>

   <td width="273">System.out.println(“f(b) = ” + ubval);</td>

  </tr>

  <tr>

   <td width="48">2728</td>

   <td width="29"> </td>

   <td width="273">// Complete the program.</td>

  </tr>

  <tr>

   <td width="48">2930</td>

   <td width="29">}</td>

   <td width="273"> </td>

  </tr>

 </tbody>

</table>

<ul>

 <li><strong>public static double </strong>f(<strong>double </strong>x) {</li>

 <li><strong>double </strong>val = Math.sin(x) + Math.cos(x);</li>

 <li><strong>return </strong>val;</li>

 <li>}</li>

 <li>}</li>

</ul>

<ol start="3">

 <li>In this exercise you will write a program that will construct a loan payment chart. Unless you are independently wealthy you will be taking out a loan for something in your lifetime. It may be to buy a car or a house. You may already have one for college. When you take out a loan the bank gives you the money in one lump sum and you pay it back with monthly payments. The bank, of course, charges you interest on the loan each month as well.</li>

</ol>

The way the bank determines you monthly payment is a follows. They take the loan amount <em>A</em>, the annual interest rate <em>R </em>in decimal form (i.e. 5% = 0.05), and the number of years the loan is to be paid back <em>Y </em>. They first calculate the term <em>T </em>by

Using this they calculate your monthly payment (call it <em>P</em>) by

If we let <em>B </em>be the balance of the loan (the amount you still owe the bank), then the amount you owe, that is the new balance, after a monthly payment is.

That is, the bank adds the interest on the loan, which is the balance times the interest rate divided by 12, . You divide by 12 since it is interest on one month instead of on an entire year. The bank then subtracts the payment you have made.

For example, say that your balance (<em>B</em>) at the beginning of the current month is $100,000, you are paying $1,250 a month (<em>P</em>) and your annual interest rate is 4.5%

(<em>R </em>= 0<em>.</em>045). Then your new balance for the next month is

and the interest for the month was

3

An example run of the program is below. Your output should look the same with the decimal points lining up, a column for months, balance, monthly interest and total interest for each month.

Input the amount of the loan: 25000

Input the number of years of the loan: 4

Input the interest rate (5% = 0.05): 0.045

Your monthly payment is 570.09

Month                     Balance                      Interest                    Total Int.

<ul>

 <li>00 0.00         0.00</li>

 <li>66 93.75       93.75</li>

 <li>54 91.96       185.71</li>

 <li>62 90.17       275.88</li>

 <li>91 88.37       364.26</li>

 <li>38 86.56       450.82</li>

 <li>05 84.75       535.57</li>

 <li>89 82.93       618.50</li>

 <li>91 81.10       699.61</li>

 <li>09 79.27       778.88</li>

 <li>44 77.43       856.31</li>

 <li>93 75.58       931.89</li>

 <li>57 73.73       1005.62</li>

 <li>35 71.87       1077.49</li>

 <li>27 70.00       1147.49</li>

 <li>30 68.12       1215.61</li>

 <li>46 66.24       1281.85</li>

 <li>72 64.35       1346.20</li>

 <li>09 62.46       1408.66</li>

 <li>55 60.55       1469.21</li>

 <li>11 58.64       1527.85</li>

 <li>74 56.72       1584.57</li>

 <li>45 54.80       1639.37</li>

 <li>23 52.87       1692.24</li>

 <li>07 50.93       1743.16</li>

 <li>96 48.98       1792.14</li>

 <li>90 47.02       1839.17</li>

 <li>88 45.06       1884.23</li>

 <li>88 43.09       1927.32</li>

 <li>92 41.12       1968.44</li>

 <li>96 39.13       2007.58</li>

 <li>02 37.14       2044.72</li>

 <li>08 35.15       2079.87</li>

 <li>13 33.14       2113.00</li>

 <li>17 31.13       2144.13</li>

 <li>18 29.10       2173.23</li>

 <li>17 27.08       2200.31</li>

 <li>13 25.04       2225.35</li>

 <li>03 23.00       2248.35</li>

 <li>89 20.94       2269.29</li>

 <li>69 18.88       2288.17</li>

 <li>42 16.82       2304.99</li>

 <li>07 14.74       2319.73</li>

 <li>65 12.66       2332.39</li>

 <li>13 10.57       2342.96</li>

 <li>51 8.47         2351.44</li>

 <li>79 6.37         2357.80</li>

 <li>96 4.25         2362.05</li>

 <li>00 2.13         2364.18</li>

</ul>

Your loan amount was 25000.00.

Your loan duration was 48.00 months.

4

Your loan monthly payment was 570.09.

Your total interest was 2364.18. Your total cost is 27364.18.

Once your program is complete, use it to answer the following questions. Include the answers with your program runs.

<ul>

 <li>Say you are buying a new car and you take out a loan for $20,000. The best interest rate you can get is 4.7% and you decide to take the loan out for 5 years. What is your monthly payment, the total interest on the loan, and how much did the car actually cost you?</li>

 <li>Say you are buying the same car above but do a 4 year loan. What is your monthly payment, the total interest on the loan, and how much did the car actually cost you? What was the difference in the monthly payment? How much did you save in interest by going with a 4 year loan?</li>

 <li>Let’s consider buying a house, say you take out a loan for $200,000. The bank is giving you an interest rate of 4% and you decide to go with the standard 30 year mortgage. What is your monthly payment, the total interest on the loan, and how much did the house actually cost you?</li>

 <li>Say you took out the same house loan but went with a 20 year mortgage. What is your monthly payment, the total interest on the loan, and how much did the house actually cost you? What was the difference in the monthly payment? How much did you save in interest by going with a 20 year loan instead of a 30 year loan?</li>

</ul>