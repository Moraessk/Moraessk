<p align="center">
  <img src="https://i.pinimg.com/originals/eb/50/87/eb50875a68b04b0480fa929af2c7547c.gif">
</p>

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Programming Languages</title>

    <style>
        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            background: #0d1117;
            color: #c9d1d9;
            font-family: "Courier New", monospace;

            display: flex;
            justify-content: center;
            align-items: center;

            height: 100vh;
        }

        .terminal {
            width: 850px;
            min-height: 300px;

            background: #161b22;

            border: 1px solid #30363d;
            border-radius: 12px;

            box-shadow: 0 0 40px rgba(130, 80, 255, 0.25);

            overflow: hidden;
        }

        .top {
            height: 38px;

            display: flex;
            align-items: center;

            padding-left: 15px;

            background: #21262d;

            gap: 7px;
        }

        .circle {
            width: 12px;
            height: 12px;

            border-radius: 50%;
        }

        .red {
            background: #ff5f56;
        }

        .yellow {
            background: #ffbd2e;
        }

        .green {
            background: #27c93f;
        }

        .content {
            padding: 35px;
        }

        .language {
            color: #a371f7;
            font-size: 18px;
            margin-bottom: 8px;
        }

        .code {
            font-size: 22px;
            color: #f0f6fc;

            min-height: 35px;
        }

        .cursor {
            display: inline-block;

            width: 10px;
            height: 22px;

            background: #a371f7;

            animation: blink 0.8s infinite;
        }

        @keyframes blink {
            50% {
                opacity: 0;
            }
        }
    </style>
</head>

<body>

<div class="terminal">

    <div class="top">
        <div class="circle red"></div>
        <div class="circle yellow"></div>
        <div class="circle green"></div>
    </div>

    <div class="content">

        <div class="language" id="language">
            Python
        </div>

        <div class="code">
            <span id="code"></span><span class="cursor"></span>
        </div>

    </div>

</div>


<script>

const codes = [

    {
        language: "Python",
        code: 'print("Hello World!")'
    },

    {
        language: "JavaScript",
        code: 'console.log("Hello World!");'
    },

    {
        language: "Java",
        code: 'System.out.println("Hello World!");'
    },

    {
        language: "C++",
        code: 'cout << "Hello World!";'
    },

    {
        language: "HTML",
        code: '<h1>Hello World!</h1>'
    },

    {
        language: "C#",
        code: 'Console.WriteLine("Hello World!");'
    },

    {
        language: "Rust",
        code: 'println!("Hello World!");'
    }

];


const language = document.getElementById("language");
const code = document.getElementById("code");


let index = 0;


async function sleep(ms) {

    return new Promise(resolve => setTimeout(resolve, ms));

}


async function typeText(text) {

    code.textContent = "";

    for (let i = 0; i < text.length; i++) {

        code.textContent += text[i];

        await sleep(60);

    }

}


async function deleteText(text) {

    for (let i = text.length; i > 0; i--) {

        code.textContent = text.substring(0, i - 1);

        await sleep(30);

    }

}


async function animation() {

    while (true) {

        const current = codes[index];

        language.textContent = current.language;

        await typeText(current.code);

        await sleep(1500);

        await deleteText(current.code);

        await sleep(300);

        index++;

        if (index >= codes.length) {

            index = 0;

        }

    }

}


animation();

</script>

</body>
</html>
