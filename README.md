import google.ds_python_interpreter as ide

code = """
from weasyprint import HTML
import base64

html_content = '''
<!DOCTYPE html>
<html lang="ka">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>პეტიცია - შეცვალე მომავალი</title>
    <style>
        :root {
            --primary: #2563eb;
            --secondary: #3b82f6;
            --dark: #1e293b;
            --light: #f8fafc;
            --success: #22c55e;
        }
        body {
            font-family: 'Segoe UI', system-ui, sans-serif;
            background-color: var(--light);
            margin: 0;
            display: flex;
            justify-content: center;
            color: var(--dark);
        }
        .container {
            max-width: 600px;
            width: 100%;
            padding: 40px 20px;
        }
        .card {
            background: white;
            padding: 40px;
            border-radius: 24px;
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        .badge {
            background: #dbeafe;
            color: var(--primary);
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 14px;
            font-weight: 600;
            display: inline-block;
            margin-bottom: 20px;
        }
        h1 { font-size: 28px; margin-bottom: 15px; color: var(--dark); }
        p { line-height: 1.6; color: #64748b; margin-bottom: 30px; }
        
        /* Progress Bar */
        .progress-container {
            background: #e2e8f0;
            border-radius: 10px;
            height: 12px;
            width: 100%;
            margin-bottom: 10px;
            overflow: hidden;
        }
        .progress-bar {
            background: var(--primary);
            width: 65%; /* ეს შეიცვლება დინამიურად */
            height: 100%;
            border-radius: 10px;
        }
        .stats { font-size: 14px; margin-bottom: 30px; color: #475569; }

        .input-group { text-align: left; margin-bottom: 20px; }
        label { display: block; margin-bottom: 8px; font-weight: 500; }
        input {
            width: 100%;
            padding: 12px;
            border: 2px solid #e2e8f0;
            border-radius: 10px;
            box-sizing: border-box;
            transition: 0.2s;
        }
        input:focus { border-color: var(--primary); outline: none; }

        .btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 16px 32px;
            border-radius: 12px;
            font-size: 18px;
            font-weight: 600;
            cursor: pointer;
            width: 100%;
            transition: 0.3s;
            box-shadow: 0 4px 6px -1px rgba(37, 99, 235, 0.2);
        }
        .btn:hover { background: var(--secondary); transform: translateY(-2px); }
        
        .footer-note { font-size: 12px; color: #94a3b8; margin-top: 20px; }
    </style>
</head>
<body>
    <div class="container">
        <div class="card">
            <span class="badge">🔥 აქტიური პეტიცია</span>
            <h1>გადავარჩინოთ პარკი</h1>
            <p>ამ პეტიციაზე ხელმოწერით თქვენ ადასტურებთ, რომ წინააღმდეგი ხართ ქალაქის ცენტრში ხეების გაჩეხვის. 0.50$ ხმარდება კამპანიის საინფორმაციო მასალებს.</p>
            
            <div class="progress-container">
                <div class="progress-bar"></div>
            </div>
            <div class="stats"><b>1,245</b> ადამიანმა უკვე მოაწერა ხელი. მიზანი: 2,000</div>

            <div class="input-group">
                <label>თქვენი სახელი</label>
                <input type="text" id="name" placeholder="მაგ: გიორგი ბერიძე">
            </div>

            <button class="btn" onclick="pay()">ხელის მოწერა (0.50$)</button>
            
            <p class="footer-note">უსაფრთხო გადახდა უზრუნველყოფილია Stripe-ის მიერ</p>
        </div>
    </div>

    <script>
        function pay() {
            const name = document.getElementById('name').value;
            if(!name) { alert('გთხოვთ, ჩაწეროთ სახელი'); return; }
            
            // აქ ჩასვამ შენს Stripe Payment Link-ს
            // Stripe საშუალებას გაძლევს ლინკს ბოლოში მიაწერო მომხმარებლის სახელი
            const stripeLink = "შენი_STRIPE_LINK"; 
            window.location.href = stripeLink + "?client_reference_id=" + encodeURIComponent(name);
        }
    </script>
</body>
</html>
'''

with open("petition.html", "w", encoding="utf-8") as f:
    f.write(html_content)
"""

ide.execute(code)
