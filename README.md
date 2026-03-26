<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3 Деңгей - Android UI</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', system-ui, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        h1 {
            text-align: center;
            color: white;
            font-size: 32px;
            margin-bottom: 30px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        .levels-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 25px;
        }

        /* === ЖЕҢІЛ ДЕҢГЕЙ === */
        .level-card {
            background: white;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 15px 40px rgba(0,0,0,0.2);
        }

        .level-header {
            padding: 20px;
            color: white;
            font-weight: 700;
            font-size: 18px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .level-easy .level-header {
            background: linear-gradient(135deg, #84fab0 0%, #8fd3f4 100%);
        }

        .level-medium .level-header {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
        }

        .level-hard .level-header {
            background: linear-gradient(135deg, #fa709a 0%, #fee140 100%);
        }

        .level-badge {
            background: rgba(255,255,255,0.3);
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
        }

        .level-content {
            padding: 25px;
        }

        /* ЖЕҢІЛ: TextView + Button */
        .simple-box {
            background: #f8f9fa;
            border-radius: 16px;
            padding: 30px;
            text-align: center;
        }

        .demo-text {
            color: #333;
            font-size: 20px;
            margin-bottom: 20px;
            padding: 15px;
            background: white;
            border-radius: 12px;
            border-left: 4px solid #84fab0;
        }

        .demo-btn {
            background: linear-gradient(135deg, #84fab0 0%, #8fd3f4 100%);
            color: white;
            border: none;
            padding: 14px 32px;
            border-radius: 25px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: transform 0.3s;
        }

        .demo-btn:hover {
            transform: scale(1.05);
        }

        /* ОРТА: 3 EditText + Button */
        .form-medium input {
            width: 100%;
            padding: 14px 16px;
            margin-bottom: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 12px;
            font-size: 14px;
            transition: all 0.3s;
        }

        .form-medium input:focus {
            outline: none;
            border-color: #f5576c;
        }

        .btn-medium {
            width: 100%;
            padding: 16px;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            border: none;
            border-radius: 12px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
        }

        /* КҮРДЕЛІ: Login системасы */
        .login-container {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
            border-radius: 16px;
            padding: 25px;
            color: white;
        }

        .login-header {
            text-align: center;
            margin-bottom: 20px;
        }

        .login-icon {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #fa709a 0%, #fee140 100%);
            border-radius: 50%;
            margin: 0 auto 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 28px;
        }

        .login-input {
            width: 100%;
            padding: 14px 16px;
            margin-bottom: 12px;
            border: none;
            border-radius: 10px;
            background: rgba(255,255,255,0.1);
            color: white;
            font-size: 14px;
        }

        .login-input::placeholder {
            color: rgba(255,255,255,0.5);
        }

        .btn-login {
            width: 100%;
            padding: 16px;
            background: linear-gradient(135deg, #fa709a 0%, #fee140 100%);
            color: #1a1a2e;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 700;
            cursor: pointer;
            margin-top: 8px;
        }

        /* Қызғылт сары нәтиже */
        .success-result {
            background: linear-gradient(135deg, #FFD93D 0%, #FF6B6B 100%);
            border-radius: 12px;
            padding: 20px;
            margin-top: 16px;
            text-align: center;
            display: none;
            animation: popIn 0.5s ease;
        }

        .success-result.show {
            display: block;
        }

        @keyframes popIn {
            from { opacity: 0; transform: scale(0.9); }
            to { opacity: 1; transform: scale(1); }
        }

        .success-title {
            font-size: 20px;
            font-weight: 800;
            color: white;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.2);
        }

        .success-icon-big {
            font-size: 40px;
            margin-bottom: 10px;
        }

        /* XML код бөлімі */
        .code-section {
            margin-top: 20px;
            background: #1e1e1e;
            border-radius: 12px;
            padding: 16px;
        }

        .code-label {
            color: #888;
            font-size: 11px;
            margin-bottom: 10px;
            text-transform: uppercase;
        }

        pre {
            color: #d4d4d4;
            font-family: 'Courier New', monospace;
            font-size: 12px;
            line-height: 1.6;
            overflow-x: auto;
        }

        .tag { color: #569cd6; }
        .attr { color: #9cdcfe; }
        .value { color: #ce9178; }
        .comment { color: #6a9955; }
        .keyword { color: #c586c0; }

        .error-msg {
            color: #ff6b6b;
            font-size: 13px;
            margin-top: 8px;
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>📱 Android UI - 3 Деңгей</h1>
        
        <div class="levels-grid">
            <!-- === ЖЕҢІЛ ДЕҢГЕЙ === -->
            <div class="level-card level-easy">
                <div class="level-header">
                    <span>🌱</span>
                    <span>ЖЕҢІЛ ДЕҢГЕЙ</span>
                    <span class="level-badge">TextView + Button</span>
                </div>
                <div class="level-content">
                    <div class="simple-box">
                        <div class="demo-text" id="easyText">
                            Сәлем, Android!
                        </div>
                        <button class="demo-btn" onclick="changeText()">
                            Мәтінді өзгерту
                        </button>
                    </div>

                    <!-- Қызғылт сары нәтиже -->
                    <div class="success-result" id="easyResult">
                        <div class="success-icon-big">✨</div>
                        <div class="success-title">TextView өзгерді!</div>
                    </div>

                    <div class="code-section">
                        <div class="code-label">XML Layout</div>
                        <pre><span class="tag">&lt;TextView</span>
    android:id=<span class="value">"@+id/tvHello"</span>
    android:text=<span class="value">"Сәлем!"</span>
    android:layout_width=<span class="value">"wrap_content"</span>
    android:layout_height=<span class="value">"wrap_content"</span> <span class="tag">/&gt;</span>

<span class="tag">&lt;Button</span>
    android:id=<span class="value">"@+id/btnClick"</span>
    android:text=<span class="value">"Басу"</span>
    android:layout_width=<span class="value">"wrap_content"</span>
    android:layout_height=<span class="value">"wrap_content"</span> <span class="tag">/&gt;</span></pre>
                    </div>
                </div>
            </div>

            <!-- === ОРТА ДЕҢГЕЙ === -->
            <div class="level-card level-medium">
                <div class="level-header">
                    <span>⚡</span>
                    <span>ОРТА ДЕҢГЕЙ</span>
                    <span class="level-badge">3 EditText + Оқиға</span>
                </div>
                <div class="level-content">
                    <div class="form-medium">
                        <input type="text" id="nameInput" placeholder="👤 Атыңыз">
                        <input type="email" id="emailInput" placeholder="✉️ Email">
                        <input type="tel" id="phoneInput" placeholder="📱 Телефон">
                        <button class="btn-medium" onclick="submitForm()">
                            Жіберу →
                        </button>
                    </div>

                    <!-- Қызғылт сары нәтиже -->
                    <div class="success-result" id="mediumResult">
                        <div class="success-icon-big">📋</div>
                        <div class="success-title">Форма жіберілді!</div>
                    </div>

                    <div class="code-section">
                        <div class="code-label">Java - Оқиға өңдеу</div>
                        <pre><span class="comment">// Батырмаға оқиға қосу</span>
btnSubmit.setOnClickListener(<span class="keyword">new</span> View.OnClickListener() {
    <span class="attr">@Override</span>
    <span class="keyword">public void</span> onClick(View v) {
        String name = etName.getText().toString();
        String email = etEmail.getText().toString();
        <span class="comment">// Деректерді өңдеу...</span>
    }
});</pre>
                    </div>
                </div>
            </div>

            <!-- === КҮРДЕЛІ ДЕҢГЕЙ === -->
            <div class="level-card level-hard">
                <div class="level-header">
                    <span>🔥</span>
                    <span>КҮРДЕЛІ ДЕҢГЕЙ</span>
                    <span class="level-badge">Login + Тексеру</span>
                </div>
                <div class="level-content">
                    <div class="login-container">
                        <div class="login-header">
                            <div class="login-icon">🔐</div>
                            <h3>Кіру</h3>
                        </div>
                        <input type="text" class="login-input" id="loginUser" placeholder="Қолданушы аты">
                        <input type="password" class="login-input" id="loginPass" placeholder="Құпия сөз">
                        <button class="btn-login" onclick="checkLogin()">
                            Кіру →
                        </button>
                        <div class="error-msg" id="errorMsg">
                            ❌ Логин немесе пароль дұрыс емес!
                        </div>
                    </div>

                    <!-- Қызғылт сары нәтиже -->
                    <div class="success-result" id="hardResult">
                        <div class="success-icon-big">🎉</div>
                        <div class="success-title">Қош келдіңіз!</div>
                        <div style="color: white; opacity: 0.9; font-size: 13px; margin-top: 8px;">
                            Жүйеге сәтті кірдіңіз
                        </div>
                    </div>

                    <div class="code-section">
                        <div class="code-label">Java - Тексеру логикасы</div>
                        <pre><span class="comment">// Логин + Пароль тексеру</span>
<span class="keyword">if</span> (username.equals(<span class="value">"admin"</span>) && 
    password.equals(<span class="value">"1234"</span>)) {
    <span class="comment">// Дұрыс - Қош келдіңіз!</span>
    tvResult.setText(<span class="value">"Қош келдіңіз!"</span>);
} <span class="keyword">else</span> {
    <span class="comment">// Қате - Қате хабарлама</span>
    tvResult.setText(<span class="value">"Дұрыс емес!"</span>);
}</pre>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // ЖЕҢІЛ: TextView өзгерту
        function changeText() {
            const texts = ["Сәлем, Android!", "Hello, World!", "Қош келдіңіз!", "Java + XML"];
            const current = document.getElementById('easyText').textContent;
            const next = texts[(texts.indexOf(current) + 1) % texts.length];
            document.getElementById('easyText').textContent = next;
            
            document.getElementById('easyResult').classList.add('show');
            setTimeout(() => {
                document.getElementById('easyResult').classList.remove('show');
            }, 2000);
        }

        // ОРТА: Форма жіберу
        function submitForm() {
            const name = document.getElementById('nameInput').value;
            const email = document.getElementById('emailInput').value;
            const phone = document.getElementById('phoneInput').value;
            
            if (name && email && phone) {
                document.getElementById('mediumResult').classList.add('show');
                setTimeout(() => {
                    document.getElementById('mediumResult').classList.remove('show');
                }, 3000);
            } else {
                alert('Барлық өрісті толтырыңыз!');
            }
        }

        // КҮРДЕЛІ: Login тексеру
        function checkLogin() {
            const user = document.getElementById('loginUser').value;
            const pass = document.getElementById('loginPass').value;
            const errorMsg = document.getElementById('errorMsg');
            const successResult = document.getElementById('hardResult');
            
            // Дұрыс логин: admin, пароль: 1234
            if (user === 'admin' && pass === '1234') {
                errorMsg.style.display = 'none';
                successResult.classList.add('show');
                setTimeout(() => {
                    successResult.classList.remove('show');
                }, 4000);
            } else {
                errorMsg.style.display = 'block';
                successResult.classList.remove('show');
            }
        }
    </script>
</body>
</html>
