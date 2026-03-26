<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Тікелей форма - Linear Layout</title>
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
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .container {
            background: #ffffff;
            border-radius: 30px;
            box-shadow: 0 25px 80px rgba(0,0,0,0.3);
            width: 100%;
            max-width: 450px;
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            padding: 40px 30px;
            text-align: center;
            position: relative;
        }

        .header::after {
            content: '';
            position: absolute;
            bottom: -20px;
            left: 0;
            right: 0;
            height: 40px;
            background: white;
            border-radius: 30px 30px 0 0;
        }

        .icon-circle {
            width: 90px;
            height: 90px;
            background: rgba(255,255,255,0.2);
            border-radius: 50%;
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 45px;
            backdrop-filter: blur(10px);
            border: 3px solid rgba(255,255,255,0.3);
            box-shadow: 0 8px 32px rgba(0,0,0,0.1);
        }

        .header h1 {
            font-size: 28px;
            font-weight: 700;
            margin-bottom: 8px;
        }

        .header p {
            opacity: 0.9;
            font-size: 15px;
        }

        .form-area {
            padding: 30px;
        }

        .input-group {
            margin-bottom: 24px;
            position: relative;
        }

        .input-group label {
            display: block;
            color: #555;
            font-size: 13px;
            font-weight: 600;
            margin-bottom: 8px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .input-wrapper {
            position: relative;
        }

        .input-icon {
            position: absolute;
            left: 16px;
            top: 50%;
            transform: translateY(-50%);
            font-size: 20px;
            opacity: 0.5;
        }

        input[type="text"],
        input[type="email"],
        input[type="password"] {
            width: 100%;
            padding: 16px 16px 16px 50px;
            border: 2px solid #e0e0e0;
            border-radius: 16px;
            font-size: 15px;
            transition: all 0.3s;
            background: #fafafa;
        }

        input:focus {
            outline: none;
            border-color: #667eea;
            background: white;
            box-shadow: 0 0 0 4px rgba(102, 126, 234, 0.1);
        }

        .toggle-password {
            position: absolute;
            right: 16px;
            top: 50%;
            transform: translateY(-50%);
            cursor: pointer;
            font-size: 20px;
            opacity: 0.5;
            transition: opacity 0.3s;
        }

        .toggle-password:hover {
            opacity: 1;
        }

        .checkbox-group {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 24px;
        }

        .custom-checkbox {
            width: 24px;
            height: 24px;
            border: 2px solid #ddd;
            border-radius: 6px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s;
        }

        .custom-checkbox.checked {
            background: #667eea;
            border-color: #667eea;
        }

        .custom-checkbox.checked::after {
            content: '✓';
            color: white;
            font-size: 14px;
            font-weight: bold;
        }

        .checkbox-label {
            color: #555;
            font-size: 14px;
            cursor: pointer;
        }

        .submit-btn {
            width: 100%;
            padding: 18px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 16px;
            font-size: 16px;
            font-weight: 700;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            transition: all 0.3s;
            box-shadow: 0 6px 20px rgba(102, 126, 234, 0.4);
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 12px 30px rgba(102, 126, 234, 0.5);
        }

        .submit-btn:active {
            transform: translateY(0);
        }

        .submit-btn::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: rgba(255,255,255,0.3);
            border-radius: 50%;
            transform: translate(-50%, -50%);
            transition: width 0.6s, height 0.6s;
        }

        .submit-btn:active::after {
            width: 400px;
            height: 400px;
        }

        /* ҚЫЗҒЫЛТ САРЫ НӘТИЖЕ */
        .success-message {
            background: linear-gradient(135deg, #FFD93D 0%, #FF6B6B 100%);
            border-radius: 20px;
            padding: 28px;
            margin-top: 24px;
            text-align: center;
            display: none;
            animation: popIn 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
        }

        .success-message.show {
            display: block;
        }

        @keyframes popIn {
            0% {
                opacity: 0;
                transform: scale(0.8) translateY(20px);
            }
            100% {
                opacity: 1;
                transform: scale(1) translateY(0);
            }
        }

        .success-icon {
            width: 70px;
            height: 70px;
            background: white;
            border-radius: 50%;
            margin: 0 auto 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 35px;
            box-shadow: 0 6px 20px rgba(0,0,0,0.1);
        }

        .success-text {
            font-size: 22px;
            font-weight: 800;
            color: white;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        .success-subtext {
            color: rgba(255,255,255,0.95);
            font-size: 14px;
            margin-top: 8px;
        }

        /* XML код бөлімі */
        .code-section {
            background: #1e1e1e;
            border-radius: 20px;
            padding: 24px;
            margin-top: 24px;
        }

        .code-header {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 16px;
        }

        .code-badge {
            background: #667eea;
            color: white;
            padding: 6px 12px;
            border-radius: 8px;
            font-size: 12px;
            font-weight: 600;
        }

        .code-title {
            color: #fff;
            font-size: 14px;
        }

        pre {
            color: #d4d4d4;
            font-family: 'Courier New', monospace;
            font-size: 13px;
            line-height: 1.8;
            overflow-x: auto;
        }

        .tag { color: #569cd6; }
        .attr { color: #9cdcfe; }
        .value { color: #ce9178; }
        .comment { color: #6a9955; }

        .divider {
            height: 1px;
            background: linear-gradient(90deg, transparent, #ddd, transparent);
            margin: 24px 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="icon-circle">📝</div>
            <h1>Тікелей форма</h1>
            <p>Linear Layout - тікелей орналасу</p>
        </div>

        <div class="form-area">
            <!-- Атыңыз -->
            <div class="input-group">
                <label>Атыңыз</label>
                <div class="input-wrapper">
                    <span class="input-icon">👤</span>
                    <input type="text" placeholder="Есіміңізді енгізіңіз" id="nameInput">
                </div>
            </div>

            <!-- Email -->
            <div class="input-group">
                <label>Email</label>
                <div class="input-wrapper">
                    <span class="input-icon">✉️</span>
                    <input type="email" placeholder="email@example.com" id="emailInput">
                </div>
            </div>

            <!-- Құпия сөз -->
            <div class="input-group">
                <label>Құпия сөз</label>
                <div class="input-wrapper">
                    <span class="input-icon">🔒</span>
                    <input type="password" placeholder="••••••••" id="passwordInput">
                    <span class="toggle-password" onclick="togglePassword()">👁️</span>
                </div>
            </div>

            <!-- Checkbox -->
            <div class="checkbox-group" onclick="toggleCheckbox()">
                <div class="custom-checkbox" id="customCheckbox"></div>
                <span class="checkbox-label">Шарттармен келісемін</span>
            </div>

            <!-- Батырма -->
            <button class="submit-btn" onclick="submitForm()">
                Тіркелу →
            </button>

            <!-- Қызғылт сары нәтиже -->
            <div class="success-message" id="successMessage">
                <div class="success-icon">🎉</div>
                <div class="success-text">Сәтті тіркелді!</div>
                <div class="success-subtext">Linear Layout форма жұмыс істейді</div>
            </div>

            <div class="divider"></div>

            <!-- XML коды -->
            <div class="code-section">
                <div class="code-header">
                    <span class="code-badge">XML</span>
                    <span class="code-title">activity_main.xml</span>
                </div>
                <pre><span class="tag">&lt;LinearLayout</span>
    xmlns:android=<span class="value">"http://schemas.android.com/apk/res/android"</span>
    android:layout_width=<span class="value">"match_parent"</span>
    android:layout_height=<span class="value">"match_parent"</span>
    android:orientation=<span class="value">"vertical"</span>
    android:padding=<span class="value">"24dp"</span><span class="tag">&gt;</span>

    <span class="comment">&lt;!-- Тікелей орналасқан элементтер --&gt;</span>
    
    <span class="tag">&lt;EditText</span>
        android:id=<span class="value">"@+id/etName"</span>
        android:layout_width=<span class="value">"match_parent"</span>
        android:layout_height=<span class="value">"wrap_content"</span>
        android:hint=<span class="value">"Атыңыз"</span> <span class="tag">/&gt;</span>

    <span class="tag">&lt;EditText</span>
        android:id=<span class="value">"@+id/etEmail"</span>
        android:layout_width=<span class="value">"match_parent"</span>
        android:layout_height=<span class="value">"wrap_content"</span>
        android:hint=<span class="value">"Email"</span> <span class="tag">/&gt;</span>

    <span class="tag">&lt;Button</span>
        android:id=<span class="value">"@+id/btnSubmit"</span>
        android:layout_width=<span class="value">"match_parent"</span>
        android:layout_height=<span class="value">"wrap_content"</span>
        android:text=<span class="value">"Тіркелу"</span> <span class="tag">/&gt;</span>

<span class="tag">&lt;/LinearLayout&gt;</span></pre>
            </div>
        </div>
    </div>

    <script>
        function togglePassword() {
            const input = document.getElementById('passwordInput');
            const toggle = document.querySelector('.toggle-password');
            
            if (input.type === 'password') {
                input.type = 'text';
                toggle.textContent = '🙈';
            } else {
                input.type = 'password';
                toggle.textContent = '👁️';
            }
        }

        function toggleCheckbox() {
            const checkbox = document.getElementById('customCheckbox');
            checkbox.classList.toggle('checked');
        }

        function submitForm() {
            const name = document.getElementById('nameInput').value;
            const email = document.getElementById('emailInput').value;
            const checkbox = document.getElementById('customCheckbox').classList.contains('checked');
            
            if (name && email && checkbox) {
                document.getElementById('successMessage').classList.add('show');
                
                setTimeout(() => {
                    document.getElementById('successMessage').classList.remove('show');
                }, 3000);
            } else {
                alert('Барлық өрісті толтырыңыз!');
            }
        }
    </script>
</body>
</html>
