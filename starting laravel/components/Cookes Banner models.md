```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GDPR Cookie Popup Designs</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .demo-section {
            margin-bottom: 40px;
            text-align: center;
        }

        .demo-title {
            color: white;
            font-size: 24px;
            margin-bottom: 20px;
            text-shadow: 0 2px 4px rgba(0,0,0,0.3);
        }

        .show-popup {
            background: rgba(255,255,255,0.2);
            border: 2px solid rgba(255,255,255,0.3);
            color: white;
            padding: 12px 24px;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
            font-size: 16px;
            margin: 10px;
        }

        .show-popup:hover {
            background: rgba(255,255,255,0.3);
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.2);
        }

        /* Design 1: Bottom Bar */
        .cookie-popup-1 {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: white;
            padding: 20px;
            box-shadow: 0 -4px 20px rgba(0,0,0,0.3);
            transform: translateY(100%);
            transition: transform 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            z-index: 1000;
        }

        .cookie-popup-1.show {
            transform: translateY(0);
        }

        .cookie-content-1 {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            align-items: center;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 20px;
        }

        .cookie-text-1 {
            flex: 1;
            min-width: 300px;
        }

        .cookie-text-1 h3 {
            font-size: 18px;
            margin-bottom: 8px;
        }

        .cookie-text-1 p {
            opacity: 0.9;
            line-height: 1.5;
        }

        .cookie-buttons-1 {
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
        }

        .btn-1 {
            padding: 12px 24px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            font-size: 14px;
        }

        .btn-accept-1 {
            background: #10b981;
            color: white;
        }

        .btn-accept-1:hover {
            background: #059669;
            transform: translateY(-2px);
        }

        .btn-decline-1 {
            background: transparent;
            color: white;
            border: 2px solid rgba(255,255,255,0.3);
        }

        .btn-decline-1:hover {
            background: rgba(255,255,255,0.1);
        }

        .btn-settings-1 {
            background: transparent;
            color: white;
            border: 2px solid rgba(255,255,255,0.3);
        }

        .btn-settings-1:hover {
            background: rgba(255,255,255,0.1);
        }

        /* Design 2: Floating Card */
        .cookie-popup-2 {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 400px;
            max-width: calc(100vw - 40px);
            background: white;
            border-radius: 16px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.15);
            transform: scale(0) rotate(10deg);
            transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            z-index: 1000;
            overflow: hidden;
        }

        .cookie-popup-2.show {
            transform: scale(1) rotate(0deg);
        }

        .cookie-header-2 {
            background: linear-gradient(135deg, #ff6b6b, #ee5a24);
            color: white;
            padding: 20px;
            text-align: center;
        }

        .cookie-header-2 h3 {
            font-size: 18px;
            margin-bottom: 5px;
        }

        .cookie-body-2 {
            padding: 20px;
        }

        .cookie-body-2 p {
            color: #666;
            line-height: 1.6;
            margin-bottom: 20px;
        }

        .cookie-buttons-2 {
            display: flex;
            gap: 10px;
        }

        .btn-2 {
            flex: 1;
            padding: 12px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            font-size: 14px;
        }

        .btn-accept-2 {
            background: #ff6b6b;
            color: white;
        }

        .btn-accept-2:hover {
            background: #ee5a24;
            transform: translateY(-2px);
        }

        .btn-decline-2 {
            background: #f8f9fa;
            color: #666;
            border: 2px solid #e9ecef;
        }

        .btn-decline-2:hover {
            background: #e9ecef;
        }

        /* Design 3: Center Modal */
        .cookie-overlay-3 {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
            z-index: 1000;
        }

        .cookie-overlay-3.show {
            opacity: 1;
            visibility: visible;
        }

        .cookie-popup-3 {
            background: white;
            border-radius: 20px;
            max-width: 500px;
            width: calc(100vw - 40px);
            transform: scale(0.8);
            transition: transform 0.3s ease;
            overflow: hidden;
            box-shadow: 0 25px 50px rgba(0,0,0,0.3);
        }

        .cookie-overlay-3.show .cookie-popup-3 {
            transform: scale(1);
        }

        .cookie-visual-3 {
            height: 120px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 48px;
        }

        .cookie-content-3 {
            padding: 30px;
            text-align: center;
        }

        .cookie-content-3 h3 {
            font-size: 24px;
            color: #333;
            margin-bottom: 15px;
        }

        .cookie-content-3 p {
            color: #666;
            line-height: 1.6;
            margin-bottom: 25px;
        }

        .cookie-buttons-3 {
            display: flex;
            gap: 15px;
            justify-content: center;
        }

        .btn-3 {
            padding: 15px 30px;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            font-size: 16px;
            min-width: 120px;
        }

        .btn-accept-3 {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }

        .btn-accept-3:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(102, 126, 234, 0.4);
        }

        .btn-decline-3 {
            background: #f8f9fa;
            color: #666;
            border: 2px solid #dee2e6;
        }

        .btn-decline-3:hover {
            background: #e9ecef;
            transform: translateY(-2px);
        }

        /* Design 4: Minimalist Top Bar */
        .cookie-popup-4 {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(0,0,0,0.1);
            padding: 15px 20px;
            transform: translateY(-100%);
            transition: transform 0.4s ease;
            z-index: 1000;
        }

        .cookie-popup-4.show {
            transform: translateY(0);
        }

        .cookie-content-4 {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 20px;
        }

        .cookie-text-4 {
            color: #333;
            font-size: 14px;
            flex: 1;
        }

        .cookie-text-4 a {
            color: #667eea;
            text-decoration: none;
            font-weight: 500;
        }

        .cookie-buttons-4 {
            display: flex;
            gap: 10px;
        }

        .btn-4 {
            padding: 8px 16px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 14px;
            transition: all 0.2s ease;
        }

        .btn-accept-4 {
            background: #333;
            color: white;
        }

        .btn-accept-4:hover {
            background: #555;
        }

        .btn-decline-4 {
            background: transparent;
            color: #666;
            border: 1px solid #ddd;
        }

        .btn-decline-4:hover {
            background: #f5f5f5;
        }

        /* Design 5: Side Slide-in */
        .cookie-popup-5 {
            position: fixed;
            left: 20px;
            bottom: 20px;
            width: 350px;
            max-width: calc(100vw - 40px);
            background: #1a1a1a;
            color: white;
            border-radius: 12px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.3);
            transform: translateX(-400px);
            transition: transform 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            z-index: 1000;
        }

        .cookie-popup-5.show {
            transform: translateX(0);
        }

        .cookie-content-5 {
            padding: 25px;
        }

        .cookie-icon-5 {
            width: 40px;
            height: 40px;
            background: #ffd700;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            margin-bottom: 15px;
        }

        .cookie-content-5 h3 {
            font-size: 18px;
            margin-bottom: 10px;
            color: #ffd700;
        }

        .cookie-content-5 p {
            font-size: 14px;
            line-height: 1.5;
            opacity: 0.9;
            margin-bottom: 20px;
        }

        .cookie-buttons-5 {
            display: flex;
            gap: 10px;
        }

        .btn-5 {
            flex: 1;
            padding: 10px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.3s ease;
            font-size: 14px;
        }

        .btn-accept-5 {
            background: #ffd700;
            color: #1a1a1a;
        }

        .btn-accept-5:hover {
            background: #ffed4e;
            transform: translateY(-2px);
        }

        .btn-decline-5 {
            background: transparent;
            color: white;
            border: 1px solid rgba(255,255,255,0.3);
        }

        .btn-decline-5:hover {
            background: rgba(255,255,255,0.1);
        }

        @media (max-width: 768px) {
            .cookie-content-1 {
                flex-direction: column;
                text-align: center;
            }

            .cookie-content-4 {
                flex-direction: column;
                gap: 15px;
                text-align: center;
            }

            .cookie-buttons-3 {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="demo-section">
        <h1 class="demo-title">GDPR Cookie Popup Designs</h1>
        <button class="show-popup" onclick="showPopup(1)">Bottom Bar Design</button>
        <button class="show-popup" onclick="showPopup(2)">Floating Card Design</button>
        <button class="show-popup" onclick="showPopup(3)">Center Modal Design</button>
        <button class="show-popup" onclick="showPopup(4)">Minimalist Top Bar</button>
        <button class="show-popup" onclick="showPopup(5)">Side Slide-in Design</button>
    </div>

    <!-- Design 1: Bottom Bar -->
    <div class="cookie-popup-1" id="popup-1">
        <div class="cookie-content-1">
            <div class="cookie-text-1">
                <h3>🍪 We use cookies</h3>
                <p>We use cookies to enhance your browsing experience, serve personalized ads or content, and analyze our traffic. By clicking "Accept All", you consent to our use of cookies.</p>
            </div>
            <div class="cookie-buttons-1">
                <button class="btn-1 btn-accept-1" onclick="hidePopup(1)">Accept All</button>
                <button class="btn-1 btn-decline-1" onclick="hidePopup(1)">Decline</button>
                <button class="btn-1 btn-settings-1" onclick="hidePopup(1)">Settings</button>
            </div>
        </div>
    </div>

    <!-- Design 2: Floating Card -->
    <div class="cookie-popup-2" id="popup-2">
        <div class="cookie-header-2">
            <h3>🍪 Cookie Consent</h3>
            <p style="opacity: 0.9; font-size: 14px; margin: 0;">Personalize your experience</p>
        </div>
        <div class="cookie-body-2">
            <p>We use cookies to improve your experience on our site. These help us understand how you use our website and allow us to show you relevant content.</p>
            <div class="cookie-buttons-2">
                <button class="btn-2 btn-accept-2" onclick="hidePopup(2)">Accept</button>
                <button class="btn-2 btn-decline-2" onclick="hidePopup(2)">Decline</button>
            </div>
        </div>
    </div>

    <!-- Design 3: Center Modal -->
    <div class="cookie-overlay-3" id="popup-3">
        <div class="cookie-popup-3">
            <div class="cookie-visual-3">🍪</div>
            <div class="cookie-content-3">
                <h3>Cookie Preferences</h3>
                <p>We value your privacy. Choose how you'd like us to use cookies to enhance your experience on our website. You can change these settings at any time.</p>
                <div class="cookie-buttons-3">
                    <button class="btn-3 btn-accept-3" onclick="hidePopup(3)">Accept All</button>
                    <button class="btn-3 btn-decline-3" onclick="hidePopup(3)">Necessary Only</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Design 4: Minimalist Top Bar -->
    <div class="cookie-popup-4" id="popup-4">
        <div class="cookie-content-4">
            <div class="cookie-text-4">
                This website uses cookies to ensure you get the best experience. 
                <a href="#" onclick="event.preventDefault()">Learn more</a>
            </div>
            <div class="cookie-buttons-4">
                <button class="btn-4 btn-accept-4" onclick="hidePopup(4)">Accept</button>
                <button class="btn-4 btn-decline-4" onclick="hidePopup(4)">Decline</button>
            </div>
        </div>
    </div>

    <!-- Design 5: Side Slide-in -->
    <div class="cookie-popup-5" id="popup-5">
        <div class="cookie-content-5">
            <div class="cookie-icon-5">🍪</div>
            <h3>Cookies & Privacy</h3>
            <p>This site uses cookies for analytics, personalized content and ads. By continuing to browse this site, you agree to this use.</p>
            <div class="cookie-buttons-5">
                <button class="btn-5 btn-accept-5" onclick="hidePopup(5)">Got it!</button>
                <button class="btn-5 btn-decline-5" onclick="hidePopup(5)">No thanks</button>
            </div>
        </div>
    </div>

    <script>
        function showPopup(design) {
            // Hide all popups first
            for (let i = 1; i <= 5; i++) {
                hidePopup(i);
            }
            
            // Show the selected popup after a short delay
            setTimeout(() => {
                const popup = document.getElementById(`popup-${design}`);
                popup.classList.add('show');
                
                // Auto-hide after 10 seconds for demo purposes
                setTimeout(() => {
                    hidePopup(design);
                }, 10000);
            }, 300);
        }

        function hidePopup(design) {
            const popup = document.getElementById(`popup-${design}`);
            popup.classList.remove('show');
        }

        // Close modal when clicking overlay
        document.getElementById('popup-3').addEventListener('click', function(e) {
            if (e.target === this) {
                hidePopup(3);
            }
        });

        // Show first popup on page load as demo
        window.addEventListener('load', () => {
            setTimeout(() => showPopup(1), 1000);
        });
    </script>
</body>
</html>
```