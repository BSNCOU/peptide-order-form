<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=0.9, maximum-scale=1.0, user-scalable=no">
    <title>Peptide Order Form</title>
    <style>
        :root {
            --primary: #1a5f7a;
            --secondary: #159895;
            --accent: #57c5b6;
            --light: #f0f8ff;
            --dark: #0d3446;
            --public-bg: #e8f4f8;
            --sales-bg: #fff7e6;
            --shadow: 0 4px 12px rgba(0,0,0,0.1);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, var(--light) 0%, #e0f2f7 100%);
            min-height: 100vh;
            padding: 8px;
        }
        
        .container {
            max-width: 100%;
            margin: 0 auto;
        }
        
        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 12px 12px;
            border-radius: 10px;
            margin-bottom: 10px;
            box-shadow: var(--shadow);
        }
        
        h1 {
            font-size: 18px;
            margin-bottom: 4px;
            font-weight: 700;
        }
        
        .subtitle {
            opacity: 0.9;
            font-size: 11px;
        }
        
        .order-section {
            background: white;
            border-radius: 10px;
            padding: 12px;
            margin-bottom: 10px;
            box-shadow: var(--shadow);
        }
        
        .order-item {
            background: #fafafa;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            padding: 10px;
            margin-bottom: 10px;
            transition: all 0.3s ease;
        }
        
        .order-item:hover {
            border-color: var(--accent);
            box-shadow: 0 2px 8px rgba(87, 197, 182, 0.2);
        }
        
        .item-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
        }
        
        .item-number {
            font-weight: 700;
            color: var(--primary);
            font-size: 12px;
        }
        
        .remove-btn {
            background: #ff4757;
            color: white;
            border: none;
            border-radius: 5px;
            padding: 5px 10px;
            font-size: 11px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.2s;
        }
        
        .remove-btn:hover {
            background: #ee2f3a;
            transform: scale(1.05);
        }
        
        label {
            display: block;
            font-weight: 600;
            margin-bottom: 5px;
            color: var(--dark);
            font-size: 11px;
        }
        
        select, input {
            width: 100%;
            padding: 8px 8px;
            border: 2px solid #e0e0e0;
            border-radius: 6px;
            font-size: 13px;
            background: white;
            transition: all 0.3s;
            margin-bottom: 8px;
        }
        
        select:focus, input:focus {
            outline: none;
            border-color: var(--secondary);
            box-shadow: 0 0 0 3px rgba(21, 152, 149, 0.1);
        }
        
        .price-display {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 8px;
            margin-top: 8px;
        }
        
        .price-box {
            padding: 8px;
            border-radius: 6px;
            text-align: center;
        }
        
        .price-box.sales {
            background: var(--sales-bg);
            border: 2px solid #ffd89b;
        }
        
        .price-box.public {
            background: var(--public-bg);
            border: 2px solid #b3e5fc;
        }
        
        .price-label {
            font-size: 9px;
            font-weight: 600;
            text-transform: uppercase;
            color: #666;
            margin-bottom: 3px;
        }
        
        .price-value {
            font-size: 16px;
            font-weight: 800;
            color: var(--dark);
        }
        
        .add-btn {
            background: var(--secondary);
            color: white;
            border: none;
            border-radius: 8px;
            padding: 10px 16px;
            font-size: 13px;
            font-weight: 700;
            cursor: pointer;
            width: 100%;
            margin-bottom: 10px;
            transition: all 0.3s;
            box-shadow: 0 4px 10px rgba(21, 152, 149, 0.3);
        }
        
        .add-btn:hover {
            background: var(--accent);
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(21, 152, 149, 0.4);
        }
        
        .totals {
            background: linear-gradient(135deg, var(--dark), var(--primary));
            color: white;
            border-radius: 10px;
            padding: 12px;
            margin-top: 10px;
            box-shadow: var(--shadow);
        }
        
        .totals h2 {
            font-size: 16px;
            margin-bottom: 10px;
            text-align: center;
        }
        
        .total-row {
            display: flex;
            justify-content: space-between;
            padding: 8px;
            background: rgba(255,255,255,0.1);
            border-radius: 6px;
            margin-bottom: 6px;
            font-size: 12px;
            font-weight: 600;
        }
        
        .total-row.grand {
            background: rgba(255,255,255,0.2);
            font-size: 14px;
            font-weight: 800;
            border: 2px solid rgba(255,255,255,0.3);
        }
        
        @media (max-width: 600px) {
            body {
                padding: 5px;
            }
            
            .price-display { 
                grid-template-columns: 1fr; 
                gap: 6px;
            }
            
            .price-value {
                font-size: 14px;
            }
            
            h1 {
                font-size: 16px;
            }
            
            .subtitle {
                font-size: 10px;
            }
            
            .total-row {
                font-size: 11px;
            }
            
            .total-row.grand {
                font-size: 13px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>🧪 Peptide Order Form</h1>
            <div class="subtitle">Select products to see instant pricing for sales and public</div>
        </header>
        
        <div class="order-section">
            <div id="orderItems"></div>
            <button class="add-btn" onclick="addOrderItem()">+ Add Product</button>
        </div>
        
        <button class="add-btn" onclick="generateOrderText()" style="background: linear-gradient(135deg, #f39c12, #e74c3c); margin-top: 10px;">
            📋 Generate Order Summary
        </button>
        
        <div id="orderTextSection" style="display: none; background: white; border-radius: 16px; padding: 25px; margin-top: 20px; box-shadow: var(--shadow);">
            <h3 style="margin-bottom: 15px; color: var(--dark);">Order Summary Text</h3>
            <textarea id="orderTextArea" readonly style="width: 100%; min-height: 300px; padding: 15px; border: 2px solid #e0e0e0; border-radius: 10px; font-family: 'Courier New', monospace; font-size: 14px; resize: vertical;"></textarea>
            <button onclick="copyOrderText()" style="background: #27ae60; color: white; border: none; border-radius: 10px; padding: 12px 20px; font-size: 15px; font-weight: 600; cursor: pointer; width: 100%; margin-top: 10px;">
                📄 Copy to Clipboard
            </button>
            <div id="copyConfirm" style="display: none; text-align: center; margin-top: 10px; color: #27ae60; font-weight: 600;">
                ✓ Copied to clipboard!
            </div>
        </div>
        
        <div class="totals">
            <h2>Order Summary</h2>
            <div class="total-row">
                <span>Sales Price Total:</span>
                <span id="salesTotal">$0.00</span>
            </div>
            <div class="total-row">
                <span>Public Price Total:</span>
                <span id="publicTotal">$0.00</span>
            </div>
            <div class="total-row grand">
                <span>Potential Profit:</span>
                <span id="profitTotal">$0.00</span>
            </div>
        </div>
    </div>

    <script>
        const products = [
            {code: "SM5", name: "Semaglutide", spec: "5mg/10vials", sales1: 40, public1: 50, sales2: 280, public2: 350},
            {code: "SM10", name: "Semaglutide", spec: "10mg/10vials", sales1: 56, public1: 70, sales2: 392, public2: 490},
            {code: "TR5", name: "Tirzepatide", spec: "5mg/10vials", sales1: 40, public1: 50, sales2: 280, public2: 350},
            {code: "TR10", name: "Tirzepatide", spec: "10mg/10vials", sales1: 56, public1: 70, sales2: 392, public2: 490},
            {code: "RT5", name: "Retatrutide", spec: "5mg/10vials", sales1: 48, public1: 60, sales2: 336, public2: 420},
            {code: "RT10", name: "Retatrutide", spec: "10mg/10vials", sales1: 64, public1: 80, sales2: 512, public2: 640},
            {code: "CGL5", name: "Cagrilintide", spec: "5mg/10vials", sales1: 48, public1: 60, sales2: 336, public2: 420},
            {code: "CGL10", name: "Cagrilintide", spec: "10mg/10vials", sales1: 64, public1: 80, sales2: 448, public2: 560},
            {code: "TSM5", name: "Tesamorelin", spec: "5mg/10vials", sales1: 48, public1: 60, sales2: 336, public2: 420},
            {code: "TSM10", name: "Tesamorelin", spec: "10mg/10vials", sales1: 60, public1: 75, sales2: 400, public2: 500},
            {code: "CS5", name: "cagrilintide+Samaglutide", spec: "2.5mg+2.5mg", sales1: 51, public1: 64, sales2: 357, public2: 446},
            {code: "CS10", name: "cagrilintide+Samaglutide", spec: "5mg+5mg", sales1: 68, public1: 85, sales2: 476, public2: 595},
            {code: "CU50", name: "GHK-CU", spec: "50mg/10vials", sales1: 29, public1: 36, sales2: 222, public2: 278},
            {code: "CU100", name: "GHK-CU", spec: "100mg/10vials", sales1: 38, public1: 48, sales2: 296, public2: 370},
            {code: "ET10", name: "Epithalon", spec: "10mg/10vials", sales1: 28, public1: 35, sales2: 196, public2: 245},
            {code: "ET50", name: "Epithalon", spec: "50mg/10vials", sales1: 40, public1: 50, sales2: 280, public2: 350},
            {code: "MS10", name: "MOTS-c", spec: "10mg/10vials", sales1: 40, public1: 50, sales2: 280, public2: 350},
            {code: "MS40", name: "MOTS-c", spec: "40mg/10vials", sales1: 144, public1: 180, sales2: 1008, public2: 1260},
            {code: "ML10", name: "MT-2 (Melanotan 2Acetate)", spec: "10mg/10vials", sales1: 32, public1: 40, sales2: 224, public2: 280},
            {code: "5AD", name: "AOD9604", spec: "5mg/10vials", sales1: 48, public1: 60, sales2: 376, public2: 470},
            {code: "CD5", name: "CJC-1295 DAC", spec: "5mg/10vials", sales1: 112, public1: 140, sales2: 784, public2: 980},
            {code: "CND5", name: "CJC-1295 NO DAC", spec: "5mg/10vials", sales1: 56, public1: 70, sales2: 392, public2: 490},
            {code: "CND10", name: "CJC-1295 NO DAC", spec: "10mg/10vials", sales1: 104, public1: 130, sales2: 728, public2: 910},
            {code: "CP10", name: "CJC-1295 NO DAC + IPA5mg", spec: "5mg+5mg/10vials", sales1: 64, public1: 80, sales2: 448, public2: 560},
            {code: "IP5", name: "Ipamorelin", spec: "5mg/10vials", sales1: 24, public1: 30, sales2: 168, public2: 210},
            {code: "IP10", name: "Ipamorelin", spec: "10mg/10vials", sales1: 48, public1: 60, sales2: 336, public2: 420},
            {code: "BC5", name: "BPC 157", spec: "5mg/10vials", sales1: 26, public1: 32, sales2: 179, public2: 224},
            {code: "BC10", name: "BPC 157", spec: "10mg/10vials", sales1: 32, public1: 40, sales2: 280, public2: 350},
            {code: "TB5", name: "TB500(Thymosin B4 Acetate)", spec: "5mg/10vials", sales1: 35, public1: 44, sales2: 246, public2: 308},
            {code: "TB10", name: "TB500(Thymosin B4 Acetate)", spec: "10mg/10vials", sales1: 44, public1: 55, sales2: 400, public2: 500},
            {code: "BB10", name: "BPC 5mg + TB 5mg", spec: "10mg/10vials", sales1: 38, public1: 48, sales2: 320, public2: 400},
            {code: "BB20", name: "BPC 10mg + TB 10mg", spec: "20mg/10vials", sales1: 48, public1: 60, sales2: 400, public2: 500},
            {code: "BBG70", name: "GLOW (BPC+GHK-CU+TB500)", spec: "70mg/10vials", sales1: 78, public1: 98, sales2: 624, public2: 780},
            {code: "BBGK", name: "KLOW (BPC+GHK-CU+TB500+KPV)", spec: "80mg/10vials", sales1: 149, public1: 186, sales2: 852, public2: 1065},
            {code: "NJ100", name: "NAD+", spec: "100mg/10vials", sales1: 45, public1: 56, sales2: 314, public2: 392},
            {code: "NJ500", name: "NAD+", spec: "500mg/10vials", sales1: 56, public1: 70, sales2: 400, public2: 500},
            {code: "G5K", name: "HCG", spec: "5000iu/10vials", sales1: 60, public1: 75, sales2: 420, public2: 525},
            {code: "G10K", name: "HCG", spec: "10000iu/10vials", sales1: 96, public1: 120, sales2: 672, public2: 840},
            {code: "332", name: "SLU-PP-332 5mg", spec: "5mg/10vials", sales1: 96, public1: 120, sales2: 672, public2: 840},
            {code: "TA5", name: "Thymosin Alpha-1", spec: "5mg/10vials", sales1: 52, public1: 65, sales2: 364, public2: 455},
            {code: "TA10", name: "Thymosin Alpha-1", spec: "10mg/10vials", sales1: 104, public1: 130, sales2: 728, public2: 910},
            {code: "2S10", name: "SS-31", spec: "10mg/10vials", sales1: 60, public1: 75, sales2: 420, public2: 525},
            {code: "2S50", name: "SS-31", spec: "50mg/10vials", sales1: 280, public1: 350, sales2: 1960, public2: 2450},
            {code: "GTT", name: "Glutathione", spec: "1500mg/10vials", sales1: 80, public1: 100, sales2: 560, public2: 700},
            {code: "NP810", name: "Snap-8", spec: "10mg/10vials", sales1: 32, public1: 40, sales2: 224, public2: 280},
            {code: "KPV5", name: "LYSINE-PROLINE-VALINE", spec: "5mg/10vials", sales1: 28, public1: 35, sales2: 196, public2: 245},
            {code: "KPV10", name: "LYSINE-PROLINE-VALINE", spec: "10mg/10vials", sales1: 44, public1: 55, sales2: 308, public2: 385},
            {code: "XA5", name: "Semax", spec: "5mg/10vials", sales1: 32, public1: 40, sales2: 224, public2: 280},
            {code: "XA11", name: "Semax", spec: "11mg/10vials", sales1: 40, public1: 50, sales2: 280, public2: 350},
            {code: "SK5", name: "Selank", spec: "5mg/10vials", sales1: 32, public1: 40, sales2: 224, public2: 280},
            {code: "SK11", name: "Selank", spec: "11mg/10vials", sales1: 40, public1: 50, sales2: 280, public2: 350},
            {code: "VIP5", name: "VIP5", spec: "5mg/10vials", sales1: 60, public1: 75, sales2: 420, public2: 525},
            {code: "VIP10", name: "VIP5", spec: "10mg/10vials", sales1: 112, public1: 140, sales2: 784, public2: 980},
            {code: "P41", name: "PT-141", spec: "10mg/10vials", sales1: 44, public1: 55, sales2: 308, public2: 385},
            {code: "DS5", name: "DSIP", spec: "5mg/10vials", sales1: 28, public1: 35, sales2: 196, public2: 245},
            {code: "DS15", name: "DSIP", spec: "10mg/10vials", sales1: 56, public1: 70, sales2: 392, public2: 490},
            {code: "WA10", name: "BAC water", spec: "10ML/10vials", sales1: 4, public1: 5, sales2: 28, public2: 35},
            {code: "CBL60", name: "cerebrolysim", spec: "60mg/6vials", sales1: 68, public1: 85, sales2: 476, public2: 595},
            {code: "375", name: "LL37", spec: "5mg/10vials", sales1: 44, public1: 55, sales2: 308, public2: 385},
            {code: "PI5", name: "Pinealon", spec: "5mg/10vials", sales1: 40, public1: 50, sales2: 280, public2: 350},
            {code: "PI10", name: "Pinealon", spec: "10mg/10vials", sales1: 50, public1: 63, sales2: 400, public2: 500},
            {code: "KS10", name: "KissPeptin-10", spec: "10mg/10vials", sales1: 40, public1: 50, sales2: 320, public2: 400},
            {code: "OT2", name: "Oxytocin Acetate", spec: "2mg*10vials", sales1: 250, public1: 313, sales2: 200, public2: 250},
            {code: "F410", name: "FOXO4", spec: "10mg*10vials", sales1: 216, public1: 270, sales2: 1512, public2: 1890},
            {code: "5AM", name: "5-amino-1mq", spec: "5mg*10vials", sales1: 52, public1: 65, sales2: 364, public2: 455},
            {code: "HA5", name: "hyaluronic acid", spec: "5mg*10vials", sales1: 56, public1: 70, sales2: 392, public2: 490}
        ];

        let itemCounter = 0;

        function addOrderItem() {
            itemCounter++;
            const itemDiv = document.createElement('div');
            itemDiv.className = 'order-item';
            itemDiv.id = `item-${itemCounter}`;
            
            itemDiv.innerHTML = `
                <div class="item-header">
                    <div class="item-number">Item #${itemCounter}</div>
                    <button class="remove-btn" onclick="removeItem(${itemCounter})">Remove</button>
                </div>
                
                <label>Select Product</label>
                <select id="product-${itemCounter}" onchange="updatePrices(${itemCounter})">
                    <option value="">-- Choose a product --</option>
                    ${products.map(p => `<option value="${p.code}">${p.code} - ${p.name} (${p.spec})</option>`).join('')}
                </select>
                
                <label>Quantity (number of bottles)</label>
                <input type="number" id="quantity-${itemCounter}" min="1" value="1" onchange="updatePrices(${itemCounter})" oninput="updatePrices(${itemCounter})">
                
                <div class="price-display">
                    <div class="price-box sales">
                        <div class="price-label">Sales Price</div>
                        <div class="price-value" id="sales-price-${itemCounter}">$0.00</div>
                    </div>
                    <div class="price-box public">
                        <div class="price-label">Public Price</div>
                        <div class="price-value" id="public-price-${itemCounter}">$0.00</div>
                    </div>
                </div>
            `;
            
            document.getElementById('orderItems').appendChild(itemDiv);
        }

        function removeItem(itemId) {
            const item = document.getElementById(`item-${itemId}`);
            if (item) {
                item.remove();
                updateTotals();
            }
        }

        function updatePrices(itemId) {
            const productCode = document.getElementById(`product-${itemId}`).value;
            const quantity = parseInt(document.getElementById(`quantity-${itemId}`).value) || 0;
            
            if (!productCode || quantity === 0) {
                document.getElementById(`sales-price-${itemId}`).textContent = '$0.00';
                document.getElementById(`public-price-${itemId}`).textContent = '$0.00';
                updateTotals();
                return;
            }
            
            const product = products.find(p => p.code === productCode);
            
            if (product) {
                let salesPricePerBottle, publicPricePerBottle;
                
                if (quantity < 10) {
                    salesPricePerBottle = product.sales1;
                    publicPricePerBottle = product.public1;
                } else {
                    salesPricePerBottle = product.sales2 / 10;
                    publicPricePerBottle = product.public2 / 10;
                }
                
                const salesTotal = salesPricePerBottle * quantity;
                const publicTotal = publicPricePerBottle * quantity;
                
                document.getElementById(`sales-price-${itemId}`).textContent = `$${salesTotal.toFixed(2)}`;
                document.getElementById(`public-price-${itemId}`).textContent = `$${publicTotal.toFixed(2)}`;
            }
            
            updateTotals();
        }

        function updateTotals() {
            let salesTotal = 0;
            let publicTotal = 0;
            
            document.querySelectorAll('[id^="sales-price-"]').forEach(el => {
                const price = parseFloat(el.textContent.replace('$', '')) || 0;
                salesTotal += price;
            });
            
            document.querySelectorAll('[id^="public-price-"]').forEach(el => {
                const price = parseFloat(el.textContent.replace('$', '')) || 0;
                publicTotal += price;
            });
            
            const profit = publicTotal - salesTotal;
            
            document.getElementById('salesTotal').textContent = `$${salesTotal.toFixed(2)}`;
            document.getElementById('publicTotal').textContent = `$${publicTotal.toFixed(2)}`;
            document.getElementById('profitTotal').textContent = `$${profit.toFixed(2)}`;
        }

        function generateOrderText() {
            const orderItems = [];
            let salesTotal = 0;
            let publicTotal = 0;
            
            document.querySelectorAll('.order-item').forEach(item => {
                const itemId = item.id.split('-')[1];
                const productSelect = document.getElementById(`product-${itemId}`);
                const quantityInput = document.getElementById(`quantity-${itemId}`);
                const salesPrice = document.getElementById(`sales-price-${itemId}`).textContent;
                const publicPrice = document.getElementById(`public-price-${itemId}`).textContent;
                
                if (productSelect && productSelect.value) {
                    const product = products.find(p => p.code === productSelect.value);
                    const quantity = parseInt(quantityInput.value) || 0;
                    
                    if (product && quantity > 0) {
                        orderItems.push({
                            code: product.code,
                            name: product.name,
                            spec: product.spec,
                            quantity: quantity,
                            salesPrice: salesPrice,
                            publicPrice: publicPrice
                        });
                        
                        salesTotal += parseFloat(salesPrice.replace('$', '')) || 0;
                        publicTotal += parseFloat(publicPrice.replace('$', '')) || 0;
                    }
                }
            });
            
            if (orderItems.length === 0) {
                alert('Please add at least one product to generate an order summary!');
                return;
            }
            
            const date = new Date().toLocaleDateString();
            let orderText = `═══════════════════════════════════════\n`;
            orderText += `         PEPTIDE ORDER SUMMARY\n`;
            orderText += `═══════════════════════════════════════\n`;
            orderText += `Date: ${date}\n\n`;
            
            orderText += `ITEMS ORDERED:\n`;
            orderText += `─────────────────────────────────────\n`;
            
            orderItems.forEach((item, index) => {
                orderText += `\n${index + 1}. ${item.code} - ${item.name}\n`;
                orderText += `   Spec: ${item.spec}\n`;
                orderText += `   Quantity: ${item.quantity} bottle(s)\n`;
                orderText += `   Sales Price: ${item.salesPrice}\n`;
                orderText += `   Public Price: ${item.publicPrice}\n`;
            });
            
            const profit = publicTotal - salesTotal;
            
            orderText += `\n═══════════════════════════════════════\n`;
            orderText += `TOTALS:\n`;
            orderText += `─────────────────────────────────────\n`;
            orderText += `Sales Cost:      $${salesTotal.toFixed(2)}\n`;
            orderText += `Public Price:    $${publicTotal.toFixed(2)}\n`;
            orderText += `Potential Profit: $${profit.toFixed(2)}\n`;
            orderText += `═══════════════════════════════════════\n`;
            
            document.getElementById('orderTextArea').value = orderText;
            document.getElementById('orderTextSection').style.display = 'block';
            
            document.getElementById('orderTextSection').scrollIntoView({ behavior: 'smooth', block: 'nearest' });
        }

        function copyOrderText() {
            const textArea = document.getElementById('orderTextArea');
            textArea.select();
            textArea.setSelectionRange(0, 99999);
            
            navigator.clipboard.writeText(textArea.value).then(() => {
                const confirm = document.getElementById('copyConfirm');
                confirm.style.display = 'block';
                
                setTimeout(() => {
                    confirm.style.display = 'none';
                }, 2000);
            }).catch(err => {
                document.execCommand('copy');
                alert('Order summary copied to clipboard!');
            });
        }

        addOrderItem();
    </script>
</body>
</html>

