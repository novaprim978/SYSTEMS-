<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>سيستم كاشير ومخزن المحل المتكامل - نسخة الحقوق</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f4f6f9;
            margin: 0;
            padding: 20px;
        }
        h1, h2, h3 {
            color: #333;
            text-align: center;
        }
        
        /* شاشة تسجيل الدخول */
        #loginScreen {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background-color: #343a40;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
        }
        .login-box {
            background: white;
            padding: 40px;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            text-align: center;
            width: 350px;
        }

        /* السيستم الأساسي */
        #mainSystem {
            display: none;
        }

        .container {
            display: flex;
            gap: 20px;
            max-width: 1400px;
            margin: 0 auto;
        }
        .panel {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            flex: 1;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        input, button, select {
            width: 100%;
            padding: 10px;
            box-sizing: border-box;
            border: 1px solid #ccc;
            border-radius: 4px;
            font-size: 16px;
        }
        
        /* الأزرار والألوان */
        button.buy-btn {
            background-color: #ffc107;
            color: #000;
            border: none;
            cursor: pointer;
            font-weight: bold;
            margin-top: 10px;
            border-radius: 4px;
        }
        button.buy-btn:hover { background-color: #e0a800; }

        /* أزرار الفاتورة السفلية */
        .invoice-buttons-container {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        button.invoice-big-yellow-btn {
            background-color: #ffc107;
            color: #000;
            border: none;
            cursor: pointer;
            font-weight: bold;
            font-size: 20px;
            padding: 15px;
            flex: 2;
            border-radius: 6px;
        }
        button.invoice-big-yellow-btn:hover { background-color: #e0a800; }

        button.invoice-big-blue-btn {
            background-color: #007bff;
            color: white;
            border: none;
            cursor: pointer;
            font-weight: bold;
            font-size: 20px;
            padding: 15px;
            flex: 1;
            border-radius: 6px;
        }
        button.invoice-big-blue-btn:hover { background-color: #0069d9; }

        button.edit-btn {
            background-color: #007bff;
            color: white;
            border: none;
            cursor: pointer;
            font-weight: bold;
            margin-top: 5px;
        }
        button.edit-btn:hover { background-color: #0069d9; }

        /* زر حذف صنف من الفاتورة */
        button.delete-item-btn {
            background-color: #dc3545;
            color: white;
            border: none;
            cursor: pointer;
            padding: 5px 10px;
            font-size: 14px;
            border-radius: 4px;
            width: auto;
            display: inline-block;
        }
        button.delete-item-btn:hover { background-color: #bd2130; }

        /* زر تصفير اليومية */
        button.reset-day-btn {
            background-color: #dc3545;
            color: white;
            border: none;
            cursor: pointer;
            font-weight: bold;
            margin-top: 15px;
            padding: 12px;
            border-radius: 4px;
            font-size: 16px;
        }
        button.reset-day-btn:hover { background-color: #bd2130; }

        .report-btn { background-color: #17a2b8; color: white; }
        .report-btn:hover { background-color: #138496; }
        
        .quick-buttons {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
            margin-bottom: 15px;
        }
        .quick-btn {
            background-color: #6f42c1;
            color: white;
            font-size: 14px;
            padding: 12px;
            cursor: pointer;
            border: none;
        }
        .quick-btn:hover { background-color: #59359a; }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 15px;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 10px;
            text-align: center;
        }
        th { background-color: #f8f9fa; }
        
        .total-box {
            background: #e9ecef;
            padding: 15px;
            font-size: 18px;
            font-weight: bold;
            text-align: center;
            margin-top: 15px;
            border-radius: 4px;
        }
        .profit-box {
            background: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }
        .low-stock { color: red; font-weight: bold; }
        .hide-toggle {
            background-color: #6c757d;
            color: white;
            font-size: 12px;
            padding: 5px;
            width: auto;
            margin: 5px auto;
            display: block;
        }

        /* الفاتورة تملأ الشاشة بالكامل */
        .modal {
            display: none;
            position: fixed;
            z-index: 10000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: #ffffff;
            box-sizing: border-box;
            overflow-y: auto;
        }
        .modal-content {
            max-width: 1000px;
            margin: 30px auto;
            padding: 40px;
            border: 2px solid #333;
            border-radius: 8px;
            background: #fff;
        }
        .invoice-header {
            text-align: center;
            border-bottom: 3px dashed #333;
            padding-bottom: 20px;
            margin-bottom: 20px;
        }
        .invoice-details {
            margin-bottom: 25px;
            font-size: 16px;
            line-height: 1.8;
        }
        .invoice-table {
            width: 100%;
            margin-bottom: 25px;
            font-size: 16px;
        }
        .invoice-footer {
            text-align: center;
            border-top: 3px dashed #333;
            padding-top: 20px;
            margin-top: 30px;
            font-weight: bold;
        }
        .dev-rights {
            margin-top: 15px;
            font-size: 13px;
            color: #777;
            font-style: italic;
            text-align: center;
        }
    </style>
</head>
<body>

    <!-- شاشة تسجيل الدخول الرئيسي للسيستم -->
    <div id="loginScreen">
        <div class="login-box">
            <h2>🔐 تسجيل الدخول للسيستم</h2>
            <p>محل مكياج وطرح المحروسة</p>
            <div class="form-group" style="margin-top: 20px;">
                <label>ادخل كود السر الخاص بك:</label>
                <input type="password" id="loginPassword" placeholder="••••">
            </div>
            <button class="edit-btn" onclick="checkLogin()">دخول 🔓</button>
        </div>
    </div>

    <!-- السيستم الأساسي المحمي -->
    <div id="mainSystem">
        <h1>سيستم مبيعات وفواتير المحل المتطور 💄🧣</h1>

        <div class="container">
            
            <!-- شاشة الكاشير والبيع -->
            <div class="panel">
                <h2>🛒 شاشة البيع (الكاشير)</h2>
                
                <div class="form-group" style="background: #fff3cd; padding: 10px; border-radius: 5px; border: 1px solid #ffeeba;">
                    <label for="customerName" style="color: #856404;">👤 اسم الزبونة (اختياري لجعل الفاتورة باسمها):</label>
                    <input type="text" id="customerName" placeholder="اكتب اسم الزبونة هنا... (مثال: سارة محمد)">
                </div>

                <div class="form-group">
                    <label for="scanInput">امسح باركود المنتج هنا بالمسدس:</label>
                    <input type="text" id="scanInput" placeholder="أعمل سكان هنا...">
                </div>

                <label>أزرار مبيعات سريعة (تتحدث تلقائياً مع المخزن):</label>
                <div class="quick-buttons" id="quickButtonsContainer"></div>

                <h3>الفاتورة الحالية:</h3>
                <table>
                    <thead>
                        <tr>
                            <th>المنتج</th>
                            <th>السعر</th>
                            <th>العدد</th>
                            <th>تحكم</th>
                        </tr>
                    </thead>
                    <tbody id="cartTable"></tbody>
                </table>
                
                <div class="total-box">
                    إجمالي حساب الزبون: <span id="cartTotal">0</span> جنيه
                </div>
                <button class="buy-btn" onclick="openInvoiceModal()">🛒 مراجعة وإصدار الفاتورة</button>
                
                <hr style="margin-top: 30px;">
                
                <h3>📊 أرباح ومبيعات اليوم (محمية)</h3>
                <button class="hide-toggle" onclick="toggleProfit()">إخفاء / إظهار الأرباح</button>
                <div id="profitSection" style="display:none;">
                    <div class="total-box">إجمالي مبيعات اليوم: <span id="daySales">0</span> جنيه</div>
                    <div class="total-box profit-box">صافي الأرباح اليومية: <span id="dayProfit">0</span> جنيه</div>
                    <!-- زر بدء يوم جديد محمي بباسوردات المستخدمين -->
                    <button class="reset-day-btn" onclick="resetDayStats()">♻️ بدء يوم جديد (تصفير اليومية)</button>
                </div>
            </div>

            <!-- لوحة التحكم وإدخال البضاعة -->
            <div class="panel">
                <h2>📦 إدارة المخزن وإضافة بضاعة (محمية 🔐)</h2>
                <form id="productForm">
                    <div class="form-group">
                        <label id="formActionTitle">إضافة منتج جديد:</label>
                    </div>
                    <div class="form-group">
                        <label>باركود المنتج (أو كود سريع مثل TR-01):</label>
                        <input type="text" id="prodBarcode" required>
                    </div>
                    <div class="form-group">
                        <label>اسم المنتج:</label>
                        <input type="text" id="prodName" required>
                    </div>
                    <div class="form-group">
                        <label>سعر الجملة (واقف عليك بكام):</label>
                        <input type="number" id="prodCost" required>
                    </div>
                    <div class="form-group">
                        <label>سعر البيع (للزبون):</label>
                        <input type="number" id="prodPrice" required>
                    </div>
                    <div class="form-group">
                        <label>الكمية المتاحة (العدد):</label>
                        <input type="number" id="prodQty" required>
                    </div>
                    <button type="submit" id="submitFormBtn">حفظ المنتج في المخزن</button>
                    <button type="button" id="cancelEditBtn" style="display:none; background-color:#dc3545;" onclick="resetProductForm()">إلغاء التعديل</button>
                </form>

                <button class="report-btn" onclick="showLowStockReport()" style="margin-top:15px;">⚠️ عرض تقرير النواقص</button>

                <h3>المخزن الحالي:</h3>
                <div style="overflow-x:auto;">
                    <table>
                        <thead>
                            <tr>
                                <th>الباركود</th>
                                <th>الاسم</th>
                                <th>المكسب المتوقع</th>
                                <th>البيع</th>
                                <th>العدد</th>
                                <th>التحكم</th>
                            </tr>
                        </thead>
                        <tbody id="inventoryTable"></tbody>
                    </table>
                </div>
            </div>

        </div>
    </div>

    <!-- نافذة الفاتورة الكاملة التي تملأ الشاشة بالكامل -->
    <div id="invoiceModal" class="modal">
        <div class="modal-content">
            <div class="invoice-header">
                <h1 style="font-size: 36px; margin: 0;">✨ محل مكياج وطرح المحروسة ✨</h1>
                <p style="font-size: 18px; color: #555;">مبارك عليكم المشتريات يا فندم تنورينا دايماً</p>
            </div>
            <div class="invoice-details">
                <table style="width: 100%; border: none; margin: 0;">
                    <tr style="background: none;">
                        <td style="text-align: right; border: none; padding: 5px;"><strong>رقم الفاتورة:</strong> <span id="invId"></span></td>
                        <td style="text-align: left; border: none; padding: 5px;"><strong>التاريخ والوقت:</strong> <span id="invDate"></span></td>
                    </tr>
                    <tr style="background: none;">
                        <td style="text-align: right; border: none; padding: 5px;"><strong>اسم الزبونة:</strong> <span id="invCustomer" style="color: #007bff; font-weight: bold; font-size: 18px;"></span></td>
                        <td style="text-align: left; border: none; padding: 5px;"><strong>الكاشير المسؤول:</strong> <span id="invCashier">ساهر</span></td>
                    </tr>
                </table>
            </div>
            
            <table class="invoice-table">
                <thead>
                    <tr style="background-color: #343a40; color: white;">
                        <th>اسم الحاجة</th>
                        <th>السعر الفردي</th>
                        <th>العدد والمشتروات</th>
                        <th>الإجمالي الكلي</th>
                    </tr>
                </thead>
                <tbody id="invoiceItemsBody"></tbody>
            </table>

            <div class="total-box" style="font-size: 28px; background: #fff3cd; border: 2px solid #ffc107; padding: 20px;">
                إجمالي الحساب النهائي: <span id="invTotal">0</span> جنيه مصري
            </div>

            <div class="invoice-footer">
                <p style="font-size: 16px;">شكراً لزيارتكم! البضاعة المباعة تستبدل خلال 14 يوم بشرط عدم الاستخدام.</p>
                
                <div class="invoice-buttons-container">
                    <button class="invoice-big-blue-btn" onclick="backToEditInvoice()">✏️ تعديل الفاتورة</button>
                    <button class="invoice-big-yellow-btn" onclick="confirmAndCloseInvoice()">🛒 إنهاء وطباعة - شراء</button>
                </div>
                
                <!-- سطر الحقوق الخاص بك -->
                <div class="dev-rights">⚙️ حقوق الطبع محفوظة لدى المبرمج ساهر © 2026</div>
            </div>
        </div>
    </div>

    <script>
        // تحديث الباسوردات حسب طلبك: ساهر 2323 واللي بعده 2424 وهكذا بالتسلسل
        const users = {
            "2323": "ساهر",
            "2424": "1",
            "2525": "2",
            "2626": "3"
        };

        let currentCashierName = "ساهر";

        // الحفاظ على المخزن نضيف تماماً من أي داتا تجريبية قديمة
        localStorage.removeItem('shopInventory');
        
        let inventory = {};
        let salesStats = JSON.parse(localStorage.getItem('shopSales')) || { totalSales: 0, totalProfit: 0 };
        let currentCart = [];

        updateInventoryTable();
        updateQuickButtonsMenu(); 
        updateSalesStats();

        function checkLogin() {
            const pass = document.getElementById('loginPassword').value;
            if (users[pass]) {
                currentCashierName = users[pass]; 
                document.getElementById('invCashier').innerText = currentCashierName;
                document.getElementById('loginScreen').style.display = 'none';
                document.getElementById('mainSystem').style.display = 'block';
                document.getElementById('scanInput').focus();
                alert(`أهلاً بك يا ${currentCashierName} 👋 تم تسجيل الدخول بنجاح.`);
            } else {
                alert('❌ الباسورد غلط! غير مسجل بقائمة المستخدمين.');
            }
        }

        function updateQuickButtonsMenu() {
            const container = document.getElementById('quickButtonsContainer');
            container.innerHTML = ''; 
            const keys = Object.keys(inventory).slice(0, 4);
            keys.forEach(barcode => {
                const btn = document.createElement('button');
                btn.className = 'quick-btn';
                btn.innerText = `🛍️ ${inventory[barcode].name}`;
                btn.onclick = function() { quickSale(barcode); };
                container.appendChild(btn);
            });
        }

        document.getElementById('productForm').addEventListener('submit', function(e) {
            e.preventDefault();

            const checkPass = prompt('🔐 العملية محمية! اكتب الباسورد الخاص بك لحفظ البيانات في المخزن:');
            if (!users[checkPass]) {
                alert('❌ الباسورد غلط أو غير مصرح لك! تم إلغاء العملية.');
                return;
            }

            const barcode = document.getElementById('prodBarcode').value.trim();
            const name = document.getElementById('prodName').value.trim();
            const cost = parseFloat(document.getElementById('prodCost').value);
            const price = parseFloat(document.getElementById('prodPrice').value);
            const qty = parseInt(document.getElementById('prodQty').value);

            inventory[barcode] = { name, cost, price, qty };
            localStorage.setItem('shopInventory', JSON.stringify(inventory));
            
            alert(`✅ تم الحفظ بنجاح بواسطة الكاشير: ${users[checkPass]}`);
            resetProductForm();
            updateInventoryTable();
            updateQuickButtonsMenu(); 
        });

        function startEditProduct(barcode) {
            const checkPass = prompt('🔐 تعديل البضاعة محمي! اكتب الباسورد أولاً للدخول لوضع التعديل:');
            if (!users[checkPass]) {
                alert('❌ الباسورد غلط! غير مسموح بالتعديل.');
                return;
            }

            const item = inventory[barcode];
            document.getElementById('prodBarcode').value = barcode;
            document.getElementById('prodBarcode').disabled = true; 
            document.getElementById('prodName').value = item.name;
            document.getElementById('prodCost').value = item.cost;
            document.getElementById('prodPrice').value = item.price;
            document.getElementById('prodQty').value = item.qty;
            
            document.getElementById('formActionTitle').innerText = "📝 تعديل بيانات المنتج الحالي:";
            document.getElementById('submitFormBtn').innerText = "تأكيد التعديل وحفظ البيانات";
            document.getElementById('submitFormBtn').className = "edit-btn"; 
            document.getElementById('cancelEditBtn').style.display = "block";
            
            document.getElementById('productForm').scrollIntoView({ behavior: 'smooth' });
        }

        function resetProductForm() {
            document.getElementById('productForm').reset();
            document.getElementById('prodBarcode').disabled = false;
            document.getElementById('formActionTitle').innerText = "إضافة منتج جديد:";
            document.getElementById('submitFormBtn').innerText = "حفظ المنتج في المخزن";
            document.getElementById('submitFormBtn').className = ""; 
            document.getElementById('cancelEditBtn').style.display = "none";
            document.getElementById('scanInput').focus();
        }

        document.getElementById('scanInput').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                const barcode = this.value.trim();
                this.value = '';
                processSale(barcode);
            }
        });

        function quickSale(barcode) {
            processSale(barcode);
        }

        function processSale(barcode) {
            if (inventory[barcode]) {
                if (inventory[barcode].qty > 0) {
                    inventory[barcode].qty -= 1;
                    localStorage.setItem('shopInventory', JSON.stringify(inventory));
                    updateInventoryTable();
                    addToCart(barcode);
                } else {
                    alert(`عفواً! صنف (${inventory[barcode].name}) خلص من المخزن.`);
                }
            } else {
                alert('الباركود ده مش متسجل في المخزن! يرجى إدخاله أولاً.');
            }
        }

        function addToCart(barcode) {
            const item = inventory[barcode];
            const cartItem = currentCart.find(i => i.barcode === barcode);
            if (cartItem) {
                cartItem.qty += 1;
            } else {
                currentCart.push({
                    barcode: barcode,
                    name: item.name,
                    price: item.price,
                    cost: item.cost,
                    qty: 1
                });
            }
            updateCartTable();
        }

        function removeOneFromCart(barcode) {
            const cartItemIndex = currentCart.findIndex(i => i.barcode === barcode);
            if (cartItemIndex > -1) {
                if (inventory[barcode]) {
                    inventory[barcode].qty += 1;
                    localStorage.setItem('shopInventory', JSON.stringify(inventory));
                    updateInventoryTable();
                }
                currentCart[cartItemIndex].qty -= 1;
                if (currentCart[cartItemIndex].qty === 0) {
                    currentCart.splice(cartItemIndex, 1);
                }
                updateCartTable();
            }
        }

        function updateInventoryTable() {
            const tbody = document.getElementById('inventoryTable');
            tbody.innerHTML = '';
            for (let barcode in inventory) {
                const item = inventory[barcode];
                const row = document.createElement('tr');
                const qtyClass = item.qty <= 2 ? 'low-stock' : '';
                const estimatedProfit = item.price - item.cost;
                row.innerHTML = `
                    <td><code>${barcode}</code></td>
                    <td>${item.name}</td>
                    <td style="color:green; font-weight:bold;">${estimatedProfit} ج</td>
                    <td>${item.price} ج</td>
                    <td class="${qtyClass}">${item.qty}</td>
                    <td>
                        <button class="edit-btn" style="padding: 5px 10px; font-size:13px; margin:0;" onclick="startEditProduct('${barcode}')">تعديل 📝</button>
                    </td>
                `;
                tbody.appendChild(row);
            }
        }

        function updateCartTable() {
            const tbody = document.getElementById('cartTable');
            tbody.innerHTML = '';
            let total = 0;
            currentCart.forEach(item => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${item.name}</td>
                    <td>${item.price} ج</td>
                    <td>${item.qty}</td>
                    <td>
                        <button class="delete-item-btn" onclick="removeOneFromCart('${item.barcode}')">إزالة ❌</button>
                    </td>
                `;
                tbody.appendChild(row);
                total += (item.price * item.qty);
            });
            document.getElementById('cartTotal').innerText = total;
        }

        function openInvoiceModal() {
            if(currentCart.length === 0) {
                alert('الفاتورة فاضية! أعمل سكان للبضاعة الأول.');
                return;
            }
            
            let billTotal = 0;
            let invoiceItemsHtml = '';

            currentCart.forEach(item => {
                let itemTotal = item.price * item.qty;
                billTotal += itemTotal;
                
                invoiceItemsHtml += `
                    <tr>
                        <td style="font-weight:bold;">${item.name}</td>
                        <td>${item.price} جنيه</td>
                        <td>${item.qty} قطع</td>
                        <td style="font-weight:bold;">${itemTotal} جنيه</td>
                    </tr>
                `;
            });

            let cName = document.getElementById('customerName').value.trim() || "زبونة كريمـة";
            document.getElementById('invCustomer').innerText = cName;
            document.getElementById('invId').innerText = 'INV-' + Math.floor(10000 + Math.random() * 90000);
            document.getElementById('invDate').innerText = new Date().toLocaleString('ar-EG');
            document.getElementById('invoiceItemsBody').innerHTML = invoiceItemsHtml;
            document.getElementById('invTotal').innerText = billTotal;
            document.getElementById('invCashier').innerText = currentCashierName;

            document.getElementById('invoiceModal').style.display = 'block';
        }

        function backToEditInvoice() {
            document.getElementById('invoiceModal').style.display = 'none';
            document.getElementById('scanInput').focus();
        }

        function confirmAndCloseInvoice() {
            let billTotal = 0;
            let billProfit = 0;

            currentCart.forEach(item => {
                billTotal += (item.price * item.qty);
                billProfit += ((item.price - item.cost) * item.qty);
            });

            salesStats.totalSales += billTotal;
            salesStats.totalProfit += billProfit;
            localStorage.setItem('shopSales', JSON.stringify(salesStats));
            updateSalesStats();

            document.getElementById('invoiceModal').style.display = 'none';
            document.getElementById('customerName').value = '';
            currentCart = [];
            updateCartTable();
            document.getElementById('scanInput').focus();
            alert(`💸 تم تسجيل عملية الشراء وإضافتها للأرباح بواسطة الكاشير: ${currentCashierName}`);
        }

        function updateSalesStats() {
            document.getElementById('daySales').innerText = salesStats.totalSales;
            document.getElementById('dayProfit').innerText = salesStats.totalProfit;
        }

        function toggleProfit() {
            const sec = document.getElementById('profitSection');
            if (sec.style.display === 'none') {
                const checkPass = prompt('🔐 لرؤية صافي أرباح المحل اليومية، ادخل كود الكاشير السرّي:');
                if (users[checkPass]) {
                    sec.style.display = 'block';
                    alert(`مرحباً يا ${users[checkPass]}، تم إظهار الأرباح المستترة.`);
                } else {
                    alert('❌ الكود السرّي غلط!');
                }
            } else {
                sec.style.display = 'none';
            }
        }

        function resetDayStats() {
            const checkPass = prompt('⚠️ تحذير: سيتم تصفير جميع الأرباح والمبيعات الحالية للبدء من جديد. ادخل الباسورد الخاص بك كـ كاشير لتأكيد الهوية:');
            
            if (users[checkPass]) {
                let cashierWhoReset = users[checkPass]; 
                
                salesStats.totalSales = 0;
                salesStats.totalProfit = 0;
                localStorage.setItem('shopSales', JSON.stringify(salesStats));
                updateSalesStats();
                
                alert(`♻️ تم تصفير إحصائيات اليومية بنجاح وبدء وردية جديدة!\n👤 المسؤول عن التصفير الحالي: الكاشير (${cashierWhoReset})`);
            } else {
                alert('❌ الباسورد غلط أو غير مسجل! تم إلغاء تصفير اليومية.');
            }
        }

        function showLowStockReport() {
            let report = "📋 أصناف قربت تخلص ومحتاجين نجيب منها:\n\n";
            let found = false;
            for (let barcode in inventory) {
                if (inventory[barcode].qty <= 2) {
                    report += `- ${inventory[barcode].name} (المتبقي: ${inventory[barcode].qty} قطع)\n`;
                    found = true;
                }
            }
            if (!found) report = "🎉 المخزن تمام ومفيش أي نواقص حالياً!";
            alert(report);
        }
    </script>
</body>
</html>
