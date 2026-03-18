<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Сәлем студент</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Roboto', 'Segoe UI', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .container {
            background: #ffffff;
            border-radius: 16px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            padding: 40px;
            max-width: 400px;
            width: 100%;
            text-align: center;
        }

        .app-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 20px;
            margin: 0 auto 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 8px 20px rgba(102, 126, 234, 0.4);
        }

        .app-icon svg {
            width: 40px;
            height: 40px;
            fill: white;
        }

        h1 {
            color: #1a1a1a;
            font-size: 24px;
            font-weight: 600;
            margin-bottom: 8px;
        }

        .subtitle {
            color: #666;
            font-size: 14px;
            margin-bottom: 32px;
        }

        .btn-primary {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 16px 32px;
            font-size: 16px;
            font-weight: 500;
            border-radius: 12px;
            cursor: pointer;
            width: 100%;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.5);
        }

        .btn-primary:active {
            transform: translateY(0);
        }

        .result-card {
            margin-top: 24px;
            padding: 20px;
            background: linear-gradient(135deg, #f5f7fa 0%, #e4e8ec 100%);
            border-radius: 12px;
            border-left: 4px solid #667eea;
            opacity: 0;
            transform: translateY(-10px);
            transition: all 0.4s ease;
        }

        .result-card.show {
            opacity: 1;
            transform: translateY(0);
        }

        .result-text {
            color: #333;
            font-size: 18px;
            font-weight: 500;
            line-height: 1.6;
        }

        .student-badge {
            display: inline-block;
            background: #667eea;
            color: white;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            margin-top: 8px;
            font-weight: 600;
        }

        /* Material ripple effect */
        .ripple {
            position: relative;
            overflow: hidden;
        }

        .ripple::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: rgba(255, 255, 255, 0.3);
            border-radius: 50%;
            transform: translate(-50%, -50%);
            transition: width 0.6s, height 0.6s;
        }

        .ripple:active::after {
            width: 300px;
            height: 300px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="app-icon">
            <svg viewBox="0 0 24 24">
                <path d="M12 3L1 9l4 2.18v6L12 21l7-3.82v-6l2-1.09V17h2V9L12 3zm6.82 6L12 12.72 5.18 9 12 5.28 18.82 9zM17 15.99l-5 2.73-5-2.73v-3.72L12 15l5-2.73v3.72z"/>
            </svg>
        </div>
        
        <h1>Қош келдіңіз!</h1>
        <p class="subtitle">Бағдарламалау әлеміне саяхат</p>
        
        <button class="btn-primary ripple" onclick="showGreeting()">
            Батырманы басыңыз
        </button>
        
        <div id="result" class="result-card">
            <p class="result-text">Сәлем - Сәлем студент!</p>
            <span class="student-badge">🎓 Студент</span>
        </div>
    </div>

    <script>
        function showGreeting() {
            const result = document.getElementById('result');
            result.classList.remove('show');
            
            // Кішкене кідіріспен анимацияны қайта іске қосу
            setTimeout(() => {
                result.classList.add('show');
            }, 100);
        }
    </script>
</body>
</html>
