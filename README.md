
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>8051 Microcontroller Program Repository</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            background-color: #f5f5f5;
            color: #333;
        }
        
        header {
            background-color: #2c3e50;
            color: white;
            padding: 1rem 0;
            text-align: center;
        }
        
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        .program-card {
            background: white;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            margin-bottom: 20px;
            overflow: hidden;
        }
        
        .program-header {
            background-color: #3498db;
            color: white;
            padding: 10px 15px;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .program-content {
            padding: 15px;
            display: none;
        }
        
        pre {
            background-color: #f8f8f8;
            padding: 15px;
            border-radius: 4px;
            overflow-x: auto;
            white-space: pre-wrap;
            word-wrap: break-word;
        }
        
        .copy-btn {
            background-color: #27ae60;
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 3px;
            cursor: pointer;
            margin-top: 10px;
        }
        
        .copy-btn:hover {
            background-color: #2ecc71;
        }
        
        .search-box {
            width: 100%;
            padding: 10px;
            margin-bottom: 20px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }
        
        .category-filter {
            margin-bottom: 20px;
        }
        
        footer {
            text-align: center;
            padding: 20px;
            background-color: #2c3e50;
            color: white;
        }
    </style>
</head>
<body>
    <header>
        <h1>8051 Microcontroller Program Repository</h1>
        <p>A collection of useful 8051 assembly and C programs</p>
    </header>
    
    <div class="container">
        <input type="text" class="search-box" placeholder="Search programs...">
        
        <div class="category-filter">
            <select>
                <option>All Categories</option>
                <option>Memory Operations</option>
                <option>Mathematical Operations</option>
                <option>Sorting Algorithms</option>
                <option>I/O Operations</option>
                <option>Wave Generation</option>
                <option>Motor Control</option>
            </select>
        </div>
        
        <!-- Program 1 -->
        <div class="program-card">
            <div class="program-header" onclick="toggleProgram(this)">
                <h3>1. Memory Block Transfer</h3>
                <span>+</span>
            </div>
            <div class="program-content">
                <p>Transfers a block of data from internal memory location 20H to 40H</p>
                <pre id="program1">
Org 0000h 
MOV R2, #0AH 
MOV R0, #20H ;
MOV R1, #40H ;
BACK: MOV A, @R0 ;
MOV @R1, A ;
INC R0 ;
DJNZ R2, BACK ; 
NOP
END</pre>
                <button class="copy-btn" onclick="copyToClipboard('program1')">Copy Code</button>
            </div>
        </div>
        
        <!-- Program 2 -->
        <div class="program-card">
            <div class="program-header" onclick="toggleProgram(this)">
                <h3>2. External to Internal Memory Transfer</h3>
                <span>+</span>
            </div>
            <div class="program-content">
                <p>Transfers data from external memory (starting at 2000H) to internal memory (starting at 20H)</p>
                <pre id="program2">
Org 0000h ;
MOV DPTR, #2000H ;
MOV R0, #20H ; 
MOV R1, #0AH ;
BACK: MOVX A, @DPTR ;
MOV @R0, A ;
INC DPTR ;
INC R0 ;
DJNZ R1,
NOP 
END</pre>
                <button class="copy-btn" onclick="copyToClipboard('program2')">Copy Code</button>
            </div>
        </div>
        
        <!-- Program 5 -->
        <div class="program-card">
            <div class="program-header" onclick="toggleProgram(this)">
                <h3>5. Addition with Carry Handling</h3>
                <span>+</span>
            </div>
            <div class="program-content">
                <p>Adds two numbers from memory locations 34H and 35H, stores result in R5, handles carry</p>
                <pre id="program5">
Org 0000h
MOV A,34H ;
ADD A,35H ;
MOV R5H,A ;
JNC LAST ;
INC R6
LAST: NOP
END</pre>
                <button class="copy-btn" onclick="copyToClipboard('program5')">Copy Code</button>
            </div>
        </div>
        
        <!-- Program 7 -->
        <div class="program-card">
            <div class="program-header" onclick="toggleProgram(this)">
                <h3>7. Multiplication</h3>
                <span>+</span>
            </div>
            <div class="program-content">
                <p>Multiplies two numbers from 30H and 31H, stores 16-bit result in 32H (LSB) and 33H (MSB)</p>
                <pre id="program7">
Org 0000h
MOV A,30H 
MOV B,31H ;
MUL AB ;
MOV 32H,A ;
MOV 33H,B ;
NOP
END</pre>
                <button class="copy-btn" onclick="copyToClipboard('program7')">Copy Code</button>
            </div>
        </div>
        
        <!-- Program 11a -->
        <div class="program-card">
            <div class="program-header" onclick="toggleProgram(this)">
                <h3>11a. Bubble Sort (Ascending Order)</h3>
                <span>+</span>
            </div>
            <div class="program-content">
                <p>Sorts 6 numbers in ascending order stored in internal memory starting at 20H</p>
                <pre id="program11a">
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
ORDER: INC R0 ;
INC R1 ;
DJNZ R2,INNERLOOP ;
DJNZ R3,EXTERNALLOOP</pre>
                <button class="copy-btn" onclick="copyToClipboard('program11a')">Copy Code</button>
            </div>
        </div>
        
        <!-- Program 13 -->
        <div class="program-card">
            <div class="program-header" onclick="toggleProgram(this)">
                <h3>13. LED Counter (Incrementing)</h3>
                <span>+</span>
            </div>
            <div class="program-content">
                <p>Counts up on Port 0 LEDs with delay between increments</p>
                <pre id="program13">
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
END</pre>
                <button class="copy-btn" onclick="copyToClipboard('program13')">Copy Code</button>
            </div>
        </div>
        
        <!-- Program 17 -->
        <div class="program-card">
            <div class="program-header" onclick="toggleProgram(this)">
                <h3>17. Sum of First 10 Numbers (C)</h3>
                <span>+</span>
            </div>
            <div class="program-content">
                <p>C program to calculate sum of first 10 natural numbers and display on P0</p>
                <pre id="program17">
#INCLUDE &lt;REG51.H&gt; 
VOID MAIN()
{
int i, sum;
sum = 0;
for (i = 1; i <= 10; i++)
{
sum += i;
}
P0=SUM;
}</pre>
                <button class="copy-btn" onclick="copyToClipboard('program17')">Copy Code</button>
            </div>
        </div>
        
        <!-- Program 21 -->
        <div class="program-card">
            <div class="program-header" onclick="toggleProgram(this)">
                <h3>21. Sine Wave Generation</h3>
                <span>+</span>
            </div>
            <div class="program-content">
                <p>Generates sine wave using lookup table output on Port 0</p>
                <pre id="program21">
#include&lt;reg51.h&gt;
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
for(a=0x00;a&lt;0x34;a++)
{
P0=wave_value[a];
}}}</pre>
                <button class="copy-btn" onclick="copyToClipboard('program21')">Copy Code</button>
            </div>
        </div>
        
        <!-- Program 22 -->
        <div class="program-card">
            <div class="program-header" onclick="toggleProgram(this)">
                <h3>22. Stepper Motor Control</h3>
                <span>+</span>
            </div>
            <div class="program-content">
                <p>Controls a stepper motor in anticlockwise direction</p>
                <pre id="program22">
#include&lt;reg51.h&gt;
#define phasea 0x07
#define phaseb 0x0b
#define phasec 0x0d
#define phased 0x0e
void anticlockwise(void);
void delay(void);
int i;
void main ()
{
while(1)
{
anticlockwise();
}}
void anticlockwise(void)
{
P0 = phasea;
delay();
delay();
P0 = phaseb;
delay();
delay();
P0 = phasec;
delay();
delay();
P0 = phased;
delay();
delay();
}
void delay(void)
{
unsigned int i;
for(i=0;i&lt;=4000;i++);
}</pre>
                <button class="copy-btn" onclick="copyToClipboard('program22')">Copy Code</button>
            </div>
        </div>
    </div>
    
    <footer>
        <p>&copy; 2023 Microcontroller Program Repository | Educational Use Only</p>
    </footer>
    
    <script>
        function toggleProgram(header) {
            const content = header.nextElementSibling;
            const icon = header.querySelector('span');
            
            if (content.style.display === 'block') {
                content.style.display = 'none';
                icon.textContent = '+';
            } else {
                content.style.display = 'block';
                icon.textContent = '-';
            }
        }
        
        function copyToClipboard(id) {
            const code = document.getElementById(id).textContent;
            navigator.clipboard.writeText(code).then(() => {
                alert('Code copied to clipboard!');
            });
        }
        
        // Simple search functionality
        document.querySelector('.search-box').addEventListener('input', function(e) {
            const searchTerm = e.target.value.toLowerCase();
            const cards = document.querySelectorAll('.program-card');
            
            cards.forEach(card => {
                const title = card.querySelector('h3').textContent.toLowerCase();
                const description = card.querySelector('p') ? card.querySelector('p').textContent.toLowerCase() : '';
                
                if (title.includes(searchTerm) || description.includes(searchTerm)) {
                    card.style.display = 'block';
                } else {
                    card.style.display = 'none';
                }
            });
        });
    </script>
</body>
</html>
