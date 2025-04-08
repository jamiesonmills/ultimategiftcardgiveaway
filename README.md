# ultimategiftcardgiveaway
free gift card for everyone just participate
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ultimate Gift Card Giveaway</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #ff1493;
            --secondary: #ffcc00;
            --accent: #00ffff;
            --dark: #120524;
            --light: #ffffff;
        }
        
        body {
            font-family: 'Poppins', sans-serif;
            background-color: var(--dark);
            overflow-x: hidden;
            margin: 0;
            padding: 0;
            color: white;
            background-image: linear-gradient(45deg, #120524 25%, #1d0836 25%, #1d0836 50%, #120524 50%, #120524 75%, #1d0836 75%, #1d0836 100%);
            background-size: 56.57px 56.57px;
        }
        
        .glow {
            text-shadow: 0 0 10px var(--accent), 0 0 20px var(--accent), 0 0 30px var(--accent);
            animation: glow 1.5s ease-in-out infinite alternate;
        }
        
        @keyframes glow {
            from {
                text-shadow: 0 0 10px var(--accent), 0 0 20px var(--accent);
            }
            to {
                text-shadow: 0 0 15px var(--accent), 0 0 25px var(--accent), 0 0 35px var(--accent);
            }
        }
        
        .pulse {
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
            100% {
                transform: scale(1);
            }
        }
        
        .signup-form {
            background: rgba(0, 0, 0, 0.7);
            border: 2px solid var(--primary);
            border-radius: 15px;
            box-shadow: 0 0 20px var(--primary), 0 0 40px rgba(255, 20, 147, 0.5);
        }
        
        .btn-glow {
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 30px;
            padding: 12px 30px;
            font-weight: bold;
            font-size: 1.2rem;
            cursor: pointer;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
            box-shadow: 0 0 10px var(--primary), 0 0 20px rgba(255, 20, 147, 0.5);
        }
        
        .btn-glow:hover {
            transform: scale(1.05);
            box-shadow: 0 0 15px var(--primary), 0 0 30px var(--primary);
        }
        
        .btn-glow:before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: rgba(255, 255, 255, 0.2);
            transform: rotate(45deg);
            animation: shine 3s infinite;
        }
        
        @keyframes shine {
            0% {
                left: -100%;
                top: -100%;
            }
            20% {
                left: 100%;
                top: 100%;
            }
            100% {
                left: 100%;
                top: 100%;
            }
        }
        
        .floating {
            animation: float 3s ease-in-out infinite;
        }
        
        @keyframes float {
            0% {
                transform: translateY(0px);
            }
            50% {
                transform: translateY(-20px);
            }
            100% {
                transform: translateY(0px);
            }
        }
        
        .input-field {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid var(--secondary);
            color: white;
            border-radius: 8px;
            padding: 12px 15px;
            width: 100%;
            margin-bottom: 15px;
            font-size: 1rem;
            transition: all 0.3s;
        }
        
        .input-field:focus {
            border-color: var(--accent);
            box-shadow: 0 0 10px var(--accent);
            outline: none;
        }
        
        .offers-container {
            display: none;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            padding: 20px;
        }
        
        .offer-card {
            background: linear-gradient(135deg, rgba(255, 20, 147, 0.2), rgba(0, 255, 255, 0.2));
            border: 2px solid var(--secondary);
            border-radius: 15px;
            overflow: hidden;
            transition: all 0.3s;
            position: relative;
            height: 300px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        .offer-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.5), 0 0 20px var(--secondary);
        }
        
        .offer-card img {
            max-width: 80%;
            max-height: 60%;
            object-fit: contain;
            transition: transform 0.3s;
        }
        
        .offer-card:hover img {
            transform: scale(1.1);
        }
        
        .offer-title {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.8);
            color: white;
            padding: 10px;
            text-align: center;
            font-weight: bold;
        }
        
        .confetti {
            position: fixed;
            width: 10px;
            height: 10px;
            background-color: var(--primary);
            opacity: 0;
            z-index: 100;
        }
        
        #jackpot-sound {
            display: none;
        }
        
        .coins {
            position: fixed;
            width: 30px;
            height: 30px;
            background: url('https://cdn.jsdelivr.net/gh/simple-icons/simple-icons@v6/icons/bitcoin.svg') no-repeat;
            background-size: contain;
            filter: invert(1) brightness(2);
            z-index: 90;
            opacity: 0;
        }
        
        .spinning-wheel {
            position: absolute;
            top: -50px;
            right: -50px;
            width: 100px;
            height: 100px;
            background: url('https://cdn.jsdelivr.net/gh/simple-icons/simple-icons@v6/icons/roundedicon.svg') no-repeat;
            background-size: contain;
            filter: brightness(2);
            animation: spin 2s linear infinite;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <!-- Sound Effects -->
    <audio id="click-sound" src="https://assets.mixkit.co/sfx/preview/mixkit-arcade-game-jump-coin-216.mp3" preload="auto"></audio>
    <audio id="success-sound" src="https://assets.mixkit.co/sfx/preview/mixkit-winning-chimes-2015.mp3" preload="auto"></audio>
    <audio id="jackpot-sound" src="https://assets.mixkit.co/sfx/preview/mixkit-slot-machine-win-siren-1929.mp3" preload="auto"></audio>
    
    <!-- Signup Section -->
    <div id="signup-section" class="min-h-screen flex items-center justify-center px-4 py-10">
        <div class="signup-form p-8 max-w-lg w-full relative overflow-hidden">
            <div class="spinning-wheel"></div>
            <h1 class="text-4xl font-bold text-center mb-8 glow">🎁 ULTIMATE GIFT CARD GIVEAWAY 🎁</h1>
            <h2 class="text-2xl text-center mb-6 text-yellow-300 pulse">Win Amazing Gift Cards Worth Up To $1000!</h2>
            
            <form id="signup-form" class="space-y-6">
                <div>
                    <label for="name" class="block text-white mb-2">Your Name</label>
                    <input type="text" id="name" name="name" required class="input-field" placeholder="Enter your name">
                </div>
                <div>
                    <label for="email" class="block text-white mb-2">Your Email</label>
                    <input type="email" id="email" name="email" required class="input-field" placeholder="Enter your email">
                </div>
                <div class="mt-8 flex justify-center">
                    <button type="submit" class="btn-glow">GET MY GIFT CARDS!</button>
                </div>
            </form>
            
            <div class="mt-6 text-center text-sm opacity-75">
                <p>Enter now to access exclusive gift card offers!</p>
                <p class="mt-2">No purchase necessary. Enter as many gift cards as you want!</p>
            </div>
            
            <div class="absolute -bottom-10 -left-10 w-40 h-40 bg-primary rounded-full opacity-20 blur-lg"></div>
            <div class="absolute -top-10 -right-10 w-40 h-40 bg-accent rounded-full opacity-20 blur-lg"></div>
        </div>
    </div>
    
    <!-- Offers Section -->
    <div id="offers-section" class="min-h-screen py-10 px-4" style="display: none;">
        <div class="max-w-7xl mx-auto">
            <h1 class="text-4xl font-bold text-center mb-3 glow">CHOOSE YOUR GIFT CARD</h1>
            <h2 class="text-xl text-center mb-10 text-yellow-300">Click on any offer to claim your chance to win!</h2>
            
            <div class="offers-container" id="offers-grid">
                <!-- Gift card offers will be inserted here by JavaScript -->
            </div>
        </div>
    </div>
    
    <script>
        // Gift card offers data
        const giftCards = [
            { title: "$750 SHEIN Card", link: "https://glstrck.com/aff_c?offer_id=76&aff_id=95854", icon: "shein" },
            { title: "$750 Sephora Card", link: "https://glstrck.com/aff_c?offer_id=163&aff_id=95854", icon: "sephora" },
            { title: "$750 PayPal Card", link: "https://glstrck.com/aff_c?offer_id=1546&aff_id=95854", icon: "paypal" },
            { title: "$750 ALDI Bonus Card", link: "https://glstrck.com/aff_c?offer_id=974&aff_id=95854", icon: "aldi" },
            { title: "Walmart Card", link: "https://glstrck.com/aff_c?offer_id=972&aff_id=95854", icon: "walmart" },
            { title: "$750 Expedia.ca Travel Voucher", link: "https://glstrck.com/aff_c?offer_id=939&aff_id=95854", icon: "expedia" },
            { title: "$1000 IKEA Card", link: "https://glstrck.com/aff_c?offer_id=926&aff_id=95854", icon: "ikea" },
            { title: "$750 iPhone 16", link: "https://glstrck.com/aff_c?offer_id=882&aff_id=95854", icon: "apple" },
            { title: "$750 Staples Card", link: "https://glstrck.com/aff_c?offer_id=881&aff_id=95854", icon: "staples" },
            { title: "$750 Uniqlo Card", link: "https://glstrck.com/aff_c?offer_id=713&aff_id=95854", icon: "uniqlo" },
            { title: "$250 Huda Beauty Card", link: "https://glstrck.com/aff_c?offer_id=665&aff_id=95854", icon: "hudabeauty" },
            { title: "$100 Taco Bell Card", link: "https://glstrck.com/aff_c?offer_id=655&aff_id=95854", icon: "tacobell" },
            { title: "$750 Uber Eats Card", link: "https://glstrck.com/aff_c?offer_id=633&aff_id=95854", icon: "ubereats" },
            { title: "$500 Primark Card", link: "https://glstrck.com/aff_c?offer_id=596&aff_id=95854", icon: "primark" },
            { title: "$100 JD Sports Card", link: "https://glstrck.com/aff_c?offer_id=509&aff_id=95854", icon: "jdsports" },
            { title: "$500 DoorDash Card", link: "https://glstrck.com/aff_c?offer_id=455&aff_id=95854", icon: "doordash" },
            { title: "$750 Lululemon Card", link: "https://glstrck.com/aff_c?offer_id=435&aff_id=95854", icon: "lululemon" },
            { title: "$500 Chewy Card", link: "https://glstrck.com/aff_c?offer_id=418&aff_id=95854", icon: "chewy" },
            { title: "$500 7-Eleven Card", link: "https://glstrck.com/aff_c?offer_id=404&aff_id=95854", icon: "7eleven" },
            { title: "$500 KFC Card", link: "https://glstrck.com/aff_c?offer_id=400&aff_id=95854", icon: "kfc" },
            { title: "$500 Alo Yoga Card", link: "https://glstrck.com/aff_c?offer_id=378&aff_id=95854", icon: "aloyoga" },
            { title: "$750 Brandy Melville Card", link: "https://glstrck.com/aff_c?offer_id=375&aff_id=95854", icon: "brandymelville" },
            { title: "$500 Amazon Card", link: "https://glstrck.com/aff_c?offer_id=358&aff_id=95854", icon: "amazon" },
            { title: "$500 Sephora Card", link: "https://glstrck.com/aff_c?offer_id=352&aff_id=95854", icon: "sephora" },
            { title: "$100 Pretty Little Thing Card", link: "https://glstrck.com/aff_c?offer_id=345&aff_id=95854", icon: "prettylittlething" },
            { title: "$500 Zara Card", link: "https://glstrck.com/aff_c?offer_id=318&aff_id=95854", icon: "zara" },
            { title: "$750 Princess Polly Card", link: "https://glstrck.com/aff_c?offer_id=295&aff_id=95854", icon: "princesspolly" },
            { title: "$750 Mango Card", link: "https://glstrck.com/aff_c?offer_id=290&aff_id=95854", icon: "mango" },
            { title: "$750 White Fox Boutique Card", link: "https://glstrck.com/aff_c?offer_id=285&aff_id=95854", icon: "whitefox" },
            { title: "$500 Foot Locker Card", link: "https://glstrck.com/aff_c?offer_id=275&aff_id=95854", icon: "footlocker" },
            { title: "$1000 StockX Card", link: "https://glstrck.com/aff_c?offer_id=273&aff_id=95854", icon: "stockx" },
            { title: "$750 TikTok Shop Card", link: "https://glstrck.com/aff_c?offer_id=272&aff_id=95854", icon: "tiktok" },
            { title: "$1000 Kohl's Card", link: "https://glstrck.com/aff_c?offer_id=270&aff_id=95854", icon: "kohls" },
            { title: "$750 Revolve Card", link: "https://glstrck.com/aff_c?offer_id=260&aff_id=95854", icon: "revolve" },
            { title: "$500 Aritzia Card", link: "https://glstrck.com/aff_c?offer_id=248&aff_id=95854", icon: "aritzia" },
            { title: "$750 Boohoo Card", link: "https://glstrck.com/aff_c?offer_id=247&aff_id=95854", icon: "boohoo" },
            { title: "$750 H&M Card", link: "https://glstrck.com/aff_c?offer_id=195&aff_id=95854", icon: "hm" },
            { title: "$1000 Apple Vision Pro", link: "https://glstrck.com/aff_c?offer_id=180&aff_id=95854", icon: "apple" },
            { title: "$250 Kylie Cosmetics Card", link: "https://glstrck.com/aff_c?offer_id=178&aff_id=95854", icon: "kyliecosmetics" },
            { title: "$750 Victoria's Secret Card", link: "https://glstrck.com/aff_c?offer_id=177&aff_id=95854", icon: "victoriassecret" },
            { title: "$500 PlayStation Card", link: "https://glstrck.com/aff_c?offer_id=176&aff_id=95854", icon: "playstation" },
            { title: "$100 Starbucks Card", link: "https://glstrck.com/aff_c?offer_id=175&aff_id=95854", icon: "starbucks" },
            { title: "$500 Pandora Card", link: "https://glstrck.com/aff_c?offer_id=174&aff_id=95854", icon: "pandora" },
            { title: "$750 Spotify Card", link: "https://glstrck.com/aff_c?offer_id=170&aff_id=95854", icon: "spotify" },
            { title: "$750 Amazon Card", link: "https://glstrck.com/aff_c?offer_id=144&aff_id=95854", icon: "amazon" },
            { title: "$100 Stanley Cup Card", link: "https://glstrck.com/aff_c?offer_id=154&aff_id=95854", icon: "stanley" },
            { title: "$100 Lowe's Card", link: "https://glstrck.com/aff_c?offer_id=137&aff_id=95854", icon: "lowes" },
            { title: "$750 SKIMS Card", link: "https://glstrck.com/aff_c?offer_id=113&aff_id=95854", icon: "skims" },
            { title: "$750 Fashion Nova Card", link: "https://glstrck.com/aff_c?offer_id=105&aff_id=95854", icon: "fashionnova" }
        ];
        
        // Default gift card image if logo not found
        const defaultGiftCardImage = "https://cdn.jsdelivr.net/gh/simple-icons/simple-icons@v6/icons/giftcard.svg";
        
        // Initialize app when DOM is loaded
        document.addEventListener("DOMContentLoaded", function() {
            // Handle form submission
            const signupForm = document.getElementById("signup-form");
            signupForm.addEventListener("submit", handleSignup);
            
            // Create gift card offer cards
            createGiftCardOffers();
            
            // Preload sounds
            document.getElementById("click-sound").load();
            document.getElementById("success-sound").load();
            document.getElementById("jackpot-sound").load();
        });
        
        // Handle signup form submission
        function handleSignup(event) {
            event.preventDefault();
            
            const name = document.getElementById("name").value;
            const email = document.getElementById("email").value;
            
            if (!name || !email) {
                alert("Please fill in all fields!");
                return;
            }
            
            // Store user data (In a real app, you would connect this to Google Sheets using Google Apps Script)
            storeUserData(name, email);
            
            // Play success sound
            document.getElementById("success-sound").play();
            
            // Show celebration effect
            celebrationEffect();
            
            // Hide signup section and show offers section
            setTimeout(() => {
                document.getElementById("signup-section").style.display = "none";
                document.getElementById("offers-section").style.display = "block";
                document.getElementById("offers-grid").style.display = "grid";
            }, 1000);
        }
        
        // Store user data (simulated - in a real app, connect to Google Sheets)
        function storeUserData(name, email) {
            console.log("User registered:", name, email);
            // In a real implementation, you would connect to Google Sheets via fetch API
            // This would require a Google Apps Script deployment as a web app
            
            // Example of how data would be stored (simulated)
            const userData = {
                name: name,
                email: email,
                timestamp: new Date().toISOString()
            };
            
            // Store in localStorage for demo purposes
            let users = JSON.parse(localStorage.getItem("giftCardUsers") || "[]");
            users.push(userData);
            localStorage.setItem("giftCardUsers", JSON.stringify(users));
        }
        
        // Create gift card offer cards
        function createGiftCardOffers() {
            const offersGrid = document.getElementById("offers-grid");
            
            giftCards.forEach(card => {
                // Create card element
                const cardElement = document.createElement("div");
                cardElement.className = "offer-card";
                
                // Try to get the icon for the brand, fallback to default if not available
                let iconUrl = defaultGiftCardImage;
                try {
                    // Check if icon exists
                    const brandIcon = card.icon.toLowerCase().replace(/[^a-z0-9]/g, "");
                    iconUrl = `https://cdn.jsdelivr.net/gh/simple-icons/simple-icons@v6/icons/${brandIcon}.svg`;
                } catch (e) {
                    console.log(`Icon not found for ${card.title}, using default`);
                }
                
                // Create card content
                cardElement.innerHTML = `
                    <img src="${iconUrl}" alt="${card.title}" class="mb-4" style="filter: invert(1) brightness(2);">
                    <div class="offer-title">${card.title}</div>
                `;
                
                // Add click event
                cardElement.addEventListener("click", () => {
                    // Play click sound
                    document.getElementById("click-sound").play();
                    
                    // Random chance to play jackpot sound (10% chance)
                    if (Math.random() < 0.1) {
                        setTimeout(() => {
                            document.getElementById("jackpot-sound").play();
                            showCoinAnimation();
                        }, 300);
                    }
                    
                    // Navigate to offer link
                    setTimeout(() => {
                        window.open(card.link, "_blank");
                    }, 500);
                });
                
                // Add to grid
                offersGrid.appendChild(cardElement);
            });
        }
        
        // Celebration confetti effect
        function celebrationEffect() {
            for (let i = 0; i < 100; i++) {
                createConfetti();
            }
        }
        
        // Create a single confetti element
        function createConfetti() {
            const confetti = document.createElement("div");
            confetti.className = "confetti";
            
            // Random properties
            const colors = ["#ff1493", "#ffcc00", "#00ffff", "#ff4500", "#7cfc00"];
            const size = Math.random() * 10 + 5;
            
            confetti.style.width = `${size}px`;
            confetti.style.height = `${size}px`;
            confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
            confetti.style.left = `${Math.random() * 100}vw`;
            confetti.style.top = `-20px`;
            confetti.style.opacity = "1";
            confetti.style.transform = `rotate(${Math.random() * 360}deg)`;
            
            document.body.appendChild(confetti);
            
            // Animate falling
            const animationDuration = Math.random() * 3 + 2;
            confetti.style.transition = `top ${animationDuration}s linear, left ${animationDuration}s ease-in-out, opacity ${animationDuration}s linear`;
            
            setTimeout(() => {
                confetti.style.top = `100vh`;
                confetti.style.left = `${Math.random() * 100}vw`;
                confetti.style.opacity = "0";
                
                // Remove after animation
                setTimeout(() => {
                    confetti.remove();
                }, animationDuration * 1000);
            }, 10);
        }
        
        // Show coin animation (casino style)
        function showCoinAnimation() {
            for (let i = 0; i < 30; i++) {
                createCoin();
            }
        }
        
        // Create a single coin
        function createCoin() {
            const coin = document.createElement("div");
            coin.className = "coins";
            
            // Random properties
            coin.style.left = `${Math.random() * 100}vw`;
            coin.style.top = `-30px`;
            coin.style.opacity = "1";
            
            document.body.appendChild(coin);
            
            // Animate falling
            const animationDuration = Math.random() * 2 + 1;
            coin.style.transition = `top ${animationDuration}s linear, transform ${animationDuration/5}s linear, opacity ${animationDuration}s linear`;
            
            // Add spinning effect
            const spinInterval = setInterval(() => {
                coin.style.transform = `rotate(${Math.random() * 360}deg)`;
            }, animationDuration * 200);
            
            setTimeout(() => {
                coin.style.top = `100vh`;
                coin.style.opacity = "0";
                
                // Remove after animation
                setTimeout(() => {
                    clearInterval(spinInterval);
                    coin.remove();
                }, animationDuration * 1000);
            }, 10);
        }
    </script>
</body>
</html>
