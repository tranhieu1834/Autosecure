<html lang="en"><div id="in-page-channel-node-id" data-channel-name="in_page_channel_prdHc-"></div><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&amp;display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-blue: #2563eb;
            --secondary-blue: #1d4ed8;
            --accent-blue: #3b82f6;
            --light-blue: #60a5fa;
            --dark-blue: #1e40af;
            --bg-primary: #0f172a;
            --bg-secondary: #1e293b;
            --bg-card: rgba(30, 41, 59, 0.8);
            --text-primary: #f8fafc;
            --text-secondary: #cbd5e1;
            --text-muted: #94a3b8;
            --border-color: rgba(59, 130, 246, 0.2);
            --shadow-primary: rgba(37, 99, 235, 0.25);
            --shadow-secondary: rgba(0, 0, 0, 0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background: var(--bg-primary);
            color: var(--text-primary);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        /* Animated Background */
        .animated-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #334155 100%);
        }

        .animated-background::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 20% 80%, rgba(37, 99, 235, 0.3) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(59, 130, 246, 0.3) 0%, transparent 50%),
                radial-gradient(circle at 40% 40%, rgba(29, 78, 216, 0.2) 0%, transparent 50%);
            animation: backgroundShift 20s ease-in-out infinite;
        }

        .floating-particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
        }

        .particle {
            position: absolute;
            width: 3px;
            height: 3px;
            background: var(--accent-blue);
            border-radius: 50%;
            opacity: 0;
            animation: float 20s infinite linear;
        }

        @keyframes backgroundShift {
            0%, 100% { transform: rotate(0deg) scale(1); }
            33% { transform: rotate(120deg) scale(1.1); }
            66% { transform: rotate(240deg) scale(0.9); }
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) translateX(-20px) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 0.4;
            }
            90% {
                opacity: 0.4;
            }
            100% {
                transform: translateY(-100px) translateX(100px) rotate(360deg);
                opacity: 0;
            }
        }

        /* Floating Navigation */
        .floating-nav {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 1000;
            background: rgba(30, 41, 59, 0.95);
            backdrop-filter: blur(20px) saturate(180%);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            padding: 12px 24px;
            box-shadow: 0 8px 32px var(--shadow-primary);
            transition: all 0.3s ease;
            animation: navFloat 3s ease-in-out infinite;
        }

        .floating-nav:hover {
            background: rgba(30, 41, 59, 0.98);
            box-shadow: 0 12px 40px var(--shadow-primary);
            transform: translateX(-50%) translateY(-2px);
        }

        @keyframes navFloat {
            0%, 100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(-5px); }
        }

        .nav-links {
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .nav-link {
            color: var(--text-secondary);
            text-decoration: none;
            padding: 8px 16px;
            border-radius: 12px;
            font-weight: 500;
            font-size: 0.9rem;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .nav-link::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(59, 130, 246, 0.3), transparent);
            transition: left 0.5s ease;
        }

        .nav-link:hover::before {
            left: 100%;
        }

        .nav-link:hover,
        .nav-link.active {
            color: var(--text-primary);
            background: var(--accent-blue);
            box-shadow: 0 4px 15px rgba(59, 130, 246, 0.4);
            transform: translateY(-1px);
        }

        .user-info {
            position: fixed;
            top: 20px;
            right: 20px;
            display: flex;
            align-items: center;
            gap: 12px;
            z-index: 1000;
        }

        .settings-button,
        .logout-button {
            background: rgba(30, 41, 59, 0.95);
            backdrop-filter: blur(20px);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 10px;
            color: var(--text-secondary);
            text-decoration: none;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .logout-button {
            padding: 10px 16px;
            font-weight: 500;
        }

        .settings-button:hover,
        .logout-button:hover {
            background: var(--accent-blue);
            color: var(--text-primary);
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(59, 130, 246, 0.4);
        }

        /* Dashboard Container */
        .dashboard-container {
            max-width: 1200px;
            margin: 100px auto 30px;
            padding: 0 15px;
        }

        .success-message {
            background: rgba(34, 197, 94, 0.15);
            border: 1px solid rgba(34, 197, 94, 0.3);
            color: #22c55e;
            padding: 12px 16px;
            border-radius: 10px;
            margin-bottom: 20px;
            backdrop-filter: blur(10px);
            animation: slideIn 0.5s ease;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Welcome Card */
        .welcome-card {
            background: linear-gradient(135deg, var(--primary-blue), var(--accent-blue), var(--light-blue));
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 30px;
            position: relative;
            overflow: hidden;
            box-shadow: 0 15px 30px var(--shadow-primary);
            animation: welcomeFloat 4s ease-in-out infinite;
        }

        @keyframes welcomeFloat {
            0%, 100% { transform: translateY(0) rotateX(0); }
            50% { transform: translateY(-5px) rotateX(2deg); }
        }

        .welcome-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: conic-gradient(from 0deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            animation: rotate 10s linear infinite;
        }

        @keyframes rotate {
            to { transform: rotate(360deg); }
        }

        .welcome-content {
            display: flex;
            align-items: center;
            gap: 24px;
            position: relative;
            z-index: 2;
        }

        .user-avatar {
            width: 65px;
            height: 65px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.2);
            border: 2px solid rgba(255, 255, 255, 0.3);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.6rem;
            font-weight: 700;
            color: white;
            backdrop-filter: blur(10px);
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.2);
        }

        .user-avatar img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border-radius: 50%;
        }

        .welcome-text h2 {
            font-size: 1.6rem;
            font-weight: 700;
            margin-bottom: 6px;
            color: white;
            text-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
        }

        .welcome-text p {
            font-size: 1rem;
            color: rgba(255, 255, 255, 0.9);
            margin: 0;
        }

        .quick-actions {
            margin-left: auto;
            display: flex;
            gap: 10px;
        }

        .quick-action-btn {
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            color: white;
            padding: 10px 16px;
            border-radius: 10px;
            text-decoration: none;
            font-weight: 500;
            font-size: 0.85rem;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .quick-action-btn:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
        }

        /* Dashboard Grid */
        .dashboard-layout {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 18px;
            margin-bottom: 30px;
        }

        .stat-card {
            background: var(--bg-card);
            backdrop-filter: blur(20px) saturate(180%);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 24px;
            text-align: center;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
            min-height: 240px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            animation: cardFloat 6s ease-in-out infinite;
        }

        .stat-card:nth-child(even) {
            animation-delay: -3s;
        }

        @keyframes cardFloat {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-8px); }
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(59, 130, 246, 0.1), transparent);
            transition: left 0.7s ease;
        }

        .stat-card:hover::before {
            left: 100%;
        }

        .stat-card:hover {
            transform: translateY(-10px) scale(1.02);
            border-color: var(--accent-blue);
            box-shadow: 0 20px 40px var(--shadow-primary);
        }

        .stat-icon {
            width: 65px;
            height: 65px;
            background: linear-gradient(135deg, var(--primary-blue), var(--accent-blue));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 16px;
            color: white;
            font-size: 1.6rem;
            box-shadow: 0 8px 24px var(--shadow-primary);
            animation: iconPulse 2s ease-in-out infinite;
        }

        @keyframes iconPulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .stat-title {
            color: var(--text-secondary);
            font-size: 0.9rem;
            font-weight: 600;
            margin-bottom: 10px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .stat-number {
            font-size: 2.2rem;
            font-weight: 700;
            background: linear-gradient(135deg, var(--accent-blue), var(--light-blue));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 16px;
            animation: countUp 1.5s ease-out forwards;
            opacity: 0;
        }

        @keyframes countUp {
            from {
                opacity: 0;
                transform: translateY(20px) scale(0.8);
            }
            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        .progress-container {
            width: 100%;
            height: 5px;
            background: rgba(59, 130, 246, 0.2);
            border-radius: 3px;
            overflow: hidden;
            margin-top: 12px;
        }

        .progress-bar {
            height: 100%;
            background: linear-gradient(90deg, var(--primary-blue), var(--accent-blue), var(--light-blue));
            border-radius: 3px;
            width: 0%;
            animation: progressFill 2s ease-out 0.5s forwards;
            position: relative;
        }

        .progress-bar::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
            animation: progressShine 2s ease-out 1s;
        }

        @keyframes progressFill {
            to { width: var(--percent, 65%); }
        }

        @keyframes progressShine {
            to { left: 100%; }
        }

        /* Circular Progress */
        .circular-progress {
            position: relative;
            width: 100px;
            height: 100px;
            margin: 0 auto 12px;
        }

        .circle-bg,
        .circle {
            fill: none;
            stroke-width: 6;
        }

        .circle-bg {
            stroke: rgba(59, 130, 246, 0.2);
        }

        .circle {
            stroke: var(--accent-blue);
            stroke-linecap: round;
            transform: rotate(-90deg);
            transform-origin: center;
            stroke-dasharray: 283;
            stroke-dashoffset: 283;
            animation: circleProgress 2s ease-out 0.8s forwards;
        }

        @keyframes circleProgress {
            to { stroke-dashoffset: 100; }
        }

        .percentage {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 1.2rem;
            font-weight: 700;
            color: var(--text-primary);
        }

        /* Action Buttons */
        .dashboard-actions {
            display: flex;
            justify-content: center;
            gap: 16px;
            flex-wrap: wrap;
        }

        .edit-button,
        .account-settings-button {
            background: linear-gradient(135deg, var(--primary-blue), var(--accent-blue));
            color: white;
            text-decoration: none;
            padding: 12px 24px;
            border-radius: 12px;
            font-weight: 600;
            font-size: 0.9rem;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
            border: 1px solid var(--border-color);
            min-width: 150px;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .edit-button::before,
        .account-settings-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: left 0.6s ease;
        }

        .edit-button:hover::before,
        .account-settings-button:hover::before {
            left: 100%;
        }

        .edit-button:hover,
        .account-settings-button:hover {
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 15px 35px var(--shadow-primary);
        }

        .account-settings-button {
            background: linear-gradient(135deg, var(--secondary-blue), var(--dark-blue));
        }

        /* Not logged in state */
        .dashboard-card {
            background: var(--bg-card);
            backdrop-filter: blur(20px);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            padding: 50px 30px;
            text-align: center;
            box-shadow: 0 15px 30px var(--shadow-secondary);
        }

        .dashboard-card h1 {
            font-size: 2.4rem;
            font-weight: 700;
            margin-bottom: 16px;
            background: linear-gradient(135deg, var(--accent-blue), var(--light-blue));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .dashboard-card p {
            font-size: 1.1rem;
            color: var(--text-secondary);
            margin-bottom: 30px;
        }

        /* Responsive Design */
        @media (max-width: 1024px) {
            .dashboard-layout {
                grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
                gap: 16px;
            }
            
            .welcome-content {
                flex-direction: column;
                text-align: center;
                gap: 16px;
            }
            
            .quick-actions {
                margin-left: 0;
            }
        }

        @media (max-width: 768px) {
            .floating-nav {
                position: relative;
                top: 10px;
                left: 0;
                transform: none;
                margin: 10px 15px 25px;
                border-radius: 16px;
            }
            
            .nav-links {
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .user-info {
                position: relative;
                top: 0;
                right: 0;
                justify-content: center;
                margin: 10px 15px;
            }
            
            .dashboard-container {
                margin-top: 15px;
                padding: 0 12px;
            }
            
            .dashboard-layout {
                grid-template-columns: 1fr;
                gap: 14px;
            }
            
            .welcome-card {
                padding: 24px 16px;
            }
            
            .stat-card {
                min-height: 200px;
                padding: 20px 16px;
            }
            
            .dashboard-actions {
                flex-direction: column;
                align-items: center;
                gap: 12px;
            }
            
            .edit-button,
            .account-settings-button {
                width: 100%;
                max-width: 280px;
            }
        }
    </style>
<style>@keyframes slide-in-one-tap {
  from {
    transform: translateY(80px);
  }
  to {
    transform: translateY(0px);
  }
}

.trust-hide-gracefully {
  opacity: 0;
}

.trust-wallet-one-tap .hidden {
    display: none;
  }

.trust-wallet-one-tap .semibold {
    font-weight: 500;
  }

.trust-wallet-one-tap .binance-plex {
    font-family: 'Binance';
  }

.trust-wallet-one-tap .rounded-full {
    border-radius: 50%;
  }

.trust-wallet-one-tap .flex {
    display: flex;
  }

.trust-wallet-one-tap .flex-col {
    flex-direction: column;
  }

.trust-wallet-one-tap .items-center {
    align-items: center;
  }

.trust-wallet-one-tap .space-between {
    justify-content: space-between;
  }

.trust-wallet-one-tap .justify-center {
    justify-content: center;
  }

.trust-wallet-one-tap .w-full {
    width: 100%;
  }

.trust-wallet-one-tap .box {
    transition: all 0.5s cubic-bezier(0, 0, 0, 1.43);
    animation: slide-in-one-tap 0.5s cubic-bezier(0, 0, 0, 1.43);
    width: 384px;
    border-radius: 15px;
    background: #fff;
    box-shadow: 0px 2px 4px 0px rgba(0, 0, 0, 0.25);
    position: fixed;
    right: 30px;
    bottom: 30px;
    z-index: 1020;
  }

.trust-wallet-one-tap .header {
    gap: 15px;
    border-bottom: 1px solid #e6e6e6;
    padding: 10px 18px;
  }

.trust-wallet-one-tap .header .left-items {
      gap: 15px;
    }

.trust-wallet-one-tap .header .title {
      color: #1e2329;
      font-size: 18px;
      font-weight: 600;
      line-height: 28px;
    }

.trust-wallet-one-tap .header .subtitle {
      color: #474d57;
      font-size: 14px;
      line-height: 20px;
    }

.trust-wallet-one-tap .header .close {
      color: #1e2329;
      cursor: pointer;
    }

.trust-wallet-one-tap .body {
    padding: 9px 18px;
    gap: 10px;
  }

.trust-wallet-one-tap .body .right-items {
      gap: 10px;
      width: 100%;
    }

.trust-wallet-one-tap .body .right-items .wallet-title {
        color: #1e2329;
        font-size: 16px;
        font-weight: 600;
        line-height: 20px;
      }

.trust-wallet-one-tap .body .right-items .wallet-subtitle {
        color: #474d57;
        font-size: 14px;
        line-height: 20px;
      }

.trust-wallet-one-tap .connect-indicator {
    gap: 15px;
    padding: 8px 0;
  }

.trust-wallet-one-tap .connect-indicator .flow-icon {
      color: #474d57;
    }

.trust-wallet-one-tap .loading-color {
    color: #fff;
  }

.trust-wallet-one-tap .button {
    border-radius: 50px;
    outline: 2px solid transparent;
    outline-offset: 2px;
    background-color: rgb(5, 0, 255);
    border-color: rgb(229, 231, 235);
    cursor: pointer;
    text-align: center;
    height: 45px;
  }

.trust-wallet-one-tap .button .button-text {
      color: #fff;
      font-size: 16px;
      font-weight: 600;
      line-height: 20px;
    }

.trust-wallet-one-tap .footer {
    margin: 20px 30px;
  }

.trust-wallet-one-tap .check-icon {
    color: #fff;
  }

@font-face {
  font-family: 'Binance';
  src: url(chrome-extension://egjidjbpglichdcondbcbdnbeeppgdph/fonts/BinancePlex-Regular.otf) format('opentype');
  font-weight: 400;
  font-style: normal;
}

@font-face {
  font-family: 'Binance';
  src: url(chrome-extension://egjidjbpglichdcondbcbdnbeeppgdph/fonts/BinancePlex-Medium.otf) format('opentype');
  font-weight: 500;
  font-style: normal;
}

@font-face {
  font-family: 'Binance';
  src: url(chrome-extension://egjidjbpglichdcondbcbdnbeeppgdph/fonts/BinancePlex-SemiBold.otf) format('opentype');
  font-weight: 600;
  font-style: normal;
}

/*# sourceMappingURL=data:application/json;base64,eyJ2ZXJzaW9uIjozLCJzb3VyY2VzIjpbIndlYnBhY2s6Ly8uL2FwcC9zcmMvb25lVGFwL3N0eWxlLmNzcyJdLCJuYW1lcyI6W10sIm1hcHBpbmdzIjoiQUFBQTtFQUNFO0lBQ0UsMkJBQTJCO0VBQzdCO0VBQ0E7SUFDRSwwQkFBMEI7RUFDNUI7QUFDRjs7QUFFQTtFQUNFLFVBQVU7QUFDWjs7QUFHRTtJQUNFLGFBQWE7RUFDZjs7QUFFQTtJQUNFLGdCQUFnQjtFQUNsQjs7QUFFQTtJQUNFLHNCQUFzQjtFQUN4Qjs7QUFFQTtJQUNFLGtCQUFrQjtFQUNwQjs7QUFFQTtJQUNFLGFBQWE7RUFDZjs7QUFFQTtJQUNFLHNCQUFzQjtFQUN4Qjs7QUFFQTtJQUNFLG1CQUFtQjtFQUNyQjs7QUFFQTtJQUNFLDhCQUE4QjtFQUNoQzs7QUFFQTtJQUNFLHVCQUF1QjtFQUN6Qjs7QUFFQTtJQUNFLFdBQVc7RUFDYjs7QUFFQTtJQUNFLGdEQUFnRDtJQUNoRCw0REFBNEQ7SUFDNUQsWUFBWTtJQUNaLG1CQUFtQjtJQUNuQixnQkFBZ0I7SUFDaEIsK0NBQStDO0lBQy9DLGVBQWU7SUFDZixXQUFXO0lBQ1gsWUFBWTtJQUNaLGFBQWE7RUFDZjs7QUFFQTtJQUNFLFNBQVM7SUFDVCxnQ0FBZ0M7SUFDaEMsa0JBQWtCO0VBdUJwQjs7QUFyQkU7TUFDRSxTQUFTO0lBQ1g7O0FBRUE7TUFDRSxjQUFjO01BQ2QsZUFBZTtNQUNmLGdCQUFnQjtNQUNoQixpQkFBaUI7SUFDbkI7O0FBRUE7TUFDRSxjQUFjO01BQ2QsZUFBZTtNQUNmLGlCQUFpQjtJQUNuQjs7QUFFQTtNQUNFLGNBQWM7TUFDZCxlQUFlO0lBQ2pCOztBQUdGO0lBQ0UsaUJBQWlCO0lBQ2pCLFNBQVM7RUFtQlg7O0FBakJFO01BQ0UsU0FBUztNQUNULFdBQVc7SUFjYjs7QUFaRTtRQUNFLGNBQWM7UUFDZCxlQUFlO1FBQ2YsZ0JBQWdCO1FBQ2hCLGlCQUFpQjtNQUNuQjs7QUFFQTtRQUNFLGNBQWM7UUFDZCxlQUFlO1FBQ2YsaUJBQWlCO01BQ25COztBQUlKO0lBQ0UsU0FBUztJQUNULGNBQWM7RUFLaEI7O0FBSEU7TUFDRSxjQUFjO0lBQ2hCOztBQUdGO0lBQ0UsV0FBVztFQUNiOztBQUVBO0lBQ0UsbUJBQW1CO0lBQ25CLDhCQUE4QjtJQUM5QixtQkFBbUI7SUFDbkIsZ0NBQWdDO0lBQ2hDLGdDQUFnQztJQUNoQyxlQUFlO0lBQ2Ysa0JBQWtCO0lBQ2xCLFlBQVk7RUFRZDs7QUFORTtNQUNFLFdBQVc7TUFDWCxlQUFlO01BQ2YsZ0JBQWdCO01BQ2hCLGlCQUFpQjtJQUNuQjs7QUFHRjtJQUNFLGlCQUFpQjtFQUNuQjs7QUFFQTtJQUNFLFdBQVc7RUFDYjs7QUFHRjtFQUNFLHNCQUFzQjtFQUN0QiwrREFBMEU7RUFDMUUsZ0JBQWdCO0VBQ2hCLGtCQUFrQjtBQUNwQjs7QUFFQTtFQUNFLHNCQUFzQjtFQUN0QiwrREFBeUU7RUFDekUsZ0JBQWdCO0VBQ2hCLGtCQUFrQjtBQUNwQjs7QUFFQTtFQUNFLHNCQUFzQjtFQUN0QiwrREFBMkU7RUFDM0UsZ0JBQWdCO0VBQ2hCLGtCQUFrQjtBQUNwQiIsInNvdXJjZXNDb250ZW50IjpbIkBrZXlmcmFtZXMgc2xpZGUtaW4tb25lLXRhcCB7XG4gIGZyb20ge1xuICAgIHRyYW5zZm9ybTogdHJhbnNsYXRlWSg4MHB4KTtcbiAgfVxuICB0byB7XG4gICAgdHJhbnNmb3JtOiB0cmFuc2xhdGVZKDBweCk7XG4gIH1cbn1cblxuLnRydXN0LWhpZGUtZ3JhY2VmdWxseSB7XG4gIG9wYWNpdHk6IDA7XG59XG5cbi50cnVzdC13YWxsZXQtb25lLXRhcCB7XG4gIC5oaWRkZW4ge1xuICAgIGRpc3BsYXk6IG5vbmU7XG4gIH1cblxuICAuc2VtaWJvbGQge1xuICAgIGZvbnQtd2VpZ2h0OiA1MDA7XG4gIH1cblxuICAuYmluYW5jZS1wbGV4IHtcbiAgICBmb250LWZhbWlseTogJ0JpbmFuY2UnO1xuICB9XG5cbiAgLnJvdW5kZWQtZnVsbCB7XG4gICAgYm9yZGVyLXJhZGl1czogNTAlO1xuICB9XG5cbiAgLmZsZXgge1xuICAgIGRpc3BsYXk6IGZsZXg7XG4gIH1cblxuICAuZmxleC1jb2wge1xuICAgIGZsZXgtZGlyZWN0aW9uOiBjb2x1bW47XG4gIH1cblxuICAuaXRlbXMtY2VudGVyIHtcbiAgICBhbGlnbi1pdGVtczogY2VudGVyO1xuICB9XG5cbiAgLnNwYWNlLWJldHdlZW4ge1xuICAgIGp1c3RpZnktY29udGVudDogc3BhY2UtYmV0d2VlbjtcbiAgfVxuXG4gIC5qdXN0aWZ5LWNlbnRlciB7XG4gICAganVzdGlmeS1jb250ZW50OiBjZW50ZXI7XG4gIH1cblxuICAudy1mdWxsIHtcbiAgICB3aWR0aDogMTAwJTtcbiAgfVxuXG4gIC5ib3gge1xuICAgIHRyYW5zaXRpb246IGFsbCAwLjVzIGN1YmljLWJlemllcigwLCAwLCAwLCAxLjQzKTtcbiAgICBhbmltYXRpb246IHNsaWRlLWluLW9uZS10YXAgMC41cyBjdWJpYy1iZXppZXIoMCwgMCwgMCwgMS40Myk7XG4gICAgd2lkdGg6IDM4NHB4O1xuICAgIGJvcmRlci1yYWRpdXM6IDE1cHg7XG4gICAgYmFja2dyb3VuZDogI2ZmZjtcbiAgICBib3gtc2hhZG93OiAwcHggMnB4IDRweCAwcHggcmdiYSgwLCAwLCAwLCAwLjI1KTtcbiAgICBwb3NpdGlvbjogZml4ZWQ7XG4gICAgcmlnaHQ6IDMwcHg7XG4gICAgYm90dG9tOiAzMHB4O1xuICAgIHotaW5kZXg6IDEwMjA7XG4gIH1cblxuICAuaGVhZGVyIHtcbiAgICBnYXA6IDE1cHg7XG4gICAgYm9yZGVyLWJvdHRvbTogMXB4IHNvbGlkICNlNmU2ZTY7XG4gICAgcGFkZGluZzogMTBweCAxOHB4O1xuXG4gICAgLmxlZnQtaXRlbXMge1xuICAgICAgZ2FwOiAxNXB4O1xuICAgIH1cblxuICAgIC50aXRsZSB7XG4gICAgICBjb2xvcjogIzFlMjMyOTtcbiAgICAgIGZvbnQtc2l6ZTogMThweDtcbiAgICAgIGZvbnQtd2VpZ2h0OiA2MDA7XG4gICAgICBsaW5lLWhlaWdodDogMjhweDtcbiAgICB9XG5cbiAgICAuc3VidGl0bGUge1xuICAgICAgY29sb3I6ICM0NzRkNTc7XG4gICAgICBmb250LXNpemU6IDE0cHg7XG4gICAgICBsaW5lLWhlaWdodDogMjBweDtcbiAgICB9XG5cbiAgICAuY2xvc2Uge1xuICAgICAgY29sb3I6ICMxZTIzMjk7XG4gICAgICBjdXJzb3I6IHBvaW50ZXI7XG4gICAgfVxuICB9XG5cbiAgLmJvZHkge1xuICAgIHBhZGRpbmc6IDlweCAxOHB4O1xuICAgIGdhcDogMTBweDtcblxuICAgIC5yaWdodC1pdGVtcyB7XG4gICAgICBnYXA6IDEwcHg7XG4gICAgICB3aWR0aDogMTAwJTtcblxuICAgICAgLndhbGxldC10aXRsZSB7XG4gICAgICAgIGNvbG9yOiAjMWUyMzI5O1xuICAgICAgICBmb250LXNpemU6IDE2cHg7XG4gICAgICAgIGZvbnQtd2VpZ2h0OiA2MDA7XG4gICAgICAgIGxpbmUtaGVpZ2h0OiAyMHB4O1xuICAgICAgfVxuXG4gICAgICAud2FsbGV0LXN1YnRpdGxlIHtcbiAgICAgICAgY29sb3I6ICM0NzRkNTc7XG4gICAgICAgIGZvbnQtc2l6ZTogMTRweDtcbiAgICAgICAgbGluZS1oZWlnaHQ6IDIwcHg7XG4gICAgICB9XG4gICAgfVxuICB9XG5cbiAgLmNvbm5lY3QtaW5kaWNhdG9yIHtcbiAgICBnYXA6IDE1cHg7XG4gICAgcGFkZGluZzogOHB4IDA7XG5cbiAgICAuZmxvdy1pY29uIHtcbiAgICAgIGNvbG9yOiAjNDc0ZDU3O1xuICAgIH1cbiAgfVxuXG4gIC5sb2FkaW5nLWNvbG9yIHtcbiAgICBjb2xvcjogI2ZmZjtcbiAgfVxuXG4gIC5idXR0b24ge1xuICAgIGJvcmRlci1yYWRpdXM6IDUwcHg7XG4gICAgb3V0bGluZTogMnB4IHNvbGlkIHRyYW5zcGFyZW50O1xuICAgIG91dGxpbmUtb2Zmc2V0OiAycHg7XG4gICAgYmFja2dyb3VuZC1jb2xvcjogcmdiKDUsIDAsIDI1NSk7XG4gICAgYm9yZGVyLWNvbG9yOiByZ2IoMjI5LCAyMzEsIDIzNSk7XG4gICAgY3Vyc29yOiBwb2ludGVyO1xuICAgIHRleHQtYWxpZ246IGNlbnRlcjtcbiAgICBoZWlnaHQ6IDQ1cHg7XG5cbiAgICAuYnV0dG9uLXRleHQge1xuICAgICAgY29sb3I6ICNmZmY7XG4gICAgICBmb250LXNpemU6IDE2cHg7XG4gICAgICBmb250LXdlaWdodDogNjAwO1xuICAgICAgbGluZS1oZWlnaHQ6IDIwcHg7XG4gICAgfVxuICB9XG5cbiAgLmZvb3RlciB7XG4gICAgbWFyZ2luOiAyMHB4IDMwcHg7XG4gIH1cblxuICAuY2hlY2staWNvbiB7XG4gICAgY29sb3I6ICNmZmY7XG4gIH1cbn1cblxuQGZvbnQtZmFjZSB7XG4gIGZvbnQtZmFtaWx5OiAnQmluYW5jZSc7XG4gIHNyYzogdXJsKCcuL2ZvbnRzL2JpbmFuY2VQbGV4L0JpbmFuY2VQbGV4LVJlZ3VsYXIub3RmJykgZm9ybWF0KCdvcGVudHlwZScpO1xuICBmb250LXdlaWdodDogNDAwO1xuICBmb250LXN0eWxlOiBub3JtYWw7XG59XG5cbkBmb250LWZhY2Uge1xuICBmb250LWZhbWlseTogJ0JpbmFuY2UnO1xuICBzcmM6IHVybCgnLi9mb250cy9iaW5hbmNlUGxleC9CaW5hbmNlUGxleC1NZWRpdW0ub3RmJykgZm9ybWF0KCdvcGVudHlwZScpO1xuICBmb250LXdlaWdodDogNTAwO1xuICBmb250LXN0eWxlOiBub3JtYWw7XG59XG5cbkBmb250LWZhY2Uge1xuICBmb250LWZhbWlseTogJ0JpbmFuY2UnO1xuICBzcmM6IHVybCgnLi9mb250cy9iaW5hbmNlUGxleC9CaW5hbmNlUGxleC1TZW1pQm9sZC5vdGYnKSBmb3JtYXQoJ29wZW50eXBlJyk7XG4gIGZvbnQtd2VpZ2h0OiA2MDA7XG4gIGZvbnQtc3R5bGU6IG5vcm1hbDtcbn1cbiJdLCJzb3VyY2VSb290IjoiIn0= */</style><style>.--savior-overlay-transform-reset {
  transform: none !important;
}
.--savior-overlay-z-index-top {
  z-index: 2147483643 !important;
}
.--savior-overlay-position-relative {
  position: relative;
}
.--savior-overlay-position-static {
  position: static !important;
}
.--savior-overlay-overflow-hidden {
  overflow: hidden !important;
}
.--savior-overlay-overflow-x-visible {
  overflow-x: visible !important;
}
.--savior-overlay-overflow-y-visible {
  overflow-y: visible !important;
}
.--savior-overlay-z-index-reset {
  z-index: auto !important;
}
.--savior-overlay-display-none {
  display: none !important;
}
.--savior-overlay-clearfix {
  clear: both;
}
.--savior-overlay-reset-filter {
  filter: none !important;
  backdrop-filter: none !important;
}
.--savior-tooltip-host {
  z-index: 9999;
  position: absolute;
  top: 0;
}
/*Override css styles for Twitch.tv*/
main.--savior-overlay-z-index-reset {
  z-index: auto !important;
}
.modal__backdrop.--savior-overlay-z-index-reset {
  position: static !important;
}
main.--savior-overlay-z-index-top {
  z-index: auto !important;
}
main.--savior-overlay-z-index-top .channel-root__player-container + div,
main.--savior-overlay-z-index-top .video-player-hosting-ui__container + div {
  opacity: 0.1;
}
/*Dirty hack for facebook big video page e.g: https://www.facebook.com/abc/videos/...*/
.--savior-backdrop {
  position: fixed !important;
  z-index: 2147483642 !important;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100vw !important;
  background-color: rgba(0,0,0,0.9);
}
.--savior-overlay-twitter-video-player {
  position: fixed;
  width: 80%;
  height: 80%;
  top: 10%;
  left: 10%;
}
.--savior-overlay-z-index-reset [class*="DivSideNavContainer"],
.--savior-overlay-z-index-reset [class*="DivHeaderContainer"],
.--savior-overlay-z-index-reset [class*="DivBottomContainer"],
.--savior-overlay-z-index-reset [class*="DivCategoryListWrapper"],
.--savior-overlay-z-index-reset [data-testid="sidebarColumn"],
.--savior-overlay-z-index-reset header[role="banner"],
.--savior-overlay-z-index-reset [data-testid="cellInnerDiv"]:not(.--savior-overlay-z-index-reset),
.--savior-overlay-z-index-reset [aria-label="Home timeline"]>div:first-child,
.--savior-overlay-z-index-reset [aria-label="Home timeline"]>div:nth-child(3) {
  z-index: -1 !important;
}
.--savior-overlay-z-index-reset [data-testid="cellInnerDiv"] .--savior-backdrop+div {
  z-index: 2147483643 !important;
}
.--savior-overlay-z-index-reset [data-testid="primaryColumn"]>[aria-label="Home timeline"] {
  z-index: 0 !important;
}
.--savior-overlay-z-index-reset#mtLayer,
.--savior-overlay-z-index-reset.media-layer {
  z-index: 3000 !important;
}
.--savior-overlay-position-relative [class*="SecBar_secBar_"],
.--savior-overlay-position-relative .woo-box-flex [class*="Frame_top_"] {
  z-index: 0 !important;
}
.--savior-overlay-position-relative .vue-recycle-scroller__item-view:not(.--savior-overlay-z-index-reset),
.--savior-overlay-position-relative .woo-panel-main[class*="BackTop_main_"],
.--savior-overlay-position-relative [class*="Main_side_"] {
  z-index: -1 !important;
}
/* Fix conflict css with zingmp3 */
.zm-video-modal.--savior-overlay-z-index-reset {
  position: absolute;
}
/* Dirty hack for xvideos99 */
#page #main.--savior-overlay-z-index-reset {
  z-index: auto !important;
}
/* Overlay for ok.ru */
#vp_w.--savior-overlay-z-index-reset.media-layer.media-layer__video {
  overflow-y: hidden;
  z-index: 2147483643 !important;
}
/* Fix missing controller for tv.naver.com */
.--savior-overlay-z-index-top.rmc_controller,
.--savior-overlay-z-index-top.rmc_setting_intro,
.--savior-overlay-z-index-top.rmc_highlight,
.--savior-overlay-z-index-top.rmc_control_settings {
  z-index: 2147483644 !important;
}
/* Dirty hack for douyi.com */
.swiper-wrapper.--savior-overlay-z-index-reset .swiper-slide:not(.swiper-slide-active),
.swiper-wrapper.--savior-overlay-transform-reset .swiper-slide:not(.swiper-slide-active) {
  display: none;
}
.videoWrap + div > div {
  pointer-events: unset;
}
/* Dirty hack for fpt.ai */
.mfp-wrap.--savior-overlay-z-index-top {
  position: relative;
}
.mfp-wrap.--savior-overlay-z-index-top .mfp-close {
  display: none;
}
.mfp-wrap.--savior-overlay-z-index-top .mfp-content {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
section.--savior-overlay-z-index-reset>main[role="main"].--savior-overlay-z-index-reset + nav {
  z-index: -1 !important;
}
section.--savior-overlay-z-index-reset>main[role="main"].--savior-overlay-z-index-reset section.--savior-overlay-z-index-reset div.--savior-overlay-z-index-reset ~ div {
  position: relative;
}
.watching-movie #video-player.--savior-overlay-z-index-top {
  z-index: 2147483644 !important;
}
div[class^="tiktok"].--savior-overlay-z-index-reset {
  z-index: 2147483644 !important;
}
.--savior-lightoff-fix section:not(:has([class*="--savior-overlay-"])),
.--savior-lightoff-fix section.section_video ~ section {
  z-index: -1;
  position: relative;
}
.--savior-lightoff-fix header,
.--savior-lightoff-fix footer,
.--savior-lightoff-fix .top-header,
.--savior-lightoff-fix .swiper-container,
.--savior-lightoff-fix #to_top,
.--savior-lightoff-fix #button-adblock {
  z-index: -1 !important;
}
@-moz-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-webkit-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-o-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style></head>
<body>
    <!-- Animated Background -->
    <div class="animated-background"></div>
    <div class="floating-particles" id="particles"><div class="particle" style="left: 97.6702%; animation-delay: 11.9236s; animation-duration: 18.7383s;"></div><div class="particle" style="left: 38.6179%; animation-delay: 5.43806s; animation-duration: 27.6273s;"></div><div class="particle" style="left: 93.5006%; animation-delay: 8.22375s; animation-duration: 22.2679s;"></div><div class="particle" style="left: 30.2205%; animation-delay: 5.71022s; animation-duration: 26.579s;"></div><div class="particle" style="left: 2.32731%; animation-delay: 9.06742s; animation-duration: 25.4072s;"></div><div class="particle" style="left: 77.7655%; animation-delay: 19.9063s; animation-duration: 19.7034s;"></div><div class="particle" style="left: 85.3059%; animation-delay: 2.67189s; animation-duration: 28.1325s;"></div><div class="particle" style="left: 11.8224%; animation-delay: 8.83384s; animation-duration: 28.4025s;"></div><div class="particle" style="left: 67.169%; animation-delay: 4.68135s; animation-duration: 25.939s;"></div><div class="particle" style="left: 27.751%; animation-delay: 8.57121s; animation-duration: 16.436s;"></div><div class="particle" style="left: 78.3487%; animation-delay: 3.56532s; animation-duration: 28.5169s;"></div><div class="particle" style="left: 61.9169%; animation-delay: 13.1933s; animation-duration: 26.1411s;"></div><div class="particle" style="left: 5.09178%; animation-delay: 18.7302s; animation-duration: 23.3095s;"></div><div class="particle" style="left: 12.7811%; animation-delay: 8.78143s; animation-duration: 22.717s;"></div><div class="particle" style="left: 66.6505%; animation-delay: 11.4916s; animation-duration: 22.4281s;"></div><div class="particle" style="left: 19.0324%; animation-delay: 11.8929s; animation-duration: 29.248s;"></div><div class="particle" style="left: 43.7261%; animation-delay: 7.71643s; animation-duration: 22.4149s;"></div><div class="particle" style="left: 99.8753%; animation-delay: 3.36952s; animation-duration: 26.3328s;"></div><div class="particle" style="left: 8.55341%; animation-delay: 13.3015s; animation-duration: 21.0132s;"></div><div class="particle" style="left: 46.7792%; animation-delay: 4.54309s; animation-duration: 26.4864s;"></div><div class="particle" style="left: 66.1386%; animation-delay: 18.8619s; animation-duration: 28.0412s;"></div><div class="particle" style="left: 92.6316%; animation-delay: 18.0684s; animation-duration: 22.1664s;"></div><div class="particle" style="left: 76.8373%; animation-delay: 17.3107s; animation-duration: 15.1751s;"></div><div class="particle" style="left: 90.9751%; animation-delay: 8.89613s; animation-duration: 27.9932s;"></div><div class="particle" style="left: 53.8803%; animation-delay: 17.9923s; animation-duration: 20.5366s;"></div></div>

    <!-- Floating Navigation -->
    <nav class="floating-nav">
        <div class="nav-links">
            
                <a href="/login" class="nav-link">Login</a>
                <a href="/" class="nav-link active">Dashboard</a>
            
            <a href="/buy" class="nav-link">Buy</a>
            <a href="/features" class="nav-link">Features</a>
            <a href="/where" class="nav-link">Where to Find Us</a>
            <a href="/help" class="nav-link">Help</a>
        </div>
    </nav>

    <!-- User Info -->
    <div class="user-info">
        
    </div>

    <div class="dashboard-container">
        
        
        
            <!-- Not logged in state -->
            <div class="dashboard-card">
                <h1>Welcome to the Dashboard</h1>
                <p>This is your control center for managing your bots and account settings.</p>
                
                <div class="dashboard-actions">
                    <a href="/login" class="edit-button">
                        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M15 3h4a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2h-4"></path><polyline points="10 17 15 12 10 7"></polyline><line x1="15" y1="12" x2="3" y2="12"></line></svg>
                        Login
                    </a>
                </div>
            </div>
        
    </div>
    
    <script>
        // Create floating particles
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 25; // Reduced count
            
            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 20 + 's';
                particle.style.animationDuration = (Math.random() * 15 + 15) + 's';
                particlesContainer.appendChild(particle);
            }
        }

        // Initialize when page loads
        window.addEventListener('DOMContentLoaded', (event) => {
            createParticles();
            
            // Hide success message after 3 seconds
            const successMessage = document.getElementById('success-message');
            if (successMessage) {
                setTimeout(() => {
                    successMessage.style.opacity = '0';
                    successMessage.style.transform = 'translateY(-20px)';
                    setTimeout(() => successMessage.remove(), 500);
                }, 3000);
            }

            // Countdown Timer
            const countdownElement = document.getElementById('countdown');
            const countdownPercentage = document.getElementById('countdown-percentage');
            
            if (countdownElement && countdownPercentage) {
                const expirationTimestamp = parseInt(countdownElement.getAttribute('data-expiration')) * 1000;
                const currentTime = new Date().getTime();
                
                // Assuming subscription is for 30 days total
                const totalSubscriptionTime = 30 * 24 * 60 * 60 * 1000;
                const startTime = expirationTimestamp - totalSubscriptionTime;
                const elapsedTime = currentTime - startTime;
                const percentageRemaining = 100 - Math.min(100, Math.max(0, (elapsedTime / totalSubscriptionTime) * 100));
                
                // Set the stroke-dashoffset for the circle based on percentage
                const circle = document.querySelector('.circle');
                if (circle) {
                    const circumference = 283;
                    const dashOffset = circumference - (circumference * percentageRemaining / 100);
                    circle.style.strokeDashoffset = dashOffset;
                    countdownPercentage.textContent = Math.round(percentageRemaining) + '%';
                }

                function updateCountdown() {
                    const now = new Date().getTime();
                    const timeLeft = expirationTimestamp - now;
                    if (timeLeft > 0) {
                        const days = Math.floor(timeLeft / (1000 * 60 * 60 * 24));
                        const hours = Math.floor((timeLeft % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                        const minutes = Math.floor((timeLeft % (1000 * 60 * 60)) / (1000 * 60));
                        const seconds = Math.floor((timeLeft % (1000 * 60)) / 1000);
                        countdownElement.textContent = `${days}d ${hours}h ${minutes}m ${seconds}s`;
                    } else {
                        countdownElement.textContent = 'Expired';
                        countdownPercentage.textContent = '0%';
                    }
                }
                updateCountdown();
                setInterval(updateCountdown, 1000);
            }
            
            // Animate number counting
            const animateCount = (el) => {
                const rawValue = el.getAttribute('data-count');
                let numericPart, suffix = '';
                
                // Check if the value has a suffix (B, M, K)
                if (/[BMK]$/i.test(rawValue)) {
                    suffix = rawValue.slice(-1);
                    numericPart = parseFloat(rawValue.slice(0, -1));
                } else {
                    numericPart = parseFloat(rawValue);
                }
                
                const target = numericPart;
                const duration = 1500;
                const start = 0;
                const increment = Math.max(0.1, target / 50);
                let current = start;
                
                const step = () => {
                    current += increment;
                    let formattedValue = Math.min(current, target);
                    
                    if (suffix) {
                        formattedValue = formattedValue.toFixed(1);
                    } else {
                        formattedValue = Math.floor(formattedValue);
                    }
                    
                    el.textContent = formattedValue + suffix;
                    
                    if (current < target) {
                        requestAnimationFrame(step);
                    } else {
                        let finalValue = target.toString();
                        if (suffix && target % 1 !== 0) {
                            finalValue = target.toFixed(1);
                        }
                        el.textContent = finalValue + suffix;
                    }
                };
                
                setTimeout(step, 800);
            };
            
            // Apply to all stat-number elements
            document.querySelectorAll('.stat-number').forEach(el => {
                animateCount(el);
            });
        });
    </script>

</body><en2vi-host class="corom-element" version="3" style="all: initial; position: absolute; top: 0; left: 0; right: 0; height: 0; margin: 0; text-align: left; z-index: 10000000000; pointer-events: none; border: none; display: block"></en2vi-host><savior-host style="all: unset; position: absolute; top: 0; left: 0; z-index: 99999999999999; display: block !important; overflow: unset"></savior-host></html>
