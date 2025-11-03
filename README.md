# Python_writen_your_num
# 🔢 ASCII Seven-Segment Number Display

A small terminal Python script that renders numbers as large ASCII "seven-segment" style digits using `#` characters.  
No external libraries required — just run the script and enter a number to see it printed in a big, readable style.

---

## Table of Contents
- [About](#about)  
- [Features](#features)  
- [Requirements](#requirements)  
- [Installation](#installation)  
- [Usage](#usage)  
- [Example](#example)  
- [How it works](#how-it-works)  
- [Customization](#customization)  
- [Contributing](#contributing)  
- [License](#license)  
- [Script (`seven_segment_display.py`)](#script-seven_segment_displaypy)

---

## About
This script maps each digit (0–9) to a 7-segment pattern and prints the number using five text lines per digit. It's a fun little utility for creating big numeric displays in a terminal.

---

## Features
- Converts any integer (positive) to a multi-digit ASCII seven-segment display.  
- Pure Python, no dependencies.  
- Clean and easy to read output.

---

## Requirements
- Python 3.x

---

## Installation
1. Create a new repository on GitHub (or use an existing one).  
2. Add a file named `README.md` and paste the contents of this README.  
3. Add the script file (recommended name: `seven_segment_display.py`) with the Python code shown below.  
4. Commit and push to GitHub.

---

## Usage
Run the script from the terminal:

```bash
python seven_segment_display.py
```

When prompted, enter the number you want to display (digits only). The script prints the number using a 5-line ASCII representation.

---

## Example
```
$ python seven_segment_display.py
Enter the number you wish to display: 2019
### ### ##### ### 
#   #   #   #   # 
#   # ### ##### # 
#   # #     #   # 
### ### ##### ### 
```

*(Each digit is drawn as a 5x3 block of characters, separated by a space.)*

---

## How it works
- The script stores seven-segment bit patterns for digits 0–9 (`digits` list).  
- `print_number(num)` converts the number to a string and for each digit:
  - Builds a 5x3 grid (`segs`) initially filled with spaces.
  - Sets `#` characters based on the bit pattern for the digit (top, upper-right, lower-right, bottom, lower-left, upper-left, middle).
  - Joins the rows for all digits and prints five lines to form the large number.
- The script reads user input, converts it to an integer, and calls `print_number()`.

---

## Customization ideas
- Replace `#` with another character (like `*` or `█`) to change the style.  
- Add support for a negative sign or non-numeric characters (e.g., `-`, `:` for a clock).  
- Save output to a text file instead of printing to the terminal.  
- Scale digits (wider/taller) by changing the internal grid and mapping logic.

---

## Contributing
Pull requests and improvements are welcome — for example, adding persistence, more symbols, or configurable styles.

---

## License
This project can be reused freely. Add an open-source license file (e.g., MIT) if you want to clarify usage rights.

---

## Script: `seven_segment_display.py`
Copy the exact code below into `seven_segment_display.py`:

```python
digits = [ '1111110',  	# 0
	   '0110000',	# 1
	   '1101101',	# 2
	   '1111001',	# 3
	   '0110011',	# 4
	   '1011011',	# 5
	   '1011111',	# 6
	   '1110000',	# 7
	   '1111111',	# 8
	   '1111011',	# 9
	   ]


def print_number(num):
	global digits
	digs = str(num)
	lines = [ '' for lin in range(5) ]
	for d in digs:
		segs = [ [' ',' ',' '] for lin in range(5) ]
		ptrn = digits[ord(d) - ord('0')]
		if ptrn[0] == '1':
			segs[0][0] = segs[0][1] = segs[0][2] = '#'
		if ptrn[1] == '1':
			segs[0][2] = segs[1][2] = segs[2][2] = '#'
		if ptrn[2] == '1':
			segs[2][2] = segs[3][2] = segs[4][2] = '#'
		if ptrn[3] == '1':
			segs[4][0] = segs[4][1] = segs[4][2] = '#'
		if ptrn[4] == '1':
			segs[2][0] = segs[3][0] = segs[4][0] = '#'
		if ptrn[5] == '1':
			segs[0][0] = segs[1][0] = segs[2][0] = '#'
		if ptrn[6] == '1':
			segs[2][0] = segs[2][1] = segs[2][2] = '#'
		for lin in range(5):
			lines[lin] += ''.join(segs[lin]) + ' '
	for lin in lines:
		print(lin)


print_number(int(input("Enter the number you wish to display: ")))
```
