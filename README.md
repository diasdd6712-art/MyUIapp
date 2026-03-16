<!DOCTYPE html>
<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Сәлем, Android!</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .container {
            background: white;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            text-align: center;
            max-width: 500px;
            width: 90%;
        }

        .logo {
            width: 100px;
            height: 100px;
            background: #3DDC84;
            border-radius: 20px;
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 50px;
        }

        h1 {
            color: #333;
            font-size: 2.5em;
            margin-bottom: 10px;
            animation: fadeIn 1s ease-in;
        }

        .subtitle {
            color: #666;
            font-size: 1.2em;
            margin-bottom: 30px;
        }

        .code-editor {
            background: #1e1e1e;
            border-radius: 10px;
            padding: 20px;
            text-align: left;
            margin-top: 20px;
            font-family: 'Courier New', monospace;
        }

        .code-header {
            display: flex;
            gap: 8px;
            margin-bottom: 15px;
        }

        .dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
        }

        .red { background: #ff5f56; }
        .yellow { background: #ffbd2e; }
        .green { background: #27c93f; }

        .code-content {
            color: #d4d4d4;
            font-size: 14px;
            line-height: 1.6;
        }

        .keyword { color: #569cd6; }
        .string { color: #ce9178; }
        .function { color: #dcdcaa; }
        .comment { color: #6a9955; }

        .run-btn {
            background: #3DDC84;
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 1.1em;
            border-radius: 30px;
            cursor: pointer;
            margin-top: 20px;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .run-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(61, 220, 132, 0.4);
        }

        .output {
            margin-top: 20px;
            padding: 15px;
            background: #f0f0f0;
            border-radius: 10px;
            border-left: 4px solid #3DDC84;
            display: none;
        }

        .output.show {
            display: block;
            animation: slideIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes slideIn {
            from { opacity: 0; transform: translateX(-20px); }
            to { opacity: 1; transform: translateX(0); }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="logo">🤖</div>
        <h1>Сәлем, Android!</h1>
        <p class="subtitle">Бірінші қосымшаңызды жасау</p>
        
        <div class="code-editor">
            <div class="code-header">
                <div class="dot red"></div>
                <div class="dot yellow"></div>
                <div class="dot green"></div>
            </div>
            <div class="code-content">
                <span class="keyword">public class</span> MainActivity {<br>
                &nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword">protected void</span> <span class="function">onCreate</span>() {<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;System.<span class="function">out</span>.<span class="function">println</span>(<br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="string">"Сәлем, Android!"</span><br>
                &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;);<br>
                &nbsp;&nbsp;&nbsp;&nbsp;}<br>
                }
            </div>
        </div>

        <button class="run-btn" onclick="runCode()">▶ Іске қосу</button>
        
        <div class="output" id="output">
            <strong>Шығыс:</strong><br>
            Сәлем, Android!
        </div>
    </div>

    <script>
        function runCode() {
            const output = document.getElementById('output');
            const btn = document.querySelector('.run-btn');
            
            // Батырма анимациясы
            btn.innerHTML = '⏳ Жүктелуде...';
            btn.style.background = '#ffa500';
            
            setTimeout(() => {
                output.classList.add('show');
                btn.innerHTML = '✓ Орындалды';
                btn.style.background = '#3DDC84';
                
                // 2 секундтан кейін батырманы қайта қалпына келтіру
                setTimeout(() => {
                    btn.innerHTML = '▶ Іске қосу';
                }, 2000);
            }, 1000);
        }
    </script>
</body>
</html>
