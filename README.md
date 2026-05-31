<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <title>Pulse Mod -- Оформление подписки</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: radial-gradient(circle at 10% 20%, #0c111d, #070a12);
            font-family: -apple-system, BlinkMacSystemFont, 'Inter', 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
            padding: 24px 16px;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #eef2ff;
            user-select: none;
            -webkit-tap-highlight-color: transparent;
        }

        .container {
            max-width: 540px;
            width: 100%;
            margin: 0 auto;
        }

        .plan-screen, .payment-screen {
            animation: fadeIn 0.3s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(8px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .plan-screen {
            display: block;
        }

        .plan-screen.hide {
            display: none;
        }

        .payment-screen {
            display: none;
        }

        .payment-screen.active {
            display: block;
        }

        .header {
            text-align: center;
            margin-bottom: 32px;
        }

        .badge {
            background: rgba(59, 130, 246, 0.2);
            backdrop-filter: blur(4px);
            display: inline-block;
            padding: 6px 14px;
            border-radius: 60px;
            font-size: 13px;
            font-weight: 500;
            color: #60a5fa;
            border: 1px solid rgba(59, 130, 246, 0.4);
            margin-bottom: 16px;
        }

        .header h1 {
            font-size: 32px;
            font-weight: 700;
            background: linear-gradient(135deg, #fff, #a5b4fc, #c084fc);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 8px;
            letter-spacing: -0.3px;
        }

        .header p {
            color: #8a99cc;
            font-size: 15px;
        }

        .pricing-card {
            background: rgba(18, 25, 45, 0.65);
            backdrop-filter: blur(12px);
            border-radius: 32px;
            padding: 20px;
            margin-bottom: 18px;
            border: 1px solid rgba(255, 255, 255, 0.06);
            transition: all 0.25s ease;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .pricing-card:hover {
            transform: translateY(-2px);
            background: rgba(25, 35, 60, 0.8);
            border-color: rgba(255, 255, 255, 0.15);
            box-shadow: 0 20px 35px -12px rgba(0, 0, 0, 0.5);
        }

        .popular-badge {
            position: absolute;
            top: 16px;
            right: 20px;
            background: linear-gradient(135deg, #f59e0b, #d97706);
            padding: 4px 12px;
            border-radius: 40px;
            font-size: 12px;
            font-weight: 700;
            color: #0c0f17;
            letter-spacing: -0.2px;
        }

        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: baseline;
            margin-bottom: 8px;
            flex-wrap: wrap;
            padding-right: 80px;
        }

        .plan-name {
            font-size: 22px;
            font-weight: 700;
        }

        .plan-price {
            font-size: 28px;
            font-weight: 800;
            background: linear-gradient(135deg, #fbbf24, #f59e0b);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .plan-desc {
            color: #9aa9d1;
            font-size: 14px;
            margin: 12px 0 8px;
        }

        .buy-btn {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            width: 100%;
            padding: 14px;
            border-radius: 48px;
            font-weight: 600;
            font-size: 16px;
            color: white;
            margin-top: 14px;
            transition: all 0.2s;
            cursor: pointer;
            font-family: inherit;
            backdrop-filter: blur(5px);
        }

        .card-week .buy-btn {
            background: #3b82f6;
            border: none;
            box-shadow: 0 4px 12px rgba(59, 130, 246, 0.3);
        }
        .card-month .buy-btn {
            background: #8b5cf6;
            border: none;
            box-shadow: 0 4px 12px rgba(139, 92, 246, 0.3);
        }
        .card-forever .buy-btn {
            background: #f59e0b;
            border: none;
            box-shadow: 0 4px 12px rgba(245, 158, 11, 0.4);
        }

        .buy-btn:active {
            transform: scale(0.97);
            opacity: 0.9;
        }

        .trust-row {
            display: flex;
            justify-content: center;
            gap: 24px;
            margin-top: 24px;
            margin-bottom: 12px;
            font-size: 13px;
            color: #7c8ab0;
        }

        .trust-item {
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .back-btn {
            background: rgba(255, 255, 255, 0.03);
            border: none;
            color: #90a3df;
            font-size: 15px;
            padding: 10px 0;
            cursor: pointer;
            margin-bottom: 20px;
            width: 100%;
            text-align: left;
            border-radius: 40px;
            padding-left: 12px;
            transition: 0.2s;
        }

        .back-btn:hover {
            color: white;
            background: rgba(255, 255, 255, 0.08);
        }

        .amount-box {
            background: linear-gradient(135deg, rgba(25, 40, 65, 0.7), rgba(15, 22, 40, 0.8));
            backdrop-filter: blur(12px);
            border-radius: 40px;
            padding: 28px 20px;
            text-align: center;
            margin-bottom: 24px;
            border: 1px solid rgba(255, 215, 0, 0.2);
        }

        .amount-label {
            color: #b9c4f0;
            font-size: 15px;
            letter-spacing: 0.5px;
        }

        .amount-value {
            font-size: 48px;
            font-weight: 800;
            color: #fbbf24;
            text-shadow: 0 0 8px rgba(251, 191, 36, 0.3);
        }

        .old-price {
            font-size: 20px;
            color: #8a99cc;
            text-decoration: line-through;
            margin-left: 12px;
            font-weight: 400;
        }

        .discount-badge {
            background: #10b981;
            border-radius: 40px;
            padding: 4px 12px;
            font-size: 12px;
            font-weight: 600;
            margin-left: 12px;
            display: inline-block;
        }

        .card-details, .promo-block, .instruction {
            background: rgba(15, 22, 40, 0.6);
            backdrop-filter: blur(12px);
            border-radius: 32px;
            padding: 22px;
            margin-bottom: 20px;
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .card-number {
            background: #0b1120;
            padding: 18px;
            border-radius: 24px;
            text-align: center;
            font-size: 22px;
            font-weight: 600;
            letter-spacing: 3px;
            margin: 16px 0;
            font-family: monospace;
            border: 1px solid #2a385c;
            color: #facc15;
            user-select: text;
            cursor: text;
        }

        .copy-btn {
            background: #3b82f6;
            border: none;
            padding: 12px;
            border-radius: 44px;
            color: white;
            width: 100%;
            font-size: 15px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.2s;
            box-shadow: 0 2px 8px rgba(59, 130, 246, 0.3);
        }

        .copy-btn:active {
            transform: scale(0.97);
        }

        .promo-input {
            width: 100%;
            background: #0b1120;
            border: 1px solid #293558;
            padding: 14px 18px;
            border-radius: 28px;
            color: white;
            font-size: 15px;
            margin-top: 12px;
            transition: 0.2s;
            user-select: text;
        }

        .promo-input:focus {
            outline: none;
            border-color: #fbbf24;
            box-shadow: 0 0 0 2px rgba(251, 191, 36, 0.2);
        }

        .promo-status {
            font-size: 12px;
            margin-top: 8px;
            transition: 0.2s;
        }

        .promo-status.success {
            color: #10b981;
        }

        .promo-status.error {
            color: #ef4444;
        }

        .instruction ol {
            margin-left: 20px;
            margin-top: 12px;
            color: #cbd5f0;
            line-height: 1.5;
        }

        .pay-btn {
            background: linear-gradient(105deg, #fbbf24, #f59e0b);
            border: none;
            width: 100%;
            padding: 18px;
            border-radius: 60px;
            font-weight: 800;
            font-size: 18px;
            color: #0c0f17;
            cursor: pointer;
            margin-bottom: 16px;
            transition: 0.2s;
            box-shadow: 0 8px 20px rgba(245, 158, 11, 0.3);
        }

        .pay-btn:active {
            transform: scale(0.97);
        }

        .security-note {
            text-align: center;
            font-size: 13px;
            color: #6c7bb0;
            display: flex;
            justify-content: center;
            gap: 16px;
            flex-wrap: wrap;
            margin-top: 16px;
        }

        .file-input-area {
            margin-top: 16px;
        }

        .file-label {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            background: rgba(59, 130, 246, 0.15);
            border: 1px dashed #3b82f6;
            border-radius: 48px;
            padding: 14px 20px;
            cursor: pointer;
            transition: all 0.2s;
            font-size: 14px;
            color: #90a3df;
        }

        .file-label:hover {
            background: rgba(59, 130, 246, 0.25);
            border-color: #60a5fa;
        }

        .file-input {
            display: none;
        }

        .selected-file {
            font-size: 12px;
            color: #7c8ab0;
            text-align: center;
            margin-top: 8px;
            word-break: break-all;
        }

        .toast {
            position: fixed;
            bottom: 30px;
            left: 20px;
            right: 20px;
            background: #1e2a3e;
            border-radius: 60px;
            padding: 14px 22px;
            text-align: center;
            font-size: 14px;
            color: white;
            opacity: 0;
            transition: opacity 0.3s;
            pointer-events: none;
            z-index: 100;
            box-shadow: 0 10px 25px -5px black;
            font-weight: 500;
        }

        .toast.show {
            opacity: 1;
        }
    </style>
</head>
<body>
<div class="container">
    <!-- Экран выбора тарифа -->
    <div id="planScreen" class="plan-screen">
        <div class="header">
            <div class="badge">⚡ Официальная подписка</div>
            <h1>PULSE MOD</h1>
            <p>Выберите доступ -- навсегда или на срок</p>
        </div>

        <div class="pricing-card card-week" data-plan="week" data-price="199">
            <div class="card-header">
                <span class="plan-name">🔹 Неделя</span>
                <span class="plan-price">199 ₽</span>
            </div>
            <div class="plan-desc">Пробный период • Все функции мода</div>
            <button class="buy-btn">Купить за 199 ₽</button>
        </div>

        <div class="pricing-card card-month" data-plan="month" data-price="499">
            <div class="popular-badge">🔥 Популярно</div>
            <div class="card-header">
                <span class="plan-name">🔸 Месяц</span>
                <span class="plan-price">499 ₽</span>
            </div>
            <div class="plan-desc">Экономия 15% • Обновления</div>
            <button class="buy-btn">Купить за 499 ₽</button>
        </div>

        <div class="pricing-card card-forever" data-plan="forever" data-price="999">
            <div class="popular-badge">⭐ Выгодно</div>
            <div class="card-header">
                <span class="plan-name">💎 Навсегда</span>
                <span class="plan-price">999 ₽</span>
            </div>
            <div class="plan-desc">Пожизненный доступ + все апдейты</div>
            <button class="buy-btn">Купить за 999 ₽</button>
        </div>

        <div class="trust-row">
            <div class="trust-item">🔒 Безопасная оплата</div>
            <div class="trust-item">⚡ Мгновенная активация</div>
            <div class="trust-item">💬 Поддержка 24/7</div>
        </div>
    </div>

    <!-- Экран оплаты -->
    <div id="paymentScreen" class="payment-screen">
        <button class="back-btn" id="backBtn">← Назад к выбору тарифа</button>

        <div class="amount-box">
            <div class="amount-label">💰 Сумма к оплате</div>
            <div>
                <span class="amount-value" id="amountValue">0 ₽</span>
                <span class="old-price" id="oldPriceSpan" style="display: none;"></span>
                <span class="discount-badge" id="discountBadge" style="display: none;">-10%</span>
            </div>
            <div style="font-size: 13px; margin-top: 8px; color: #b9c4f0;">после оплаты доступ откроется сразу</div>
        </div>

        <div class="card-details">
            <div style="font-weight: 600; margin-bottom: 4px; display: flex; gap: 8px;">💳 <span>Тинькофф / СБП</span></div>
            <div class="card-number" id="cardNumber">2200 7019 7610 2084</div>
            <button class="copy-btn" id="copyCardBtn">📋 Копировать номер карты</button>
            <div style="font-size: 12px; color: #7a89c2; text-align: center; margin-top: 12px;">Нажмите, чтобы скопировать</div>
        </div>

        <div class="promo-block">
            <div style="font-weight: 500;">🎟 Промокод</div>
            <input type="text" class="promo-input" id="promoInput" placeholder="Введите промокод">
            <div id="promoStatus" class="promo-status"></div>
        </div>

        <div class="instruction">
            <div style="font-weight: 600; margin-bottom: 6px;">📌 Что делать?</div>
            <ol>
                <li>Скопируйте карту выше</li>
                <li>Переведите <strong id="instructionAmount">199</strong> ₽ в Тинькофф / любом банке</li>
                <li>Нажмите «Выбрать чек» и приложите скрин оплаты</li>
                <li>Нажмите «Отправить чек» -- мы проверим и активируем доступ</li>
            </ol>
        </div>

        <div class="file-input-area">
            <label class="file-label" id="fileLabel">
                📎 Выбрать чек (скриншот)
                <input type="file" id="receiptFile" class="file-input" accept="image/*,.pdf">
            </label>
            <div id="fileNameDisplay" class="selected-file"></div>
        </div>

        <button class="pay-btn" id="payBtn">📨 Отправить чек и подтвердить оплату</button>
        <div class="security-note">
            <span>🛡️ Данные защищены</span>
            <span>📄 Чек обязателен для активации</span>
        </div>
    </div>
</div>

<div id="toast" class="toast"></div>

<script>
    // Запрет на копирование всего содержимого (кроме поля ввода промокода и блока с номером карты)
    document.addEventListener('copy', function(e) {
        const target = e.target;
        const isPromoInput = target.id === 'promoInput';
        const isCardNumber = target.id === 'cardNumber' || target.parentElement?.id === 'cardNumber';
        
        if (!isPromoInput && !isCardNumber && target.tagName !== 'INPUT' && target.tagName !== 'TEXTAREA') {
            e.preventDefault();
            return false;
        }
    });
    
    // Запрет контекстного меню (правой кнопки мыши)
    document.addEventListener('contextmenu', function(e) {
        e.preventDefault();
        return false;
    });

    let currentPlan = '';
    let currentPrice = 0;
    let currentDiscount = 0;
    let finalPrice = 0;
    let selectedFile = null;

    const PROMO_CODE = "PULSAR20";
    const DISCOUNT = 0.10;

    function showMessage(text, isError = false) {
        const toast = document.getElementById('toast');
        toast.textContent = text;
        toast.style.background = isError ? '#b91c1c' : '#1a2c3e';
        toast.classList.add('show');
        setTimeout(() => {
            toast.classList.remove('show');
        }, 2800);
    }

    let tg = null;
    if (window.Telegram && window.Telegram.WebApp) {
        tg = window.Telegram.WebApp;
        tg.expand();
        tg.MainButton.hide();
        tg.BackButton.hide();
    }

    function updatePriceWithPromo() {
        const promoInput = document.getElementById('promoInput').value.trim().toUpperCase();
        const isValid = (promoInput === PROMO_CODE);
        const promoStatusDiv = document.getElementById('promoStatus');
        
        if (isValid) {
            currentDiscount = DISCOUNT;
            finalPrice = Math.floor(currentPrice * (1 - currentDiscount));
            promoStatusDiv.innerHTML = '✅ Скидка 10% активирована!';
            promoStatusDiv.className = 'promo-status success';
        } else if (promoInput === '') {
            currentDiscount = 0;
            finalPrice = currentPrice;
            promoStatusDiv.innerHTML = '';
            promoStatusDiv.className = 'promo-status';
        } else {
            currentDiscount = 0;
            finalPrice = currentPrice;
            promoStatusDiv.innerHTML = '❌ Неверный промокод';
            promoStatusDiv.className = 'promo-status error';
        }
        
        const amountSpan = document.getElementById('amountValue');
        const oldPriceSpan = document.getElementById('oldPriceSpan');
        const discountBadge = document.getElementById('discountBadge');
        const instructionAmount = document.getElementById('instructionAmount');
        
        if (currentDiscount > 0) {
            amountSpan.innerHTML = finalPrice + ' ₽';
            oldPriceSpan.innerHTML = currentPrice + ' ₽';
            oldPriceSpan.style.display = 'inline';
            discountBadge.style.display = 'inline';
            instructionAmount.innerText = finalPrice;
        } else {
            amountSpan.innerHTML = currentPrice + ' ₽';
            oldPriceSpan.style.display = 'none';
            discountBadge.style.display = 'none';
            instructionAmount.innerText = currentPrice;
        }
    }

    function showPaymentScreen(plan, price) {
        currentPlan = plan;
        currentPrice = price;
        currentDiscount = 0;
        finalPrice = price;
        selectedFile = null;
        
        document.getElementById('fileNameDisplay').innerHTML = '';
        document.getElementById('receiptFile').value = '';
        document.getElementById('promoInput').value = '';
        document.getElementById('promoStatus').innerHTML = '';
        document.getElementById('promoStatus').className = 'promo-status';
        
        document.getElementById('planScreen').classList.add('hide');
        document.getElementById('paymentScreen').classList.add('active');
        
        document.getElementById('amountValue').innerHTML = price + ' ₽';
        document.getElementById('oldPriceSpan').style
        document.getElementById('discountBadge').style.display = 'none';
        document.getElementById('instructionAmount').innerText = price;
    }

    document.querySelectorAll('.buy-btn').forEach(btn => {
        btn.addEventListener('click', (e) => {
            e.stopPropagation();
            const card = btn.closest('.pricing-card');
            const plan = card.getAttribute('data-plan');
            const price = parseInt(card.getAttribute('data-price'));
            showPaymentScreen(plan, price);
        });
    });

    document.querySelectorAll('.pricing-card').forEach(card => {
        card.addEventListener('click', (e) => {
            if (e.target.classList.contains('buy-btn')) return;
            const btn = card.querySelector('.buy-btn');
            if (btn) btn.click();
        });
    });

    document.getElementById('backBtn').addEventListener('click', () => {
        document.getElementById('planScreen').classList.remove('hide');
        document.getElementById('paymentScreen').classList.remove('active');
    });

    const promoInput = document.getElementById('promoInput');
    promoInput.addEventListener('input', updatePriceWithPromo);
    promoInput.addEventListener('blur', updatePriceWithPromo);

    // Копирование номера карты (работает всегда)
    document.getElementById('copyCardBtn').addEventListener('click', async () => {
        const cardNumberElement = document.getElementById('cardNumber');
        let cardNumber = cardNumberElement.innerText.replace(/\s/g, '');
        
        // Пробуем современный метод
        if (navigator.clipboard && navigator.clipboard.writeText) {
            try {
                await navigator.clipboard.writeText(cardNumber);
                showMessage('✅ Номер карты скопирован!');
                return;
            } catch (err) {
                // fallback
            }
        }
        
        // Резервный метод для старых браузеров
        const textarea = document.createElement('textarea');
        textarea.value = cardNumber;
        textarea.style.position = 'fixed';
        textarea.style.opacity = '0';
        document.body.appendChild(textarea);
        textarea.select();
        try {
            document.execCommand('copy');
            showMessage('✅ Номер карты скопирован!');
        } catch (err) {
            showMessage('❌ Не удалось скопировать, скопируйте вручную', true);
        }
        document.body.removeChild(textarea);
    });

    const fileInput = document.getElementById('receiptFile');
    const fileNameDisplay = document.getElementById('fileNameDisplay');

    fileInput.addEventListener('change', (e) => {
        if (e.target.files && e.target.files[0]) {
            selectedFile = e.target.files[0];
            fileNameDisplay.innerHTML = `✅ Выбран чек: ${selectedFile.name}`;
            fileNameDisplay.style.color = '#86efac';
        } else {
            selectedFile = null;
            fileNameDisplay.innerHTML = '';
        }
    });

    async function sendReceiptToBot(file, planText, originalPrice, finalPriceValue, promo) {
        return new Promise((resolve, reject) => {
            if (!tg) {
                resolve(false);
                return;
            }

            const reader = new FileReader();
            reader.onload = function(evt) {
                const base64 = evt.target.result.split(',')[1];
                
                tg.sendData(JSON.stringify({
                    action: 'paid_with_receipt',
                    plan: currentPlan,
                    planText: planText,
                    originalPrice: originalPrice,
                    finalPrice: finalPriceValue,
                    discountApplied: currentDiscount > 0,
                    promoCode: promo || null,
                    fileName: file.name,
                    fileType: file.type,
                    fileBase64: base64,
                    timestamp: Date.now()
                }));
                resolve(true);
            };
            reader.onerror = () => reject(false);
            reader.readAsDataURL(file);
        });
    }

    document.getElementById('payBtn').addEventListener('click', async () => {
        const promo = document.getElementById('promoInput').value.trim().toUpperCase();
        const isPromoValid = (promo === PROMO_CODE);
        const appliedPromo = isPromoValid ? promo : null;
        const priceToPay = isPromoValid ? finalPrice : currentPrice;
        
        let planText = '';
        if (currentPlan === 'week') planText = 'Неделя (199₽)';
        else if (currentPlan === 'month') planText = 'Месяц (499₽)';
        else if (currentPlan === 'forever') planText = 'Навсегда (999₽)';
        
        if (isPromoValid) {
            planText += ` (скидка 10% → ${priceToPay}₽)`;
        }

        if (!selectedFile) {
            showMessage('❌ Пожалуйста, выберите чек (скриншот оплаты)', true);
            return;
        }

        if (selectedFile.size > 10 * 1024 * 1024) {
            showMessage('❌ Файл слишком большой (максимум 10 МБ)', true);
            return;
        }

        showMessage('📤 Отправка чека...');

        try {
            if (tg) {
                await sendReceiptToBot(selectedFile, planText, currentPrice, priceToPay, appliedPromo);
                showMessage(`✅ Чек отправлен! Мы проверим оплату и активируем доступ в течение 5 минут.`);
                tg.close();
            } else {
                showMessage(`✅ Демо-режим: чек "${selectedFile.name}" отправлен. Промокод: ${appliedPromo || 'не использован'}`, false);
            }
        } catch (err) {
            showMessage('❌ Ошибка отправки чека, попробуйте ещё раз', true);
        }
    });
</script>
</body>
</html>
