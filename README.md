# Budget
<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تطبيق طلب إنهاء الخدمة</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            direction: rtl;
            text-align: right;
            margin: 20px;
            background-color: #f8f9fa;
        }
        .container {
            max-width: 400px;
            margin: auto;
            padding: 20px;
            background: white;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        label {
            font-weight: bold;
        }
        input, textarea, select {
            width: 100%;
            padding: 8px;
            margin: 5px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #5bc0de;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 10px;
        }
        button:hover {
            background-color: #31b0d5;
        }
    </style>
</head>
<body>

    <div class="container" id="formSection">
        <h2>طلب إنهاء الخدمة</h2>
        
        <label for="name">الاسم الكامل:</label>
        <input type="text" id="name" placeholder="أدخل اسمك" required>

        <label for="email">البريد الإلكتروني:</label>
        <input type="email" id="email" placeholder="example@email.com" required>

        <label for="reason">سبب إنهاء الخدمة:</label>
        <select id="reason" required>
            <option value="">اختر السبب</option>
            <option value="عرض وظيفي جديد">عرض وظيفي جديد</option>
            <option value="مشاكل في بيئة العمل">مشاكل في بيئة العمل</option>
            <option value="أسباب شخصية">أسباب شخصية</option>
            <option value="أخرى">أخرى</option>
        </select>

        <label for="details">تفاصيل إضافية:</label>
        <textarea id="details" rows="4" placeholder="أدخل التفاصيل هنا..."></textarea>

        <button onclick="generateReport()">عرض الطلب</button>
    </div>

    <div class="container" id="printSection" style="display: none;">
        <h2>طلب إنهاء الخدمة</h2>
        <p><strong>الاسم الكامل:</strong> <span id="displayName"></span></p>
        <p><strong>البريد الإلكتروني:</strong> <span id="displayEmail"></span></p>
        <p><strong>سبب إنهاء الخدمة:</strong> <span id="displayReason"></span></p>
        <p><strong>تفاصيل إضافية:</strong></p>
        <p id="displayDetails"></p>

        <button onclick="printForm()">🖨️ طباعة الطلب</button>
        <button onclick="editForm()">✏️ تعديل الطلب</button>
    </div>

    <script>
        function generateReport() {
            document.getElementById("displayName").innerText = document.getElementById("name").value;
            document.getElementById("displayEmail").innerText = document.getElementById("email").value;
            document.getElementById("displayReason").innerText = document.getElementById("reason").value;
            document.getElementById("displayDetails").innerText = document.getElementById("details").value;
            
            document.getElementById("formSection").style.display = "none";
            document.getElementById("printSection").style.display = "block";
        }

        function editForm() {
            document.getElementById("formSection").style.display = "block";
            document.getElementById("printSection").style.display = "none";
        }

        function printForm() {
            window.print();
        }
    </script>
</body>
</html>
