<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Birthday Surprise 🎂</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:'Poppins',sans-serif;
}

body{
    overflow:hidden;
    background:#050816;
    color:white;
}

/* ==========================
   BACKGROUND
========================== */

.background{
    position:fixed;
    width:100%;
    height:100%;
    overflow:hidden;
    z-index:-10;
    background:
    linear-gradient(135deg,#0f2027,#203a43,#2c5364);
}

.stars{
    position:absolute;
    width:100%;
    height:100%;
    background:url('https://i.ibb.co/8rZ5N7P/stars.png');
    animation:moveStars 80s linear infinite;
    opacity:0.4;
}

@keyframes moveStars{
    from{
        transform:translateY(0);
    }
    to{
        transform:translateY(-2000px);
    }
}

/* ==========================
   LOGIN PAGE
========================== */

#loginPage{
    width:100%;
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    position:absolute;
    overflow:hidden;
}

/* Animated Background */

.islamic-bg{
    position:absolute;
    width:100%;
    height:100%;
    background:
    radial-gradient(circle at top,#1f4037,#0f2027,#000);
    animation:bgMove 8s infinite alternate;
    z-index:-1;
}

@keyframes bgMove{
    from{
        filter:hue-rotate(0deg);
        transform:scale(1);
    }
    to{
        filter:hue-rotate(40deg);
        transform:scale(1.1);
    }
}

/* Floating circles */

.circle{
    position:absolute;
    border-radius:50%;
    background:rgba(255,255,255,0.05);
    animation:float 10s linear infinite;
}

@keyframes float{
    from{
        transform:translateY(100vh) rotate(0deg);
    }
    to{
        transform:translateY(-120vh) rotate(360deg);
    }
}

/* Login Box */

.login-box{
    width:90%;
    max-width:420px;
    padding:45px 35px;
    border-radius:30px;
    background:rgba(255,255,255,0.08);
    border:1px solid rgba(255,255,255,0.15);
    backdrop-filter:blur(12px);
    text-align:center;
    box-shadow:0 0 40px rgba(0,255,200,0.3);
    animation:glowBox 3s infinite alternate;
}

@keyframes glowBox{
    from{
        box-shadow:0 0 20px #00ffd5;
    }
    to{
        box-shadow:0 0 40px #7f5cff;
    }
}

/* Dynamic Text */

.dynamic-text{
    margin-bottom:30px;
}

.dynamic-text h1{
    font-size:1.5rem;
    color:#7fffd4;
    text-shadow:0 0 15px #7fffd4;
    min-height:60px;
    line-height:1.6;
}

.dynamic-text p{
    margin-top:15px;
    font-size:1.2rem;
    color:#fff;
    opacity:0;
    transition:1s;
}

/* Title */

.title{
    margin-bottom:25px;
    font-size:2rem;
    color:white;
    text-shadow:0 0 20px #ff4fd8;
}

/* Inputs */

.input-box{
    margin:20px 0;
}

.input-box input{
    width:100%;
    padding:15px;
    border:none;
    outline:none;
    border-radius:15px;
    background:rgba(255,255,255,0.12);
    color:white;
    font-size:1rem;
}

.input-box input::placeholder{
    color:#ddd;
}

/* Button */

.unlock-btn{
    margin-top:20px;
    width:100%;
    padding:15px;
    border:none;
    border-radius:20px;
    background:linear-gradient(45deg,#00ffd5,#7f5cff);
    color:white;
    font-size:1rem;
    cursor:pointer;
    transition:0.4s;
    box-shadow:0 0 20px #00ffd5;
}

.unlock-btn:hover{
    transform:scale(1.05);
    box-shadow:0 0 30px #7f5cff;
}

/* Error */

#error{
    margin-top:15px;
    color:#ff8f8f;
}

/* Responsive */

@media(max-width:768px){

    .dynamic-text h1{
        font-size:1.2rem;
    }

    .dynamic-text p{
        font-size:1rem;
    }

    .title{
        font-size:1.7rem;
    }
}

</style>
</head>

<body>

<div class="background">
    <div class="stars"></div>
</div>

<!-- LOGIN PAGE -->

<section id="loginPage">

    <div class="islamic-bg"></div>

    <!-- Floating Circles -->

    <div class="circle" style="width:120px;height:120px;left:10%;animation-duration:12s;"></div>
    <div class="circle" style="width:180px;height:180px;left:70%;animation-duration:18s;"></div>
    <div class="circle" style="width:90px;height:90px;left:40%;animation-duration:15s;"></div>

    <div class="login-box">

        <!-- Dynamic Text -->

        <div class="dynamic-text">
            <h1 id="salamText"></h1>
            <p id="jawabText">Jawab do ✨</p>
        </div>

        <h2 class="title">🎂 Birthday Surprise</h2>

        <!-- Username -->

        <div class="input-box">
            <input type="text" id="username" placeholder="Enter Username">
        </div>

        <!-- Password -->

        <div class="input-box">
            <input type="password" id="password" placeholder="Enter Password">
        </div>

        <!-- Button -->

        <button class="unlock-btn" onclick="login()">
            Unlock Surprise ✨
        </button>

        <!-- Error -->

        <div id="error"></div>

    </div>

</section>

<script>

/* ==========================
   SALAM TYPING EFFECT
========================== */

const salam =
"Assalamualaikum warahmatullah barakatuhu";

let sIndex = 0;

function typeSalam(){

    if(sIndex < salam.length){

        document.getElementById("salamText").innerHTML +=
        salam.charAt(sIndex);

        sIndex++;

        setTimeout(typeSalam,80);
    }
}

typeSalam();

/* Show Jawab Do */

setTimeout(()=>{

    document.getElementById("jawabText")
    .style.opacity="1";

},4000);

/* ==========================
   LOGIN
========================== */

function login(){

    const user =
    document.getElementById('username').value;

    const pass =
    document.getElementById('password').value;

    if(user === "bestfriend" &&
       pass === "happybirthday"){

        alert("Login Successful 🎉");

    }else{

        document.getElementById('error')
        .innerHTML =
        "Wrong Username or Password 💔";
    }
}

</script>

</body>
</html>
