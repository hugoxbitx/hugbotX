<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> CBNH| Banca Premium de HUGO</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700&family=Playfair+Display:wght@400;500;600;700&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        :root {
            --primary: #0c1a2a;
            --secondary: #1c2d44;
            --accent: #3498db;
            --gold: #d4af37;
            --silver: #c0c0c0;
            --light: #f5f7fa;
            --success: #2ecc71;
            --danger: #e74c3c;
            --warning: #f39c12;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Montserrat', sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #0c1a2a, #1c2d44);
            color: var(--light);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }
        
        body::before {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at 10% 20%, rgba(52, 152, 219, 0.1) 0%, rgba(0, 0, 0, 0) 20%),
                        radial-gradient(circle at 90% 80%, rgba(212, 175, 55, 0.1) 0%, rgba(0, 0, 0, 0) 20%);
            z-index: -1;
            animation: backgroundPulse 15s infinite alternate;
        }
        
        @keyframes backgroundPulse {
            0% { opacity: 0.1; }
            100% { opacity: 0.3; }
        }
        
        .container {
            width: 90%;
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }
        
        /* Header */
        header {
            padding: 20px 0;
            position: sticky;
            top: 0;
            z-index: 100;
            background: rgba(12, 26, 42, 0.95);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(52, 152, 219, 0.2);
        }
        
        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .logo-icon {
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, var(--accent), var(--gold));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            font-weight: 700;
            color: var(--primary);
        }
        
        .logo-text {
            font-family: 'Playfair Display', serif;
            font-size: 28px;
            font-weight: 700;
            background: linear-gradient(to right, var(--accent), var(--gold));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: 1px;
        }
        
        nav ul {
            display: flex;
            list-style: none;
            gap: 30px;
        }
        
        nav a {
            color: var(--light);
            text-decoration: none;
            font-weight: 500;
            position: relative;
            padding: 10px 5px;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        nav a:hover {
            color: var(--accent);
        }
        
        nav a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--accent);
            transition: width 0.3s ease;
        }
        
        nav a:hover::after {
            width: 100%;
        }
        
        .user-menu {
            display: flex;
            align-items: center;
            gap: 15px;
            cursor: pointer;
        }
        
        .user-avatar {
            width: 45px;
            height: 45px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--accent), var(--gold));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            font-weight: 600;
        }
        
        .user-info {
            display: flex;
            flex-direction: column;
        }
        
        .user-name {
            font-weight: 600;
            font-size: 16px;
        }
        
        .user-status {
            font-size: 12px;
            color: var(--accent);
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .user-status::before {
            content: '';
            width: 8px;
            height: 8px;
            background: var(--success);
            border-radius: 50%;
            display: inline-block;
        }
        
        /* Dashboard */
        .dashboard {
            padding: 40px 0;
        }
        
        .welcome-banner {
            background: linear-gradient(135deg, rgba(28, 45, 68, 0.7), rgba(12, 26, 42, 0.7));
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 40px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(52, 152, 219, 0.2);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            animation: fadeIn 1s ease-out;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .welcome-banner h1 {
            font-size: 32px;
            margin-bottom: 10px;
            font-weight: 600;
            background: linear-gradient(to right, var(--light), var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .welcome-banner p {
            color: #b0c4de;
            font-size: 18px;
            margin-bottom: 20px;
        }
        
        .security-info {
            display: flex;
            gap: 20px;
            margin-top: 20px;
            color: #b0c4de;
            font-size: 14px;
        }
        
        .quick-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }
        
        .stat-card {
            background: linear-gradient(135deg, rgba(28, 45, 68, 0.7), rgba(12, 26, 42, 0.7));
            border-radius: 15px;
            padding: 25px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(52, 152, 219, 0.2);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease;
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
        }
        
        .stat-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .stat-icon {
            width: 50px;
            height: 50px;
            background: rgba(52, 152, 219, 0.1);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            color: var(--accent);
        }
        
        .stat-title {
            font-size: 18px;
            font-weight: 500;
            color: #b0c4de;
        }
        
        .stat-value {
            font-size: 32px;
            font-weight: 700;
            margin-bottom: 10px;
        }
        
        .stat-change {
            display: flex;
            align-items: center;
            gap: 5px;
            font-size: 14px;
            font-weight: 600;
        }
        
        .positive {
            color: var(--success);
        }
        
        .negative {
            color: var(--danger);
        }
        
        /* Cards Section */
        .section-title {
            font-size: 28px;
            font-weight: 600;
            margin: 50px 0 30px;
            position: relative;
            display: inline-block;
            padding-bottom: 10px;
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 60px;
            height: 3px;
            background: linear-gradient(to right, var(--accent), var(--gold));
            border-radius: 3px;
        }
        
        .cards-container {
            display: flex;
            gap: 30px;
            overflow-x: auto;
            padding: 20px 10px;
            margin-bottom: 50px;
            scrollbar-width: thin;
            scrollbar-color: var(--accent) var(--secondary);
        }
        
        .cards-container::-webkit-scrollbar {
            height: 8px;
        }
        
        .cards-container::-webkit-scrollbar-track {
            background: var(--secondary);
            border-radius: 10px;
        }
        
        .cards-container::-webkit-scrollbar-thumb {
            background: linear-gradient(to right, var(--accent), var(--gold));
            border-radius: 10px;
        }
        
        .credit-card {
            min-width: 350px;
            height: 220px;
            border-radius: 20px;
            padding: 25px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            position: relative;
            overflow: hidden;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.3);
            transition: transform 0.4s ease;
            animation: cardAppear 0.6s ease-out;
        }
        
        @keyframes cardAppear {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .credit-card:hover {
            transform: translateY(-10px) rotate(2deg);
        }
        
        .credit-card::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.15) 0%, rgba(255,255,255,0) 70%);
            transform: rotate(30deg);
        }
        
        .premium {
            background: linear-gradient(135deg, #1a3b5a, #0d2538);
        }
        
        .black {
            background: linear-gradient(135deg, #0d0d0d, #1a1a1a);
        }
        
        .gold {
            background: linear-gradient(135deg, #d4af37, #b8860b);
        }
        
        .card-logo {
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 24px;
        }
        
        .card-logo span {
            font-size: 14px;
            font-weight: 700;
            letter-spacing: 1px;
            background: rgba(0, 0, 0, 0.2);
            padding: 5px 15px;
            border-radius: 20px;
            text-transform: uppercase;
        }
        
        .card-number {
            font-size: 22px;
            letter-spacing: 3px;
            margin: 15px 0;
            font-family: 'Courier New', monospace;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
        }
        
        .card-info {
            display: flex;
            justify-content: space-between;
            font-size: 16px;
            letter-spacing: 1px;
        }
        
        .card-chip {
            position: absolute;
            width: 50px;
            height: 40px;
            background: linear-gradient(135deg, #c9a227, #e5c100);
            border-radius: 8px;
            top: 50%;
            left: 25px;
            transform: translateY(-50%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            color: #333;
        }
        
        /* Accounts */
        .accounts-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 30px;
            margin-bottom: 50px;
        }
        
        .account-card {
            background: linear-gradient(135deg, rgba(28, 45, 68, 0.7), rgba(12, 26, 42, 0.7));
            border-radius: 20px;
            padding: 30px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(52, 152, 219, 0.2);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease;
            animation: fadeIn 0.8s ease-out;
        }
        
        .account-card:hover {
            transform: translateY(-10px);
        }
        
        .account-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
        }
        
        .account-icon {
            width: 50px;
            height: 50px;
            background: rgba(52, 152, 219, 0.1);
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            color: var(--accent);
        }
        
        .account-title {
            font-size: 22px;
            font-weight: 600;
        }
        
        .account-number {
            font-size: 16px;
            color: #b0c4de;
            margin-bottom: 25px;
            font-family: 'Courier New', monospace;
        }
        
        .account-balance {
            font-size: 32px;
            font-weight: 700;
            margin-bottom: 15px;
        }
        
        .account-actions {
            display: flex;
            gap: 15px;
            margin-top: 25px;
        }
        
        .btn {
            padding: 12px 25px;
            border-radius: 12px;
            border: none;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .btn-primary {
            background: linear-gradient(to right, var(--accent), #2980b9);
            color: white;
        }
        
        .btn-outline {
            background: transparent;
            border: 2px solid var(--accent);
            color: var(--accent);
        }
        
        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        /* Transactions */
        .transactions-container {
            background: linear-gradient(135deg, rgba(28, 45, 68, 0.7), rgba(12, 26, 42, 0.7));
            border-radius: 20px;
            padding: 30px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(52, 152, 219, 0.2);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            margin-bottom: 50px;
        }
        
        .transactions-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
        }
        
        .transactions-filter {
            display: flex;
            gap: 15px;
        }
        
        .filter-btn {
            padding: 10px 20px;
            background: rgba(52, 152, 219, 0.1);
            border-radius: 10px;
            border: none;
            color: #b0c4de;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .filter-btn.active {
            background: var(--accent);
            color: white;
        }
        
        .transactions-list {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .transaction-item {
            display: flex;
            align-items: center;
            padding: 20px;
            background: rgba(12, 26, 42, 0.5);
            border-radius: 15px;
            transition: all 0.3s ease;
            animation: fadeIn 0.5s ease-out;
        }
        
        .transaction-item:hover {
            background: rgba(28, 45, 68, 0.7);
            transform: translateX(5px);
        }
        
        .transaction-icon {
            width: 50px;
            height: 50px;
            background: rgba(52, 152, 219, 0.1);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            margin-right: 20px;
        }
        
        .transaction-info {
            flex: 1;
        }
        
        .transaction-title {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 5px;
        }
        
        .transaction-date {
            font-size: 14px;
            color: #b0c4de;
        }
        
        .transaction-amount {
            font-size: 20px;
            font-weight: 700;
        }
        
        .transaction-status {
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 14px;
            font-weight: 600;
            margin-left: 20px;
        }
        
        .status-completed {
            background: rgba(46, 204, 113, 0.1);
            color: var(--success);
        }
        
        .status-pending {
            background: rgba(243, 156, 18, 0.1);
            color: var(--warning);
        }
        
        /* Charts */
        .charts-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(500px, 1fr));
            gap: 30px;
            margin-bottom: 50px;
        }
        
        .chart-card {
            background: linear-gradient(135deg, rgba(28, 45, 68, 0.7), rgba(12, 26, 42, 0.7));
            border-radius: 20px;
            padding: 30px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(52, 152, 219, 0.2);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }
        
        .chart-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
        }
        
        .chart-title {
            font-size: 22px;
            font-weight: 600;
        }
        
        .chart-actions {
            display: flex;
            gap: 10px;
        }
        
        .chart-content {
            height: 300px;
            position: relative;
        }
        
        /* Footer */
        footer {
            background: rgba(8, 18, 30, 0.95);
            border-top: 1px solid rgba(52, 152, 219, 0.2);
            padding: 50px 0 30px;
            margin-top: 50px;
        }
        
        .footer-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
        }
        
        .footer-column h3 {
            font-size: 20px;
            font-weight: 600;
            margin-bottom: 25px;
            position: relative;
            padding-bottom: 10px;
        }
        
        .footer-column h3::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 40px;
            height: 3px;
            background: var(--accent);
            border-radius: 3px;
        }
        
        .footer-links {
            list-style: none;
        }
        
        .footer-links li {
            margin-bottom: 15px;
        }
        
        .footer-links a {
            color: #b0c4de;
            text-decoration: none;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .footer-links a:hover {
            color: var(--accent);
            transform: translateX(5px);
        }
        
        .contact-info {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .contact-item {
            display: flex;
            align-items: center;
            gap: 15px;
            color: #b0c4de;
        }
        
        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }
        
        .social-link {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: rgba(52, 152, 219, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 18px;
            color: var(--light);
            transition: all 0.3s ease;
        }
        
        .social-link:hover {
            background: var(--accent);
            transform: translateY(-5px);
        }
        
        .copyright {
            text-align: center;
            padding-top: 30px;
            margin-top: 40px;
            border-top: 1px solid rgba(52, 152, 219, 0.1);
            color: #b0c4de;
            font-size: 14px;
        }
        
        /* Animations */
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }
        
        .floating {
            animation: float 4s ease-in-out infinite;
        }
        
        /* Responsive */
        @media (max-width: 992px) {
            nav ul {
                gap: 15px;
            }
            
            .charts-container {
                grid-template-columns: 1fr;
            }
        }
        
        @media (max-width: 768px) {
            .header-container {
                flex-direction: column;
                gap: 20px;
            }
            
            nav ul {
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .cards-container {
                flex-direction: column;
            }
            
            .credit-card {
                min-width: 100%;
            }
            
            .transaction-item {
                flex-direction: column;
                align-items: flex-start;
            }
            
            .transaction-amount, .transaction-status {
                align-self: flex-end;
                margin-top: 15px;
                margin-left: 0;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container header-container">
            <div class="logo">
                <div class="logo-icon">GE</div>
                <div class="logo-text">CBNH</div>
            </div>
            
            <nav>
                <ul>
                    <li><a href="#"><i class="fas fa-home"></i> Inicio</a></li>
                    <li><a href="#"><i class="fas fa-wallet"></i> Cuentas</a></li>
                    <li><a href="#"><i class="fas fa-exchange-alt"></i> Transacciones</a></li>
                    <li><a href="#"><i class="fas fa-credit-card"></i> Tarjetas</a></li>
                    <li><a href="#"><i class="fas fa-chart-line"></i> Inversiones</a></li>
                    <li><a href="#"><i class="fas fa-cog"></i> Configuración</a></li>
                </ul>
            </nav>
            
            <div class="user-menu">
                <div class="user-avatar">HM</div>
                <div class="user-info">
                    <div class="user-name">HUGO MONJAS</div>
                    <div class="user-status">Conectado</div>
                </div>
                <i class="fas fa-chevron-down"></i>
            </div>
        </div>
    </header>
    
    <!-- Dashboard -->
    <main class="dashboard">
        <div class="container">
            <div class="welcome-banner">
                <h1>Bienvenido a su Banca Premium</h1>
                <p>Gestiona tus finanzas con las herramientas más avanzadas y el servicio exclusivo que mereces</p>
                
                <div class="security-info">
                    <div><i class="fas fa-lock"></i> Sesión segura 256-bit SSL</div>
                    <div><i class="fas fa-shield-alt"></i> Último acceso: Hoy, 14:32</div>
                    <div><i class="fas fa-map-marker-alt"></i> Desde: Madrid, ES</div>
                </div>
            </div>
            
            <div class="quick-stats">
                <div class="stat-card">
                    <div class="stat-header">
                        <div class="stat-title">Balance Total</div>
                        <div class="stat-icon">
                            <i class="fas fa-coins"></i>
                        </div>
                    </div>
                    <div class="stat-value">€ 489,256.80</div>
                    <div class="stat-change positive">
                        <i class="fas fa-arrow-up"></i> 2.4% este mes
                    </div>
                </div>
                
                <div class="stat-card">
                    <div class="stat-header">
                        <div class="stat-title">Ingresos Mensuales</div>
                        <div class="stat-icon">
                            <i class="fas fa-arrow-down"></i>
                        </div>
                    </div>
                    <div class="stat-value">€ 234,450.00</div>
                    <div class="stat-change positive">
                        <i class="fas fa-arrow-up"></i> 5.2% este mes
                    </div>
                </div>
                
                <div class="stat-card">
                    <div class="stat-header">
                        <div class="stat-title">Gastos Mensuales</div>
                        <div class="stat-icon">
                            <i class="fas fa-arrow-up"></i>
                        </div>
                    </div>
                    <div class="stat-value">€ 7,890.50</div>
                    <div class="stat-change negative">
                        <i class="fas fa-arrow-down"></i> 1.8% este mes
                    </div>
                </div>
                
                <div class="stat-card">
                    <div class="stat-header">
                        <div class="stat-title">Rendimiento Inversiones</div>
                        <div class="stat-icon">
                            <i class="fas fa-chart-line"></i>
                        </div>
                    </div>
                    <div class="stat-value">€ 24,560.40</div>
                    <div class="stat-change positive">
                        <i class="fas fa-arrow-up"></i> 3.7% este mes
                    </div>
                </div>
            </div>
            
            <h2 class="section-title">Tus Tarjetas</h2>
            <div class="cards-container">
                <div class="credit-card premium floating">
                    <div class="card-logo">
                        <i class="fab fa-cc-visa"></i>
                        <span>Premium</span>
                    </div>
                    <div class="card-number">**** **** **** 4532</div>
                    <div class="card-info">
                        <div class="card-holder">HUGO MONJAS</div>
                        <div class="card-expiry">09/25</div>
                    </div>
                    <div class="card-chip">
                        <i class="fas fa-microchip"></i>
                    </div>
                </div>
                
                <div class="credit-card black floating" style="animation-delay: 0.5s;">
                    <div class="card-logo">
                        <i class="fab fa-cc-mastercard"></i>
                        <span>Black</span>
                    </div>
                    <div class="card-number">**** **** **** 7841</div>
                    <div class="card-info">
                        <div class="card-holder">HUGO MONJAS</div>
                        <div class="card-expiry">12/26</div>
                    </div>
                    <div class="card-chip">
                        <i class="fas fa-microchip"></i>
                    </div>
                </div>
                
                <div class="credit-card gold floating" style="animation-delay: 1s;">
                    <div class="card-logo">
                        <i class="fab fa-cc-amex"></i>
                        <span>Gold</span>
                    </div>
                    <div class="card-number">**** **** **** 6219</div>
                    <div class="card-info">
                        <div class="card-holder">HUGO MONJAS</div>
                        <div class="card-expiry">06/27</div>
                    </div>
                    <div class="card-chip">
                        <i class="fas fa-microchip"></i>
                    </div>
                </div>
            </div>
            
            <h2 class="section-title">Tus Cuentas</h2>
            <div class="accounts-grid">
                <div class="account-card">
                    <div class="account-header">
                        <div class="account-icon">
                            <i class="fas fa-euro-sign"></i>
                        </div>
                        <div class="account-title">Cuenta Corriente</div>
                    </div>
                    <div class="account-number">ES76 2100 0813 6101 2345 6789</div>
                    <div class="account-balance">€ 56,780.90</div>
                    <div class="stat-change positive">
                        <i class="fas fa-arrow-up"></i> +€ 1,240.00 este mes
                    </div>
                    <div class="account-actions">
                        <button class="btn btn-primary"><i class="fas fa-exchange-alt"></i> Transferir</button>
                        <button class="btn btn-outline"><i class="fas fa-history"></i> Historial</button>
                    </div>
                </div>
                
                <div class="account-card">
                    <div class="account-header">
                        <div class="account-icon">
                            <i class="fas fa-piggy-bank"></i>
                        </div>
                        <div class="account-title">Cuenta Ahorro</div>
                    </div>
                    <div class="account-number">ES12 0049 1892 6910 1234 5678</div>
                    <div class="account-balance">€ 142,560.25</div>
                    <div class="stat-change positive">
                        <i class="fas fa-arrow-up"></i> +€ 3,450.00 este mes
                    </div>
                    <div class="account-actions">
                        <button class="btn btn-primary"><i class="fas fa-exchange-alt"></i> Transferir</button>
                        <button class="btn btn-outline"><i class="fas fa-history"></i> Historial</button>
                    </div>
                </div>
                
                <div class="account-card">
                    <div class="account-header">
                        <div class="account-icon">
                            <i class="fas fa-chart-line"></i>
                        </div>
                        <div class="account-title">Inversiones Globales</div>
                    </div>
                    <div class="account-number">ES34 0128 0010 0501 2345 6789</div>
                    <div class="account-balance">€ 289,915.65</div>
                    <div class="stat-change positive">
                        <i class="fas fa-arrow-up"></i> +€ 132,560.40 este mes
                    </div>
                    <div class="account-actions">
                        <button class="btn btn-primary"><i class="fas fa-exchange-alt"></i> Invertir</button>
                        <button class="btn btn-outline"><i class="fas fa-history"></i> Rendimiento</button>
                    </div>
                </div>
            </div>
            
            <h2 class="section-title">Últimas Transacciones</h2>
            <div class="transactions-container">
                <div class="transactions-header">
                    <h3>Historial de Actividad</h3>
                    <div class="transactions-filter">
                        <button class="filter-btn active">Todos</button>
                        <button class="filter-btn">Ingresos</button>
                        <button class="filter-btn">Gastos</button>
                        <button class="filter-btn">Transferencias</button>
                    </div>
                </div>
                
                <div class="transactions-list" id="transactions-list">
                    <!-- Transactions will be added here by JavaScript -->
                </div>
            </div>
            
            <h2 class="section-title">Análisis Financiero</h2>
            <div class="charts-container">
                <div class="chart-card">
                    <div class="chart-header">
                        <div class="chart-title">Balance Mensual</div>
                        <div class="chart-actions">
                            <button class="filter-btn active">Mensual</button>
                            <button class="filter-btn">Trimestral</button>
                            <button class="filter-btn">Anual</button>
                        </div>
                    </div>
                    <div class="chart-content">
                        <canvas id="balanceChart"></canvas>
                    </div>
                </div>
                
                <div class="chart-card">
                    <div class="chart-header">
                        <div class="chart-title">Distribución de Gastos</div>
                        <div class="chart-actions">
                            <button class="filter-btn active">Categorías</button>
                            <button class="filter-btn">Por Cuenta</button>
                        </div>
                    </div>
                    <div class="chart-content">
                        <canvas id="expensesChart"></canvas>
                    </div>
                </div>
            </div>
        </div>
    </main>
    
    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-container">
                <div class="footer-column">
                    <h3>Global Elite Bank</h3>
                    <p style="color: #b0c4de; line-height: 1.6; margin-bottom: 20px;">Banca premium para clientes exclusivos, ofreciendo los más altos estándares de servicio y seguridad financiera.</p>
                    <div class="social-links">
                        <a href="#" class="social-link"><i class="fab fa-facebook-f"></i></a>
                        <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
                        <a href="#" class="social-link"><i class="fab fa-linkedin-in"></i></a>
                        <a href="#" class="social-link"><i class="fab fa-instagram"></i></a>
                    </div>
                </div>
                
                <div class="footer-column">
                    <h3>Servicios</h3>
                    <ul class="footer-links">
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Banca Personal</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Banca Empresas</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Inversiones</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Préstamos</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Hipotecas</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Enlaces Rápidos</h3>
                    <ul class="footer-links">
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Sucursales</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Tarifas</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Atención al Cliente</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Preguntas Frecuentes</a></li>
                        <li><a href="#"><i class="fas fa-chevron-right"></i> Trabaja con Nosotros</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Contacto</h3>
                    <div class="contact-info">
                        <div class="contact-item">
                            <i class="fas fa-map-marker-alt"></i>
                            <span>Paseo de la Castellana, 259, Madrid</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-phone"></i>
                            <span>+34 91 123 45 67</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-envelope"></i>
                            <span>info@globalelitebank.com</span>
                        </div>
                        <div class="contact-item">
                            <i class="fas fa-shield-alt"></i>
                            <span>Soporte 24/7 para clientes premium</span>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="copyright">
                &copy; BANCO CREADO POR HUGO MONJAS CON VS CODE - 2023. Todos los derechos reservados.
            </div>
        </div>
    </footer>
    
    <script>
        // Sample transaction data
        const transactions = [
            { id: 1, title: "Transferencia recibida", date: "Hoy, 15:24", amount: "+€ 1,250.00", category: "income", icon: "fa-exchange-alt", status: "completed" },
            { id: 2, title: "Compra en Amazon", date: "Ayer, 19:45", amount: "-€ 89.99", category: "shopping", icon: "fa-shopping-cart", status: "completed" },
            { id: 3, title: "Pago de hipoteca", date: "15 Jun 2023", amount: "-€ 1,850.00", category: "home", icon: "fa-home", status: "completed" },
            { id: 4, title: "Recibo de luz", date: "14 Jun 2023", amount: "-€ 125.60", category: "utilities", icon: "fa-bolt", status: "completed" },
            { id: 5, title: "Depósito de nómina", date: "12 Jun 2023", amount: "+€ 4,250.00", category: "income", icon: "fa-building", status: "completed" },
            { id: 6, title: "Restaurante La Tagliatella", date: "10 Jun 2023", amount: "-€ 68.50", category: "dining", icon: "fa-utensils", status: "completed" },
            { id: 7, title: "Transferencia a inversiones", date: "8 Jun 2023", amount: "-€ 5,000.00", category: "transfer", icon: "fa-random", status: "pending" },
            { id: 8, title: "Ingreso dividendos", date: "5 Jun 2023", amount: "+€ 1,560.40", category: "investment", icon: "fa-chart-line", status: "completed" }
        ];
        
        // Render transactions
        function renderTransactions() {
            const container = document.getElementById('transactions-list');
            container.innerHTML = '';
            
            transactions.forEach(transaction => {
                const transactionEl = document.createElement('div');
                transactionEl.className = 'transaction-item';
                
                // Determine icon color based on transaction type
                const iconColor = transaction.amount.startsWith('+') ? 'color: #2ecc70;' : 'color: #e74c3c;';
                
                transactionEl.innerHTML = `
                    <div class="transaction-icon" style="background: ${getCategoryColor(transaction.category)}">
                        <i class="fas ${transaction.icon}" style="${iconColor}"></i>
                    </div>
                    <div class="transaction-info">
                        <div class="transaction-title">${transaction.title}</div>
                        <div class="transaction-date">${transaction.date}</div>
                    </div>
                    <div class="transaction-amount" style="${iconColor}">${transaction.amount}</div>
                    <div class="transaction-status status-${transaction.status}">
                        ${transaction.status === 'completed' ? 'Completado' : 'Pendiente'}
                    </div>
                `;
                
                container.appendChild(transactionEl);
            });
        }
        
        // Get category color
        function getCategoryColor(category) {
            const colors = {
                'income': 'rgba(46, 204, 113, 0.1)',
                'shopping': 'rgba(231, 76, 60, 0.1)',
                'home': 'rgba(155, 89, 182, 0.1)',
                'utilities': 'rgba(241, 196, 15, 0.1)',
                'dining': 'rgba(230, 126, 34, 0.1)',
                'transfer': 'rgba(52, 152, 219, 0.1)',
                'investment': 'rgba(26, 188, 156, 0.1)'
            };
            
            return colors[category] || 'rgba(52, 152, 219, 0.1)';
        }
        
        // Initialize charts
        function initCharts() {
            // Balance Chart
            const balanceCtx = document.getElementById('balanceChart').getContext('2d');
            const balanceChart = new Chart(balanceCtx, {
                type: 'line',
                data: {
                    labels: ['Ene', 'Feb', 'Mar', 'Abr', 'May', 'Jun'],
                    datasets: [{
                        label: 'Ingresos',
                        data: [11200, 12400, 11800, 13500, 14200, 15400],
                        borderColor: '#2ecc71',
                        backgroundColor: 'rgba(46, 204, 113, 0.1)',
                        tension: 0.3,
                        fill: true
                    }, {
                        label: 'Gastos',
                        data: [7850, 8120, 7650, 8540, 7920, 7890],
                        borderColor: '#e74c3c',
                        backgroundColor: 'rgba(231, 76, 60, 0.1)',
                        tension: 0.3,
                        fill: true
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            labels: {
                                color: '#f0f0f0'
                            }
                        }
                    },
                    scales: {
                        y: {
                            beginAtZero: true,
                            grid: {
                                color: 'rgba(255, 255, 255, 0.1)'
                            },
                            ticks: {
                                color: '#b0c4de'
                            }
                        },
                        x: {
                            grid: {
                                color: 'rgba(255, 255, 255, 0.1)'
                            },
                            ticks: {
                                color: '#b0c4de'
                            }
                        }
                    }
                }
            });
            
            // Expenses Chart
            const expensesCtx = document.getElementById('expensesChart').getContext('2d');
            const expensesChart = new Chart(expensesCtx, {
                type: 'doughnut',
                data: {
                    labels: ['Vivienda', 'Transporte', 'Comida', 'Entretenimiento', 'Compras', 'Otros'],
                    datasets: [{
                        data: [35, 15, 20, 10, 15, 5],
                        backgroundColor: [
                            '#3498db',
                            '#2ecc71',
                            '#e74c3c',
                            '#f39c12',
                            '#9b59b6',
                            '#1abc9c'
                        ],
                        borderWidth: 0
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'right',
                            labels: {
                                color: '#f0f0f0',
                                padding: 20
                            }
                        }
                    }
                }
            });
        }
        
        // Card hover effect
        function initCardHover() {
            const cards = document.querySelectorAll('.credit-card');
            
            cards.forEach(card => {
                card.addEventListener('mousemove', (e) => {
                    const rect = card.getBoundingClientRect();
                    const x = e.clientX - rect.left;
                    const y = e.clientY - rect.top;
                    
                    const centerX = rect.width / 2;
                    const centerY = rect.height / 2;
                    
                    const angleY = (x - centerX) / 25;
                    const angleX = (centerY - y) / 25;
                    
                    card.style.transform = `perspective(1000px) rotateX(${angleX}deg) rotateY(${angleY}deg) scale(1.05)`;
                });
                
                card.addEventListener('mouseleave', () => {
                    card.style.transform = 'perspective(1000px) rotateX(0) rotateY(0) scale(1)';
                });
            });
        }
        
        // Initialize the app
        document.addEventListener('DOMContentLoaded', () => {
            renderTransactions();
            initCharts();
            initCardHover();
            
            // Simulate loading
            setTimeout(() => {
                document.querySelector('.welcome-banner').style.opacity = '1';
            }, 300);
            
            // Add animation to stat cards
            const statCards = document.querySelectorAll('.stat-card');
            statCards.forEach((card, index) => {
                setTimeout(() => {
                    card.style.opacity = '1';
                    card.style.transform = 'translateY(0)';
                }, 200 * index);
            });
        });
    </script>
</body>
</html>
