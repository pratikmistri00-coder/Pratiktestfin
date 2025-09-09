# Pratiktestfin
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Personal Finance Manager - Login</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
    <style>
        :root {
            --primary: #1976d2;
            --primary-dark: #115293;
            --secondary: #4caf50;
            --secondary-dark: #388e3c;
            --accent: #ff9800;
            --accent-dark: #f57c00;
            --danger: #f44336;
            --danger-dark: #d32f2f;
            --background: #f5f5f5;
            --card: #ffffff;
            --text: #212121;
            --text-light: #757575;
            --border: #e0e0e0;
            --shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Roboto', sans-serif;
            background-color: var(--background);
            color: var(--text);
            line-height: 1.6;
            height: 100vh;
            display: flex;
            flex-direction: column;
        }

        /* Login Page Styles */
        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(135deg, var(--primary), var(--primary-dark));
        }

        .login-card {
            background-color: var(--card);
            border-radius: 12px;
            box-shadow: 0 8px 30px rgba(0, 0, 0, 0.2);
            width: 100%;
            max-width: 400px;
            padding: 40px;
            text-align: center;
        }

        .login-logo {
            margin-bottom: 30px;
        }

        .login-logo .material-icons {
            font-size: 64px;
            color: var(--primary);
        }

        .login-title {
            font-size: 28px;
            font-weight: 500;
            margin-bottom: 10px;
            color: var(--text);
        }

        .login-subtitle {
            color: var(--text-light);
            margin-bottom: 30px;
        }

        .form-group {
            margin-bottom: 20px;
            text-align: left;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: var(--text);
        }

        .form-control {
            width: 100%;
            padding: 14px;
            border: 1px solid var(--border);
            border-radius: 6px;
            font-size: 16px;
            transition: border-color 0.3s;
        }

        .form-control:focus {
            outline: none;
            border-color: var(--primary);
        }

        .btn {
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 14px 20px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 500;
            width: 100%;
            transition: background-color 0.3s;
        }

        .btn:hover {
            background-color: var(--primary-dark);
        }

        .error-message {
            color: var(--danger);
            margin-top: 15px;
            font-size: 14px;
            display: none;
        }

        .login-footer {
            margin-top: 30px;
            font-size: 14px;
            color: var(--text-light);
        }

        /* Main App Styles (hidden until login) */
        .app-container {
            display: none;
            flex-direction: column;
            height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            flex: 1;
            overflow-y: auto;
        }

        header {
            background-color: var(--primary);
            color: white;
            padding: 15px 0;
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .logo {
            font-size: 24px;
            font-weight: 500;
            display: flex;
            align-items: center;
        }

        .logo .material-icons {
            margin-right: 10px;
        }

        .user-info {
            display: flex;
            align-items: center;
        }

        .user-info .material-icons {
            margin-right: 10px;
        }

        .currency-selector {
            display: flex;
            align-items: center;
            background-color: rgba(255, 255, 255, 0.2);
            border-radius: 4px;
            padding: 5px 10px;
            margin-left: 15px;
        }

        .currency-selector select {
            background: none;
            border: none;
            color: white;
            font-size: 14px;
            outline: none;
        }

        .currency-selector .material-icons {
            font-size: 18px;
            margin-right: 5px;
        }

        .logout-btn {
            background: none;
            border: none;
            color: white;
            cursor: pointer;
            display: flex;
            align-items: center;
            margin-left: 15px;
            padding: 5px 10px;
            border-radius: 4px;
            transition: background-color 0.3s;
        }

        .logout-btn:hover {
            background-color: rgba(255, 255, 255, 0.2);
        }

        .logout-btn .material-icons {
            margin-right: 5px;
        }

        nav {
            background-color: var(--primary-dark);
            padding: 10px 0;
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            overflow-x: auto;
        }

        .nav-item {
            color: white;
            text-decoration: none;
            padding: 10px 15px;
            border-radius: 4px;
            margin-right: 5px;
            white-space: nowrap;
            transition: background-color 0.3s;
        }

        .nav-item:hover, .nav-item.active {
            background-color: rgba(255, 255, 255, 0.2);
        }

        .main-content {
            padding: 20px 0;
        }

        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .card {
            background-color: var(--card);
            border-radius: 8px;
            box-shadow: var(--shadow);
            padding: 20px;
            margin-bottom: 20px;
        }

        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px solid var(--border);
        }

        .card-title {
            font-size: 20px;
            font-weight: 500;
        }

        .btn {
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 500;
            display: inline-flex;
            align-items: center;
            transition: background-color 0.3s;
        }

        .btn:hover {
            background-color: var(--primary-dark);
        }

        .btn .material-icons {
            font-size: 18px;
            margin-right: 5px;
        }

        .btn-secondary {
            background-color: var(--secondary);
        }

        .btn-secondary:hover {
            background-color: var(--secondary-dark);
        }

        .btn-danger {
            background-color: var(--danger);
        }

        .btn-danger:hover {
            background-color: var(--danger-dark);
        }

        .btn-accent {
            background-color: var(--accent);
        }

        .btn-accent:hover {
            background-color: var(--accent-dark);
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
        }

        .form-control {
            width: 100%;
            padding: 10px;
            border: 1px solid var(--border);
            border-radius: 4px;
            font-size: 14px;
        }

        .form-control:focus {
            outline: none;
            border-color: var(--primary);
        }

        .table {
            width: 100%;
            border-collapse: collapse;
        }

        .table th, .table td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid var(--border);
        }

        .table th {
            background-color: var(--background);
            font-weight: 500;
        }

        .table tr:hover {
            background-color: rgba(0, 0, 0, 0.02);
        }

        .table-actions {
            display: flex;
            gap: 5px;
        }

        .icon-btn {
            background: none;
            border: none;
            cursor: pointer;
            color: var(--text-light);
            padding: 5px;
            border-radius: 50%;
            transition: background-color 0.3s;
        }

        .icon-btn:hover {
            background-color: rgba(0, 0, 0, 0.1);
        }

        .icon-btn.edit {
            color: var(--primary);
        }

        .icon-btn.delete {
            color: var(--danger);
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 20px;
        }

        .stat-card {
            background-color: var(--card);
            border-radius: 8px;
            padding: 15px;
            box-shadow: var(--shadow);
            text-align: center;
        }

        .stat-value {
            font-size: 28px;
            font-weight: 700;
            margin: 10px 0;
        }

        .stat-label {
            color: var(--text-light);
            font-size: 14px;
        }

        .stat-card.income {
            border-top: 4px solid var(--secondary);
        }

        .stat-card.expense {
            border-top: 4px solid var(--danger);
        }

        .stat-card.savings {
            border-top: 4px solid var(--primary);
        }

        .stat-card.net-worth {
            border-top: 4px solid var(--accent);
        }

        .chart-container {
            height: 300px;
            position: relative;
        }

        .budget-progress {
            margin-top: 10px;
        }

        .progress-bar {
            height: 10px;
            background-color: var(--border);
            border-radius: 5px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            border-radius: 5px;
        }

        .progress-fill.good {
            background-color: var(--secondary);
        }

        .progress-fill.warning {
            background-color: var(--accent);
        }

        .progress-fill.danger {
            background-color: var(--danger);
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            background-color: var(--card);
            border-radius: 8px;
            width: 90%;
            max-width: 600px;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }

        .modal-header {
            padding: 15px 20px;
            border-bottom: 1px solid var(--border);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .modal-title {
            font-size: 20px;
            font-weight: 500;
        }

        .modal-close {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: var(--text-light);
        }

        .modal-body {
            padding: 20px;
        }

        .modal-footer {
            padding: 15px 20px;
            border-top: 1px solid var(--border);
            display: flex;
            justify-content: flex-end;
            gap: 10px;
        }

        .section {
            display: none;
        }

        .section.active {
            display: block;
        }

        .empty-state {
            text-align: center;
            padding: 40px 20px;
            color: var(--text-light);
        }

        .empty-state .material-icons {
            font-size: 48px;
            margin-bottom: 15px;
            color: var(--border);
        }

        .filter-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            flex-wrap: wrap;
            gap: 10px;
        }

        .search-box {
            display: flex;
            align-items: center;
            background-color: var(--card);
            border: 1px solid var(--border);
            border-radius: 4px;
            padding: 5px 10px;
            width: 250px;
        }

        .search-box .material-icons {
            color: var(--text-light);
            margin-right: 5px;
        }

        .search-box input {
            border: none;
            background: none;
            outline: none;
            width: 100%;
        }

        .filter-select {
            padding: 8px 10px;
            border: 1px solid var(--border);
            border-radius: 4px;
            background-color: var(--card);
        }

        .toast {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: var(--card);
            color: var(--text);
            padding: 15px 20px;
            border-radius: 4px;
            box-shadow: var(--shadow);
            display: flex;
            align-items: center;
            z-index: 1001;
            transform: translateY(100px);
            opacity: 0;
            transition: transform 0.3s, opacity 0.3s;
        }

        .toast.show {
            transform: translateY(0);
            opacity: 1;
        }

        .toast.success {
            border-left: 4px solid var(--secondary);
        }

        .toast.error {
            border-left: 4px solid var(--danger);
        }

        .toast .material-icons {
            margin-right: 10px;
        }

        .toast.success .material-icons {
            color: var(--secondary);
        }

        .toast.error .material-icons {
            color: var(--danger);
        }

        .loan-details {
            margin-top: 15px;
        }

        .loan-details h4 {
            margin-bottom: 10px;
            font-size: 16px;
        }

        .loan-details p {
            margin-bottom: 5px;
            font-size: 14px;
        }

        .amortization-table {
            margin-top: 20px;
            max-height: 300px;
            overflow-y: auto;
        }

        .import-export {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        .file-input {
            display: none;
        }

        .file-label {
            display: inline-flex;
            align-items: center;
            background-color: var(--primary);
            color: white;
            padding: 10px 15px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 500;
            transition: background-color 0.3s;
        }

        .file-label:hover {
            background-color: var(--primary-dark);
        }

        .file-label .material-icons {
            font-size: 18px;
            margin-right: 5px;
        }

        .currency-info {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 10px;
            font-size: 14px;
            color: var(--text-light);
        }

        .currency-rate {
            font-weight: 500;
        }

        .currency-converter {
            background-color: var(--card);
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 20px;
            box-shadow: var(--shadow);
        }

        .converter-form {
            display: flex;
            gap: 15px;
            align-items: flex-end;
            flex-wrap: wrap;
        }

        .converter-group {
            flex: 1;
            min-width: 150px;
        }

        .converter-result {
            margin-top: 15px;
            padding: 15px;
            background-color: var(--background);
            border-radius: 4px;
            text-align: center;
            font-size: 18px;
            font-weight: 500;
        }

        @media (max-width: 768px) {
            .dashboard-grid {
                grid-template-columns: 1fr;
            }
            
            .stats-grid {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .filter-bar {
                flex-direction: column;
                align-items: stretch;
            }
            
            .search-box {
                width: 100%;
            }
            
            .converter-form {
                flex-direction: column;
            }
            
            .login-card {
                margin: 20px;
                padding: 30px 20px;
            }
        }
    </style>
</head>
<body>
    <!-- Login Page -->
    <div id="login-page" class="login-container">
        <div class="login-card">
            <div class="login-logo">
                <span class="material-icons">account_balance_wallet</span>
            </div>
            <h1 class="login-title">Personal Finance Manager</h1>
            <p class="login-subtitle">Please login to access your financial dashboard</p>
            
            <form id="login-form">
                <div class="form-group">
                    <label for="username">Username</label>
                    <input type="text" id="username" class="form-control" placeholder="Enter your username" required>
                </div>
                <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" id="password" class="form-control" placeholder="Enter your password" required>
                </div>
                <button type="submit" class="btn">Login</button>
                <div class="error-message" id="login-error">Invalid username or password</div>
            </form>
            
            <div class="login-footer">
                <p>© 2023 Personal Finance Manager. All rights reserved.</p>
            </div>
        </div>
    </div>

    <!-- Main Application (hidden until login) -->
    <div id="app" class="app-container">
        <header>
            <div class="header-content">
                <div class="logo">
                    <span class="material-icons">account_balance_wallet</span>
                    Personal Finance Manager
                </div>
                <div class="user-info">
                    <span class="material-icons">account_circle</span>
                    <span id="username">pmistri</span>
                    <div class="currency-selector">
                        <span class="material-icons">currency_exchange</span>
                        <select id="currency-selector">
                            <option value="USD">USD</option>
                            <option value="EUR">EUR</option>
                            <option value="GBP">GBP</option>
                            <option value="JPY">JPY</option>
                            <option value="CAD">CAD</option>
                            <option value="AUD">AUD</option>
                            <option value="INR">INR</option>
                        </select>
                    </div>
                    <button class="logout-btn" id="logout-btn">
                        <span class="material-icons">logout</span>
                        Logout
                    </button>
                </div>
            </div>
        </header>

        <nav>
            <div class="nav-container">
                <a href="#" class="nav-item active" data-section="dashboard">Dashboard</a>
                <a href="#" class="nav-item" data-section="income">Income</a>
                <a href="#" class="nav-item" data-section="expenditure">Expenditure</a>
                <a href="#" class="nav-item" data-section="loans">Loans</a>
                <a href="#" class="nav-item" data-section="budgets">Budgets</a>
                <a href="#" class="nav-item" data-section="reports">Reports</a>
                <a href="#" class="nav-item" data-section="settings">Settings</a>
            </div>
        </nav>

        <div class="container">
            <div class="main-content">
                <!-- Currency Converter -->
                <div class="currency-converter" id="currency-converter">
                    <div class="card-header">
                        <h3 class="card-title">Currency Converter</h3>
                    </div>
                    <div class="currency-info">
                        <span>Base Currency: <span class="currency-rate" id="base-currency-info">USD</span></span>
                        <span>Last Updated: <span class="currency-rate" id="last-updated">Never</span></span>
                    </div>
                    <div class="converter-form">
                        <div class="converter-group">
                            <label for="convert-from">From</label>
                            <select id="convert-from" class="form-control">
                                <option value="USD">USD</option>
                                <option value="EUR">EUR</option>
                                <option value="GBP">GBP</option>
                                <option value="JPY">JPY</option>
                                <option value="CAD">CAD</option>
                                <option value="AUD">AUD</option>
                                <option value="INR">INR</option>
                            </select>
                        </div>
                        <div class="converter-group">
                            <label for="convert-amount">Amount</label>
                            <input type="number" id="convert-amount" class="form-control" value="1" min="0" step="0.01">
                        </div>
                        <div class="converter-group">
                            <label for="convert-to">To</label>
                            <select id="convert-to" class="form-control">
                                <option value="USD">USD</option>
                                <option value="EUR">EUR</option>
                                <option value="GBP">GBP</option>
                                <option value="JPY">JPY</option>
                                <option value="CAD">CAD</option>
                                <option value="AUD">AUD</option>
                                <option value="INR">INR</option>
                            </select>
                        </div>
                        <div class="converter-group">
                            <button class="btn" id="convert-btn">Convert</button>
                        </div>
                    </div>
                    <div class="converter-result" id="converter-result">
                        Enter amount and click Convert
                    </div>
                </div>

                <!-- Dashboard Section -->
                <div id="dashboard" class="section active">
                    <div class="stats-grid">
                        <div class="stat-card income">
                            <div class="stat-label">Monthly Income</div>
                            <div class="stat-value" id="monthly-income">$0.00</div>
                        </div>
                        <div class="stat-card expense">
                            <div class="stat-label">Monthly Expenses</div>
                            <div class="stat-value" id="monthly-expenses">$0.00</div>
                        </div>
                        <div class="stat-card savings">
                            <div class="stat-label">Monthly Savings</div>
                            <div class="stat-value" id="monthly-savings">$0.00</div>
                        </div>
                        <div class="stat-card net-worth">
                            <div class="stat-label">Net Worth</div>
                            <div class="stat-value" id="net-worth">$0.00</div>
                        </div>
                    </div>

                    <div class="dashboard-grid">
                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">Income vs Expenses</h3>
                            </div>
                            <div class="chart-container">
                                <canvas id="income-expense-chart"></canvas>
                            </div>
                        </div>

                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">Expense Categories</h3>
                            </div>
                            <div class="chart-container">
                                <canvas id="expense-categories-chart"></canvas>
                            </div>
                        </div>

                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">Budget Status</h3>
                            </div>
                            <div id="budget-status-container">
                                <div class="empty-state">
                                    <span class="material-icons">pie_chart</span>
                                    <p>No budgets set up yet</p>
                                </div>
                            </div>
                        </div>

                        <div class="card">
                            <div class="card-header">
                                <h3 class="card-title">Recent Transactions</h3>
                            </div>
                            <div id="recent-transactions">
                                <div class="empty-state">
                                    <span class="material-icons">receipt_long</span>
                                    <p>No recent transactions</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Income Section -->
                <div id="income" class="section">
                    <div class="card">
                        <div class="card-header">
                            <h3 class="card-title">Income Sources</h3>
                            <button class="btn" id="add-income-btn">
                                <span class="material-icons">add</span>
                                Add Income
                            </button>
                        </div>
                        <div class="filter-bar">
                            <div class="search-box">
                                <span class="material-icons">search</span>
                                <input type="text" placeholder="Search income..." id="income-search">
                            </div>
                            <select class="filter-select" id="income-filter">
                                <option value="all">All Types</option>
                                <option value="salary">Salary</option>
                                <option value="freelance">Freelance</option>
                                <option value="investment">Investment</option>
                                <option value="rental">Rental</option>
                                <option value="other">Other</option>
                            </select>
                        </div>
                        <div class="table-container">
                            <table class="table" id="income-table">
                                <thead>
                                    <tr>
                                        <th>Source</th>
                                        <th>Type</th>
                                        <th>Amount</th>
                                        <th>Frequency</th>
                                        <th>Category</th>
                                        <th>Actions</th>
                                    </tr>
                                </thead>
                                <tbody id="income-tbody">
                                    <!-- Income rows will be added here -->
                                </tbody>
                            </table>
                            <div class="empty-state" id="income-empty">
                                <span class="material-icons">payments</span>
                                <p>No income sources added yet</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Expenditure Section -->
                <div id="expenditure" class="section">
                    <div class="card">
                        <div class="card-header">
                            <h3 class="card-title">Expenses</h3>
                            <button class="btn" id="add-expense-btn">
                                <span class="material-icons">add</span>
                                Add Expense
                            </button>
                        </div>
                        <div class="filter-bar">
                            <div class="search-box">
                                <span class="material-icons">search</span>
                                <input type="text" placeholder="Search expenses..." id="expense-search">
                            </div>
                            <select class="filter-select" id="expense-filter">
                                <option value="all">All Categories</option>
                                <option value="food">Food</option>
                                <option value="utilities">Utilities</option>
                                <option value="entertainment">Entertainment</option>
                                <option value="transportation">Transportation</option>
                                <option value="housing">Housing</option>
                                <option value="healthcare">Healthcare</option>
                                <option value="other">Other</option>
                            </select>
                        </div>
                        <div class="table-container">
                            <table class="table" id="expense-table">
                                <thead>
                                    <tr>
                                        <th>Description</th>
                                        <th>Category</th>
                                        <th>Amount</th>
                                        <th>Date</th>
                                        <th>Payment Method</th>
                                        <th>Actions</th>
                                    </tr>
                                </thead>
                                <tbody id="expense-tbody">
                                    <!-- Expense rows will be added here -->
                                </tbody>
                            </table>
                            <div class="empty-state" id="expense-empty">
                                <span class="material-icons">shopping_cart</span>
                                <p>No expenses recorded yet</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Loans Section -->
                <div id="loans" class="section">
                    <div class="card">
                        <div class="card-header">
                            <h3 class="card-title">Loans</h3>
                            <button class="btn" id="add-loan-btn">
                                <span class="material-icons">add</span>
                                Add Loan
                            </button>
                        </div>
                        <div class="table-container">
                            <table class="table" id="loan-table">
                                <thead>
                                    <tr>
                                        <th>Lender</th>
                                        <th>Type</th>
                                        <th>Principal</th>
                                        <th>Interest Rate</th>
                                        <th>EMI</th>
                                        <th>End Date</th>
                                        <th>Actions</th>
                                    </tr>
                                </thead>
                                <tbody id="loan-tbody">
                                    <!-- Loan rows will be added here -->
                                </tbody>
                            </table>
                            <div class="empty-state" id="loan-empty">
                                <span class="material-icons">account_balance</span>
                                <p>No loans recorded yet</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Budgets Section -->
                <div id="budgets" class="section">
                    <div class="card">
                        <div class="card-header">
                            <h3 class="card-title">Budgets</h3>
                            <button class="btn" id="add-budget-btn">
                                <span class="material-icons">add</span>
                                Add Budget
                            </button>
                        </div>
                        <div class="table-container">
                            <table class="table" id="budget-table">
                                <thead>
                                    <tr>
                                        <th>Category</th>
                                        <th>Budget Amount</th>
                                        <th>Spent</th>
                                        <th>Remaining</th>
                                        <th>Progress</th>
                                        <th>Actions</th>
                                    </tr>
                                </thead>
                                <tbody id="budget-tbody">
                                    <!-- Budget rows will be added here -->
                                </tbody>
                            </table>
                            <div class="empty-state" id="budget-empty">
                                <span class="material-icons">savings</span>
                                <p>No budgets set up yet</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Reports Section -->
                <div id="reports" class="section">
                    <div class="card">
                        <div class="card-header">
                            <h3 class="card-title">Financial Reports</h3>
                        </div>
                        <div class="import-export">
                            <label for="import-csv" class="file-label">
                                <span class="material-icons">file_upload</span>
                                Import CSV
                            </label>
                            <input type="file" id="import-csv" class="file-input" accept=".csv">
                            <button class="btn" id="export-csv-btn">
                                <span class="material-icons">file_download</span>
                                Export CSV
                            </button>
                        </div>
                        <div class="dashboard-grid">
                            <div class="card">
                                <div class="card-header">
                                    <h3 class="card-title">Income Report</h3>
                                </div>
                                <div class="chart-container">
                                    <canvas id="income-report-chart"></canvas>
                                </div>
                            </div>
                            <div class="card">
                                <div class="card-header">
                                    <h3 class="card-title">Expense Report</h3>
                                </div>
                                <div class="chart-container">
                                    <canvas id="expense-report-chart"></canvas>
                                </div>
                            </div>
                            <div class="card">
                                <div class="card-header">
                                    <h3 class="card-title">Cash Flow</h3>
                                </div>
                                <div class="chart-container">
                                    <canvas id="cash-flow-chart"></canvas>
                                </div>
                            </div>
                            <div class="card">
                                <div class="card-header">
                                    <h3 class="card-title">Net Worth Trend</h3>
                                </div>
                                <div class="chart-container">
                                    <canvas id="net-worth-chart"></canvas>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Settings Section -->
                <div id="settings" class="section">
                    <div class="card">
                        <div class="card-header">
                            <h3 class="card-title">Account Settings</h3>
                        </div>
                        <div class="form-group">
                            <label for="name">Full Name</label>
                            <input type="text" id="name" class="form-control" value="Guest User">
                        </div>
                        <div class="form-group">
                            <label for="email">Email</label>
                            <input type="email" id="email" class="form-control" value="guest@example.com">
                        </div>
                        <div class="form-group">
                            <label for="currency">Default Currency</label>
                            <select id="currency" class="form-control">
                                <option value="USD">US Dollar (USD)</option>
                                <option value="EUR">Euro (EUR)</option>
                                <option value="GBP">British Pound (GBP)</option>
                                <option value="JPY">Japanese Yen (JPY)</option>
                                <option value="CAD">Canadian Dollar (CAD)</option>
                                <option value="AUD">Australian Dollar (AUD)</option>
                                <option value="INR">Indian Rupee (INR)</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label>
                                <input type="checkbox" id="auto-update-rates" checked> Auto-update exchange rates
                            </label>
                        </div>
                        <div class="form-group">
                            <button class="btn" id="save-settings-btn">Save Changes</button>
                            <button class="btn btn-secondary" id="update-rates-btn">Update Exchange Rates Now</button>
                        </div>
                    </div>
                    <div class="card">
                        <div class="card-header">
                            <h3 class="card-title">Data Management</h3>
                        </div>
                        <div class="form-group">
                            <button class="btn btn-danger" id="clear-data-btn">Clear All Data</button>
                            <p class="text-light" style="margin-top: 10px; font-size: 14px;">
                                This will permanently delete all your financial data. This action cannot be undone.
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Income Modal -->
    <div id="income-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title" id="income-modal-title">Add Income</h3>
                <button class="modal-close">&times;</button>
            </div>
            <div class="modal-body">
                <form id="income-form">
                    <input type="hidden" id="income-id">
                    <div class="form-group">
                        <label for="income-source">Source Name</label>
                        <input type="text" id="income-source" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="income-type">Income Type</label>
                        <select id="income-type" class="form-control" required>
                            <option value="salary">Salary</option>
                            <option value="freelance">Freelance</option>
                            <option value="investment">Investment</option>
                            <option value="rental">Rental</option>
                            <option value="other">Other</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="income-amount">Amount</label>
                        <input type="number" id="income-amount" class="form-control" min="0" step="0.01" required>
                    </div>
                    <div class="form-group">
                        <label for="income-currency">Currency</label>
                        <select id="income-currency" class="form-control" required>
                            <option value="USD">USD</option>
                            <option value="EUR">EUR</option>
                            <option value="GBP">GBP</option>
                            <option value="JPY">JPY</option>
                            <option value="CAD">CAD</option>
                            <option value="AUD">AUD</option>
                            <option value="INR">INR</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="income-frequency">Frequency</label>
                        <select id="income-frequency" class="form-control" required>
                            <option value="weekly">Weekly</option>
                            <option value="bi-weekly">Bi-weekly</option>
                            <option value="monthly">Monthly</option>
                            <option value="quarterly">Quarterly</option>
                            <option value="yearly">Yearly</option>
                            <option value="one-time">One-time</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="income-start-date">Start Date</label>
                        <input type="date" id="income-start-date" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="income-end-date">End Date (if applicable)</label>
                        <input type="date" id="income-end-date" class="form-control">
                    </div>
                    <div class="form-group">
                        <label for="income-category">Category</label>
                        <select id="income-category" class="form-control" required>
                            <option value="active">Active Income</option>
                            <option value="passive">Passive Income</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="income-taxes">Taxes/Deductions</label>
                        <input type="number" id="income-taxes" class="form-control" min="0" step="0.01" value="0">
                    </div>
                    <div class="form-group">
                        <label for="income-description">Description</label>
                        <textarea id="income-description" class="form-control" rows="3"></textarea>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" id="cancel-income-btn">Cancel</button>
                <button type="button" class="btn" id="save-income-btn">Save</button>
            </div>
        </div>
    </div>

    <!-- Expense Modal -->
    <div id="expense-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title" id="expense-modal-title">Add Expense</h3>
                <button class="modal-close">&times;</button>
            </div>
            <div class="modal-body">
                <form id="expense-form">
                    <input type="hidden" id="expense-id">
                    <div class="form-group">
                        <label for="expense-description">Description</label>
                        <input type="text" id="expense-description" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="expense-category">Category</label>
                        <select id="expense-category" class="form-control" required>
                            <option value="food">Food</option>
                            <option value="utilities">Utilities</option>
                            <option value="entertainment">Entertainment</option>
                            <option value="transportation">Transportation</option>
                            <option value="housing">Housing</option>
                            <option value="healthcare">Healthcare</option>
                            <option value="other">Other</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="expense-amount">Amount</label>
                        <input type="number" id="expense-amount" class="form-control" min="0" step="0.01" required>
                    </div>
                    <div class="form-group">
                        <label for="expense-currency">Currency</label>
                        <select id="expense-currency" class="form-control" required>
                            <option value="USD">USD</option>
                            <option value="EUR">EUR</option>
                            <option value="GBP">GBP</option>
                            <option value="JPY">JPY</option>
                            <option value="CAD">CAD</option>
                            <option value="AUD">AUD</option>
                            <option value="INR">INR</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="expense-date">Date</label>
                        <input type="date" id="expense-date" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="expense-payment-method">Payment Method</label>
                        <select id="expense-payment-method" class="form-control" required>
                            <option value="cash">Cash</option>
                            <option value="credit-card">Credit Card</option>
                            <option value="debit-card">Debit Card</option>
                            <option value="bank-transfer">Bank Transfer</option>
                            <option value="digital-wallet">Digital Wallet</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="expense-recurrence">Recurrence</label>
                        <select id="expense-recurrence" class="form-control">
                            <option value="one-time">One-time</option>
                            <option value="daily">Daily</option>
                            <option value="weekly">Weekly</option>
                            <option value="monthly">Monthly</option>
                            <option value="yearly">Yearly</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="expense-tags">Tags (comma separated)</label>
                        <input type="text" id="expense-tags" class="form-control" placeholder="e.g. essential, groceries">
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" id="cancel-expense-btn">Cancel</button>
                <button type="button" class="btn" id="save-expense-btn">Save</button>
            </div>
        </div>
    </div>

    <!-- Loan Modal -->
    <div id="loan-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title" id="loan-modal-title">Add Loan</h3>
                <button class="modal-close">&times;</button>
            </div>
            <div class="modal-body">
                <form id="loan-form">
                    <input type="hidden" id="loan-id">
                    <div class="form-group">
                        <label for="loan-lender">Lender Name</label>
                        <input type="text" id="loan-lender" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="loan-type">Loan Type</label>
                        <select id="loan-type" class="form-control" required>
                            <option value="personal">Personal Loan</option>
                            <option value="home">Home Loan</option>
                            <option value="car">Car Loan</option>
                            <option value="student">Student Loan</option>
                            <option value="other">Other</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="loan-principal">Principal Amount</label>
                        <input type="number" id="loan-principal" class="form-control" min="0" step="0.01" required>
                    </div>
                    <div class="form-group">
                        <label for="loan-currency">Currency</label>
                        <select id="loan-currency" class="form-control" required>
                            <option value="USD">USD</option>
                            <option value="EUR">EUR</option>
                            <option value="GBP">GBP</option>
                            <option value="JPY">JPY</option>
                            <option value="CAD">CAD</option>
                            <option value="AUD">AUD</option>
                            <option value="INR">INR</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="loan-interest-rate">Interest Rate (%)</label>
                        <input type="number" id="loan-interest-rate" class="form-control" min="0" step="0.01" required>
                    </div>
                    <div class="form-group">
                        <label for="loan-interest-type">Interest Type</label>
                        <select id="loan-interest-type" class="form-control" required>
                            <option value="fixed">Fixed</option>
                            <option value="variable">Variable</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="loan-start-date">Start Date</label>
                        <input type="date" id="loan-start-date" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="loan-end-date">End Date</label>
                        <input type="date" id="loan-end-date" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="loan-repayment-frequency">Repayment Frequency</label>
                        <select id="loan-repayment-frequency" class="form-control" required>
                            <option value="weekly">Weekly</option>
                            <option value="bi-weekly">Bi-weekly</option>
                            <option value="monthly">Monthly</option>
                            <option value="quarterly">Quarterly</option>
                        </select>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" id="cancel-loan-btn">Cancel</button>
                <button type="button" class="btn" id="save-loan-btn">Save</button>
            </div>
        </div>
    </div>

    <!-- Budget Modal -->
    <div id="budget-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title" id="budget-modal-title">Add Budget</h3>
                <button class="modal-close">&times;</button>
            </div>
            <div class="modal-body">
                <form id="budget-form">
                    <input type="hidden" id="budget-id">
                    <div class="form-group">
                        <label for="budget-category">Category</label>
                        <select id="budget-category" class="form-control" required>
                            <option value="food">Food</option>
                            <option value="utilities">Utilities</option>
                            <option value="entertainment">Entertainment</option>
                            <option value="transportation">Transportation</option>
                            <option value="housing">Housing</option>
                            <option value="healthcare">Healthcare</option>
                            <option value="other">Other</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="budget-amount">Budget Amount</label>
                        <input type="number" id="budget-amount" class="form-control" min="0" step="0.01" required>
                    </div>
                    <div class="form-group">
                        <label for="budget-currency">Currency</label>
                        <select id="budget-currency" class="form-control" required>
                            <option value="USD">USD</option>
                            <option value="EUR">EUR</option>
                            <option value="GBP">GBP</option>
                            <option value="JPY">JPY</option>
                            <option value="CAD">CAD</option>
                            <option value="AUD">AUD</option>
                            <option value="INR">INR</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label for="budget-period">Period</label>
                        <select id="budget-period" class="form-control" required>
                            <option value="monthly">Monthly</option>
                            <option value="yearly">Yearly</option>
                        </select>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" id="cancel-budget-btn">Cancel</button>
                <button type="button" class="btn" id="save-budget-btn">Save</button>
            </div>
        </div>
    </div>

    <!-- Loan Details Modal -->
    <div id="loan-details-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title">Loan Details</h3>
                <button class="modal-close">&times;</button>
            </div>
            <div class="modal-body">
                <div id="loan-details-content">
                    <!-- Loan details will be populated here -->
                </div>
                <div class="amortization-table">
                    <h4>Amortization Schedule</h4>
                    <table class="table">
                        <thead>
                            <tr>
                                <th>Payment Date</th>
                                <th>Payment</th>
                                <th>Principal</th>
                                <th>Interest</th>
                                <th>Balance</th>
                            </tr>
                        </thead>
                        <tbody id="amortization-tbody">
                            <!-- Amortization rows will be added here -->
                        </tbody>
                    </table>
                </div>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-secondary" id="close-loan-details-btn">Close</button>
            </div>
        </div>
    </div>

    <!-- Toast Notification -->
    <div id="toast" class="toast">
        <span class="material-icons" id="toast-icon"></span>
        <span id="toast-message"></span>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script>
        // Login credentials
        const VALID_USERNAME = "pmistri";
        const VALID_PASSWORD = "Yayati@1993";

        // Check if user is logged in
        function checkLogin() {
            const isLoggedIn = localStorage.getItem('isLoggedIn');
            if (isLoggedIn === 'true') {
                showApp();
            } else {
                showLoginPage();
            }
        }

        // Show login page
        function showLoginPage() {
            document.getElementById('login-page').style.display = 'flex';
            document.getElementById('app').style.display = 'none';
        }

        // Show main app
        function showApp() {
            document.getElementById('login-page').style.display = 'none';
            document.getElementById('app').style.display = 'flex';
            initApp();
        }

        // Handle login form submission
        document.getElementById('login-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            const errorMessage = document.getElementById('login-error');
            
            if (username === VALID_USERNAME && password === VALID_PASSWORD) {
                // Successful login
                localStorage.setItem('isLoggedIn', 'true');
                showApp();
            } else {
                // Show error message
                errorMessage.style.display = 'block';
                
                // Clear password field
                document.getElementById('password').value = '';
                
                // Hide error after 3 seconds
                setTimeout(() => {
                    errorMessage.style.display = 'none';
                }, 3000);
            }
        });

        // Handle logout
        document.getElementById('logout-btn').addEventListener('click', function() {
            localStorage.removeItem('isLoggedIn');
            showLoginPage();
            
            // Clear login form
            document.getElementById('username').value = '';
            document.getElementById('password').value = '';
        });

        // Data storage
        let incomes = JSON.parse(localStorage.getItem('incomes')) || [];
        let expenses = JSON.parse(localStorage.getItem('expenses')) || [];
        let loans = JSON.parse(localStorage.getItem('loans')) || [];
        let budgets = JSON.parse(localStorage.getItem('budgets')) || [];
        let user = JSON.parse(localStorage.getItem('user')) || { 
            name: 'Guest User', 
            email: 'guest@example.com',
            currency: 'USD',
            autoUpdateRates: true
        };
        
        // Exchange rates storage
        let exchangeRates = JSON.parse(localStorage.getItem('exchangeRates')) || {};
        let lastRatesUpdate = localStorage.getItem('lastRatesUpdate') || null;
        let currentCurrency = localStorage.getItem('currentCurrency') || 'USD';

        // DOM elements
        const sections = document.querySelectorAll('.section');
        const navItems = document.querySelectorAll('.nav-item');
        const usernameEl = document.getElementById('username');
        const nameInput = document.getElementById('name');
        const emailInput = document.getElementById('email');
        const currencySelector = document.getElementById('currency-selector');
        const currencyConverter = document.getElementById('currency-converter');
        const baseCurrencyInfo = document.getElementById('base-currency-info');
        const lastUpdatedInfo = document.getElementById('last-updated');

        // Initialize app
        function initApp() {
            // Set user info
            usernameEl.textContent = VALID_USERNAME; // Show the logged-in username
            nameInput.value = user.name;
            emailInput.value = user.email;
            document.getElementById('currency').value = user.currency || 'USD';
            document.getElementById('auto-update-rates').checked = user.autoUpdateRates !== false;
            
            // Set currency selector
            currencySelector.value = currentCurrency;
            baseCurrencyInfo.textContent = user.currency || 'USD';
            
            // Update last updated info
            if (lastRatesUpdate) {
                const date = new Date(parseInt(lastRatesUpdate));
                lastUpdatedInfo.textContent = date.toLocaleString();
            }
            
            // Set up navigation
            navItems.forEach(item => {
                item.addEventListener('click', (e) => {
                    e.preventDefault();
                    const sectionId = item.getAttribute('data-section');
                    showSection(sectionId);
                    
                    // Update active nav item
                    navItems.forEach(nav => nav.classList.remove('active'));
                    item.classList.add('active');
                });
            });

            // Set up currency selector
            currencySelector.addEventListener('change', (e) => {
                currentCurrency = e.target.value;
                localStorage.setItem('currentCurrency', currentCurrency);
                updateDashboard();
                generateReports();
                showToast(`Currency changed to ${currentCurrency}`, 'success');
            });

            // Set up modals
            setupModals();

            // Set up forms
            setupForms();

            // Set up buttons
            setupButtons();

            // Set up currency converter
            setupCurrencyConverter();

            // Load exchange rates if needed
            if (user.autoUpdateRates && (!lastRatesUpdate || (Date.now() - parseInt(lastRatesUpdate)) > 24 * 60 * 60 * 1000)) {
                updateExchangeRates();
            }

            // Load data
            loadIncomes();
            loadExpenses();
            loadLoans();
            loadBudgets();
            updateDashboard();
            generateReports();
        }

        // Show section
        function showSection(sectionId) {
            sections.forEach(section => {
                section.classList.remove('active');
            });
            document.getElementById(sectionId).classList.add('active');
            
            // Hide currency converter on all sections except dashboard
            if (sectionId === 'dashboard') {
                currencyConverter.style.display = 'block';
            } else {
                currencyConverter.style.display = 'none';
            }
        }

        // Setup currency converter
        function setupCurrencyConverter() {
            const convertBtn = document.getElementById('convert-btn');
            const convertFrom = document.getElementById('convert-from');
            const convertTo = document.getElementById('convert-to');
            const convertAmount = document.getElementById('convert-amount');
            const converterResult = document.getElementById('converter-result');
            
            // Set default currencies
            convertFrom.value = user.currency || 'USD';
            convertTo.value = currentCurrency;
            
            convertBtn.addEventListener('click', () => {
                const from = convertFrom.value;
                const to = convertTo.value;
                const amount = parseFloat(convertAmount.value) || 0;
                
                if (from === to) {
                    converterResult.textContent = `${formatCurrency(amount, from)} = ${formatCurrency(amount, to)}`;
                    return;
                }
                
                if (!exchangeRates[from] || !exchangeRates[to]) {
                    showToast('Exchange rates not available for selected currencies', 'error');
                    return;
                }
                
                // Convert to USD first, then to target currency
                const amountInUSD = amount / exchangeRates[from];
                const convertedAmount = amountInUSD * exchangeRates[to];
                
                converterResult.textContent = `${formatCurrency(amount, from)} = ${formatCurrency(convertedAmount, to)}`;
            });
            
            // Auto-convert when amount changes
            convertAmount.addEventListener('input', () => {
                if (convertAmount.value) {
                    convertBtn.click();
                }
            });
        }

        // Update exchange rates
        async function updateExchangeRates() {
            try {
                showToast('Updating exchange rates...', 'success');
                
                // Using a free exchange rate API (without API key for demo purposes)
                const response = await fetch('https://open.er-api.com/v6/latest/USD');
                const data = await response.json();
                
                if (data.result === 'success') {
                    exchangeRates = data.rates;
                    localStorage.setItem('exchangeRates', JSON.stringify(exchangeRates));
                    lastRatesUpdate = Date.now().toString();
                    localStorage.setItem('lastRatesUpdate', lastRatesUpdate);
                    
                    // Update UI
                    const date = new Date(parseInt(lastRatesUpdate));
                    lastUpdatedInfo.textContent = date.toLocaleString();
                    
                    showToast('Exchange rates updated successfully', 'success');
                    
                    // Refresh dashboard and reports with new rates
                    updateDashboard();
                    generateReports();
                } else {
                    showToast('Failed to update exchange rates', 'error');
                }
            } catch (error) {
                console.error('Error updating exchange rates:', error);
                showToast('Failed to update exchange rates', 'error');
            }
        }

        // Format currency with conversion
        function formatCurrency(amount, currency = null) {
            const targetCurrency = currency || currentCurrency;
            const baseCurrency = user.currency || 'USD';
            
            // If amount is already in target currency, no conversion needed
            if (baseCurrency === targetCurrency) {
                return new Intl.NumberFormat(undefined, {
                    style: 'currency',
                    currency: targetCurrency,
                    minimumFractionDigits: 2
                }).format(amount);
            }
            
            // Convert to target currency if exchange rates are available
            if (exchangeRates[baseCurrency] && exchangeRates[targetCurrency]) {
                const amountInUSD = amount / exchangeRates[baseCurrency];
                const convertedAmount = amountInUSD * exchangeRates[targetCurrency];
                
                return new Intl.NumberFormat(undefined, {
                    style: 'currency',
                    currency: targetCurrency,
                    minimumFractionDigits: 2
                }).format(convertedAmount);
            }
            
            // Fallback to original currency if conversion not possible
            return new Intl.NumberFormat(undefined, {
                style: 'currency',
                currency: baseCurrency,
                minimumFractionDigits: 2
            }).format(amount);
        }

        // Setup modals
        function setupModals() {
            // Income modal
            const incomeModal = document.getElementById('income-modal');
            const addIncomeBtn = document.getElementById('add-income-btn');
            const cancelIncomeBtn = document.getElementById('cancel-income-btn');
            const saveIncomeBtn = document.getElementById('save-income-btn');
            const incomeModalClose = incomeModal.querySelector('.modal-close');

            addIncomeBtn.addEventListener('click', () => {
                openIncomeModal();
            });

            cancelIncomeBtn.addEventListener('click', () => {
                closeIncomeModal();
            });

            incomeModalClose.addEventListener('click', () => {
                closeIncomeModal();
            });

            saveIncomeBtn.addEventListener('click', () => {
                saveIncome();
            });

            // Expense modal
            const expenseModal = document.getElementById('expense-modal');
            const addExpenseBtn = document.getElementById('add-expense-btn');
            const cancelExpenseBtn = document.getElementById('cancel-expense-btn');
            const saveExpenseBtn = document.getElementById('save-expense-btn');
            const expenseModalClose = expenseModal.querySelector('.modal-close');

            addExpenseBtn.addEventListener('click', () => {
                openExpenseModal();
            });

            cancelExpenseBtn.addEventListener('click', () => {
                closeExpenseModal();
            });

            expenseModalClose.addEventListener('click', () => {
                closeExpenseModal();
            });

            saveExpenseBtn.addEventListener('click', () => {
                saveExpense();
            });

            // Loan modal
            const loanModal = document.getElementById('loan-modal');
            const addLoanBtn = document.getElementById('add-loan-btn');
            const cancelLoanBtn = document.getElementById('cancel-loan-btn');
            const saveLoanBtn = document.getElementById('save-loan-btn');
            const loanModalClose = loanModal.querySelector('.modal-close');

            addLoanBtn.addEventListener('click', () => {
                openLoanModal();
            });

            cancelLoanBtn.addEventListener('click', () => {
                closeLoanModal();
            });

            loanModalClose.addEventListener('click', () => {
                closeLoanModal();
            });

            saveLoanBtn.addEventListener('click', () => {
                saveLoan();
            });

            // Budget modal
            const budgetModal = document.getElementById('budget-modal');
            const addBudgetBtn = document.getElementById('add-budget-btn');
            const cancelBudgetBtn = document.getElementById('cancel-budget-btn');
            const saveBudgetBtn = document.getElementById('save-budget-btn');
            const budgetModalClose = budgetModal.querySelector('.modal-close');

            addBudgetBtn.addEventListener('click', () => {
                openBudgetModal();
            });

            cancelBudgetBtn.addEventListener('click', () => {
                closeBudgetModal();
            });

            budgetModalClose.addEventListener('click', () => {
                closeBudgetModal();
            });

            saveBudgetBtn.addEventListener('click', () => {
                saveBudget();
            });

            // Loan details modal
            const loanDetailsModal = document.getElementById('loan-details-modal');
            const closeLoanDetailsBtn = document.getElementById('close-loan-details-btn');
            const loanDetailsModalClose = loanDetailsModal.querySelector('.modal-close');

            closeLoanDetailsBtn.addEventListener('click', () => {
                closeLoanDetailsModal();
            });

            loanDetailsModalClose.addEventListener('click', () => {
                closeLoanDetailsModal();
            });
        }

        // Setup forms
        function setupForms() {
            // Income form
            const incomeForm = document.getElementById('income-form');
            incomeForm.addEventListener('submit', (e) => {
                e.preventDefault();
                saveIncome();
            });

            // Expense form
            const expenseForm = document.getElementById('expense-form');
            expenseForm.addEventListener('submit', (e) => {
                e.preventDefault();
                saveExpense();
            });

            // Loan form
            const loanForm = document.getElementById('loan-form');
            loanForm.addEventListener('submit', (e) => {
                e.preventDefault();
                saveLoan();
            });

            // Budget form
            const budgetForm = document.getElementById('budget-form');
            budgetForm.addEventListener('submit', (e) => {
                e.preventDefault();
                saveBudget();
            });
        }

        // Setup buttons
        function setupButtons() {
            // Clear data button
            const clearDataBtn = document.getElementById('clear-data-btn');
            clearDataBtn.addEventListener('click', () => {
                if (confirm('Are you sure you want to clear all data? This action cannot be undone.')) {
                    localStorage.removeItem('incomes');
                    localStorage.removeItem('expenses');
                    localStorage.removeItem('loans');
                    localStorage.removeItem('budgets');
                    incomes = [];
                    expenses = [];
                    loans = [];
                    budgets = [];
                    loadIncomes();
                    loadExpenses();
                    loadLoans();
                    loadBudgets();
                    updateDashboard();
                    generateReports();
                    showToast('All data cleared successfully', 'success');
                }
            });

            // Export CSV button
            const exportCsvBtn = document.getElementById('export-csv-btn');
            exportCsvBtn.addEventListener('click', () => {
                exportToCsv();
            });

            // Import CSV button
            const importCsvInput = document.getElementById('import-csv');
            importCsvInput.addEventListener('change', (e) => {
                const file = e.target.files[0];
                if (file) {
                    const reader = new FileReader();
                    reader.onload = (event) => {
                        try {
                            const data = parseCsv(event.target.result);
                            importData(data);
                            showToast('Data imported successfully', 'success');
                        } catch (error) {
                            showToast('Error importing data', 'error');
                        }
                    };
                    reader.readAsText(file);
                }
            });

            // Save settings button
            const saveSettingsBtn = document.getElementById('save-settings-btn');
            saveSettingsBtn.addEventListener('click', () => {
                user.name = document.getElementById('name').value;
                user.email = document.getElementById('email').value;
                user.currency = document.getElementById('currency').value;
                user.autoUpdateRates = document.getElementById('auto-update-rates').checked;
                
                localStorage.setItem('user', JSON.stringify(user));
                baseCurrencyInfo.textContent = user.currency;
                
                showToast('Settings saved successfully', 'success');
                
                // Update dashboard with new settings
                updateDashboard();
                generateReports();
            });

            // Update rates button
            const updateRatesBtn = document.getElementById('update-rates-btn');
            updateRatesBtn.addEventListener('click', () => {
                updateExchangeRates();
            });
        }

        // Income functions
        function openIncomeModal(incomeId = null) {
            const modal = document.getElementById('income-modal');
            const modalTitle = document.getElementById('income-modal-title');
            const form = document.getElementById('income-form');
            
            form.reset();
            
            if (incomeId) {
                const income = incomes.find(i => i.id === incomeId);
                if (income) {
                    modalTitle.textContent = 'Edit Income';
                    document.getElementById('income-id').value = income.id;
                    document.getElementById('income-source').value = income.source;
                    document.getElementById('income-type').value = income.type;
                    document.getElementById('income-amount').value = income.amount;
                    document.getElementById('income-currency').value = income.currency || user.currency;
                    document.getElementById('income-frequency').value = income.frequency;
                    document.getElementById('income-start-date').value = income.startDate;
                    document.getElementById('income-end-date').value = income.endDate || '';
                    document.getElementById('income-category').value = income.category;
                    document.getElementById('income-taxes').value = income.taxes || 0;
                    document.getElementById('income-description').value = income.description || '';
                }
            } else {
                modalTitle.textContent = 'Add Income';
                document.getElementById('income-id').value = '';
                document.getElementById('income-currency').value = user.currency;
                document.getElementById('income-start-date').value = new Date().toISOString().split('T')[0];
            }
            
            modal.style.display = 'flex';
        }

        function closeIncomeModal() {
            document.getElementById('income-modal').style.display = 'none';
        }

        function saveIncome() {
            const id = document.getElementById('income-id').value;
            const source = document.getElementById('income-source').value;
            const type = document.getElementById('income-type').value;
            const amount = parseFloat(document.getElementById('income-amount').value);
            const currency = document.getElementById('income-currency').value;
            const frequency = document.getElementById('income-frequency').value;
            const startDate = document.getElementById('income-start-date').value;
            const endDate = document.getElementById('income-end-date').value;
            const category = document.getElementById('income-category').value;
            const taxes = parseFloat(document.getElementById('income-taxes').value) || 0;
            const description = document.getElementById('income-description').value;

            if (!source || !amount || !frequency || !startDate || !category) {
                showToast('Please fill all required fields', 'error');
                return;
            }

            const income = {
                id: id || Date.now().toString(),
                source,
                type,
                amount,
                currency,
                frequency,
                startDate,
                endDate: endDate || null,
                category,
                taxes,
                description
            };

            if (id) {
                // Update existing income
                const index = incomes.findIndex(i => i.id === id);
                if (index !== -1) {
                    incomes[index] = income;
                }
            } else {
                // Add new income
                incomes.push(income);
            }

            localStorage.setItem('incomes', JSON.stringify(incomes));
            loadIncomes();
            updateDashboard();
            generateReports();
            closeIncomeModal();
            showToast(id ? 'Income updated successfully' : 'Income added successfully', 'success');
        }

        function loadIncomes() {
            const tbody = document.getElementById('income-tbody');
            const emptyState = document.getElementById('income-empty');
            const table = document.getElementById('income-table');
            
            tbody.innerHTML = '';
            
            if (incomes.length === 0) {
                table.style.display = 'none';
                emptyState.style.display = 'block';
                return;
            }
            
            table.style.display = 'table';
            emptyState.style.display = 'none';
            
            incomes.forEach(income => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${income.source}</td>
                    <td>${capitalizeFirst(income.type)}</td>
                    <td>${formatCurrency(income.amount, income.currency)}</td>
                    <td>${capitalizeFirst(income.frequency.replace('-', ' '))}</td>
                    <td>${capitalizeFirst(income.category)}</td>
                    <td>
                        <div class="table-actions">
                            <button class="icon-btn edit" onclick="openIncomeModal('${income.id}')">
                                <span class="material-icons">edit</span>
                            </button>
                            <button class="icon-btn delete" onclick="deleteIncome('${income.id}')">
                                <span class="material-icons">delete</span>
                            </button>
                        </div>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function deleteIncome(id) {
            if (confirm('Are you sure you want to delete this income?')) {
                incomes = incomes.filter(i => i.id !== id);
                localStorage.setItem('incomes', JSON.stringify(incomes));
                loadIncomes();
                updateDashboard();
                generateReports();
                showToast('Income deleted successfully', 'success');
            }
        }

        // Expense functions
        function openExpenseModal(expenseId = null) {
            const modal = document.getElementById('expense-modal');
            const modalTitle = document.getElementById('expense-modal-title');
            const form = document.getElementById('expense-form');
            
            form.reset();
            
            if (expenseId) {
                const expense = expenses.find(e => e.id === expenseId);
                if (expense) {
                    modalTitle.textContent = 'Edit Expense';
                    document.getElementById('expense-id').value = expense.id;
                    document.getElementById('expense-description').value = expense.description;
                    document.getElementById('expense-category').value = expense.category;
                    document.getElementById('expense-amount').value = expense.amount;
                    document.getElementById('expense-currency').value = expense.currency || user.currency;
                    document.getElementById('expense-date').value = expense.date;
                    document.getElementById('expense-payment-method').value = expense.paymentMethod;
                    document.getElementById('expense-recurrence').value = expense.recurrence;
                    document.getElementById('expense-tags').value = expense.tags ? expense.tags.join(', ') : '';
                }
            } else {
                modalTitle.textContent = 'Add Expense';
                document.getElementById('expense-id').value = '';
                document.getElementById('expense-currency').value = user.currency;
                document.getElementById('expense-date').value = new Date().toISOString().split('T')[0];
            }
            
            modal.style.display = 'flex';
        }

        function closeExpenseModal() {
            document.getElementById('expense-modal').style.display = 'none';
        }

        function saveExpense() {
            const id = document.getElementById('expense-id').value;
            const description = document.getElementById('expense-description').value;
            const category = document.getElementById('expense-category').value;
            const amount = parseFloat(document.getElementById('expense-amount').value);
            const currency = document.getElementById('expense-currency').value;
            const date = document.getElementById('expense-date').value;
            const paymentMethod = document.getElementById('expense-payment-method').value;
            const recurrence = document.getElementById('expense-recurrence').value;
            const tagsInput = document.getElementById('expense-tags').value;
            const tags = tagsInput ? tagsInput.split(',').map(tag => tag.trim()) : [];

            if (!description || !category || !amount || !date || !paymentMethod) {
                showToast('Please fill all required fields', 'error');
                return;
            }

            const expense = {
                id: id || Date.now().toString(),
                description,
                category,
                amount,
                currency,
                date,
                paymentMethod,
                recurrence,
                tags
            };

            if (id) {
                // Update existing expense
                const index = expenses.findIndex(e => e.id === id);
                if (index !== -1) {
                    expenses[index] = expense;
                }
            } else {
                // Add new expense
                expenses.push(expense);
            }

            localStorage.setItem('expenses', JSON.stringify(expenses));
            loadExpenses();
            updateDashboard();
            generateReports();
            closeExpenseModal();
            showToast(id ? 'Expense updated successfully' : 'Expense added successfully', 'success');
        }

        function loadExpenses() {
            const tbody = document.getElementById('expense-tbody');
            const emptyState = document.getElementById('expense-empty');
            const table = document.getElementById('expense-table');
            
            tbody.innerHTML = '';
            
            if (expenses.length === 0) {
                table.style.display = 'none';
                emptyState.style.display = 'block';
                return;
            }
            
            table.style.display = 'table';
            emptyState.style.display = 'none';
            
            expenses.forEach(expense => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${expense.description}</td>
                    <td>${capitalizeFirst(expense.category)}</td>
                    <td>${formatCurrency(expense.amount, expense.currency)}</td>
                    <td>${formatDate(expense.date)}</td>
                    <td>${capitalizeFirst(expense.paymentMethod.replace('-', ' '))}</td>
                    <td>
                        <div class="table-actions">
                            <button class="icon-btn edit" onclick="openExpenseModal('${expense.id}')">
                                <span class="material-icons">edit</span>
                            </button>
                            <button class="icon-btn delete" onclick="deleteExpense('${expense.id}')">
                                <span class="material-icons">delete</span>
                            </button>
                        </div>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function deleteExpense(id) {
            if (confirm('Are you sure you want to delete this expense?')) {
                expenses = expenses.filter(e => e.id !== id);
                localStorage.setItem('expenses', JSON.stringify(expenses));
                loadExpenses();
                updateDashboard();
                generateReports();
                showToast('Expense deleted successfully', 'success');
            }
        }

        // Loan functions
        function openLoanModal(loanId = null) {
            const modal = document.getElementById('loan-modal');
            const modalTitle = document.getElementById('loan-modal-title');
            const form = document.getElementById('loan-form');
            
            form.reset();
            
            if (loanId) {
                const loan = loans.find(l => l.id === loanId);
                if (loan) {
                    modalTitle.textContent = 'Edit Loan';
                    document.getElementById('loan-id').value = loan.id;
                    document.getElementById('loan-lender').value = loan.lender;
                    document.getElementById('loan-type').value = loan.type;
                    document.getElementById('loan-principal').value = loan.principal;
                    document.getElementById('loan-currency').value = loan.currency || user.currency;
                    document.getElementById('loan-interest-rate').value = loan.interestRate;
                    document.getElementById('loan-interest-type').value = loan.interestType;
                    document.getElementById('loan-start-date').value = loan.startDate;
                    document.getElementById('loan-end-date').value = loan.endDate;
                    document.getElementById('loan-repayment-frequency').value = loan.repaymentFrequency;
                }
            } else {
                modalTitle.textContent = 'Add Loan';
                document.getElementById('loan-id').value = '';
                document.getElementById('loan-currency').value = user.currency;
                document.getElementById('loan-start-date').value = new Date().toISOString().split('T')[0];
            }
            
            modal.style.display = 'flex';
        }

        function closeLoanModal() {
            document.getElementById('loan-modal').style.display = 'none';
        }

        function saveLoan() {
            const id = document.getElementById('loan-id').value;
            const lender = document.getElementById('loan-lender').value;
            const type = document.getElementById('loan-type').value;
            const principal = parseFloat(document.getElementById('loan-principal').value);
            const currency = document.getElementById('loan-currency').value;
            const interestRate = parseFloat(document.getElementById('loan-interest-rate').value);
            const interestType = document.getElementById('loan-interest-type').value;
            const startDate = document.getElementById('loan-start-date').value;
            const endDate = document.getElementById('loan-end-date').value;
            const repaymentFrequency = document.getElementById('loan-repayment-frequency').value;

            if (!lender || !type || !principal || !interestRate || !startDate || !endDate || !repaymentFrequency) {
                showToast('Please fill all required fields', 'error');
                return;
            }

            // Calculate amortization
            const amortization = calculateAmortization(principal, interestRate, startDate, endDate, repaymentFrequency);
            
            const loan = {
                id: id || Date.now().toString(),
                lender,
                type,
                principal,
                currency,
                interestRate,
                interestType,
                startDate,
                endDate,
                repaymentFrequency,
                emi: amortization.emi,
                totalInterest: amortization.totalInterest,
                repaymentSchedule: amortization.schedule
            };

            if (id) {
                // Update existing loan
                const index = loans.findIndex(l => l.id === id);
                if (index !== -1) {
                    loans[index] = loan;
                }
            } else {
                // Add new loan
                loans.push(loan);
            }

            localStorage.setItem('loans', JSON.stringify(loans));
            loadLoans();
            updateDashboard();
            generateReports();
            closeLoanModal();
            showToast(id ? 'Loan updated successfully' : 'Loan added successfully', 'success');
        }

        function loadLoans() {
            const tbody = document.getElementById('loan-tbody');
            const emptyState = document.getElementById('loan-empty');
            const table = document.getElementById('loan-table');
            
            tbody.innerHTML = '';
            
            if (loans.length === 0) {
                table.style.display = 'none';
                emptyState.style.display = 'block';
                return;
            }
            
            table.style.display = 'table';
            emptyState.style.display = 'none';
            
            loans.forEach(loan => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${loan.lender}</td>
                    <td>${capitalizeFirst(loan.type)}</td>
                    <td>${formatCurrency(loan.principal, loan.currency)}</td>
                    <td>${loan.interestRate}%</td>
                    <td>${formatCurrency(loan.emi, loan.currency)}</td>
                    <td>${formatDate(loan.endDate)}</td>
                    <td>
                        <div class="table-actions">
                            <button class="icon-btn edit" onclick="openLoanModal('${loan.id}')">
                                <span class="material-icons">edit</span>
                            </button>
                            <button class="icon-btn delete" onclick="deleteLoan('${loan.id}')">
                                <span class="material-icons">delete</span>
                            </button>
                            <button class="icon-btn" onclick="showLoanDetails('${loan.id}')">
                                <span class="material-icons">visibility</span>
                            </button>
                        </div>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function deleteLoan(id) {
            if (confirm('Are you sure you want to delete this loan?')) {
                loans = loans.filter(l => l.id !== id);
                localStorage.setItem('loans', JSON.stringify(loans));
                loadLoans();
                updateDashboard();
                generateReports();
                showToast('Loan deleted successfully', 'success');
            }
        }

        function showLoanDetails(id) {
            const loan = loans.find(l => l.id === id);
            if (!loan) return;
            
            const modal = document.getElementById('loan-details-modal');
            const detailsContent = document.getElementById('loan-details-content');
            const amortizationTbody = document.getElementById('amortization-tbody');
            
            detailsContent.innerHTML = `
                <div class="loan-details">
                    <h4>${loan.type} Loan</h4>
                    <p><strong>Lender:</strong> ${loan.lender}</p>
                    <p><strong>Principal:</strong> ${formatCurrency(loan.principal, loan.currency)}</p>
                    <p><strong>Interest Rate:</strong> ${loan.interestRate}% (${loan.interestType})</p>
                    <p><strong>EMI:</strong> ${formatCurrency(loan.emi, loan.currency)}</p>
                    <p><strong>Total Interest:</strong> ${formatCurrency(loan.totalInterest, loan.currency)}</p>
                    <p><strong>Start Date:</strong> ${formatDate(loan.startDate)}</p>
                    <p><strong>End Date:</strong> ${formatDate(loan.endDate)}</p>
                    <p><strong>Repayment Frequency:</strong> ${capitalizeFirst(loan.repaymentFrequency)}</p>
                </div>
            `;
            
            amortizationTbody.innerHTML = '';
            loan.repaymentSchedule.forEach(payment => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${formatDate(payment.date)}</td>
                    <td>${formatCurrency(payment.payment, loan.currency)}</td>
                    <td>${formatCurrency(payment.principal, loan.currency)}</td>
                    <td>${formatCurrency(payment.interest, loan.currency)}</td>
                    <td>${formatCurrency(payment.balance, loan.currency)}</td>
                `;
                amortizationTbody.appendChild(row);
            });
            
            modal.style.display = 'flex';
        }

        function closeLoanDetailsModal() {
            document.getElementById('loan-details-modal').style.display = 'none';
        }

        // Budget functions
        function openBudgetModal(budgetId = null) {
            const modal = document.getElementById('budget-modal');
            const modalTitle = document.getElementById('budget-modal-title');
            const form = document.getElementById('budget-form');
            
            form.reset();
            
            if (budgetId) {
                const budget = budgets.find(b => b.id === budgetId);
                if (budget) {
                    modalTitle.textContent = 'Edit Budget';
                    document.getElementById('budget-id').value = budget.id;
                    document.getElementById('budget-category').value = budget.category;
                    document.getElementById('budget-amount').value = budget.amount;
                    document.getElementById('budget-currency').value = budget.currency || user.currency;
                    document.getElementById('budget-period').value = budget.period;
                }
            } else {
                modalTitle.textContent = 'Add Budget';
                document.getElementById('budget-id').value = '';
                document.getElementById('budget-currency').value = user.currency;
            }
            
            modal.style.display = 'flex';
        }

        function closeBudgetModal() {
            document.getElementById('budget-modal').style.display = 'none';
        }

        function saveBudget() {
            const id = document.getElementById('budget-id').value;
            const category = document.getElementById('budget-category').value;
            const amount = parseFloat(document.getElementById('budget-amount').value);
            const currency = document.getElementById('budget-currency').value;
            const period = document.getElementById('budget-period').value;

            if (!category || !amount || !period) {
                showToast('Please fill all required fields', 'error');
                return;
            }

            const budget = {
                id: id || Date.now().toString(),
                category,
                amount,
                currency,
                period
            };

            if (id) {
                // Update existing budget
                const index = budgets.findIndex(b => b.id === id);
                if (index !== -1) {
                    budgets[index] = budget;
                }
            } else {
                // Add new budget
                budgets.push(budget);
            }

            localStorage.setItem('budgets', JSON.stringify(budgets));
            loadBudgets();
            updateDashboard();
            generateReports();
            closeBudgetModal();
            showToast(id ? 'Budget updated successfully' : 'Budget added successfully', 'success');
        }

        function loadBudgets() {
            const tbody = document.getElementById('budget-tbody');
            const emptyState = document.getElementById('budget-empty');
            const table = document.getElementById('budget-table');
            
            tbody.innerHTML = '';
            
            if (budgets.length === 0) {
                table.style.display = 'none';
                emptyState.style.display = 'block';
                return;
            }
            
            table.style.display = 'table';
            emptyState.style.display = 'none';
            
            budgets.forEach(budget => {
                // Calculate spent amount
                const spent = expenses
                    .filter(e => e.category === budget.category)
                    .reduce((sum, expense) => {
                        // Convert to budget currency if different
                        if (expense.currency !== budget.currency) {
                            return sum + convertToCurrency(expense.amount, expense.currency, budget.currency);
                        }
                        return sum + expense.amount;
                    }, 0);
                
                const remaining = budget.amount - spent;
                const percentage = (spent / budget.amount) * 100;
                
                let progressClass = 'good';
                if (percentage > 90) {
                    progressClass = 'danger';
                } else if (percentage > 75) {
                    progressClass = 'warning';
                }
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${capitalizeFirst(budget.category)}</td>
                    <td>${formatCurrency(budget.amount, budget.currency)}</td>
                    <td>${formatCurrency(spent, budget.currency)}</td>
                    <td>${formatCurrency(remaining, budget.currency)}</td>
                    <td>
                        <div class="budget-progress">
                            <div class="progress-bar">
                                <div class="progress-fill ${progressClass}" style="width: ${Math.min(percentage, 100)}%"></div>
                            </div>
                            <div>${percentage.toFixed(1)}%</div>
                        </div>
                    </td>
                    <td>
                        <div class="table-actions">
                            <button class="icon-btn edit" onclick="openBudgetModal('${budget.id}')">
                                <span class="material-icons">edit</span>
                            </button>
                            <button class="icon-btn delete" onclick="deleteBudget('${budget.id}')">
                                <span class="material-icons">delete</span>
                            </button>
                        </div>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function deleteBudget(id) {
            if (confirm('Are you sure you want to delete this budget?')) {
                budgets = budgets.filter(b => b.id !== id);
                localStorage.setItem('budgets', JSON.stringify(budgets));
                loadBudgets();
                updateDashboard();
                generateReports();
                showToast('Budget deleted successfully', 'success');
            }
        }

        // Dashboard functions
        function updateDashboard() {
            // Calculate monthly income
            const monthlyIncome = calculateMonthlyIncome();
            document.getElementById('monthly-income').textContent = formatCurrency(monthlyIncome);
            
            // Calculate monthly expenses
            const monthlyExpenses = calculateMonthlyExpenses();
            document.getElementById('monthly-expenses').textContent = formatCurrency(monthlyExpenses);
            
            // Calculate monthly savings
            const monthlySavings = monthlyIncome - monthlyExpenses;
            document.getElementById('monthly-savings').textContent = formatCurrency(monthlySavings);
            
            // Calculate net worth
            const totalAssets = calculateTotalAssets();
            const totalLiabilities = calculateTotalLiabilities();
            const netWorth = totalAssets - totalLiabilities;
            document.getElementById('net-worth').textContent = formatCurrency(netWorth);
            
            // Update income vs expense chart
            updateIncomeExpenseChart();
            
            // Update expense categories chart
            updateExpenseCategoriesChart();
            
            // Update budget status
            updateBudgetStatus();
            
            // Update recent transactions
            updateRecentTransactions();
        }

        function calculateMonthlyIncome() {
            const now = new Date();
            const currentMonth = now.getMonth();
            const currentYear = now.getFullYear();
            
            return incomes.reduce((total, income) => {
                if (income.frequency === 'one-time') {
                    const incomeDate = new Date(income.startDate);
                    if (incomeDate.getMonth() === currentMonth && incomeDate.getFullYear() === currentYear) {
                        // Convert to default currency if different
                        if (income.currency !== user.currency) {
                            return total + convertToCurrency(income.amount, income.currency, user.currency);
                        }
                        return total + income.amount;
                    }
                } else {
                    let multiplier = 0;
                    switch (income.frequency) {
                        case 'weekly': multiplier = 4.33; break;
                        case 'bi-weekly': multiplier = 2.17; break;
                        case 'monthly': multiplier = 1; break;
                        case 'quarterly': multiplier = 0.33; break;
                        case 'yearly': multiplier = 0.083; break;
                    }
                    
                    // Convert to default currency if different
                    let amount = income.amount;
                    if (income.currency !== user.currency) {
                        amount = convertToCurrency(income.amount, income.currency, user.currency);
                    }
                    
                    return total + (amount * multiplier);
                }
                return total;
            }, 0);
        }

        function calculateMonthlyExpenses() {
            const now = new Date();
            const currentMonth = now.getMonth();
            const currentYear = now.getFullYear();
            
            return expenses
                .filter(expense => {
                    const expenseDate = new Date(expense.date);
                    return expenseDate.getMonth() === currentMonth && expenseDate.getFullYear() === currentYear;
                })
                .reduce((total, expense) => {
                    // Convert to default currency if different
                    if (expense.currency !== user.currency) {
                        return total + convertToCurrency(expense.amount, expense.currency, user.currency);
                    }
                    return total + expense.amount;
                }, 0);
        }

        function calculateTotalAssets() {
            // For simplicity, we'll consider incomes as assets
            // In a real app, this would include savings, investments, property, etc.
            return incomes.reduce((total, income) => {
                if (income.category === 'passive') {
                    // Convert to default currency if different
                    if (income.currency !== user.currency) {
                        return total + convertToCurrency(income.amount, income.currency, user.currency);
                    }
                    return total + income.amount;
                }
                return total;
            }, 0);
        }

        function calculateTotalLiabilities() {
            // For simplicity, we'll consider loan principals as liabilities
            return loans.reduce((total, loan) => {
                // Convert to default currency if different
                if (loan.currency !== user.currency) {
                    return total + convertToCurrency(loan.principal, loan.currency, user.currency);
                }
                return total + loan.principal;
            }, 0);
        }

        function updateIncomeExpenseChart() {
            const ctx = document.getElementById('income-expense-chart').getContext('2d');
            
            // Get last 6 months data
            const months = [];
            const incomeData = [];
            const expenseData = [];
            
            for (let i = 5; i >= 0; i--) {
                const date = new Date();
                date.setMonth(date.getMonth() - i);
                const month = date.toLocaleString('default', { month: 'short' });
                const year = date.getFullYear();
                months.push(`${month} ${year}`);
                
                // Calculate income for this month
                const monthIncome = incomes.reduce((total, income) => {
                    if (income.frequency === 'one-time') {
                        const incomeDate = new Date(income.startDate);
                        if (incomeDate.getMonth() === date.getMonth() && incomeDate.getFullYear() === date.getFullYear()) {
                            // Convert to default currency if different
                            if (income.currency !== user.currency) {
                                return total + convertToCurrency(income.amount, income.currency, user.currency);
                            }
                            return total + income.amount;
                        }
                    } else {
                        let multiplier = 0;
                        switch (income.frequency) {
                            case 'weekly': multiplier = 4.33; break;
                            case 'bi-weekly': multiplier = 2.17; break;
                            case 'monthly': multiplier = 1; break;
                            case 'quarterly': multiplier = 0.33; break;
                            case 'yearly': multiplier = 0.083; break;
                        }
                        
                        // Convert to default currency if different
                        let amount = income.amount;
                        if (income.currency !== user.currency) {
                            amount = convertToCurrency(income.amount, income.currency, user.currency);
                        }
                        
                        return total + (amount * multiplier);
                    }
                    return total;
                }, 0);
                
                // Calculate expenses for this month
                const monthExpenses = expenses
                    .filter(expense => {
                        const expenseDate = new Date(expense.date);
                        return expenseDate.getMonth() === date.getMonth() && expenseDate.getFullYear() === date.getFullYear();
                    })
                    .reduce((total, expense) => {
                        // Convert to default currency if different
                        if (expense.currency !== user.currency) {
                            return total + convertToCurrency(expense.amount, expense.currency, user.currency);
                        }
                        return total + expense.amount;
                    }, 0);
                
                incomeData.push(monthIncome);
                expenseData.push(monthExpenses);
            }
            
            new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: months,
                    datasets: [
                        {
                            label: 'Income',
                            data: incomeData,
                            backgroundColor: 'rgba(76, 175, 80, 0.6)',
                            borderColor: 'rgba(76, 175, 80, 1)',
                            borderWidth: 1
                        },
                        {
                            label: 'Expenses',
                            data: expenseData,
                            backgroundColor: 'rgba(244, 67, 54, 0.6)',
                            borderColor: 'rgba(244, 67, 54, 1)',
                            borderWidth: 1
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: true,
                            ticks: {
                                callback: function(value) {
                                    return formatCurrency(value, user.currency);
                                }
                            }
                        }
                    }
                }
            });
        }

        function updateExpenseCategoriesChart() {
            const ctx = document.getElementById('expense-categories-chart').getContext('2d');
            
            // Calculate expenses by category
            const categories = {};
            expenses.forEach(expense => {
                if (!categories[expense.category]) {
                    categories[expense.category] = 0;
                }
                
                // Convert to default currency if different
                if (expense.currency !== user.currency) {
                    categories[expense.category] += convertToCurrency(expense.amount, expense.currency, user.currency);
                } else {
                    categories[expense.category] += expense.amount;
                }
            });
            
            const labels = Object.keys(categories);
            const data = Object.values(categories);
            
            new Chart(ctx, {
                type: 'pie',
                data: {
                    labels: labels.map(label => capitalizeFirst(label)),
                    datasets: [{
                        data: data,
                        backgroundColor: [
                            'rgba(255, 99, 132, 0.6)',
                            'rgba(54, 162, 235, 0.6)',
                            'rgba(255, 206, 86, 0.6)',
                            'rgba(75, 192, 192, 0.6)',
                            'rgba(153, 102, 255, 0.6)',
                            'rgba(255, 159, 64, 0.6)',
                            'rgba(199, 199, 199, 0.6)'
                        ],
                        borderColor: [
                            'rgba(255, 99, 132, 1)',
                            'rgba(54, 162, 235, 1)',
                            'rgba(255, 206, 86, 1)',
                            'rgba(75, 192, 192, 1)',
                            'rgba(153, 102, 255, 1)',
                            'rgba(255, 159, 64, 1)',
                            'rgba(199, 199, 199, 1)'
                        ],
                        borderWidth: 1
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'right'
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    const label = context.label || '';
                                    const value = formatCurrency(context.raw, user.currency);
                                    return label + ': ' + value;
                                }
                            }
                        }
                    }
                }
            });
        }

        function updateBudgetStatus() {
            const container = document.getElementById('budget-status-container');
            
            if (budgets.length === 0) {
                container.innerHTML = `
                    <div class="empty-state">
                        <span class="material-icons">pie_chart</span>
                        <p>No budgets set up yet</p>
                    </div>
                `;
                return;
            }
            
            container.innerHTML = '';
            
            budgets.forEach(budget => {
                // Calculate spent amount
                const spent = expenses
                    .filter(e => e.category === budget.category)
                    .reduce((sum, expense) => {
                        // Convert to budget currency if different
                        if (expense.currency !== budget.currency) {
                            return sum + convertToCurrency(expense.amount, expense.currency, budget.currency);
                        }
                        return sum + expense.amount;
                    }, 0);
                
                const remaining = budget.amount - spent;
                const percentage = (spent / budget.amount) * 100;
                
                let progressClass = 'good';
                if (percentage > 90) {
                    progressClass = 'danger';
                } else if (percentage > 75) {
                    progressClass = 'warning';
                }
                
                const budgetCard = document.createElement('div');
                budgetCard.className = 'card';
                budgetCard.innerHTML = `
                    <div class="card-header">
                        <h3 class="card-title">${capitalizeFirst(budget.category)}</h3>
                    </div>
                    <div class="budget-progress">
                        <div class="progress-bar">
                            <div class="progress-fill ${progressClass}" style="width: ${Math.min(percentage, 100)}%"></div>
                        </div>
                        <div style="display: flex; justify-content: space-between; margin-top: 5px;">
                            <span>${formatCurrency(spent, budget.currency)} of ${formatCurrency(budget.amount, budget.currency)}</span>
                            <span>${percentage.toFixed(1)}%</span>
                        </div>
                    </div>
                `;
                container.appendChild(budgetCard);
            });
        }

        function updateRecentTransactions() {
            const container = document.getElementById('recent-transactions');
            
            if (expenses.length === 0) {
                container.innerHTML = `
                    <div class="empty-state">
                        <span class="material-icons">receipt_long</span>
                        <p>No recent transactions</p>
                    </div>
                `;
                return;
            }
            
            // Sort expenses by date (newest first)
            const sortedExpenses = [...expenses].sort((a, b) => new Date(b.date) - new Date(a.date));
            
            // Get last 5 transactions
            const recentTransactions = sortedExpenses.slice(0, 5);
            
            container.innerHTML = '';
            
            recentTransactions.forEach(transaction => {
                const transactionCard = document.createElement('div');
                transactionCard.className = 'card';
                transactionCard.style.marginBottom = '10px';
                transactionCard.innerHTML = `
                    <div style="display: flex; justify-content: space-between; align-items: center;">
                        <div>
                            <div style="font-weight: 500;">${transaction.description}</div>
                            <div style="font-size: 14px; color: var(--text-light);">${capitalizeFirst(transaction.category)} • ${formatDate(transaction.date)}</div>
                        </div>
                        <div style="font-weight: 500; color: var(--danger);">${formatCurrency(transaction.amount, transaction.currency)}</div>
                    </div>
                `;
                container.appendChild(transactionCard);
            });
        }

        // Reports functions
        function generateReports() {
            // Income report chart
            const incomeCtx = document.getElementById('income-report-chart').getContext('2d');
            
            // Calculate income by type
            const incomeTypes = {};
            incomes.forEach(income => {
                if (!incomeTypes[income.type]) {
                    incomeTypes[income.type] = 0;
                }
                
                // Convert to default currency if different
                if (income.currency !== user.currency) {
                    incomeTypes[income.type] += convertToCurrency(income.amount, income.currency, user.currency);
                } else {
                    incomeTypes[income.type] += income.amount;
                }
            });
            
            new Chart(incomeCtx, {
                type: 'doughnut',
                data: {
                    labels: Object.keys(incomeTypes).map(type => capitalizeFirst(type)),
                    datasets: [{
                        data: Object.values(incomeTypes),
                        backgroundColor: [
                            'rgba(76, 175, 80, 0.6)',
                            'rgba(33, 150, 243, 0.6)',
                            'rgba(255, 193, 7, 0.6)',
                            'rgba(156, 39, 176, 0.6)',
                            'rgba(255, 87, 34, 0.6)'
                        ],
                        borderColor: [
                            'rgba(76, 175, 80, 1)',
                            'rgba(33, 150, 243, 1)',
                            'rgba(255, 193, 7, 1)',
                            'rgba(156, 39, 176, 1)',
                            'rgba(255, 87, 34, 1)'
                        ],
                        borderWidth: 1
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'right'
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    const label = context.label || '';
                                    const value = formatCurrency(context.raw, user.currency);
                                    return label + ': ' + value;
                                }
                            }
                        }
                    }
                }
            });
            
            // Expense report chart
            const expenseCtx = document.getElementById('expense-report-chart').getContext('2d');
            
            // Get last 6 months data
            const months = [];
            const expenseData = [];
            
            for (let i = 5; i >= 0; i--) {
                const date = new Date();
                date.setMonth(date.getMonth() - i);
                const month = date.toLocaleString('default', { month: 'short' });
                const year = date.getFullYear();
                months.push(`${month} ${year}`);
                
                // Calculate expenses for this month
                const monthExpenses = expenses
                    .filter(expense => {
                        const expenseDate = new Date(expense.date);
                        return expenseDate.getMonth() === date.getMonth() && expenseDate.getFullYear() === date.getFullYear();
                    })
                    .reduce((total, expense) => {
                        // Convert to default currency if different
                        if (expense.currency !== user.currency) {
                            return total + convertToCurrency(expense.amount, expense.currency, user.currency);
                        }
                        return total + expense.amount;
                    }, 0);
                
                expenseData.push(monthExpenses);
            }
            
            new Chart(expenseCtx, {
                type: 'line',
                data: {
                    labels: months,
                    datasets: [{
                        label: 'Expenses',
                        data: expenseData,
                        backgroundColor: 'rgba(244, 67, 54, 0.2)',
                        borderColor: 'rgba(244, 67, 54, 1)',
                        borderWidth: 2,
                        tension: 0.3,
                        fill: true
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: true,
                            ticks: {
                                callback: function(value) {
                                    return formatCurrency(value, user.currency);
                                }
                            }
                        }
                    }
                }
            });
            
            // Cash flow chart
            const cashFlowCtx = document.getElementById('cash-flow-chart').getContext('2d');
            
            // Calculate cash flow for last 6 months
            const cashFlowData = [];
            
            for (let i = 5; i >= 0; i--) {
                const date = new Date();
                date.setMonth(date.getMonth() - i);
                
                // Calculate income for this month
                const monthIncome = incomes.reduce((total, income) => {
                    if (income.frequency === 'one-time') {
                        const incomeDate = new Date(income.startDate);
                        if (incomeDate.getMonth() === date.getMonth() && incomeDate.getFullYear() === date.getFullYear()) {
                            // Convert to default currency if different
                            if (income.currency !== user.currency) {
                                return total + convertToCurrency(income.amount, income.currency, user.currency);
                            }
                            return total + income.amount;
                        }
                    } else {
                        let multiplier = 0;
                        switch (income.frequency) {
                            case 'weekly': multiplier = 4.33; break;
                            case 'bi-weekly': multiplier = 2.17; break;
                            case 'monthly': multiplier = 1; break;
                            case 'quarterly': multiplier = 0.33; break;
                            case 'yearly': multiplier = 0.083; break;
                        }
                        
                        // Convert to default currency if different
                        let amount = income.amount;
                        if (income.currency !== user.currency) {
                            amount = convertToCurrency(income.amount, income.currency, user.currency);
                        }
                        
                        return total + (amount * multiplier);
                    }
                    return total;
                }, 0);
                
                // Calculate expenses for this month
                const monthExpenses = expenses
                    .filter(expense => {
                        const expenseDate = new Date(expense.date);
                        return expenseDate.getMonth() === date.getMonth() && expenseDate.getFullYear() === date.getFullYear();
                    })
                    .reduce((total, expense) => {
                        // Convert to default currency if different
                        if (expense.currency !== user.currency) {
                            return total + convertToCurrency(expense.amount, expense.currency, user.currency);
                        }
                        return total + expense.amount;
                    }, 0);
                
                cashFlowData.push(monthIncome - monthExpenses);
            }
            
            new Chart(cashFlowCtx, {
                type: 'bar',
                data: {
                    labels: months,
                    datasets: [{
                        label: 'Cash Flow',
                        data: cashFlowData,
                        backgroundColor: cashFlowData.map(value => 
                            value >= 0 ? 'rgba(76, 175, 80, 0.6)' : 'rgba(244, 67, 54, 0.6)'
                        ),
                        borderColor: cashFlowData.map(value => 
                            value >= 0 ? 'rgba(76, 175, 80, 1)' : 'rgba(244, 67, 54, 1)'
                        ),
                        borderWidth: 1
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            ticks: {
                                callback: function(value) {
                                    return formatCurrency(value, user.currency);
                                }
                            }
                        }
                    }
                }
            });
            
            // Net worth chart
            const netWorthCtx = document.getElementById('net-worth-chart').getContext('2d');
            
            // Calculate net worth for last 6 months
            const netWorthData = [];
            
            for (let i = 5; i >= 0; i--) {
                const date = new Date();
                date.setMonth(date.getMonth() - i);
                
                // Calculate assets (simplified)
                const assets = incomes.reduce((total, income) => {
                    if (income.category === 'passive') {
                        // Convert to default currency if different
                        if (income.currency !== user.currency) {
                            return total + convertToCurrency(income.amount, income.currency, user.currency);
                        }
                        return total + income.amount;
                    }
                    return total;
                }, 0);
                
                // Calculate liabilities (simplified)
                const liabilities = loans.reduce((total, loan) => {
                    // Convert to default currency if different
                    if (loan.currency !== user.currency) {
                        return total + convertToCurrency(loan.principal, loan.currency, user.currency);
                    }
                    return total + loan.principal;
                }, 0);
                
                netWorthData.push(assets - liabilities);
            }
            
            new Chart(netWorthCtx, {
                type: 'line',
                data: {
                    labels: months,
                    datasets: [{
                        label: 'Net Worth',
                        data: netWorthData,
                        backgroundColor: 'rgba(255, 152, 0, 0.2)',
                        borderColor: 'rgba(255, 152, 0, 1)',
                        borderWidth: 2,
                        tension: 0.3,
                        fill: true
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            ticks: {
                                callback: function(value) {
                                    return formatCurrency(value, user.currency);
                                }
                            }
                        }
                    }
                }
            });
        }

        // Utility functions
        function calculateAmortization(principal, interestRate, startDate, endDate, repaymentFrequency) {
            const start = new Date(startDate);
            const end = new Date(endDate);
            const months = Math.ceil((end - start) / (1000 * 60 * 60 * 24 * 30));
            
            const monthlyRate = interestRate / 100 / 12;
            const emi = principal * monthlyRate * Math.pow(1 + monthlyRate, months) / 
                        (Math.pow(1 + monthlyRate, months) - 1);
            
            let balance = principal;
            const schedule = [];
            let currentDate = new Date(start);
            
            for (let i = 0; i < months; i++) {
                const interest = balance * monthlyRate;
                const principalPayment = emi - interest;
                balance -= principalPayment;
                
                // Adjust date based on repayment frequency
                if (repaymentFrequency === 'weekly') {
                    currentDate.setDate(currentDate.getDate() + 7);
                } else if (repaymentFrequency === 'bi-weekly') {
                    currentDate.setDate(currentDate.getDate() + 14);
                } else if (repaymentFrequency === 'monthly') {
                    currentDate.setMonth(currentDate.getMonth() + 1);
                } else if (repaymentFrequency === 'quarterly') {
                    currentDate.setMonth(currentDate.getMonth() + 3);
                }
                
                schedule.push({
                    date: new Date(currentDate),
                    payment: emi,
                    principal: principalPayment,
                    interest: interest,
                    balance: balance > 0 ? balance : 0
                });
            }
            
            const totalInterest = schedule.reduce((sum, payment) => sum + payment.interest, 0);
            
            return {
                emi,
                totalInterest,
                schedule
            };
        }

        function convertToCurrency(amount, fromCurrency, toCurrency) {
            if (fromCurrency === toCurrency) {
                return amount;
            }
            
            if (!exchangeRates[fromCurrency] || !exchangeRates[toCurrency]) {
                // If we don't have rates, return the original amount
                return amount;
            }
            
            // Convert to USD first, then to target currency
            const amountInUSD = amount / exchangeRates[fromCurrency];
            return amountInUSD * exchangeRates[toCurrency];
        }

        function capitalizeFirst(str) {
            return str.charAt(0).toUpperCase() + str.slice(1);
        }

        function formatDate(dateString) {
            const options = { year: 'numeric', month: 'short', day: 'numeric' };
            return new Date(dateString).toLocaleDateString(undefined, options);
        }

        function showToast(message, type = 'success') {
            const toast = document.getElementById('toast');
            const toastIcon = document.getElementById('toast-icon');
            const toastMessage = document.getElementById('toast-message');
            
            toast.className = `toast ${type}`;
            toastIcon.textContent = type === 'success' ? 'check_circle' : 'error';
            toastMessage.textContent = message;
            
            toast.classList.add('show');
            
            setTimeout(() => {
                toast.classList.remove('show');
            }, 3000);
        }

        function exportToCsv() {
            let csv = 'Type,Category,Description,Amount,Currency,Date\n';
            
            // Add incomes
            incomes.forEach(income => {
                csv += `Income,${income.type},${income.source},${income.amount},${income.currency},${income.startDate}\n`;
            });
            
            // Add expenses
            expenses.forEach(expense => {
                csv += `Expense,${expense.category},${expense.description},${expense.amount},${expense.currency},${expense.date}\n`;
            });
            
            // Add loans
            loans.forEach(loan => {
                csv += `Loan,${loan.type},${loan.lender},${loan.principal},${loan.currency},${loan.startDate}\n`;
            });
            
            // Create download link
            const blob = new Blob([csv], { type: 'text/csv' });
            const url = window.URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.setAttribute('hidden', '');
            a.setAttribute('href', url);
            a.setAttribute('download', 'financial_data.csv');
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            
            showToast('Data exported successfully', 'success');
        }

        function parseCsv(csv) {
            const lines = csv.split('\n');
            const result = [];
            const headers = lines[0].split(',');
            
            for (let i = 1; i < lines.length; i++) {
                const obj = {};
                const currentline = lines[i].split(',');
                
                for (let j = 0; j < headers.length; j++) {
                    obj[headers[j].trim()] = currentline[j] ? currentline[j].trim() : '';
                }
                
                result.push(obj);
            }
            
            return result;
        }

        function importData(data) {
            data.forEach(item => {
                if (item.Type === 'Income') {
                    incomes.push({
                        id: Date.now().toString() + Math.random().toString(36).substr(2, 5),
                        source: item.Description,
                        type: item.Category,
                        amount: parseFloat(item.Amount),
                        currency: item.Currency || user.currency,
                        frequency: 'monthly',
                        startDate: item.Date,
                        endDate: null,
                        category: 'active',
                        taxes: 0,
                        description: ''
                    });
                } else if (item.Type === 'Expense') {
                    expenses.push({
                        id: Date.now().toString() + Math.random().toString(36).substr(2, 5),
                        description: item.Description,
                        category: item.Category,
                        amount: parseFloat(item.Amount),
                        currency: item.Currency || user.currency,
                        date: item.Date,
                        paymentMethod: 'cash',
                        recurrence: 'one-time',
                        tags: []
                    });
                } else if (item.Type === 'Loan') {
                    // Simplified loan import
                    const amortization = calculateAmortization(
                        parseFloat(item.Amount),
                        5, // Default interest rate
                        item.Date,
                        new Date(new Date(item.Date).setFullYear(new Date(item.Date).getFullYear() + 5)).toISOString().split('T')[0],
                        'monthly'
                    );
                    
                    loans.push({
                        id: Date.now().toString() + Math.random().toString(36).substr(2, 5),
                        lender: item.Description,
                        type: item.Category,
                        principal: parseFloat(item.Amount),
                        currency: item.Currency || user.currency,
                        interestRate: 5,
                        interestType: 'fixed',
                        startDate: item.Date,
                        endDate: new Date(new Date(item.Date).setFullYear(new Date(item.Date).getFullYear() + 5)).toISOString().split('T')[0],
                        repaymentFrequency: 'monthly',
                        emi: amortization.emi,
                        totalInterest: amortization.totalInterest,
                        repaymentSchedule: amortization.schedule
                    });
                }
            });
            
            localStorage.setItem('incomes', JSON.stringify(incomes));
            localStorage.setItem('expenses', JSON.stringify(expenses));
            localStorage.setItem('loans', JSON.stringify(loans));
            
            loadIncomes();
            loadExpenses();
            loadLoans();
            updateDashboard();
            generateReports();
        }

        // Initialize the app
        window.onload = function() {
            checkLogin();
        };
    </script>
</body>
</html>
