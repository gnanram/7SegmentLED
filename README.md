# 🕒 7-Segment Digital Clock (Web + Arduino)

This project teaches how digital clocks work using:
- A **real ticking browser clock**
- A **7-segment LED simulation**
- A **real Arduino wiring + code example**

Perfect for STEM classes and beginner electronics.

---

## 🌐 Web Version
Open `index.html` in a browser.
- Displays real time (HH:MM:SS)
- Large LED-style digits
- Uses JavaScript to update every second

---

## 🔌 Arduino Version

### Parts Needed
- Arduino Uno / Nano
- 1× 7-segment display (common cathode)
- 7× 220Ω resistors
- Breadboard + wires

### Segment Wiring

| Segment | Arduino Pin |
|-------|-------------|
| A | 2 |
| B | 3 |
| C | 4 |
| D | 5 |
| E | 6 |
| F | 7 |
| G | 8 |

Upload `arduino/SevenSegmentClock.ino`

---

## 📁 Project Structure

```
mystery-7seg-clock/
├── index.html
├── README.md
├── Teacher_Guide.md
└── arduino/
    └── SevenSegmentClock.ino
```

---

## 👶 Recommended Age
- 8–12: Web clock & segment logic
- 13+: Arduino wiring & multiplexing

---

## 📜 License
Free for education and learning.


Prompt:

Need a show and tel programming of seven segment LED via html pages, with introduction and and how circuit works and to get them introduce to light coding. 
Idea is to introduce them to build a clock with hours, mins and secs

Love this idea — it’s perfect for introducing “light coding” and gently connecting software to electronics 💡⏱️
Below is a show-and-tell style lesson that starts simple, stays visual, and ends with a working clock (HH:MM:SS) using a 7-segment LED simulation in HTML.
This works great for kids / beginners because:


No hardware needed at first


They see how code turns lights on/off


The same logic later transfers to real LEDs or Arduino



1️⃣ Introduction: What is a 7-Segment Display?
A 7-segment display is a set of 7 small lights (LEDs) arranged like this:
  ─ A ─
 |     |
 F     B
 |     |
  ─ G ─
 |     |
 E     C
 |     |
  ─ D ─

Each segment is named A to G.
By turning some lights ON and others OFF, we can show numbers 0–9.
Example


Number 1 → segments B, C


Number 8 → all segments ON


Number 0 → all except G


👉 This is the core idea of light coding:
code = ON / OFF instructions for lights

2️⃣ How the Circuit Works (Concept Only – No Hardware Yet)
When we later use real LEDs:


Each segment is a tiny light


A wire connects it to a pin


Code tells the pin:


HIGH → light ON


LOW → light OFF




💡 Right now, we’ll pretend each segment is an LED using HTML + CSS.

3️⃣ Show & Tell: One Digit Made of Lights (HTML)
This is a single 7-segment digit made using HTML.
Copy-paste and run in a browser
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background: #111;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .digit {
      position: relative;
      width: 120px;
      height: 200px;
    }

    .seg {
      position: absolute;
      background: #333;
      border-radius: 8px;
    }

    .on {
      background: red;
      box-shadow: 0 0 20px red;
    }

    .a { top: 0; left: 20px; width: 80px; height: 15px; }
    .b { top: 15px; right: 0; width: 15px; height: 80px; }
    .c { bottom: 15px; right: 0; width: 15px; height: 80px; }
    .d { bottom: 0; left: 20px; width: 80px; height: 15px; }
    .e { bottom: 15px; left: 0; width: 15px; height: 80px; }
    .f { top: 15px; left: 0; width: 15px; height: 80px; }
    .g { top: 92px; left: 20px; width: 80px; height: 15px; }
  </style>
</head>
<body>

<div class="digit" style="font-color:white;font-size:145px">
  <div class="seg a on"></div>
  <div class="seg b on"></div>
  <div class="seg c on">C</div>
  <div class="seg d "></div>
  <div class="seg e on"></div>
  <div class="seg f on"></div>
  <div class="seg g"></div>
</div>

</body>
</html>

🎉 This displays number 0
Ask kids:

“What happens if I turn G ON?” → 8


4️⃣ Turning Numbers Into Code (Key Learning Moment)
We describe numbers using arrays of segments:
const numbers = {
  0: ["a","b","c","d","e","f"],
  1: ["b","c"],
  2: ["a","b","g","e","d"],
  3: ["a","b","c","d","g"],
  4: ["f","g","b","c"],
  5: ["a","f","g","c","d"],
  6: ["a","f","e","d","c","g"],
  7: ["a","b","c"],
  8: ["a","b","c","d","e","f","g"],
  9: ["a","b","c","d","f","g"]
};

💡 This is exactly how real clocks work inside!

5️⃣ Final Showpiece: Build a Digital Clock (HH:MM:SS)
What this teaches


Time


Loops


Functions


Turning logic into light patterns


Complete Working Clock (HTML + JS)
<!DOCTYPE html>
<html>
<head>
<style>
body {
  background:#000;
  display:flex;
  justify-content:center;
  align-items:center;
  height:100vh;
  color:white;
}

.clock {
  display:flex;
  gap:20px;
}

.digit {
  position: relative;
  width: 60px;
  height: 100px;
}

.seg {
  position: absolute;
  background: #222;
  border-radius: 5px;
}

.on {
  background: red;
  box-shadow: 0 0 10px red;
}

.a { top:0; left:10px; width:40px; height:8px; }
.b { top:8px; right:0; width:8px; height:40px; }
.c { bottom:8px; right:0; width:8px; height:40px; }
.d { bottom:0; left:10px; width:40px; height:8px; }
.e { bottom:8px; left:0; width:8px; height:40px; }
.f { top:8px; left:0; width:8px; height:40px; }
.g { top:46px; left:10px; width:40px; height:8px; }
</style>
</head>
<body>

<div class="clock" id="clock"></div>

<script>
const numbers = {
  0:["a","b","c","d","e","f"],
  1:["b","c"],
  2:["a","b","g","e","d"],
  3:["a","b","c","d","g"],
  4:["f","g","b","c"],
  5:["a","f","g","c","d"],
  6:["a","f","e","d","c","g"],
  7:["a","b","c"],
  8:["a","b","c","d","e","f","g"],
  9:["a","b","c","d","f","g"]
};

function createDigit() {
  const d = document.createElement("div");
  d.className = "digit";
  ["a","b","c","d","e","f","g"].forEach(s=>{
    const seg = document.createElement("div");
    seg.className = "seg " + s;
    d.appendChild(seg);
  });
  return d;
}

function showNumber(digit, num) {
  digit.querySelectorAll(".seg").forEach(s=>{
    s.classList.remove("on");
  });
  numbers[num].forEach(s=>{
    digit.querySelector("." + s).classList.add("on");
  });
}

const clock = document.getElementById("clock");
const digits = [];
for(let i=0;i<6;i++){
  const d = createDigit();
  digits.push(d);
  clock.appendChild(d);
}

function updateClock() {
  const t = new Date();
  const time = [
    Math.floor(t.getHours()/10), t.getHours()%10,
    Math.floor(t.getMinutes()/10), t.getMinutes()%10,
    Math.floor(t.getSeconds()/10), t.getSeconds()%10
  ];
  time.forEach((n,i)=>showNumber(digits[i], n));
}

setInterval(updateClock,1000);
updateClock();
</script>

</body>
</html>

🎉 You now have a fully working 7-segment digital clock

6️⃣ Wrap-Up Talking Points (For Kids)


“Each number is just lights ON or OFF”


“Code is telling lights what to do”


“This is how real clocks, microwaves, and elevators work”


“We built hardware behavior using software!”



7️⃣ Next Natural Steps (Optional)


Add blinking colon


Change colors


Build the same clock with:


Arduino


ESP32


Real 7-segment LED module




Turn this into a stopwatch


If you want, I can:


Convert this into a lesson plan PDF


Simplify for 7–9 year olds


Map this 1:1 to Arduino pins


Create a drag-and-drop version


Just tell me the age group 👨‍🏫✨