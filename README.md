# basic-calculator
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button class="btn" onclick="clearDisplay()">C</button>
            <button class="btn" onclick="appendNumber('/')">/</button>
            <button class="btn" onclick="appendNumber('*')">*</button>
            <button class="btn" onclick="deleteNumber()">DEL</button>
            <button class="btn" onclick="appendNumber('7')">7</button>
            <button class="btn" onclick="appendNumber('8')">8</button>
            <button class="btn" onclick="appendNumber('9')">9</button>
            <button class="btn" onclick="appendNumber('-')">-</button>
            <button class="btn" onclick="appendNumber('4')">4</button>
            <button class="btn" onclick="appendNumber('5')">5</button>
            <button class="btn" onclick="appendNumber('6')">6</button>
            <button class="btn" onclick="appendNumber('+')">+</button>
            <button class="btn" onclick="appendNumber('1')">1</button>
            <button class="btn" onclick="appendNumber('2')">2</button>
            <button class="btn" onclick="appendNumber('3')">3</button>
            <button class="btn" onclick="calculate()">=</button>
            <button class="btn" onclick="appendNumber('0')">0</button>
            <button class="btn" onclick="appendNumber('.')">.</button>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>


#css
body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f0f0f0;
    margin: 0;
    font-family: Arial, sans-serif;
}

.calculator {
    border: 1px solid #ccc;
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.display {
    background-color: #333;
    color: #fff;
    text-align: right;
    padding: 20px;
    font-size: 2em;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
}

.btn {
    padding: 20px;
    border: 1px solid #ccc;
    background-color: #fff;
    font-size: 1.5em;
    cursor: pointer;
    outline: none;
    transition: background-color 0.3s;
}

.btn:hover {
    background-color: #f0f0f0;
}

.btn:active {
    background-color: #ddd;
}

#javascript
let display = document.getElementById('display');
let currentInput = '';
let operation = '';

function clearDisplay() {
    display.innerText = '0';
    currentInput = '';
    operation = '';
}

function appendNumber(number) {
    if (currentInput === '' && number === '.') {
        currentInput = '0.';
    } else {
        currentInput += number;
    }
    display.innerText = currentInput;
}

function deleteNumber() {
    currentInput = currentInput.slice(0, -1);
    if (currentInput === '') {
        display.innerText = '0';
    } else {
        display.innerText = currentInput;
    }
}

function calculate() {
    try {
        currentInput = eval(currentInput).toString();
        display.innerText = currentInput;
    } catch {
        display.innerText = 'Error';
        currentInput = '';
    }
}

