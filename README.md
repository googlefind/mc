<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>8051 Programs</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      background: #f9f9f9;
      color: #333;
    }
    h1 {
      text-align: center;
    }
    .program {
      background: white;
      border: 1px solid #ccc;
      padding: 15px;
      margin-bottom: 20px;
      border-radius: 8px;
      position: relative;
      color:white;
    }
    button.copy {
      position: absolute;
      top: 10px;
      right: 10px;
      padding: 5px 10px;
      background: #007BFF;
      color: #fff;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    pre {
      white-space: pre-wrap;
      word-wrap: break-word;
    }
    input[type="text"] {
      width: 100%;
      padding: 10px;
      margin-bottom: 20px;
      font-size: 16px;
    }
  </style>
</head>
<body>
  <h1>
    <img src="https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png" 
     alt="Google Logo" 
     width="150">
</h1>
  <input type="text" id="search" placeholder="Search Program (e.g., 12b or factorial)">
  <div id="programs"></div>

  <script>
    const programs = `
1)
ORG 0000h
MOV R2, #0AH
MOV R0, #20H
MOV R1, #40H
BACK: MOV A, @R0
MOV @R1, A
INC R0
DJNZ R2, BACK
NOP
END

2)
ORG 0000h
MOV DPTR, #2000H
MOV R0, #20H
MOV R1, #0AH
BACK: MOVX A, @DPTR
MOV @R0, A
INC DPTR
INC R0
DJNZ R1
NOP
END

3)
Org 0000H ;
MOV R2, #05H ;
MOV R0, #20H ;
MOV R1, #40H ;
AGAIN: MOV A, @R0
XCH A, @R1 ;.
MOV @R0, A ;
INC R0 ;
INC R1 ;
DJNZ R2, AGAIN ;
STOP: SJMP STOP
END

4)
Org 0000H ;n
MOV R2, #06H ;
MOV R0, #10H ;
MOV DPTR, #00H ;
AGAIN: MOVX A, @DPTR ;
MOV B , @R0 ;
XCH A,B ;
MOV X @DPTR,A ;
MOV @R0,B ;
INC R0 ;.
INC DPTR ;
DJNZ R2, AGAIN ;
STOP: SJMP STOP
END

5)
Org 0000h
MOV A,34H ;
ADD A,35H ;
MOV R5H,A ;
JNC LAST ;
INC R6
LAST: NOP
END

6)
Org 0000h
MOV A,34H ;
SUBB A,35H ;
MOV R5H,A ;
JNC LAST
DEC R6
LAST: NOP
END

7)
Org 0000h
MOV A,30H 
MOV B,31H ;
MUL AB ;
MOV 32H,A ;
MOV 33H,B ;
NOP
END

8)
Org 0000h ;
MOV A,30H
DIV AB ; 
MOV 32H,A ; 
MOV 33H,B ; 
NOP
END

9)
ORG 0000H
MOV DPTR,#1000H ;
MOV R0,#20H 
MOV R1,#30H ;
MOV R2,#08H ;
UP: MOVX A,@DPTR ;
MOV B,A ;
RLC A ;
JC NEG ;
MOV @R0,B ;
INC R0 
JMP LAST
NEG:MOV @R1,B 
INC R1 ;
LAST: INC DPTR 
DJNZ R2,UP ;
NOP
END

10)
ORG 0000H
MOV DPTR,#1000H ;
MOV R0,#20H 
MOV R1,#30H ;
MOV R2,#08H ;
UP: MOVX A,@DPTR ;
MOV B,A ;
RRC A ;
JC ODD ;
MOV @R0,B ;
INC R0 
JMP LAST
ODD:MOV @R1,B 
INC R1 ;
LAST: INC DPTR 
DJNZ R2,UP ;
NOP
END


11a)
ORG 0000H 
MOV R3,#06H 
EXTERNALLOOP: MOV R0,#20H ;
MOV R1,#21H ;
MOV R2,#06H ;
INNERLOOP: MOV A,@R0 ;
MOV B,@R1 
CJNE A,B,CONTINUE ;
CONTINUE: JC ORDER ;
MOV @R1,A 
MOV @R0,B
ORDER: INC R0 ;r
INC R1 ;
DJNZ R2,INNERLOOP ;
DJNZ R3,EXTERNALLOOP

11b)
ORG 0000H ;
MOV R3,#06H 
EXTERNALLOOP: MOV R0,#20H ;
MOV R1,#21H ;
MOV R2,#06H 
INNERLOOP: MOV A,@R0
MOV B,@R1 ;
CJNE A,B,CONTINUE 
CONTINUE: JNC ORDER 
MOV @R1,A ;
MOV @R0,B
ORDER: INC R0 
DJNZ R2,INNERLOOP


12a)
ORG 0000H ;
MOV R2,#05H ;
MOV R0,#20H ;
MOV A,@R0 ;
UP:INC R0 ;
MOV B,@R0
CJNE A,B,CONT ;
CONT: JNC LARGEST ;
MOV A,B ;
LARGEST:DJNZ R2,UP ;
MOV 40H,A ;
NOP
END

12b)
ORG 0000H ;
MOV R2,#05H ;
MOV R0,#20H ;
MOV A,@R0 ;
UP:INC R0 ;
MOV B,@R0
CJNE A,B,CONT ;
CONT: JC SMALLEST ;
MOV A,B ;
SMALLEST:DJNZ R2,UP ;
MOV 40H,A ;
NOP
END

13
ORG 0000H
MOV A,#00H
BACK:MOV P0,A
INC A
CALL DELAY
JMP BACK
DELAY:NOP
MOV R0,#0AAH
UP3:MOV R1,#0FFH
UP2:MOV R2,#0FFH
UP1:DJNZ R2,UP1
DJNZ R1,UP2
DJNZ R0,UP3
RET
END

14
ORG 0000H
MOV A,#0FFH
BACK:MOV P0,A
DEC A
CALL DELAY
JMP BACK
DELAY:NOP
MOV R0,#0AAH
UP3:MOV R1,#0FFH
UP2:MOV R2,#0FFH
UP1:DJNZ R2,UP1
DJNZ R1,UP2
DJNZ R0,UP3
RET
END


15

ORG 0000H
BEGIN:MOV A,#00H
BACK:MOV P0,A
INC A
CALL DELAY
CJNE A,#0AH ,BACK
JMP BEGIN
DELAY:NOP
MOV R0,#0AAH
UP3:MOV R1,#0FFH
UP2:MOV R2,#0FFH
UP1:DJNZ R2,UP1
DJNZ R1,UP2
DJNZ R0,UP3
RET
END

16

ORG 0000H
BEGIN:MOV A,#09H
BACK:MOV P0,A
CALL DELAY
DEC A
CJNE A,#0FFH,BACK
JMP BEGIN
DELAY:NOP
MOV R0,#0AAH
UP3 :MOV R1,#0FFH
UP2:MOV R2,#0FFH
UP1:DJNZ R2,UP1
DJNZ R1,UP2
DJNZ R0,UP3
RET
END

17)
#INCLUDE <REG51.H> VOID MAIN()
{
int i, sum;
sum = 0;
for (i = 1; i <= 10; i++)
{
sum += i;
}
P0=SUM;
}

18)
#include <reg51.h>
 unsigned int FACTORIAL(unsigned int N)
{
unsigned int I ,RESULT = 1;
 for (I = 1; I <= N; I++)
  {
RESULT = RESULT * I;
}
return RESULT;
}
void  main()
{
unsigned int N = 5; 

 unsigned int RESULT = FACTORIAL(N);
P0=RESULT;
}


19
#include<reg51.h>
unsigned int square_lookup_table[] = {0, 1, 4, 9, 16, 25, 36, 49, 64, 81,100};
void main()
{
unsigned char n = 5; 
square_lookup_table[n];
P0=square;
}

20)
#INCLUDE <REG51.H> 
 void main ()
{
UNSIGNED CHAR NUM1, NUM2, I, COUNT_ONES = 0, COUNT_ZEROS = 0;

num1 = 0x23;
num2 = 0x23;
for(i = 0; i < 8; i++)
{
if((num1 & (1 << i)) != 0)
{
count_ones++;
}
else
{
count_zeros++;
}
if((num2 & (1 << i)) != 0)
{
count_ones++;
} else
{
count_zeros++;
}
}
while(1)
{
}
}


21)sine wave
#include<reg51.h>
void main(void)
{
unsigned char
wave_value[53]={0x80,0x90,0xa1,0xb1,0xc0,0xcd,0xda,0xe5,0xee,0xf6,0xfb,0xfe,0xff,0xff,0xfe,
0xfb,0xf6,0xee,0xe5,0xda,0xcd,0xc0,0xb1,0xa1,0x90,0x80,0x80,0x70,0x5f,0x4f,0x40,0x33,0x26,0
x1b,0x12,0x0a,
0x05,0x02,0x00,0x00,0x00,0x02,0x5,0xa,0x12,0x1b,0x26,0x33,0x40,0x4f,0x5f,0x70,0x80};
unsigned char a;
while(1)
{
for(a=0x00;a<0x34;a++)
{
P0=wave_value[a];
}}}

21 square wave
#include<reg51.h>
void delay(unsigned int);
void main(void)
{
while(1)
{
P0=0x00;
delay(10);
P0=0xff;
delay(10);
}}
void delay(unsigned int itime)
{
unsigned int i,j;
for(i=0;i<itime;i++)
for(j=0;j<25;j++);
}




22)
#include<reg51.h>
#define phasea 0x07
#define phaseb 0x0b
#define phasec 0x0d
#define phased 0x0e
void anticlockwise(void);
void delay(void);
int i;
void main () {
  while(1) {
    anticlockwise();
  }
}
void anticlockwise(void) {
  P0 = phasea; delay(); delay();
  P0 = phaseb; delay(); delay();
  P0 = phasec; delay(); delay();
  P0 = phased; delay(); delay();
}
void delay(void) {
  unsigned int i;
  for(i=0;i<=4000;i++);
}
    `.trim().split(/\n(?=\d+\))/);

    const container = document.getElementById('programs');

    programs.forEach(p => {
      const div = document.createElement('div');
      div.className = 'program';

      const pre = document.createElement('pre');
      pre.textContent = p.trim();
      div.appendChild(pre);

      const btn = document.createElement('button');
      btn.textContent = 'Copy';
      btn.className = 'copy';
      btn.onclick = () => navigator.clipboard.writeText(pre.textContent);
      div.appendChild(btn);

      container.appendChild(div);
    });

    document.getElementById('search').addEventListener('input', function() {
      const value = this.value.toLowerCase();
      const divs = document.querySelectorAll('.program');
      divs.forEach(div => {
        const text = div.textContent.toLowerCase();
        div.style.display = text.includes(value) ? 'block' : 'none';
      });
    });
  </script>
</body>
</html>
