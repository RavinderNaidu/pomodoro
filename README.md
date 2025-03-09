# pomodoro
index.html
<!DOCTYPE html>
<html>

<head> </head>

<body>
    <div class="cont">
        <h1 class="head">Pomodoro Timer</h1>
        <p class="time" id="para">25:00</p>
        <div>
            <div class="b1">
                <button id="start" onclick="st()" class="st btn">START</button>
                <button id="stop" onclick="stp()" class="stp btn">STOP</button>
                <button id="reset" onclick="rst()" class="reset btn">RESET</button>
            </div>
            <div class="b1">
                <button id="shrt" onclick="sb()" class="sb btn1">SHORT BREAK</button>
                <button id="long" onclick="lb()" class="lb btn1">LONG BREAK</button>
            </div>
        </div>
    </div>
</body>

</html>

index.css
@import url('https://fonts.googleapis.com/css2?family=Bree+Serif&family=Caveat:wght@400;700&family=Lobster&family=Monoton&family=Open+Sans:ital,wght@0,400;0,700;1,400;1,700&family=Playfair+Display+SC:ital,wght@0,400;0,700;1,700&family=Playfair+Display:ital,wght@0,400;0,700;1,700&family=Roboto:ital,wght@0,400;0,700;1,400;1,700&family=Source+Sans+Pro:ital,wght@0,400;0,700;1,700&family=Work+Sans:ital,wght@0,400;0,700;1,700&display=swap');

.cont {
    padding: 10px;
    margin: 50px;
}

.head {
    font-family: "Roboto";
    font-size: 30px;
    text-align: center;
}

.b1 {
    display: flex;
    flex-direction: row;
    justify-content: center;
    padding: 10px;
}

.btn {
    margin: 10px;
    height: 30px;
    cursor: pointer;
    border-radius: 5px;
}

.st {
    background-color: green;
    color: white;
    border-color: green;
}

.stp {
    background-color: red;
    color: white;
    border-color: red;
}

.reset {
    background-color: grey;
    color: white;
    border-color: grey;
}

.sb {
    background-color: blue;
    color: white;
    border-color: blue;
}

.lb {
    background-color: purple;
    color: white;
    border-color: purple;
}

.btn1 {
    margin: 4px;
    height: 35px;
    cursor: pointer;
    border-radius: 5px;
}

.time {
    font-size: 46px;
    text-align: center;
    font-family: "Roboto";
}

index.js:
let p = document.getElementById("para");

let timerInterval = null;

function rst() {
    clearInterval(timerInterval);
    p.textContent = "25:00";
}

function st() {
    clearInterval(timerInterval);

    let timeParts = p.textContent.split(":");
    let minutes = parseInt(timeParts[0]);
    let seconds = parseInt(timeParts[1]);
    let totalSeconds = minutes * 60 + seconds;

    timerInterval = setInterval(() => {
        if (totalSeconds <= 0) {
            clearInterval(timerInterval);
            p.textContent = "00:00";
            return;
        }

        totalSeconds--;

        let displayMinutes = Math.floor(totalSeconds / 60);
        let displaySeconds = totalSeconds % 60;

        p.textContent = `${String(displayMinutes).padStart(2, '0')}:${String(displaySeconds).padStart(2, '0')}`;
    }, 1000);
}

function stp() {
    clearInterval(timerInterval);
}

function sb() {
    clearInterval(timerInterval);
    p.textContent = "05:00";
}

function lb() {
    clearInterval(timerInterval);
    p.textContent = "15:00";
}
