# Code-Conversion-Using-8085

## Aim:

To write 8085 microprocessor programs for converting:
1.	Hexadecimal to ASCII
2.	ASCII to Hexadecimal

## Apparatus Required:
•	Laptop with an internet connection

## Program 1: Hexadecimal to ASCII Conversion

## Algorithm:

1.	Load the hexadecimal number from memory location 4200H.
2.	Mask the upper nibble and check if it is less than 10H.
3.	If it is less than 10H, add 30H to convert it to ASCII.
4.	If it is greater than 10H, add 37H to convert it to ASCII.
5.	Repeat the process for the lower nibble.
6.	Store the ASCII equivalent in memory location 4300H and 4301H.

## Program:
```
LDA 4200H
MOV B,A
ANI 0F0H
RRC
RRC
RRC
RRC
CPI 0AH
JC ADD30
ADI 37H
JMP STORE1
ADD30: ADI 30H
STORE1:STA 4300H
MOV A,B
ANI 0FH
CPI 0AH
JC ADD30L
ADI 37H
JMP STORE2
ADD30L: ADI 30H
STORE2: STA 4301H
HLT
```
## Theory:
![WhatsApp Image 2026-02-20 at 8 55 22 AM](https://github.com/user-attachments/assets/4c016a79-95f5-4c91-83c8-d562231fc451)
![WhatsApp Image 2026-02-20 at 8 56 34 AM](https://github.com/user-attachments/assets/da2b9d47-2cc8-48a8-b9ef-d688e1e72333)
![WhatsApp Image 2026-02-20 at 9 02 02 AM](https://github.com/user-attachments/assets/2c714153-4117-4014-ae78-8634edb0d332)

## Output:
<img width="1872" height="893" alt="Screenshot 2026-02-19 142121" src="https://github.com/user-attachments/assets/cab1941c-ac92-44b4-bc66-c0634b14161e" />
<img width="1882" height="891" alt="Screenshot 2026-02-19 142148" src="https://github.com/user-attachments/assets/c15e5e4e-95bc-4f13-b572-8a7c7ccda36c" />


## Program 2: ASCII to Hexadecimal Conversion

## Algorithm:

1.	Load the first ASCII digit from memory location 4200H.
2.	Convert it to hexadecimal by subtracting 30H (if it's a number) or 37H (if it's a letter A-F).
3.	Load the second ASCII digit from memory location 4201H and repeat the process.
4.	Combine the upper and lower nibbles to form a hexadecimal number.
5.	Store the result in memory location 4300H.

## Program:
```
LDA 4200H
CPI 3AH
JC SUB30
SUI 37H
JMP STOREH
SUB30: SUI 30H

STOREH:MOV C,A
LDA 4201H
CPI 3AH
SUI 37H
JMP STOREL
SUB30L: SUI 30H
STOREL: MOV B,A
MOV A,C
RLC 
RLC
RLC
RLC
ADD B
STA 4300H
HLT
```
## Theory:
![WhatsApp Image 2026-02-20 at 9 10 25 AM](https://github.com/user-attachments/assets/3dc15f9d-aefa-4cde-8490-ba75e3fe483d)
![WhatsApp Image 2026-02-20 at 9 11 29 AM](https://github.com/user-attachments/assets/a88fd510-5a86-4f34-8e71-90c3dfe66922)
![WhatsApp Image 2026-02-20 at 9 13 48 AM](https://github.com/user-attachments/assets/05fa8f64-9957-42b5-8288-007f45b18574)
![WhatsApp Image 2026-02-20 at 9 15 09 AM](https://github.com/user-attachments/assets/45f62fcd-b368-4d82-9bba-8c06bec9100c)
![WhatsApp Image 2026-02-20 at 9 16 09 AM](https://github.com/user-attachments/assets/cf9c8453-17c4-489d-af27-2d7a81b973ce)

## Output:
<img width="1871" height="896" alt="Screenshot 2026-02-19 203450" src="https://github.com/user-attachments/assets/215ca4bc-7361-4e22-8fe8-cdd5c8c3502b" />
<img width="1866" height="894" alt="Screenshot 2026-02-19 203511" src="https://github.com/user-attachments/assets/5c044a4b-3b45-4912-8f65-a8e5adafc583" />



## Result:

The 8085 microprocessor successfully converts hexadecimal numbers to ASCII and vice versa, storing the results in memory.



