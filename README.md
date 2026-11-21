# Arthimetic_Operations_Using_8086
MPMC Ex1
# Arithmetic-operation-using-8086
# 8086 Assembly Language Programs for Arithmetic Operations

## AIM

To write and execute Assembly Language Programs to perform arithmetic operations for the 8086 microprocessor.

---

## APPARATUS REQUIRED

* Personal Computer with MASM Software

---

## 1. ADDITION

#### Algorithm

1.Start the program.

2.Initialize the Data Segment (DS).

3.Load memory address 2000H into SI.

4.Load the first number into AX.

5.Load the second number into BX.

6.Clear CL to store the carry.

7.Add AX and BX using ADD.

8.Check the Carry Flag.

9.If carry is generated, increment CL.

10.Store the sum (AX) into 2004H.

11.Store the carry (CL) into 2006H.

12.Terminate the program.


## FLOW CHART
<img width="942" height="1412" alt="image" src="https://github.com/user-attachments/assets/cf5da4d8-fbfb-405a-b962-4f36f101d155" />



#### Program

```asm
CODE SEGMENT
ASSUME CS:CODE, DS:CODE
ORG 1000H
START:
    MOV AX, CODE
    MOV DS, AX
    MOV SI, 2000H        
    MOV AX, [SI]         
    MOV BX, [SI+02H]     
    MOV CL, 00H          
    ADD AX, BX           
    JNC L1               
    INC CL               
L1:
    MOV [SI+04H], AX     
    MOV [SI+06H], CL     
    MOV AH, 4CH          
    INT 21H
CODE ENDS
END START
END
```

#### Output Table

| INPUT MEMORY LOCATION | INPUT DATA | OUTPUT MEMORY LOCATION | OUTPUT DATA |
| -------------|---------- | -------------|----------- |
|        2000 | FF          |    2004| FE               |
|        2001 | FF          |    2005 |FF               |
|        2002 | FF          |    2006| 01               |
|        2003 | FF          |                         |


#### Manual Calculations

<img width="1600" height="1481" alt="WhatsApp Image 2026-11-17 at 2 30 27 PM" src="https://github.com/user-attachments/assets/467dcd44-df97-431f-bec7-53cc0b72d3ed" />


---

## OUTPUT IMAGE FROM MASM SOFTWARE
<img width="628" height="265" alt="Screenshot 2026-10-10 142120" src="https://github.com/user-attachments/assets/b4589a79-731b-4629-8662-28a176056bad" />


## 2. SUBTRACTION

#### Algorithm

1.	Start the program.

2.	Initialize the Data Segment (DS).

3.	Load memory address 2000H into SI.

4.	Load the first number into AX.

5.	Load the second number into BX.

6.	Clear CL to store the borrow.

7.	Subtract BX from AX using SUB.

8.	Check the Carry Flag (borrow).

9.	If borrow occurs, increment CL.

10.	Store the difference (AX) into 2004H.

11.	Store the borrow (CL) into 2006H.

12.	Terminate the program.


## FLOWCHART

<img width="929" height="1394" alt="image" src="https://github.com/user-attachments/assets/36981e27-3f0f-4507-844b-5c8e7a461faa" />


#### Program
```asm
CODE SEGMENT
ASSUME CS:CODE, DS:CODE
ORG 1000H
START:
    MOV AX, CODE
    MOV DS, AX
    MOV SI, 2000H        
    MOV AX, [SI]         
    MOV BX, [SI+02H]     
    MOV CL, 00H          
    SUB AX, BX           
    JNC L1               
    INC CL               
L1:
    MOV [SI+04H], AX     
    MOV [SI+06H], CL     
    MOV AH, 4CH          
    INT 21H
CODE ENDS
END START
END
```


#### Output Table

| INPUT MEMORY LOCATION | INPUT DATA | OUTPUT MEMORY LOCATION | OUTPUT DATA |
| -------------|---------- | -------------|----------- |
|        2000 | 22          |    2004| 11               |
|        2001 | 22          |    2005 |11               |
|        2002 | 11          |    2006| 00               |
|        2003 | 11          |                         |

#### Manual Calculations

<img width="1600" height="1235" alt="WhatsApp Image 2026-11-17 at 2 30 50 PM" src="https://github.com/user-attachments/assets/6acac1f7-916c-4944-8ea6-224de95a1e72" />


---


## OUTPUT SCREEN FROM MASM SOFTWARE
<img width="648" height="262" alt="Screenshot 2026-10-12 084639" src="https://github.com/user-attachments/assets/50fb56c6-2312-448e-8385-689767f55e02" />


## 3. MULTIPLICATION

#### Algorithm

1.	Start the program.

2.	Initialize the Data Segment (DS).

3.	Load memory address 2000H into SI.

4.	Load the first 16-bit number into AX.

5.	Load the second 16-bit number into BX.

6.	Multiply AX by BX using MUL.

7.	Store the lower 16 bits (AX) into 2004H.

8.	Store the upper 16 bits (DX) into 2006H.

9.	Terminate the program using INT 21H.


##FLOWCHART

<img width="989" height="1484" alt="image" src="https://github.com/user-attachments/assets/239c8029-a75f-4b6e-848e-032654372237" />



#### Program

```asm
CODE SEGMENT
ASSUME CS:CODE, DS:CODE
ORG 1000H
START:
    MOV AX, CODE
    MOV DS, AX
    MOV SI,2000H
    MOV DX,0000H
    MOV AX,[SI]
    MOV BX,[SI+02H]
    MUL BX
    MOV [SI+04H],AX
    MOV [SI+06H],DX
    MOV AH,4CH
    INT 21H
CODE ENDS
END START
```

#### Output Table


| INPUT MEMORY LOCATION | INPUT DATA | OUTPUT MEMORY LOCATION | OUTPUT DATA |
| -------------|---------- | -------------|----------- |
|        2000 | FF          |    2004| 01               |
|        2001 | 44          |    2005 |76               |
|        2002 | FF          |    2006| 98               |
|        2003 | 44          |    2007|12                     |


#### Manual Calculations

<img width="1600" height="1325" alt="WhatsApp Image 2026-11-17 at 2 31 05 PM" src="https://github.com/user-attachments/assets/c2b34a5b-e7c8-41fb-87ac-be0a120f9b2c" />


---

## OUTPUT SCREEN FROM MASM SOFTWARE
<img width="622" height="252" alt="Screenshot 2026-10-12 085727" src="https://github.com/user-attachments/assets/7c991ff1-f62c-442b-8a4f-94bbf4b12c25" />


## 4. DIVISION

#### Algorithm

1.	Start the program.

2.	Initialize the Data Segment (DS).

3.	Load the starting memory address (2000H) into SI.

4.	Clear register DX before performing division.

5.	Load the 16-bit dividend from memory location 2000H into AX.

6.	Load the 16-bit divisor from memory location 2002H into BX.

7.	Divide DX:AX by BX using DIV.

8.	Store the quotient (AX) into memory location 2004H.

9.	Store the remainder (DX) into memory location 2006H.

10.	Stop/terminate the program.


   ## FLOWCHART
<img width="920" height="1114" alt="image" src="https://github.com/user-attachments/assets/392f8c80-8dc2-4912-b064-8fb780711047" />



#### Program

```asm
CODE SEGMENT
ASSUME CS:CODE, DS:CODE
ORG 1000H
START:
    MOV AX, CODE
    MOV DS, AX
    MOV SI,2000H
    MOV DX,0000H        
    MOV AX,[SI]         
    MOV BX,[SI+02H]     
    DIV BX              
    MOV [SI+04H],AX     
    MOV [SI+06H],DX     
    INT 3               
CODE ENDS
END START
END
```

#### Output Table

| INPUT MEMORY LOCATION | INPUT DATA | OUTPUT MEMORY LOCATION | OUTPUT DATA |
| -------------|---------- | -------------|----------- |
|        2000 | 44          |    2004| 02               |
|        2001 | 00          |    2005 |00              |
|        2002 | 22          |    2006| 00               |
|        2003 | 00          |    2007|00                     |

#### Manual Calculations

<img width="1600" height="1333" alt="WhatsApp Image 2026-11-17 at 2 31 20 PM" src="https://github.com/user-attachments/assets/3f0c5535-464d-4b04-80d6-4498b3d189e8" />


---
## OUTPUT FROM MASM SOFTWARE
<img width="647" height="371" alt="Screenshot 2026-10-12 090723" src="https://github.com/user-attachments/assets/9249de76-a7f9-438e-a79e-7492d8cdbe75" />




## RESULT
Thus, the Assembly Language Programs for 8086 to perform arithmetic operations (Addition, Subtraction, Multiplication, and Division) using both direct and indirect methods were successfully written and executed using MASM.

