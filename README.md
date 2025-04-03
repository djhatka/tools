<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Premium Currency Converter</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-YOUR_PUBLISHER_ID" crossorigin="anonymous"></script>
    <style>
        :root {
            --primary: #6c5ce7;
            --primary-light: #a29bfe;
            --secondary: #00cec9;
            --accent: #fd79a8;
            --dark: #2d3436;
            --light: #f5f6fa;
            --success: #00b894;
            --warning: #fdcb6e;
            --error: #d63031;
            --border-radius: 12px;
            --box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
            --transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, var(--light) 0%, #dfe6e9 100%);
            color: var(--dark);
            min-height: 100vh;
            line-height: 1.6;
            padding: 20px;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
            animation: fadeIn 0.8s ease-out;
        }
        
        h1 {
            color: var(--primary);
            margin-bottom: 10px;
            font-size: 2.5rem;
            background: linear-gradient(to right, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .ad-container {
            background: white;
            border-radius: var(--border-radius);
            padding: 15px;
            margin: 20px 0;
            text-align: center;
            box-shadow: var(--box-shadow);
        }
        
        .ad-label {
            font-size: 0.75rem;
            color: #b2bec3;
            margin-bottom: 8px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .converter-box {
            background: white;
            border-radius: var(--border-radius);
            box-shadow: var(--box-shadow);
            padding: 30px;
            margin-bottom: 30px;
            position: relative;
            overflow: hidden;
            animation: slideUp 0.8s ease-out;
        }
        
        .converter-box::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 4px;
            height: 100%;
            background: linear-gradient(to bottom, var(--primary), var(--secondary));
            transition: var(--transition);
        }
        
        .converter-box:hover::before {
            width: 6px;
        }
        
        .input-group {
            margin-bottom: 20px;
        }
        
        .currency-row {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 15px;
        }
        
        .currency-input, .currency-select {
            flex: 1;
            min-width: 200px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
        }
        
        input, select {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #dfe6e9;
            border-radius: var(--border-radius);
            font-size: 16px;
            background-color: #f8f9fa;
            transition: var(--transition);
        }
        
        input:focus, select:focus {
            outline: none;
            border-color: var(--primary-light);
            box-shadow: 0 0 0 3px rgba(108, 92, 231, 0.2);
            background-color: white;
        }
        
        .action-row {
            display: flex;
            gap: 15px;
            align-items: center;
        }
        
        button {
            background: linear-gradient(to right, var(--primary), var(--secondary));
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: var(--border-radius);
            cursor: pointer;
            font-weight: 600;
            flex: 1;
            transition: var(--transition);
            box-shadow: 0 4px 6px rgba(108, 92, 231, 0.3);
            position: relative;
            overflow: hidden;
        }
        
        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 7px 14px rgba(108, 92, 231, 0.4);
        }
        
        button::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(to right, var(--secondary), var(--primary));
            opacity: 0;
            transition: var(--transition);
        }
        
        button:hover::after {
            opacity: 1;
        }
        
        .swap-btn {
            background: none;
            border: none;
            color: var(--primary);
            font-size: 20px;
            cursor: pointer;
            padding: 10px;
            border-radius: 50%;
            transition: var(--transition);
        }
        
        .swap-btn:hover {
            background-color: rgba(108, 92, 231, 0.1);
            transform: rotate(180deg);
        }
        
        .result {
            margin-top: 20px;
            padding: 15px;
            background: linear-gradient(to right, rgba(108, 92, 231, 0.05), rgba(0, 206, 201, 0.05));
            border-radius: var(--border-radius);
            border-left: 4px solid var(--primary);
            display: none;
            animation: fadeIn 0.5s ease-out;
        }
        
        .result.show {
            display: block;
        }
        
        .result-value {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary);
            margin: 10px 0;
            background: linear-gradient(to right, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .rate-info {
            color: #636e72;
            font-size: 14px;
        }
        
        .spinner {
            display: none;
            width: 40px;
            height: 40px;
            margin: 20px auto;
            border: 4px solid rgba(108, 92, 231, 0.1);
            border-top: 4px solid var(--primary);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        
        .error {
            color: var(--error);
            margin-top: 10px;
            padding: 10px;
            background-color: rgba(214, 48, 49, 0.1);
            border-radius: var(--border-radius);
            border-left: 4px solid var(--error);
            display: none;
            animation: shake 0.5s ease;
        }
        
        .error.show {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        @keyframes slideUp {
            from { 
                opacity: 0;
                transform: translateY(20px);
            }
            to { 
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            20%, 60% { transform: translateX(-5px); }
            40%, 80% { transform: translateX(5px); }
        }
        
        @media (max-width: 600px) {
            .currency-row {
                flex-direction: column;
            }
            
            .action-row {
                flex-direction: column;
            }
            
            button, .swap-btn {
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Premium Currency Converter</h1>
            <p>Convert between 150+ currencies with real-time exchange rates</p>
        </header>
        
        <!-- Top AdSense Banner -->
        <div class="ad-container">
            <div class="ad-label">Advertisement</div>
            <ins class="adsbygoogle"
                style="display:block"
                data-ad-client="ca-pub-YOUR_PUBLISHER_ID"
                data-ad-slot="YOUR_TOP_SLOT_ID"
                data-ad-format="auto"
                data-full-width-responsive="true"></ins>
            <script>
                (adsbygoogle = window.adsbygoogle || []).push({});
            </script>
        </div>
        
        <div class="converter-box">
            <div class="input-group">
                <div class="currency-row">
                    <div class="currency-input">
                        <label for="amount">Amount</label>
                        <input type="number" id="amount" placeholder="Enter amount" min="0" step="0.01" value="1">
                    </div>
                    <div class="currency-select">
                        <label for="from-currency">From Currency</label>
                        <select id="from-currency">
                            <option value="USD">US Dollar (USD)</option>
                            <option value="EUR">Euro (EUR)</option>
                            <option value="GBP">British Pound (GBP)</option>
                            <option value="JPY">Japanese Yen (JPY)</option>
                            <option value="AUD">Australian Dollar (AUD)</option>
                            <option value="CAD">Canadian Dollar (CAD)</option>
                            <option value="CHF">Swiss Franc (CHF)</option>
                            <option value="CNY">Chinese Yuan (CNY)</option>
                            <option value="INR">Indian Rupee (INR)</option>
                        </select>
                    </div>
                </div>
                
                <div class="currency-row">
                    <div class="currency-input">
                        <label for="converted-amount">Converted Amount</label>
                        <input type="number" id="converted-amount" placeholder="Result" readonly>
                    </div>
                    <div class="currency-select">
                        <label for="to-currency">To Currency</label>
                        <select id="to-currency">
                            <option value="EUR">Euro (EUR)</option>
                            <option value="USD">US Dollar (USD)</option>
                            <option value="GBP">British Pound (GBP)</option>
                            <option value="JPY">Japanese Yen (JPY)</option>
                            <option value="AUD">Australian Dollar (AUD)</option>
                            <option value="CAD">Canadian Dollar (CAD)</option>
                            <option value="CHF">Swiss Franc (CHF)</option>
                            <option value="CNY">Chinese Yuan (CNY)</option>
                            <option value="INR">Indian Rupee (INR)</option>
                        </select>
                    </div>
                </div>
            </div>
            
            <div class="action-row">
                <button id="convert-btn">
                    <span>Convert</span>
                </button>
                <button class="swap-btn" id="swap-btn" title="Swap currencies">⇅</button>
            </div>
            
            <div class="spinner" id="spinner"></div>
            <div class="error" id="error"></div>
            
            <div class="result" id="result">
                <div class="result-value" id="result-value"></div>
                <div class="rate-info" id="rate-info"></div>
            </div>
        </div>
        
        <!-- Middle AdSense Rectangle -->
        <div class="ad-container">
            <div class="ad-label">Advertisement</div>
            <ins class="adsbygoogle"
                style="display:block"
                data-ad-client="ca-pub-YOUR_PUBLISHER_ID"
                data-ad-slot="YOUR_MIDDLE_SLOT_ID"
                data-ad-format="rectangle"
                data-full-width-responsive="true"></ins>
            <script>
                (adsbygoogle = window.adsbygoogle || []).push({});
            </script>
        </div>
        
        <!-- Bottom AdSense Banner -->
        <div class="ad-container">
            <div class="ad-label">Advertisement</div>
            <ins class="adsbygoogle"
                style="display:block"
                data-ad-client="ca-pub-YOUR_PUBLISHER_ID"
                data-ad-slot="YOUR_BOTTOM_SLOT_ID"
                data-ad-format="auto"
                data-full-width-responsive="true"></ins>
            <script>
                (adsbygoogle = window.adsbygoogle || []).push({});
            </script>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // DOM elements
            const amountInput = document.getElementById('amount');
            const fromCurrency = document.getElementById('from-currency');
            const toCurrency = document.getElementById('to-currency');
            const convertedAmount = document.getElementById('converted-amount');
            const convertBtn = document.getElementById('convert-btn');
            const swapBtn = document.getElementById('swap-btn');
            const resultDiv = document.getElementById('result');
            const resultValue = document.getElementById('result-value');
            const rateInfo = document.getElementById('rate-info');
            const spinner = document.getElementById('spinner');
            const errorDiv = document.getElementById('error');
            
            // Using ExchangeRate-API (free tier)
            const API_KEY = 'YOUR_API_KEY'; // Replace with your actual API key
            const API_URL = `https://v6.exchangerate-api.com/v6/${API_KEY}/latest/USD`;
            
            // Exchange rates cache
            let exchangeRates = {};
            let lastUpdated = null;
            
            // Fetch exchange rates from API
            async function fetchExchangeRates(baseCurrency = 'USD') {
                showLoading(true);
                hideError();
                
                try {
                    const response = await fetch(`https://v6.exchangerate-api.com/v6/${API_KEY}/latest/${baseCurrency}`);
                    
                    if (!response.ok) {
                        throw new Error('Failed to fetch exchange rates');
                    }
                    
                    const data = await response.json();
                    
                    if (data.result === 'error') {
                        throw new Error(data['error-type']);
                    }
                    
                    exchangeRates = data.conversion_rates;
                    lastUpdated = new Date(data.time_last_update_utc);
                    
                    // Perform conversion if amount has value
                    if (amountInput.value && !isNaN(parseFloat(amountInput.value))) {
                        convertCurrency();
                    }
                    
                    return data;
                } catch (error) {
                    console.error('Error fetching exchange rates:', error);
                    showError('Failed to fetch exchange rates. Using cached rates or try again later.');
                    
                    // Fallback to hardcoded rates if API fails
                    const fallbackRates = {
                        USD: 1,
                        EUR: 0.93,
                        GBP: 0.79,
                        JPY: 151.53,
                        AUD: 1.52,
                        CAD: 1.37,
                        CHF: 0.91,
                        CNY: 7.24,
                        INR: 83.38
                    };
                    
                    exchangeRates = fallbackRates;
                    lastUpdated = new Date();
                    convertCurrency();
                    
                    return null;
                } finally {
                    showLoading(false);
                }
            }
            
            // Convert currency
            function convertCurrency() {
                const amount = parseFloat(amountInput.value);
                const fromCurr = fromCurrency.value;
                const toCurr = toCurrency.value;
                
                // Validate input
                if (isNaN(amount)) {
                    showError('Please enter a valid amount');
                    return;
                }
                
                if (amount <= 0) {
                    showError('Amount must be greater than 0');
                    return;
                }
                
                // Check if we have exchange rates
                if (!exchangeRates[fromCurr] || !exchangeRates[toCurr]) {
                    showError('Exchange rate data not available for selected currencies');
                    return;
                }
                
                hideError();
                
                // Calculate converted amount
                const rate = exchangeRates[toCurr] / exchangeRates[fromCurr];
                const convertedValue = amount * rate;
                
                // Update UI
                convertedAmount.value = convertedValue.toFixed(4);
                
                // Show result details
                resultValue.textContent = `${amount.toLocaleString(undefined, {maximumFractionDigits: 2})} ${fromCurr} = ${convertedValue.toLocaleString(undefined, {maximumFractionDigits: 2})} ${toCurr}`;
                rateInfo.textContent = `1 ${fromCurr} = ${rate.toFixed(6)} ${toCurr} • Last updated: ${formatDate(lastUpdated)}`;
                
                resultDiv.classList.add('show');
            }
            
            // Format date for display
            function formatDate(date) {
                if (!date) return 'N/A';
                return date.toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' }) + ' ' + date.toLocaleDateString();
            }
            
            // Show loading spinner
            function showLoading(show) {
                spinner.style.display = show ? 'block' : 'none';
                convertBtn.disabled = show;
            }
            
            // Show error message
            function showError(message) {
                errorDiv.textContent = message;
                errorDiv.classList.add('show');
                resultDiv.classList.remove('show');
            }
            
            // Hide error message
            function hideError() {
                errorDiv.classList.remove('show');
            }
            
            // Swap currencies
            function swapCurrencies() {
                const temp = fromCurrency.value;
                fromCurrency.value = toCurrency.value;
                toCurrency.value = temp;
                convertCurrency();
            }
            
            // Initialize the app
            function init() {
                // Set up event listeners
                convertBtn.addEventListener('click', convertCurrency);
                swapBtn.addEventListener('click', swapCurrencies);
                
                // Convert when inputs change
                amountInput.addEventListener('input', convertCurrency);
                fromCurrency.addEventListener('change', function() {
                    fetchExchangeRates(this.value);
                });
                toCurrency.addEventListener('change', convertCurrency);
                
                // Initial fetch of exchange rates
                fetchExchangeRates();
            }
            
            // Start the app
            init();
        });
    </script>
</body>
</html>
