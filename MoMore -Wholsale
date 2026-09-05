<!DOCTYPE html>
<html lang="km">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MOMORE Wholesale Store</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; }
        body { background-color: #f4f6f9; padding: 12px; color: #333; padding-bottom: 120px; }
        
        .banner { background: linear-gradient(135deg, #1b5e20, #43a047); color: white; padding: 18px; border-radius: 16px; text-align: center; margin-bottom: 15px; box-shadow: 0 4px 10px rgba(27, 94, 32, 0.2); }
        .banner h1 { font-size: 22px; font-weight: 800; }
        .banner p { font-size: 13px; opacity: 0.9; margin-top: 4px; }

        .section-title { font-size: 15px; font-weight: bold; margin: 15px 0 10px 4px; color: #444; }

        .product-card { background: white; border-radius: 14px; padding: 12px; margin-bottom: 12px; display: flex; gap: 12px; align-items: center; box-shadow: 0 2px 6px rgba(0,0,0,0.04); }
        .product-img { width: 70px; height: 70px; background: #e8f5e9; border-radius: 10px; display: flex; align-items: center; justify-content: center; font-size: 30px; flex-shrink: 0; }
        .product-info { flex: 1; }
        .product-info h3 { font-size: 15px; color: #222; margin-bottom: 4px; }
        .product-info .price { font-size: 14px; color: #2e7d32; font-weight: bold; }
        .product-info .unit { font-size: 11px; color: #666; }

        .qty-controls { display: flex; align-items: center; background: #e8f5e9; border-radius: 8px; padding: 3px; }
        .btn-qty { width: 28px; height: 28px; background: white; border: none; border-radius: 6px; font-size: 16px; font-weight: bold; color: #2e7d32; cursor: pointer; box-shadow: 0 1px 2px rgba(0,0,0,0.1); }
        .qty-num { width: 28px; text-align: center; font-weight: bold; font-size: 13px; }

        .summary-card { background: white; border-radius: 14px; padding: 14px; margin-top: 15px; box-shadow: 0 2px 6px rgba(0,0,0,0.04); }
        .summary-row { display: flex; justify-content: space-between; font-size: 13px; color: #555; margin-bottom: 8px; }
        .summary-row.discount { color: #d32f2f; font-weight: bold; }
        .summary-row.total { font-size: 16px; font-weight: bold; color: #222; border-top: 1px dashed #eee; padding-top: 8px; margin-bottom: 0; }

        .form-card { background: white; border-radius: 14px; padding: 14px; margin-top: 15px; box-shadow: 0 2px 6px rgba(0,0,0,0.04); }
        .form-group { margin-bottom: 10px; }
        .form-group label { display: block; font-size: 12px; font-weight: bold; color: #555; margin-bottom: 4px; }
        .form-group input, .form-group textarea { width: 100%; padding: 10px; border: 1px solid #ddd; border-radius: 8px; font-size: 13px; outline: none; }

        .footer-bar { position: fixed; bottom: 0; left: 0; right: 0; background: white; padding: 12px 16px; box-shadow: 0 -4px 12px rgba(0,0,0,0.08); display: flex; justify-content: space-between; align-items: center; border-top-left-radius: 16px; border-top-right-radius: 16px; }
        .footer-total { font-size: 18px; color: #2e7d32; font-weight: bold; }
        .btn-submit { background: #2e7d32; color: white; border: none; padding: 12px 22px; border-radius: 10px; font-weight: bold; font-size: 15px; cursor: pointer; }
    </style>
</head>
<body>

    <div class="banner">
        <h1>📦 MOMORE Wholesale</h1>
        <p>ប្រព័ន្ធបញ្ជាទិញបោះដុំដំណាប់ចេក និងចេកបំពងស្រួយ ម៉ូម៉័រ</p>
    </div>

    <div class="section-title">📦 ជ្រើសរើសទំនិញបោះដុំ (គិតជាកេស/ឡូ)</div>

    <!-- ទំនិញទី ១ -->
    <div class="product-card">
        <div class="product-img">🍌</div>
        <div class="product-info">
            <h3>ចែមចេកអាំង (Soft Jam)</h3>
            <div class="price">$30.00 / កេស</div>
            <div class="unit">១ កេស = 10 កញ្ចប់</div>
        </div>
        <div class="qty-controls">
            <button class="btn-qty" onclick="updateQty(0, -1)">-</button>
            <span class="qty-num" id="qty-0">0</span>
            <button class="btn-qty" onclick="updateQty(0, 1)">+</button>
        </div>
    </div>

    <!-- ទំនិញទី ២ -->
    <div class="product-card">
        <div class="product-img">🍌</div>
        <div class="product-info">
            <h3>ចេកបន្ទះស្តើង (Thin Slices)</h3>
            <div class="price">$35.00 / កេស</div>
            <div class="unit">១ កេស = 10 កញ្ចប់</div>
        </div>
        <div class="qty-controls">
            <button class="btn-qty" onclick="updateQty(1, -1)">-</button>
            <span class="qty-num" id="qty-1">0</span>
            <button class="btn-qty" onclick="updateQty(1, 1)">+</button>
        </div>
    </div>

    <!-- បូកសរុបតម្លៃ & ប្រូម៉ូសិន -->
    <div class="summary-card">
        <div class="summary-row">
            <span>តម្លៃសរុបដើម:</span>
            <span id="subtotal">$0.00</span>
        </div>
        <div class="summary-row discount">
            <span>បញ្ចុះតម្លៃបោះដុំ (<span id="discount-percent">0%</span>):</span>
            <span id="discount-amount">-$0.00</span>
        </div>
        <div class="summary-row total">
            <span>ទូទាត់សរុប:</span>
            <span id="grand-total" style="color: #2e7d32;">$0.00</span>
        </div>
    </div>

    <!-- ព័ត៌មានម៉ូយ/ដេប៉ូ -->
    <div class="section-title">🏢 ព័ត៌មានដេប៉ូ / អ្នកទិញដុំ</div>
    <div class="form-card">
        <div class="form-group">
            <label>ឈ្មោះហាង/ដេប៉ូ ឬឈ្មោះអ្នកទិញ:</label>
            <input type="text" id="cust-name" placeholder="ឧ. ដេប៉ូ ស្រីមុំ ផ្សារអូរឫស្សី">
        </div>
        <div class="form-group">
            <label>លេខទូរស័ព្ទ / Phone Number:</label>
            <input type="tel" id="cust-phone" placeholder="ឧ. 012345678">
        </div>
        <div class="form-group">
            <label>ទីតាំង/អាសយដ្ឋានប្រគល់ទំនិញ:</label>
            <textarea id="cust-address" rows="2" placeholder="បញ្ចូលអាសយដ្ឋាន ឬ ជើងសាដឹកជញ្ជូន..."></textarea>
        </div>
    </div>

    <div class="footer-bar">
        <div>
            <div style="font-size: 11px; color: #777;">សរុបចុងក្រោយ</div>
            <div class="footer-total" id="footer-price">$0.00</div>
        </div>
        <button class="btn-submit" onclick="submitWholesaleOrder()">បញ្ជាទិញបោះដុំ</button>
    </div>

    <script>
        const products = [
            { id: 1, name: "ចែមចេកអាំង (Soft Jam)", price: 30.00, qty: 0 },
            { id: 2, name: "ចេកបន្ទះស្តើង (Thin Slices)", price: 35.00, qty: 0 }
        ];

        function updateQty(index, change) {
            if (products[index].qty + change >= 0) {
                products[index].qty += change;
                document.getElementById(`qty-${index}`).innerText = products[index].qty;
                calculateAll();
            }
        }

        function calculateAll() {
            let subtotal = 0;
            let totalBoxes = 0;

            products.forEach(p => { 
                subtotal += p.price * p.qty; 
                totalBoxes += p.qty;
            });

            // លក្ខខណ្ឌបញ្ចុះតម្លៃបោះដុំ
            let discountRate = 0;
            if (totalBoxes >= 10) {
                discountRate = 0.10; // បញ្ចុះ 10% បើទិញចាប់ពី 10 កេសឡើង
            } else if (totalBoxes >= 5) {
                discountRate = 0.05; // បញ្ចុះ 5% បើទិញចាប់ពី 5 កេសឡើង
            }

            let discountAmount = subtotal * discountRate;
            let grandTotal = subtotal - discountAmount;

            document.getElementById('subtotal').innerText = `$${subtotal.toFixed(2)}`;
            document.getElementById('discount-percent').innerText = `${discountRate * 100}%`;
            document.getElementById('discount-amount').innerText = `-$${discountAmount.toFixed(2)}`;
            document.getElementById('grand-total').innerText = `$${grandTotal.toFixed(2)}`;
            document.getElementById('footer-price').innerText = `$${grandTotal.toFixed(2)}`;
        }

        function submitWholesaleOrder() {
            const selected = products.filter(p => p.qty > 0);
            const name = document.getElementById('cust-name').value.trim();
            const phone = document.getElementById('cust-phone').value.trim();
            const address = document.getElementById('cust-address').value.trim();

            if (selected.length === 0) {
                alert("សូមជ្រើសរើសទំនិញយ៉ាងហោចណាស់ ១ កេស!");
                return;
            }

            if (!name || !phone || !address) {
                alert("សូមបំពេញឈ្មោះ លេខទូរស័ព្ទ និងអាសយដ្ឋានឱ្យបានគ្រប់គ្រប់!");
                return;
            }

            let totalBoxes = selected.reduce((sum, p) => sum + p.qty, 0);
            let subtotal = selected.reduce((sum, p) => sum + (p.price * p.qty), 0);
            let discountRate = totalBoxes >= 10 ? 0.10 : (totalBoxes >= 5 ? 0.05 : 0);
            let grandTotal = subtotal - (subtotal * discountRate);

            const payload = {
                type: "WHOLESALE_ORDER",
                customerName: name,
                phone: phone,
                address: address,
                items: selected,
                totalBoxes: totalBoxes,
                totalAmount: grandTotal
            };

            if (window.Telegram && window.Telegram.WebApp) {
                Telegram.WebApp.sendData(JSON.stringify(payload));
            } else {
                alert("កុម្ម៉ង់ទិញបោះដុំជោគជ័យ! សរុប: $" + payload.totalAmount.toFixed(2));
            }
        }

        if (window.Telegram && window.Telegram.WebApp) {
            Telegram.WebApp.ready();
            Telegram.WebApp.expand();
        }
    </script>
</body>
</html>
