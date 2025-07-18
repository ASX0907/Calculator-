# Calculator-
1st git project 
<br/>
Author - ASX
<br>
#html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Modern Calculator</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <div class="calculator">
    <div class="display">
      <input type="text" id="result" disabled>
    </div>
    <div class="buttons">
      <button class="btn special" onclick="clearDisplay()">C</button>
      <button class="btn special" onclick="deleteLast()">DEL</button>
      <button class="btn operator" onclick="append('%')">%</button>
      <button class="btn operator" onclick="append('/')">÷</button>

      <button class="btn" onclick="append('7')">7</button>
      <button class="btn" onclick="append('8')">8</button>
      <button class="btn" onclick="append('9')">9</button>
      <button class="btn operator" onclick="append('*')">×</button>

      <button class="btn" onclick="append('4')">4</button>
      <button class="btn" onclick="append('5')">5</button>
      <button class="btn" onclick="append('6')">6</button>
      <button class="btn operator" onclick="append('-')">−</button>

      <button class="btn" onclick="append('1')">1</button>
      <button class="btn" onclick="append('2')">2</button>
      <button class="btn" onclick="append('3')">3</button>
      <button class="btn operator" onclick="append('+')">+</button>

      <button class="btn zero" onclick="append('0')">0</button>
      <button class="btn" onclick="append('.')">.</button>
      <button class="btn equal" onclick="calculate()">=</button>
    </div>
  </div>

  <script src="script.js"></script>
</body>
</html>
#---------------------------------------

#css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #1e1e2f;
  font-family: 'Segoe UI', sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.calculator {
  background: #2c2f4a;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0px 0px 20px rgba(0,0,0,0.4);
  width: 320px;
}

.display input {
  width: 100%;
  height: 60px;
  background: #1e1e2f;
  color: #fff;
  font-size: 2rem;
  text-align: right;
  padding: 10px;
  border: none;
  border-radius: 10px;
  margin-bottom: 15px;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

.btn {
  height: 60px;
  font-size: 1.5rem;
  border: none;
  border-radius: 10px;
  background: #3a3d5a;
  color: #fff;
  transition: background 0.2s ease;
  cursor: pointer;
}

.btn:hover {
  background: #50536d;
}

.operator {
  background: #f39c12;
}

.operator:hover {
  background: #e67e22;
}

.equal {
  background: #27ae60;
  grid-column: span 1;
}

.equal:hover {
  background: #1e8449;
}

.zero {
  grid-column: span 2;
}

.special {
  background: #c0392b;
}

.special:hover {
  background: #922b21;
}

#---------------------------

#js

const result = document.getElementById("result");

function append(value) {
  result.value += value;
}

function clearDisplay() {
  result.value = "";
}

function deleteLast() {
  result.value = result.value.slice(0, -1);
}

function calculate() {
  try {
    result.value = eval(result.value.replace(/[^-()\d/*+.%]/g, ''));
  } catch {
    result.value = "Error";
  }
}

// Keyboard support
document.addEventListener("keydown", function (e) {
  const key = e.key;

  if (!isNaN(key) || "+-*/.%".includes(key)) {
    append(key);
  } else if (key === "Enter") {
    calculate();
  } else if (key === "Backspace") {
    deleteLast();
  } else if (key === "Escape") {
    clearDisplay();
  }
});


#---------------------------
