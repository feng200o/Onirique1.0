# Onirique1.0
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Temperature of Memory</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Crimson+Text:ital,wght@0,400;0,600;1,400&family=Source+Code+Pro:wght@300;400&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: linear-gradient(135deg, #0c0c0c 0%, #1a1a2e 50%, #16213e 100%);
            color: #e8e8e8;
            font-family: 'Crimson Text', serif;
            line-height: 1.6;
            min-height: 100vh;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }
        
        .header {
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
        }
        
        .title {
            font-size: 3rem;
            font-weight: 600;
            background: linear-gradient(45deg, #ffd700, #ffed4e, #ffffff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 0.5rem;
            animation: shimmer 3s ease-in-out infinite;
        }
        
        @keyframes shimmer {
            0%, 100% { filter: brightness(1); }
            50% { filter: brightness(1.2); }
        }
        
        .subtitle {
            font-style: italic;
            color: #b8b8b8;
            font-size: 1.2rem;
        }
        
        .story-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            margin-bottom: 3rem;
        }
        
        .story-panel {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 2rem;
            position: relative;
            overflow: hidden;
        }
        
        .story-panel::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 215, 0, 0.1), transparent);
            animation: rotate 6s linear infinite;
            z-index: -1;
        }
        
        @keyframes rotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        .panel-title {
            font-size: 1.5rem;
            color: #ffd700;
            margin-bottom: 1.5rem;
            text-align: center;
            font-weight: 600;
        }
        
        .dream-section {
            margin-bottom: 2rem;
        }
        
        .section-header {
            font-size: 1.1rem;
            color: #ffed4e;
            margin-bottom: 0.5rem;
            font-weight: 600;
        }
        
        .dream-text {
            font-size: 1rem;
            line-height: 1.7;
            margin-bottom: 1rem;
        }
        
        .reality-panel {
            background: rgba(0, 100, 200, 0.1);
        }
        
        .dream-panel {
            background: rgba(200, 0, 100, 0.1);
        }
        
        .temperature-indicator {
            position: fixed;
            top: 20px;
            right: 20px;
            background: rgba(0, 0, 0, 0.7);
            border: 2px solid #ffd700;
            border-radius: 50px;
            padding: 10px 20px;
            font-family: 'Source Code Pro', monospace;
            font-size: 0.9rem;
            z-index: 1000;
            transition: all 0.3s ease;
        }
        
        .memory-fragments {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }
        
        .fragment {
            position: absolute;
            width: 2px;
            height: 2px;
            background: #ffd700;
            border-radius: 50%;
            animation: float 4s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px) translateX(0px); opacity: 0.3; }
            50% { transform: translateY(-20px) translateX(10px); opacity: 1; }
        }
        
        .interactive-section {
            background: rgba(255, 255, 255, 0.03);
            border-radius: 20px;
            padding: 2rem;
            margin: 3rem 0;
            text-align: center;
        }
        
        .warmth-detector {
            display: inline-block;
            padding: 15px 30px;
            background: linear-gradient(45deg, #ff6b6b, #ffd700);
            border: none;
            border-radius: 50px;
            color: #000;
            font-weight: 600;
            cursor: pointer;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            margin: 10px;
        }
        
        .warmth-detector:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 30px rgba(255, 215, 0, 0.3);
        }
        
        .dialogue-container {
            background: rgba(0, 0, 0, 0.3);
            border-left: 4px solid #ffd700;
            padding: 1.5rem;
            margin: 1.5rem 0;
            border-radius: 0 15px 15px 0;
        }
        
        .character-name {
            color: #ffd700;
            font-weight: 600;
            font-size: 1.1rem;
            margin-bottom: 0.5rem;
        }
        
        .dialogue {
            font-style: italic;
            margin-bottom: 0.5rem;
        }
        
        .internal-thought {
            color: #b8b8b8;
            font-size: 0.9rem;
            margin-left: 1rem;
        }
        
        .ending-section {
            background: linear-gradient(135deg, rgba(255, 0, 0, 0.1), rgba(0, 0, 0, 0.5));
            border-radius: 20px;
            padding: 3rem;
            margin-top: 3rem;
            text-align: center;
            position: relative;
        }
        
        .fade-text {
            animation: fadeInOut 4s ease-in-out infinite;
        }
        
        @keyframes fadeInOut {
            0%, 100% { opacity: 0.3; }
            50% { opacity: 1; }
        }
        
        .temperature-reading {
            font-family: 'Source Code Pro', monospace;
            color: #00ff00;
            font-weight: 300;
        }
        
        @media (max-width: 768px) {
            .story-container {
                grid-template-columns: 1fr;
                gap: 2rem;
            }
            
            .title {
                font-size: 2rem;
            }
            
            .temperature-indicator {
                position: static;
                margin: 1rem auto;
                display: block;
                width: fit-content;
            }
        }
        
        .emotional-pulse {
            animation: heartbeat 2s ease-in-out infinite;
        }
        
        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.02); }
        }
    </style>
</head>
<body>
    <div class="memory-fragments" id="fragments"></div>
    
    <div class="temperature-indicator" id="tempIndicator">
        <span class="temperature-reading">WARMTH: DETECTING...</span>
    </div>
    
    <div class="container">
        <div class="header">
            <h1 class="title">The Temperature of Memory</h1>
            <p class="subtitle">A study in ephemeral attachment and the physics of dreams</p>
        </div>
        
        <div class="story-container">
            <div class="story-panel dream-panel">
                <h2 class="panel-title">🌙 THE DREAM KINGDOM</h2>
                
                <div class="dream-section">
                    <h3 class="section-header">Initial Conditions</h3>
                    <p class="dream-text">Subject materializes in alternate timeline as puppet monarch. Half-colonized kingdom. Revolutionary undercurrents detected. Survival probability: uncertain.</p>
                </div>
                
                <div class="dialogue-container">
                    <div class="character-name">THE KING</div>
                    <div class="dialogue">"The histories of the common rebellions are kept two shelves higher."</div>
                    <div class="internal-thought">First contact protocol: protect the thief. Reason: unknown.</div>
                </div>
                
                <div class="dream-section">
                    <h3 class="section-header">Variable: Adrian</h3>
                    <p class="dream-text">Enemy's son. Revolutionary's tool. Triple agent by inheritance. Observable characteristics: sharp eyes, dangerous loyalty, intensity that cuts through imperial pretense.</p>
                </div>
                
                <div class="dialogue-container">
                    <div class="character-name">ADRIAN</div>
                    <div class="dialogue">"You don't belong here. Not in the violence, not in the blood and politics. You're too clean."</div>
                    <div class="internal-thought">Classification: beautiful. Danger level: maximum.</div>
                </div>
                
                <div class="dream-section">
                    <h3 class="section-header">The Warmth Protocol</h3>
                    <p class="dream-text">Dreams register as cold. Reality maintains temperature above 98.6°F. Touching Adrian's cheek: verification method established. Side effect: cardiac irregularities detected.</p>
                </div>
            </div>
            
            <div class="story-panel reality-panel">
                <h2 class="panel-title">☀️ THE WAKING WORLD</h2>
                
                <div class="dream-section">
                    <h3 class="section-header">Baseline Reality</h3>
                    <p class="dream-text">University acceptance letter. Job applications pending. Electric lights hang inverted but function normally. War exists in textbooks only. Loneliness: constant.</p>
                </div>
                
                <div class="dialogue-container">
                    <div class="character-name">THE DREAMER</div>
                    <div class="dialogue">"Everyone has enough to eat. Children go to school instead of battlefields."</div>
                    <div class="internal-thought">Paradise described. Terror response: why?</div>
                </div>
                
                <div class="dream-section">
                    <h3 class="section-header">Childhood Data</h3>
                    <p class="dream-text">Frequent nightmares. Reality anchor: sunlight through windows. Warmth = truth. Cold = fiction. System works until...</p>
                </div>
                
                <div class="dream-section">
                    <h3 class="section-header">The Attachment Problem</h3>
                    <p class="dream-text">What happens when the warmth you crave exists only in dreams? When the cold reality becomes unbearable not because it's harsh, but because it's empty?</p>
                </div>
            </div>
        </div>
        
        <div class="interactive-section">
            <h2>Reality Check Protocol</h2>
            <p>In childhood: Press palm to sunlit window</p>
            <p>In dreams: Touch another's skin</p>
            <p>In love: Which world feels more real?</p>
            <button class="warmth-detector" onclick="checkWarmth()">CHECK WARMTH LEVELS</button>
            <button class="warmth-detector" onclick="generateFragment()">RELEASE MEMORY</button>
        </div>
        
        <div class="story-panel emotional-pulse" style="width: 100%; margin: 2rem 0;">
            <h2 class="panel-title">💔 THE UNSENT MESSAGES</h2>
            
            <div class="dialogue-container">
                <div class="character-name">WHAT HE SAID</div>
                <div class="dialogue">"We all die eventually."</div>
                <div class="character-name">WHAT HE MEANT</div>
                <div class="internal-thought">"I've wanted to die for years."</div>
            </div>
            
            <div class="dialogue-container">
                <div class="character-name">WHAT HE SAID</div>
                <div class="dialogue">"Let me die for you."</div>
                <div class="character-name">WHAT HE MEANT</div>
                <div class="internal-thought">"You're the first thing worth dying for."</div>
            </div>
            
            <div class="dialogue-container">
                <div class="character-name">WHAT HE SAID</div>
                <div class="dialogue">"Is that so wrong?"</div>
                <div class="character-name">WHAT HE MEANT</div>
                <div class="internal-thought">"Please say yes. Please stop me."</div>
            </div>
            
            <div class="dialogue-container" style="background: rgba(255, 0, 0, 0.1);">
                <div class="character-name">WHAT HE NEVER SAID</div>
                <div class="dialogue">"I wish you'd dedicated your life to me instead."</div>
                <div class="internal-thought">Found in his journal. Censored by history. Both characters trying to hide their feelings but failed.</div>
            </div>
        </div>
        
        <div class="ending-section">
            <h2 class="fade-text">SYSTEM SHUTDOWN</h2>
            <p class="dream-text">Vision blurring. Touch sensitivity lost. Connection to Adrian... severing...</p>
            <p class="dream-text">"I wanted to tell you—"</p>
            <p class="dream-text fade-text">Signal lost.</p>
            <br>
            <p class="dream-text">WAKE UP PROTOCOL INITIATED</p>
            <p class="internal-thought">Temperature reading: Normal. Loneliness reading: Critical. Attachment to non-existent entity: Confirmed.</p>
            <br>
            <p class="fade-text">"Somewhere, in a world that might never have existed, a boy with sharp eyes and dangerous loyalty was probably wondering why a king had vanished in the middle of a sentence..."</p>
        </div>
    </div>
    
    <script>
        // Create floating memory fragments
        function createFragment() {
            const fragment = document.createElement('div');
            fragment.className = 'fragment';
            fragment.style.left = Math.random() * 100 + '%';
            fragment.style.top = Math.random() * 100 + '%';
            fragment.style.animationDelay = Math.random() * 4 + 's';
            document.getElementById('fragments').appendChild(fragment);
            
            setTimeout(() => {
                fragment.remove();
            }, 4000);
        }
        
        // Generate fragments continuously
        setInterval(createFragment, 500);
        
        // Temperature indicator updates
        const temperatures = [
            "WARMTH: 98.6°F - REALITY CONFIRMED",
            "WARMTH: 32°F - DREAM STATE DETECTED", 
            "WARMTH: 99.1°F - EMOTIONAL SPIKE",
            "WARMTH: UNDEFINED - SYSTEM ERROR",
            "WARMTH: MEMORY TRACE ONLY"
        ];
        
        function updateTemperature() {
            const indicator = document.getElementById('tempIndicator');
            const temp = temperatures[Math.floor(Math.random() * temperatures.length)];
            indicator.querySelector('.temperature-reading').textContent = temp;
        }
        
        setInterval(updateTemperature, 3000);
        
        // Interactive functions
        function checkWarmth() {
            const readings = [
                "DETECTING... Subject's cheek: 98.7°F",
                "DETECTING... Sunlight through window: 78°F", 
                "DETECTING... Memory of touch: 0°F",
                "DETECTING... Longing: Unmeasurable",
                "ERROR: Cannot distinguish dream from reality"
            ];
            alert(readings[Math.floor(Math.random() * readings.length)]);
        }
        
        function generateFragment() {
            for(let i = 0; i < 20; i++) {
                setTimeout(() => createFragment(), i * 100);
            }
        }
        
        // Fade in animation on scroll
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        });
        
        document.querySelectorAll('.story-panel, .dialogue-container').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(20px)';
            el.style.transition = 'all 0.6s ease';
            observer.observe(el);
        });
    </script>
</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>The Temperature of Memory</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Crimson+Text:ital,wght@0,400;0,600;1,400&family=Source+Code+Pro:wght@300;400&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: linear-gradient(135deg, #0c0c0c 0%, #1a1a2e 50%, #16213e 100%);
            color: #e8e8e8;
            font-family: 'Crimson Text', serif;
            line-height: 1.6;
            min-height: 100vh;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }
        
        .header {
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
        }
        
        .title {
            font-size: 3rem;
            font-weight: 600;
            background: linear-gradient(45deg, #ffd700, #ffed4e, #ffffff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 0.5rem;
            animation: shimmer 3s ease-in-out infinite;
        }
        
        @keyframes shimmer {
            0%, 100% { filter: brightness(1); }
            50% { filter: brightness(1.2); }
        }
        
        .subtitle {
            font-style: italic;
            color: #b8b8b8;
            font-size: 1.2rem;
        }
        
        .story-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            margin-bottom: 3rem;
        }
        
        .story-panel {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 2rem;
            position: relative;
            overflow: hidden;
        }
        
        .story-panel::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 215, 0, 0.1), transparent);
            animation: rotate 6s linear infinite;
            z-index: -1;
        }
        
        @keyframes rotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        .panel-title {
            font-size: 1.5rem;
            color: #ffd700;
            margin-bottom: 1.5rem;
            text-align: center;
            font-weight: 600;
        }
        
        .dream-section {
            margin-bottom: 2rem;
        }
        
        .section-header {
            font-size: 1.1rem;
            color: #ffed4e;
            margin-bottom: 0.5rem;
            font-weight: 600;
        }
        
        .dream-text {
            font-size: 1rem;
            line-height: 1.7;
            margin-bottom: 1rem;
        }
        
        .reality-panel {
            background: rgba(0, 100, 200, 0.1);
        }
        
        .dream-panel {
            background: rgba(200, 0, 100, 0.1);
        }
        
        .temperature-indicator {
            position: fixed;
            top: 20px;
            right: 20px;
            background: rgba(0, 0, 0, 0.7);
            border: 2px solid #ffd700;
            border-radius: 50px;
            padding: 10px 20px;
            font-family: 'Source Code Pro', monospace;
            font-size: 0.9rem;
            z-index: 1000;
            transition: all 0.3s ease;
        }
        
        .memory-fragments {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }
        
        .fragment {
            position: absolute;
            width: 2px;
            height: 2px;
            background: #ffd700;
            border-radius: 50%;
            animation: float 4s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px) translateX(0px); opacity: 0.3; }
            50% { transform: translateY(-20px) translateX(10px); opacity: 1; }
        }
        
        .interactive-section {
            background: rgba(255, 255, 255, 0.03);
            border-radius: 20px;
            padding: 2rem;
            margin: 3rem 0;
            text-align: center;
        }
        
        .warmth-detector {
            display: inline-block;
            padding: 15px 30px;
            background: linear-gradient(45deg, #ff6b6b, #ffd700);
            border: none;
            border-radius: 50px;
            color: #000;
            font-weight: 600;
            cursor: pointer;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            margin: 10px;
        }
        
        .warmth-detector:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 30px rgba(255, 215, 0, 0.3);
        }
        
        .dialogue-container {
            background: rgba(0, 0, 0, 0.3);
            border-left: 4px solid #ffd700;
            padding: 1.5rem;
            margin: 1.5rem 0;
            border-radius: 0 15px 15px 0;
        }
        
        .character-name {
            color: #ffd700;
            font-weight: 600;
            font-size: 1.1rem;
            margin-bottom: 0.5rem;
        }
        
        .dialogue {
            font-style: italic;
            margin-bottom: 0.5rem;
        }
        
        .internal-thought {
            color: #b8b8b8;
            font-size: 0.9rem;
            margin-left: 1rem;
        }
        
        .ending-section {
            background: linear-gradient(135deg, rgba(255, 0, 0, 0.1), rgba(0, 0, 0, 0.5));
            border-radius: 20px;
            padding: 3rem;
            margin-top: 3rem;
            text-align: center;
            position: relative;
        }
        
        .fade-text {
            animation: fadeInOut 4s ease-in-out infinite;
        }
        
        @keyframes fadeInOut {
            0%, 100% { opacity: 0.3; }
            50% { opacity: 1; }
        }
        
        .temperature-reading {
            font-family: 'Source Code Pro', monospace;
            color: #00ff00;
            font-weight: 300;
        }
        
        @media (max-width: 768px) {
            .story-container {
                grid-template-columns: 1fr;
                gap: 2rem;
            }
            
            .title {
                font-size: 2rem;
            }
            
            .temperature-indicator {
                position: static;
                margin: 1rem auto;
                display: block;
                width: fit-content;
            }
        }
        
        .emotional-pulse {
            animation: heartbeat 2s ease-in-out infinite;
        }
        
        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.02); }
        }
    </style>
</head>
<body>
    <div class="memory-fragments" id="fragments"></div>
    
    <div class="temperature-indicator" id="tempIndicator">
        <span class="temperature-reading">WARMTH: DETECTING...</span>
    </div>
    
    <div class="container">
        <div class="header">
            <h1 class="title">The Temperature of Memory</h1>
            <p class="subtitle">A study in ephemeral attachment and the physics of dreams</p>
        </div>
        
        <div class="story-container">
            <div class="story-panel dream-panel">
                <h2 class="panel-title">🌙 THE DREAM KINGDOM</h2>
                
                <div class="dream-section">
                    <h3 class="section-header">Initial Conditions</h3>
                    <p class="dream-text">Subject materializes in alternate timeline as puppet monarch. Half-colonized kingdom. Revolutionary undercurrents detected. Survival probability: uncertain.</p>
                </div>
                
                <div class="dialogue-container">
                    <div class="character-name">THE KING</div>
                    <div class="dialogue">"The histories of the common rebellions are kept two shelves higher."</div>
                    <div class="internal-thought">First contact protocol: protect the thief. Reason: unknown.</div>
                </div>
                
                <div class="dream-section">
                    <h3 class="section-header">Variable: Adrian</h3>
                    <p class="dream-text">Enemy's son. Revolutionary's tool. Triple agent by inheritance. Observable characteristics: sharp eyes, dangerous loyalty, intensity that cuts through imperial pretense.</p>
                </div>
                
                <div class="dialogue-container">
                    <div class="character-name">ADRIAN</div>
                    <div class="dialogue">"You don't belong here. Not in the violence, not in the blood and politics. You're too clean."</div>
                    <div class="internal-thought">Classification: beautiful. Danger level: maximum.</div>
                </div>
                
                <div class="dream-section">
                    <h3 class="section-header">The Warmth Protocol</h3>
                    <p class="dream-text">Dreams register as cold. Reality maintains temperature above 98.6°F. Touching Adrian's cheek: verification method established. Side effect: cardiac irregularities detected.</p>
                </div>
            </div>
            
            <div class="story-panel reality-panel">
                <h2 class="panel-title">☀️ THE WAKING WORLD</h2>
                
                <div class="dream-section">
                    <h3 class="section-header">Baseline Reality</h3>
                    <p class="dream-text">University acceptance letter. Job applications pending. Electric lights hang inverted but function normally. War exists in textbooks only. Loneliness: constant.</p>
                </div>
                
                <div class="dialogue-container">
                    <div class="character-name">THE DREAMER</div>
                    <div class="dialogue">"Everyone has enough to eat. Children go to school instead of battlefields."</div>
                    <div class="internal-thought">Paradise described. Terror response: why?</div>
                </div>
                
                <div class="dream-section">
                    <h3 class="section-header">Childhood Data</h3>
                    <p class="dream-text">Frequent nightmares. Reality anchor: sunlight through windows. Warmth = truth. Cold = fiction. System works until...</p>
                </div>
                
                <div class="dream-section">
                    <h3 class="section-header">The Attachment Problem</h3>
                    <p class="dream-text">What happens when the warmth you crave exists only in dreams? When the cold reality becomes unbearable not because it's harsh, but because it's empty?</p>
                </div>
            </div>
        </div>
        
        <div class="interactive-section">
            <h2>Reality Check Protocol</h2>
            <p>In childhood: Press palm to sunlit window</p>
            <p>In dreams: Touch another's skin</p>
            <p>In love: Which world feels more real?</p>
            <button class="warmth-detector" onclick="checkWarmth()">CHECK WARMTH LEVELS</button>
            <button class="warmth-detector" onclick="generateFragment()">RELEASE MEMORY</button>
        </div>
        
        <div class="story-panel emotional-pulse" style="width: 100%; margin: 2rem 0;">
            <h2 class="panel-title">💔 THE UNSENT MESSAGES</h2>
            
            <div class="dialogue-container">
                <div class="character-name">WHAT HE SAID</div>
                <div class="dialogue">"We all die eventually."</div>
                <div class="character-name">WHAT HE MEANT</div>
                <div class="internal-thought">"I've wanted to die for years."</div>
            </div>
            
            <div class="dialogue-container">
                <div class="character-name">WHAT HE SAID</div>
                <div class="dialogue">"Let me die for you."</div>
                <div class="character-name">WHAT HE MEANT</div>
                <div class="internal-thought">"You're the first thing worth dying for."</div>
            </div>
            
            <div class="dialogue-container">
                <div class="character-name">WHAT HE SAID</div>
                <div class="dialogue">"Is that so wrong?"</div>
                <div class="character-name">WHAT HE MEANT</div>
                <div class="internal-thought">"Please say yes. Please stop me."</div>
            </div>
            
            <div class="dialogue-container" style="background: rgba(255, 0, 0, 0.1);">
                <div class="character-name">WHAT HE NEVER SAID</div>
                <div class="dialogue">"I wish you'd dedicated your life to me instead."</div>
                <div class="internal-thought">Found in his journal. Censored by history. Both characters trying to hide their feelings but failed.</div>
            </div>
        </div>
        
        <div class="ending-section">
            <h2 class="fade-text">SYSTEM SHUTDOWN</h2>
            <p class="dream-text">Vision blurring. Touch sensitivity lost. Connection to Adrian... severing...</p>
            <p class="dream-text">"I wanted to tell you—"</p>
            <p class="dream-text fade-text">Signal lost.</p>
            <br>
            <p class="dream-text">WAKE UP PROTOCOL INITIATED</p>
            <p class="internal-thought">Temperature reading: Normal. Loneliness reading: Critical. Attachment to non-existent entity: Confirmed.</p>
            <br>
            <p class="fade-text">"Somewhere, in a world that might never have existed, a boy with sharp eyes and dangerous loyalty was probably wondering why a king had vanished in the middle of a sentence..."</p>
        </div>
    </div>
    
    <script>
        // Create floating memory fragments
        function createFragment() {
            const fragment = document.createElement('div');
            fragment.className = 'fragment';
            fragment.style.left = Math.random() * 100 + '%';
            fragment.style.top = Math.random() * 100 + '%';
            fragment.style.animationDelay = Math.random() * 4 + 's';
            document.getElementById('fragments').appendChild(fragment);
            
            setTimeout(() => {
                fragment.remove();
            }, 4000);
        }
        
        // Generate fragments continuously
        setInterval(createFragment, 500);
        
        // Temperature indicator updates
        const temperatures = [
            "WARMTH: 98.6°F - REALITY CONFIRMED",
            "WARMTH: 32°F - DREAM STATE DETECTED", 
            "WARMTH: 99.1°F - EMOTIONAL SPIKE",
            "WARMTH: UNDEFINED - SYSTEM ERROR",
            "WARMTH: MEMORY TRACE ONLY"
        ];
        
        function updateTemperature() {
            const indicator = document.getElementById('tempIndicator');
            const temp = temperatures[Math.floor(Math.random() * temperatures.length)];
            indicator.querySelector('.temperature-reading').textContent = temp;
        }
        
        setInterval(updateTemperature, 3000);
        
        // Interactive functions
        function checkWarmth() {
            const readings = [
                "DETECTING... Subject's cheek: 98.7°F",
                "DETECTING... Sunlight through window: 78°F", 
                "DETECTING... Memory of touch: 0°F",
                "DETECTING... Longing: Unmeasurable",
                "ERROR: Cannot distinguish dream from reality"
            ];
            alert(readings[Math.floor(Math.random() * readings.length)]);
        }
        
        function generateFragment() {
            for(let i = 0; i < 20; i++) {
                setTimeout(() => createFragment(), i * 100);
            }
        }
        
        // Fade in animation on scroll
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        });
        
        document.querySelectorAll('.story-panel, .dialogue-container').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(20px)';
            el.style.transition = 'all 0.6s ease';
            observer.observe(el);
        });
    </script>
</body>
</html>
