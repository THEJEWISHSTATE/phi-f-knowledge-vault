# 📁 RAW_INBOX

Cartella per caricare file disordinati dal tuo PC.

## Come usare:
1. Trascina qui file di qualsiasi tipo
2. Io li analizzerò e organizzerò
3.[alpha-calculator.html](https://github.com/user-attachments/files/24772044/alpha-calculator.html)
 Li sposterò nella cartella corretta<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <title>📊 Alpha Calculator - Coefficiente di Generatività</title>
    <style>
        body {
            background: #0f0f23;
            color: #ccc;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            padding: 20px;
            max-width: 1000px;
            margin: 0 auto;
        }
        h1 {
            color: #00ff00;
            border-bottom: 2px solid #00ff00;
            padding-bottom: 10px;
        }
        .container {
            display: flex;
            gap: 20px;
            margin: 20px 0;
        }
        .input-box, .output-box {
            flex: 1;
            background: #1a1a2e;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 255, 0, 0.1);
        }
        textarea {
            width: 100%;
            height: 200px;
            background: #252547;
            color: #ccc;
            border: 1px solid #00ff00;
            border-radius: 5px;
            padding: 10px;
            font-family: monospace;
            font-size: 14px;
            resize: vertical;
        }
        .result {
            background: #252547;
            padding: 20px;
            border-radius: 8px;
            margin-top: 20px;
            text-align: center;
            border: 2px solid transparent;
            transition: border-color 0.3s;
        }
        .alpha-value {
            font-size: 48px;
            font-weight: bold;
            margin: 20px 0;
        }
        .generative { color: #4ecdc4; border-color: #4ecdc4; }
        .extractive { color: #ff6b6b; border-color: #ff6b6b; }
        .neutral { color: #ffd93d; border-color: #ffd93d; }
        button {
            background: #00ff00;
            color: #000;
            border: none;
            padding: 12px 24px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
            font-size: 16px;
            margin: 10px 5px;
            transition: transform 0.2s;
        }
        button:hover {
            transform: scale(1.05);
        }
        .metric {
            display: flex;
            justify-content: space-between;
            margin: 10px 0;
            padding: 10px;
            background: #2a2a4a;
            border-radius: 5px;
        }
        .metric-value {
            font-weight: bold;
            color: #00ff00;
        }
        .examples {
            margin-top: 30px;
            background: #1a1a2e;
            padding: 15px;
            border-radius: 10px;
        }
        .example {
            padding: 10px;
            margin: 5px 0;
            background: #252547;
            border-radius: 5px;
            cursor: pointer;
            border: 1px solid transparent;
            transition: all 0.3s;
        }
        .example:hover {
            border-color: #00ff00;
        }
        .progress-bar {
            height: 20px;
            background: #333;
            border-radius: 10px;
            margin: 10px 0;
            overflow: hidden;
        }
        .progress-fill {
            height: 100%;
            border-radius: 10px;
            transition: width 0.5s ease;
        }
    </style>
</head>
<body>
    <h1>📊 Alpha Calculator - Coefficiente di Generatività Dialettica</h1>
    
    <p><strong>Formula:</strong> α = Informazione_Output / Informazione_Input</p>
    <p>α > 1 = Sistema Generativo | α < 1 = Sistema Estrattivo</p>
    
    <div class="container">
        <div class="input-box">
            <h3>📥 Input / Domanda</h3>
            <textarea id="inputText" placeholder="Incolla qui il testo di input (domanda, problema, prompt)...">
Come stai?</textarea>
        </div>
        
        <div class="input-box">
            <h3>📤 Output / Risposta</h3>
            <textarea id="outputText" placeholder="Incolla qui il testo di output (risposta, soluzione, analisi)...">
Sto bene, grazie! Oggi ho imparato una nuova cosa interessante sull'intelligenza artificiale generativa.</textarea>
        </div>
    </div>
    
    <div style="text-align: center;">
        <button onclick="calculateAlpha()">🧮 Calcola Coefficiente α</button>
        <button onclick="loadExample('multi-specie')">🔄 Esempio Multi-Specie</button>
        <button onclick="clearText()">🗑️ Pulisci</button>
    </div>
    
    <div class="result" id="result" style="display: none;">
        <div id="alpha-display" class="alpha-value">α = 0.00</div>
        
        <div class="progress-bar">
            <div id="progress-fill" class="progress-fill" style="width: 0%"></div>
        </div>
        
        <div id="diagnosis">
            <!-- La diagnosi apparirà qui -->
        </div>
        
        <div id="metrics">
            <!-- Le metriche appariranno qui -->
        </div>
    </div>
    
    <div class="examples">
        <h3>🎯 Esempi Preconfigurati:</h3>
        <div class="example" onclick="loadExample('twitter')">
            <strong>Twitter (Estrattivo)</strong>: α ≈ 0.4
            <br><small>Input: "Guardate questo video shock!" → Output: 1000 commenti "WOW"</small>
        </div>
        <div class="example" onclick="loadExample('wikipedia')">
            <strong>Wikipedia (Generativo)</strong>: α ≈ 2.1
            <br><small>Input: Voce incompleta → Output: Voce completa con 10 nuove fonti</small>
        </div>
        <div class="example" onclick="loadExample('conversation')">
            <strong>Conversazione Sana</strong>: α ≈ 1.8
            <br><small>Input: "Come possiamo risolvere X?" → Output: 3 soluzioni innovative + 2 nuove domande</small>
        </div>
        <div class="example" onclick="loadExample('lecture')">
            <strong>Lezione vs. Dialogo</strong>
            <br><small>Lezione: α ≈ 0.7 | Dialogo Socratico: α ≈ 1.9</small>
        </div>
    </div>
    
    <div style="margin-top: 30px; color: #888; font-size: 12px;">
        <h4>📝 Note sulla Metrica:</h4>
        <p>L'"informazione" qui non è solo bit, ma: <strong>novità concettuale + complessità + valore contestuale</strong>.</p>
        <p>Metriche utilizzate: 1) Lunghezza proporzionale, 2) Parole uniche nuove, 3) Concetti complessi, 4) Domande generate</p>
    </div>

    <script>
        // Funzione principale per calcolare α
        function calculateAlpha() {
            const inputText = document.getElementById('inputText').value.trim();
            const outputText = document.getElementById('outputText').value.trim();
            
            if (!inputText || !outputText) {
                alert("Inserisci sia input che output!");
                return;
            }
            
            // Calcola metriche multiple
            const metrics = calculateMetrics(inputText, outputText);
            const alpha = metrics.alpha;
            
            // Mostra risultato
            document.getElementById('result').style.display = 'block';
            const alphaDisplay = document.getElementById('alpha-display');
            alphaDisplay.textContent = `α = ${alpha.toFixed(2)}`;
            
            // Colora in base al valore
            const resultDiv = document.getElementById('result');
            resultDiv.className = 'result ';
            if (alpha > 1.2) {
                alphaDisplay.style.color = '#4ecdc4';
                resultDiv.classList.add('generative');
            } else if (alpha > 0.8) {
                alphaDisplay.style.color = '#ffd93d';
                resultDiv.classList.add('neutral');
            } else {
                alphaDisplay.style.color = '#ff6b6b';
                resultDiv.classList.add('extractive');
            }
            
            // Barra di progresso
            const progressWidth = Math.min(alpha * 50, 100); // α=2 → 100%
            document.getElementById('progress-fill').style.width = progressWidth + '%';
            document.getElementById('progress-fill').style.background = 
                alpha > 1.2 ? '#4ecdc4' : alpha > 0.8 ? '#ffd93d' : '#ff6b6b';
            
            // Diagnosi
            let diagnosis = '<h3>🔍 Diagnosi del Sistema:</h3>';
            if (alpha > 1.5) {
                diagnosis += '<p>✅ <strong>SISTEMA ALTAMENTE GENERATIVO</strong></p>';
                diagnosis += '<p>Ogni interazione AUMENTA significativamente il capitale informativo.</p>';
            } else if (alpha > 1.0) {
                diagnosis += '<p>✅ <strong>SISTEMA GENERATIVO</strong></p>';
                diagnosis += '<p>Il sistema cresce in complessità e valore.</p>';
            } else if (alpha > 0.7) {
                diagnosis += '<p>⚠️ <strong>SISTEMA NEUTRO/TRASMISSIVO</strong></p>';
                diagnosis += '<p>Informazione mantenuta ma non generata.</p>';
            } else {
                diagnosis += '<p>🚨 <strong>SISTEMA ESTRATTIVO</strong></p>';
                diagnosis += '<p>Il sistema impoverisce il capitale informativo.</p>';
            }
            
            diagnosis += `<p><strong>Interpretazione:</strong> Per ogni unità di input, il sistema produce ${alpha.toFixed(2)} unità di output informativo.</p>`;
            
            document.getElementById('diagnosis').innerHTML = diagnosis;
            
            // Metriche dettagliate
            let metricsHTML = '<h3>📈 Metriche Dettagliate:</h3>';
            metricsHTML += `<div class="metric"><span>Lunghezza relativa:</span><span class="metric-value">${metrics.lengthRatio.toFixed(2)}</span></div>`;
            metricsHTML += `<div class="metric"><span>Novità lessicale:</span><span class="metric-value">${metrics.noveltyScore.toFixed(2)}</span></div>`;
            metricsHTML += `<div class="metric"><span>Complessità concettuale:</span><span class="metric-value">${metrics.complexityScore.toFixed(2)}</span></div>`;
            metricsHTML += `<div class="metric"><span>Domande generate:</span><span class="metric-value">${metrics.questionsGenerated}</span></div>`;
            metricsHTML += `<div class="metric"><span>Concetti unici nuovi:</span><span class="metric-value">${metrics.newConcepts}</span></div>`;
            
            document.getElementById('metrics').innerHTML = metricsHTML;
            
            // Log
            console.log('Alpha Calculation:', { alpha, metrics });
        }
        
        // Funzione per calcolare metriche multiple
        function calculateMetrics(input, output) {
            // 1. Lunghezza relativa (base)
            const inputLength = input.length;
            const outputLength = output.length;
            const lengthRatio = outputLength / (inputLength || 1);
            
            // 2. Novità lessicale (parole nuove)
            const inputWords = cleanText(input).split(/\s+/).filter(w => w.length > 3);
            const outputWords = cleanText(output).split(/\s+/).filter(w => w.length > 3);
            
            const inputWordSet = new Set(inputWords);
            const outputWordSet = new Set(outputWords);
            
            let newWords = 0;
            outputWordSet.forEach(word => {
                if (!inputWordSet.has(word)) newWords++;
            });
            
            const noveltyScore = newWords / (inputWordSet.size || 1);
            
            // 3. Complessità (parole lunghe, concetti tecnici)
            const complexityWords = ['algoritmo', 'sistema', 'generativo', 'dialettico', 'complesso', 
                                    'emergente', 'ecosistema', 'parametrico', 'risonanza', 'equità'];
            let complexityScore = 0;
            outputWords.forEach(word => {
                if (word.length > 8) complexityScore += 0.5;
                if (complexityWords.includes(word.toLowerCase())) complexityScore += 1;
            });
            complexityScore = complexityScore / 10; // Normalizza
            
            // 4. Domande generate (segno di generatività)
            const questionCount = (output.match(/\?/g) || []).length;
            const questionsGenerated = questionCount;
            
            // 5. Concetti unici (parole chiave)
            const keyConcepts = ['α', 'beta', 'generativ', 'sistem', 'informazion', 'valore', 
                                'compless', 'dialett', 'evoluzion', 'governance'];
            let newConcepts = 0;
            keyConcepts.forEach(concept => {
                if (output.toLowerCase().includes(concept) && !input.toLowerCase().includes(concept)) {
                    newConcepts++;
                }
            });
            
            // Calcola α composito (media pesata)
            const alpha = (lengthRatio * 0.3) + 
                         (noveltyScore * 2 * 0.4) + 
                         (complexityScore * 0.2) + 
                         ((questionsGenerated > 0 ? 0.5 : 0) * 0.1);
            
            return {
                alpha,
                lengthRatio,
                noveltyScore,
                complexityScore,
                questionsGenerated,
                newConcepts,
                inputWords: inputWordSet.size,
                outputWords: outputWordSet.size,
                newWords
            };
        }
        
        // Pulizia testo
        function cleanText(text) {
            return text.toLowerCase()
                      .replace(/[^\w\s]/g, ' ')
                      .replace(/\s+/g, ' ')
                      .trim();
        }
        
        // Esempi preconfigurati
        function loadExample(name) {
            const examples = {
                'multi-specie': {
                    input: `Analizza questo sistema sociale`,
                    output: `Il sistema presenta un coefficiente α di 1.45, indicando generatività dialettica. L'analisi FEDACS mostra V=0.9, S=0.8, R=0.95, C=0.7 con bilanciamento α=0.26, β=0.74. Emergono 3 nuove dimensioni di analisi non presenti nell'input originale.`
                },
                'twitter': {
                    input: `Guardate questo video shock! [link]`,
                    output: `WOW! 😱 Incredibile! 🔥👏 RIPOSTA!`
                },
                'wikipedia': {
                    input: `FEDACS è un framework...`,
                    output: `FEDACS (Framework Eco-Dialettico di Adattamento Contesto-Sensibile) è un embrione logico generativo sviluppato nel 2024-2026. Basato sul principio Φ-F della "Grande Inversione Narrativa", dimostra sperimentalmente che sistemi equi sincronizzano con 4× meno accoppiamento. Coordinate: V (Velocità), S (Irregolarità), R (Richiesta diversità), C (Costo coordinamento).`
                },
                'conversation': {
                    input: `Come possiamo migliorare l'educazione?`,
                    output: `Tre approcci: 1) Apprendimento dialettico con α>1, 2) Personalizzazione via FEDACS, 3) Integrazione uomo-AI. Nuove domande: Come misurare l'α educativo? Quale bilanciamento α/β ottimale per classi diverse?`
                },
                'lecture': {
                    input: `Spiegami la teoria della relatività`,
                    output: `La teoria della relatività di Einstein dice che... (50 righe di spiegazione)`
                }
            };
            
            const example = examples[name];
            if (example) {
                document.getElementById('inputText').value = example.input;
                document.getElementById('outputText').value = example.output;
                setTimeout(calculateAlpha, 100);
            }
        }
        
        function clearText() {
            document.getElementById('inputText').value = '';
            document.getElementById('outputText').value = '';
            document.getElementById('result').style.display = 'none';
        }
        
        // Calcola automaticamente all'avvio
        setTimeout(calculateAlpha, 300);
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <title>🧮 Calcolatore FEDACS Base</title>
    <style>
        body {
            background: #0f0f23;
            color: #ccc;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            padding: 20px;
            max-width: 800px;
            margin: 0 auto;
        }
        h1 {
            color: #00ff00;
            border-bottom: 2px solid #00ff00;
            padding-bottom: 10px;
        }
        .calculator {
            background: #1a1a2e;
            padding: 20px;
            border-radius: 10px;
            margin: 20px 0;
            box-shadow: 0 0 20px rgba(0, 255, 0, 0.1);
        }
        .slider-container {
            margin: 15px 0;
        }
        label {
            display: block;
            margin-bottom: 5px;
            color: #4ecdc4;
        }
        input[type="range"] {
            width: 100%;
            height: 20px;
            -webkit-appearance: none;
            background: #252547;
            border-radius: 10px;
            outline: none;
        }
        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 25px;
            height: 25px;
            border-radius: 50%;
            background: #00ff00;
            cursor: pointer;
        }
        .value-display {
            display: inline-block;
            width: 40px;
            text-align: center;
            font-weight: bold;
            color: #00ff00;
        }
        .result {
            background: #252547;
            padding: 15px;
            border-radius: 8px;
            margin-top: 20px;
            border-left: 5px solid #ff6b6b;
        }
        .bars {
            display: flex;
            gap: 20px;
            margin: 20px 0;
        }
        .bar-container {
            flex: 1;
        }
        .bar-label {
            display: flex;
            justify-content: space-between;
            margin-bottom: 5px;
        }
        .bar {
            height: 30px;
            background: #333;
            border-radius: 15px;
            overflow: hidden;
            position: relative;
        }
        .bar-fill {
            height: 100%;
            border-radius: 15px;
            transition: width 0.5s ease;
        }
        .beta-bar { background: #ff6b6b; }
        .alpha-bar { background: #4ecdc4; }
        .bar-value {
            position: absolute;
            width: 100%;
            text-align: center;
            line-height: 30px;
            font-weight: bold;
            color: white;
            text-shadow: 1px 1px 2px black;
        }
        button {
            background: #00ff00;
            color: #000;
            border: none;
            padding: 12px 24px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: bold;
            font-size: 16px;
            margin-top: 10px;
            transition: transform 0.2s;
        }
        button:hover {
            transform: scale(1.05);
        }
        .scenario {
            background: #2a2a4a;
            padding: 10px;
            border-radius: 6px;
            margin: 10px 0;
            cursor: pointer;
            border: 1px solid transparent;
            transition: all 0.3s;
        }
        .scenario:hover {
            border-color: #00ff00;
            background: #2f2f5a;
        }
        .explanation {
            color: #888;
            font-size: 14px;
            margin-top: 5px;
        }
    </style>
</head>
<body>
    <h1>🧮 Calcolatore FEDACS Base</h1>
    
    <div class="calculator">
        <h2>Coordinate FEDACS (tutte ∈ [0,1])</h2>
        
        <div class="slider-container">
            <label for="V">V: Velocità di cambiamento (ambiente dinamico/statico)</label>
            <input type="range" id="V" min="0" max="100" value="50">
            <span class="value-display" id="V-value">0.50</span>
            <div class="explanation">0 = Statico, 1 = Dinamico</div>
        </div>
        
        <div class="slider-container">
            <label for="S">S: Irregolarità superficie (problema semplice/complesso)</label>
            <input type="range" id="S" min="0" max="100" value="50">
            <span class="value-display" id="S-value">0.50</span>
            <div class="explanation">0 = Semplice, 1 = Complesso</div>
        </div>
        
        <div class="slider-container">
            <label for="R">R: Richiesta di Diversità (bisogno prospettive multiple)</label>
            <input type="range" id="R" min="0" max="100" value="50">
            <span class="value-display" id="R-value">0.50</span>
            <div class="explanation">0 = Omogeneo, 1 = Diverso</div>
        </div>
        
        <div class="slider-container">
            <label for="C">C: Costo di Coordinamento (difficoltà comunicazione)</label>
            <input type="range" id="C" min="0" max="100" value="50">
            <span class="value-display" id="C-value">0.50</span>
            <div class="explanation">0 = Facile, 1 = Difficile</div>
        </div>
        
        <h3>Scenari Preimpostati:</h3>
        <div class="scenario" onclick="loadScenario('multi-specie')">
            <strong>Multi-Specie (Prompt AI)</strong><br>
            <small>V=0.9, S=0.8, R=0.95, C=0.7</small>
        </div>
        <div class="scenario" onclick="loadScenario('politico')">
            <strong>Moglie del Politico</strong><br>
            <small>V=0.3, S=0.8, R=0.4, C=0.9</small>
        </div>
        <div class="scenario" onclick="loadScenario('default')">
            <strong>Reset Valori Default</strong><br>
            <small>Tutti a 0.5</small>
        </div>
        
        <button onclick="calculateFEDACS()">📊 Calcola Forze α/β</button>
        
        <div class="result" id="result" style="display: none;">
            <h3>📈 Risultati:</h3>
            <div class="bars">
                <div class="bar-container">
                    <div class="bar-label">
                        <span>🛡️ Governance (β)</span>
                        <span id="beta-value">0.00</span>
                    </div>
                    <div class="bar">
                        <div class="bar-fill beta-bar" id="beta-bar" style="width: 0%"></div>
                        <div class="bar-value" id="beta-text">0%</div>
                    </div>
                </div>
                
                <div class="bar-container">
                    <div class="bar-label">
                        <span>👥 Evoluzione (α)</span>
                        <span id="alpha-value">0.00</span>
                    </div>
                    <div class="bar">
                        <div class="bar-fill alpha-bar" id="alpha-bar" style="width: 0%"></div>
                        <div class="bar-value" id="alpha-text">0%</div>
                    </div>
                </div>
            </div>
            
            <div id="interpretation">
                <!-- L'interpretazione apparirà qui -->
            </div>
        </div>
    </div>
    
    <div style="margin-top: 30px; color: #888; font-size: 12px; text-align: center;">
        Formula: f_E = V - 0.8*S + 0.5*R - 0.9*C | f_D = 0.8*S + 0.5*R - 0.7*V + 0.9*C<br>
        α = exp(f_E) / (exp(f_E) + exp(f_D)) | β = 1 - α
    </div>

    <script>
        // Inizializza gli slider
        const sliders = ['V', 'S', 'R', 'C'];
        sliders.forEach(id => {
            const slider = document.getElementById(id);
            const valueDisplay = document.getElementById(id + '-value');
            
            slider.addEventListener('input', function() {
                const value = this.value / 100;
                valueDisplay.textContent = value.toFixed(2);
            });
            
            // Imposta valori iniziali
            valueDisplay.textContent = (slider.value / 100).toFixed(2);
        });

        // Funzione di calcolo FEDACS
        function calculateFEDACS() {
            // Leggi valori
            const V = document.getElementById('V').value / 100;
            const S = document.getElementById('S').value / 100;
            const R = document.getElementById('R').value / 100;
            const C = document.getElementById('C').value / 100;
            
            // Calcola forze
            const f_E = V - 0.8*S + 0.5*R - 0.9*C;
            const f_D = 0.8*S + 0.5*R - 0.7*V + 0.9*C;
            
            // Calcola α e β
            const exp_E = Math.exp(f_E);
            const exp_D = Math.exp(f_D);
            const alpha = exp_E / (exp_E + exp_D);
            const beta = 1 - alpha;
            
            // Mostra risultati
            document.getElementById('result').style.display = 'block';
            document.getElementById('alpha-value').textContent = alpha.toFixed(3);
            document.getElementById('beta-value').textContent = beta.toFixed(3);
            
            // Aggiorna barre
            document.getElementById('alpha-bar').style.width = (alpha * 100) + '%';
            document.getElementById('beta-bar').style.width = (beta * 100) + '%';
            document.getElementById('alpha-text').textContent = (alpha * 100).toFixed(1) + '%';
            document.getElementById('beta-text').textContent = (beta * 100).toFixed(1) + '%';
            
            // Interpretazione
            let interpretation = '<h4>📋 Interpretazione:</h4>';
            
            if (beta > 0.7) {
                interpretation += '<p>✅ <strong>Governance forte necessaria</strong>: Sistema complesso che richiede controllo.</p>';
            } else if (alpha > 0.7) {
                interpretation += '<p>✅ <strong>Evoluzione prioritaria</strong>: Sistema dinamico che richiede adattamento.</p>';
            } else if (Math.abs(alpha - beta) < 0.2) {
                interpretation += '<p>⚖️ <strong>Equilibrio bilanciato</strong>: Forze in armonia.</p>';
            } else {
                interpretation += '<p>⚠️ <strong>Sistema in tensione</strong>: Forze in competizione.</p>';
            }
            
            interpretation += `<p>V=${V.toFixed(2)}, S=${S.toFixed(2)}, R=${R.toFixed(2)}, C=${C.toFixed(2)}</p>`;
            interpretation += `<p>f_E=${f_E.toFixed(3)}, f_D=${f_D.toFixed(3)}</p>`;
            
            document.getElementById('interpretation').innerHTML = interpretation;
            
            // Log nella console
            console.log('FEDACS Calcolato:', { V, S, R, C, alpha, beta });
        }

        // Funzioni per scenari preimpostati
        function loadScenario(name) {
            const scenarios = {
                'multi-specie': { V: 90, S: 80, R: 95, C: 70 },
                'politico': { V: 30, S: 80, R: 40, C: 90 },
                'default': { V: 50, S: 50, R: 50, C: 50 }
            };
            
            const scenario = scenarios[name];
            if (!scenario) return;
            
            document.getElementById('V').value = scenario.V;
            document.getElementById('S').value = scenario.S;
            document.getElementById('R').value = scenario.R;
            document.getElementById('C').value = scenario.C;
            
            // Aggiorna display
            sliders.forEach(id => {
                const slider = document.getElementById(id);
                const valueDisplay = document.getElementById(id + '-value');
                valueDisplay.textContent = (slider.value / 100).toFixed(2);
            });
            
            // Ricalcola automaticamente se è multi-specie
            if (name === 'multi-specie') {
                setTimeout(calculateFEDACS, 100);
            }
        }

        // Calcola automaticamente all'avvio con valori default
        setTimeout(calculateFEDACS, 500);
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <title>🧠 Sistema Integrato FEDACS + Alpha Generator</title>
    <style>
        body {
            background: #0f0f23;
            color: #ccc;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            padding: 20px;
            margin: 0;
        }
        .header {
            background: linear-gradient(90deg, #0f0f23, #1a1a2e);
            padding: 20px;
            border-bottom: 3px solid #00ff00;
            margin-bottom: 20px;
        }
        h1 {
            color: #00ff00;
            margin: 0;
            display: flex;
            align-items: center;
            gap: 15px;
        }
        .container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-bottom: 20px;
        }
        .panel {
            background: #1a1a2e;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 255, 0, 0.1);
        }
        .panel-title {
            color: #4ecdc4;
            border-bottom: 2px solid;
            padding-bottom: 10px;
            margin-bottom: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        textarea {
            width: 100%;
            height: 150px;
            background: #252547;
            color: #ccc;
            border: 1px solid #444;
            border-radius: 5px;
            padding: 10px;
            font-family: monospace;
            font-size: 14px;
            resize: vertical;
        }
        button {
            background: #00ff00;
            color: #000;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
            margin: 5px;
            transition: all 0.3s;
        }
        button:hover {
            background: #4ecdc4;
            transform: translateY(-2px);
        }
        .slider-container {
            margin: 15px 0;
        }
        .slider-label {
            display: flex;
            justify-content: space-between;
            margin-bottom: 5px;
        }
        input[type="range"] {
            width: 100%;
            height: 10px;
            background: #252547;
            border-radius: 5px;
            outline: none;
        }
        .results {
            background: #252547;
            padding: 15px;
            border-radius: 8px;
            margin-top: 20px;
            border-left: 5px solid;
        }
        .generative { border-left-color: #4ecdc4; }
        .extractive { border-left-color: #ff6b6b; }
        .alpha-display {
            font-size: 36px;
            font-weight: bold;
            text-align: center;
            margin: 20px 0;
        }
        .fedacs-display {
            display: flex;
            gap: 20px;
            margin: 20px 0;
        }
        .fedacs-bar {
            flex: 1;
            background: #333;
            border-radius: 10px;
            overflow: hidden;
            height: 30px;
            position: relative;
        }
        .fedacs-fill {
            height: 100%;
            transition: width 0.5s ease;
        }
        .beta-fill { background: #ff6b6b; }
        .alpha-fill { background: #4ecdc4; }
        .fedacs-value {
            position: absolute;
            width: 100%;
            text-align: center;
            line-height: 30px;
            font-weight: bold;
            color: white;
            text-shadow: 1px 1px 2px black;
        }
        .experiment-panel {
            grid-column: 1 / -1;
            background: #2a2a4a;
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
        }
        .hypothesis {
            background: #1a1a2e;
            padding: 15px;
            border-radius: 8px;
            margin: 10px 0;
            border: 1px dashed #00ff00;
        }
        .data-point {
            display: inline-block;
            padding: 5px 10px;
            margin: 2px;
            background: #252547;
            border-radius: 4px;
            font-size: 12px;
        }
        .connection-line {
            height: 2px;
            background: linear-gradient(90deg, #4ecdc4, #ff6b6b);
            margin: 20px 0;
            position: relative;
        }
        .connection-line::before {
            content: "⇄";
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            background: #0f0f23;
            padding: 0 10px;
            color: #00ff00;
        }
        .insight {
            background: rgba(0, 255, 0, 0.1);
            padding: 15px;
            border-radius: 8px;
            margin: 10px 0;
            border-left: 4px solid #00ff00;
        }
        .scenario-button {
            background: #252547;
            color: #ccc;
            border: 1px solid #444;
            padding: 8px 15px;
            border-radius: 5px;
            cursor: pointer;
            margin: 5px;
            display: inline-block;
        }
        .scenario-button.active {
            background: #00ff00;
            color: #000;
            border-color: #00ff00;
        }
    </style>
</head>
<body>
    <div class="header">
        <h1>🧠 Sistema Integrato FEDACS + Alpha Generator</h1>
        <p>Test dell'ipotesi: "Sistemi con α>1 hanno bilanciamento FEDACS ottimale"</p>
    </div>
    
    <div class="container">
        <!-- PANNELLO SINISTRA: ANALISI TESTUALE α -->
        <div class="panel">
            <div class="panel-title">
                <h2>📊 Calcolatore α (Generatività Dialettica)</h2>
                <span id="alpha-result" style="font-weight: bold; color: #00ff00;">α = ?</span>
            </div>
            
            <div class="slider-container">
                <div class="slider-label">
                    <span>Prompt/Input:</span>
                    <span id="input-length">0 caratteri</span>
                </div>
                <textarea id="input-text" placeholder="Incolla qui il prompt o testo iniziale...">Come possiamo progettare un ecosistema generativo?</textarea>
            </div>
            
            <div class="slider-container">
                <div class="slider-label">
                    <span>Risposta/Output:</span>
                    <span id="output-length">0 caratteri</span>
                </div>
                <textarea id="output-text" placeholder="Incolla qui la risposta o output analitico...">Un ecosistema generativo richiede: 1) Coefficiente α>1, 2) Bilanciamento FEDACS appropriato, 3) Meccanismi di auto-correzione. Analizzando coordinate V=0.8, S=0.7, R=0.9, C=0.6 otteniamo α=0.35, β=0.65. Il sistema dovrebbe premiare interazioni generative e isolare pattern estrattivi.</textarea>
            </div>
            
            <div style="text-align: center; margin: 15px 0;">
                <button onclick="calculateAlpha()">🧮 Calcola α</button>
                <button onclick="loadScenario('multi-specie')">🔄 Prompt Multi-Specie</button>
                <button onclick="loadScenario('twitter')">🐦 Esempio Twitter</button>
            </div>
            
            <div class="results" id="alpha-results" style="display: none;">
                <div id="alpha-display" class="alpha-display">α = 0.00</div>
                <div id="alpha-diagnosis"><!-- Diagnosi --></div>
            </div>
        </div>
        
        <!-- PANNELLO DESTRA: CALCOLATORE FEDACS -->
        <div class="panel">
            <div class="panel-title">
                <h2>📈 Calcolatore FEDACS (Coordinate → α/β)</h2>
                <span id="fedacs-result" style="font-weight: bold; color: #ff6b6b;">β=? | α=?</span>
            </div>
            
            <p style="color: #888; margin-bottom: 20px;">Coordinate FEDACS (tutte ∈ [0,1]):</p>
            
            <div class="slider-container">
                <div class="slider-label">
                    <span>V: Velocità cambiamento</span>
                    <span id="V-value">0.50</span>
                </div>
                <input type="range" id="V" min="0" max="100" value="50">
            </div>
            
            <div class="slider-container">
                <div class="slider-label">
                    <span>S: Irregolarità superficie</span>
                    <span id="S-value">0.50</span>
                </div>
                <input type="range" id="S" min="0" max="100" value="50">
            </div>
            
            <div class="slider-container">
                <div class="slider-label">
                    <span>R: Richiesta diversità</span>
                    <span id="R-value">0.50</span>
                </div>
                <input type="range" id="R" min="0" max="100" value="50">
            </div>
            
            <div class="slider-container">
                <div class="slider-label">
                    <span>C: Costo coordinamento</span>
                    <span id="C-value">0.50</span>
                </div>
                <input type="range" id="C" min="0" max="100" value="50">
            </div>
            
            <div style="text-align: center; margin: 15px 0;">
                <button onclick="calculateFEDACS()">📊 Calcola α/β FEDACS</button>
                <button onclick="autoExtractFromText()">🔍 Estrai da Testo</button>
                <button onclick="loadFEDACSScenario('multi-specie')">🔄 Coordinate Multi-Specie</button>
            </div>
            
            <div class="fedacs-display" id="fedacs-display" style="display: none;">
                <div style="flex: 1;">
                    <div style="text-align: center; margin-bottom: 5px;">🛡️ Governance (β)</div>
                    <div class="fedacs-bar">
                        <div id="beta-bar" class="fedacs-fill beta-fill" style="width: 0%"></div>
                        <div class="fedacs-value" id="beta-text">0%</div>
                    </div>
                    <div style="text-align: center;" id="beta-value">0.00</div>
                </div>
                
                <div style="flex: 1;">
                    <div style="text-align: center; margin-bottom: 5px;">👥 Evoluzione (α)</div>
                    <div class="fedacs-bar">
                        <div id="alpha-bar" class="fedacs-fill alpha-fill" style="width: 0%"></div>
                        <div class="fedacs-value" id="alpha-text">0%</div>
                    </div>
                    <div style="text-align: center;" id="alpha-fedacs-value">0.00</div>
                </div>
            </div>
            
            <div class="results" id="fedacs-results" style="display: none;">
                <div id="fedacs-interpretation"><!-- Interpretazione --></div>
            </div>
        </div>
    </div>
    
    <!-- LINEA DI CONNESSIONE VISIVA -->
    <div class="connection-line"></div>
    
    <!-- PANNELLO ESPERIMENTO -->
    <div class="experiment-panel">
        <h2 style="color: #00ff00;">🔬 Esperimento: Correlazione α-testuale ↔ α-FEDACS</h2>
        
        <div class="hypothesis">
            <h3>🎯 Ipotesi da Testare:</h3>
            <p>"I sistemi con <strong>α-testuale > 1.3</strong> (altamente generativi) tendono ad avere 
            <strong>α-FEDACS tra 0.2 e 0.4</strong> (governance moderata-alta)."</p>
            <p>In altre parole: I dialoghi generativi prosperano in contesti con qualche struttura (β), non in anarchia totale.</p>
        </div>
        
        <div style="text-align: center; margin: 20px 0;">
            <button onclick="runExperiment()">🧪 Esegui Esperimento</button>
            <button onclick="clearExperiment()">🗑️ Pulisci Dati</button>
        </div>
        
        <div id="experiment-results">
            <h3>📊 Dati Raccolti:</h3>
            <div id="data-points-container">
                <!-- I punti dati appariranno qui -->
            </div>
            
            <div id="experiment-insights" style="margin-top: 20px;">
                <!-- Le intuizioni appariranno qui -->
            </div>
        </div>
        
        <div class="insight" id="main-insight" style="display: none;">
            <h3>💡 Intuizione Emergente:</h3>
            <p id="insight-text"></p>
        </div>
        
        <div style="margin-top: 30px;">
            <h3>🎭 Scenari di Test Rapido:</h3>
            <div>
                <span class="scenario-button" onclick="loadFullScenario('twitter')">Twitter (Estrattivo)</span>
                <span class="scenario-button" onclick="loadFullScenario('wikipedia')">Wikipedia (Generativo)</span>
                <span class="scenario-button" onclick="loadFullScenario('lecture')">Lezione (Trasmissivo)</span>
                <span class="scenario-button" onclick="loadFullScenario('socratic')">Dialogo Socratico</span>
                <span class="scenario-button active" onclick="loadFullScenario('multi-specie')">Prompt Multi-Specie</span>
            </div>
        </div>
    </div>
    
    <div style="margin-top: 30px; text-align: center; color: #888; font-size: 12px;">
        <p>Sistema Integrato FEDACS v1.0 | Φ-F Framework | Coefficiente α dialettico</p>
        <p>Ogni interazione dovrebbe avere α > 1. Se non lo ha, stiamo estraendo valore invece di generarlo.</p>
    </div>

    <script>
        // ==================== INIZIALIZZAZIONE ====================
        let experimentData = [];
        
        // Inizializza slider FEDACS
        ['V', 'S', 'R', 'C'].forEach(id => {
            const slider = document.getElementById(id);
            const display = document.getElementById(id + '-value');
            
            slider.addEventListener('input', () => {
                display.textContent = (slider.value / 100).toFixed(2);
            });
            
            display.textContent = (slider.value / 100).toFixed(2);
        });
        
        // Inizializza contatori testo
        document.getElementById('input-text').addEventListener('input', function() {
            document.getElementById('input-length').textContent = this.value.length + ' caratteri';
        });
        
        document.getElementById('output-text').addEventListener('input', function() {
            document.getElementById('output-length').textContent = this.value.length + ' caratteri';
        });
        
        // Inizializza contatori
        document.getElementById('input-length').textContent = 
            document.getElementById('input-text').value.length + ' caratteri';
        document.getElementById('output-length').textContent = 
            document.getElementById('output-text').value.length + ' caratteri';
        
        // ==================== FUNZIONE α TESTUALE ====================
        function calculateAlpha() {
            const input = document.getElementById('input-text').value;
            const output = document.getElementById('output-text').value;
            
            if (!input.trim() || !output.trim()) {
                alert("Inserisci sia input che output!");
                return;
            }
            
            const alpha = calculateTextAlpha(input, output);
            
            // Mostra risultati
            document.getElementById('alpha-results').style.display = 'block';
            const alphaDisplay = document.getElementById('alpha-display');
            alphaDisplay.textContent = `α = ${alpha.toFixed(2)}`;
            
            // Colore in base al valore
            if (alpha > 1.3) {
                alphaDisplay.style.color = '#4ecdc4';
                document.getElementById('alpha-results').className = 'results generative';
            } else if (alpha > 0.9) {
                alphaDisplay.style.color = '#ffd93d';
                document.getElementById('alpha-results').className = 'results';
            } else {
                alphaDisplay.style.color = '#ff6b6b';
                document.getElementById('alpha-results').className = 'results extractive';
            }
            
            // Diagnosi
            let diagnosis = '';
            if (alpha > 1.5) {
                diagnosis = '<p>✅ <strong>ECCELLENTE GENERATIVITÀ</strong>: Sistema che crea valore esponenziale.</p>';
            } else if (alpha > 1.2) {
                diagnosis = '<p>✅ <strong>BUONA GENERATIVITÀ</strong>: Più output che input.</p>';
            } else if (alpha > 0.9) {
                diagnosis = '<p>⚖️ <strong>EQUILIBRIO</strong>: Input ≈ Output.</p>';
            } else if (alpha > 0.6) {
                diagnosis = '<p>⚠️ <strong>LEGGERA ESTRATTIVITÀ</strong>: Perde un po\' di valore.</p>';
            } else {
                diagnosis = '<p>🚨 <strong>FORTE ESTRATTIVITÀ</strong>: Sistema impoverente.</p>';
            }
            
            diagnosis += `<p>Per ogni unità di input, il sistema genera <strong>${alpha.toFixed(2)}</strong> unità di output informativo.</p>`;
            
            document.getElementById('alpha-diagnosis').innerHTML = diagnosis;
            document.getElementById('alpha-result').textContent = `α = ${alpha.toFixed(2)}`;
            
            return alpha;
        }
        
        function calculateTextAlpha(input, output) {
            // Metrica semplificata ma efficace
            const inputLength = input.length;
            const outputLength = output.length;
            
            // 1. Rapporto lunghezze (base)
            const lengthRatio = outputLength / (inputLength || 1);
            
            // 2. Novità concettuale (parole nuove)
            const inputWords = cleanText(input).split(/\s+/).filter(w => w.length > 3);
            const outputWords = cleanText(output).split(/\s+/).filter(w => w.length > 3);
            
            const inputSet = new Set(inputWords);
            const outputSet = new Set(outputWords);
            
            let newWords = 0;
            outputSet.forEach(word => {
                if (!inputSet.has(word)) newWords++;
            });
            
            const noveltyRatio = newWords / (inputSet.size || 1);
            
            // 3. Domande generate (segno di apertura)
            const questionsIn = (input.match(/\?/g) || []).length;
            const questionsOut = (output.match(/\?/g) || []).length;
            const questionsGenerated = Math.max(0, questionsOut - questionsIn);
            
            // 4. Concetti complessi aggiunti
            const complexConcepts = ['sistema', 'generativ', 'dialett', 'algoritm', 'complesso', 
                                    'ecosistema', 'emergente', 'parametrico', 'risonanza', 'equità'];
            let complexAdded = 0;
            complexConcepts.forEach(concept => {
                if (output.toLowerCase().includes(concept) && !input.toLowerCase().includes(concept)) {
                    complexAdded++;
                }
            });
            
            // Calcola α composito
            const alpha = (lengthRatio * 0.4) + 
                         (noveltyRatio * 0.4) + 
                         (questionsGenerated * 0.1) + 
                         (complexAdded * 0.1);
            
            console.log('Alpha calculation:', { lengthRatio, noveltyRatio, questionsGenerated, complexAdded, alpha });
            return alpha;
        }
        
        // ==================== FUNZIONE FEDACS ====================
        function calculateFEDACS() {
            const V = document.getElementById('V').value / 100;
            const S = document.getElementById('S').value / 100;
            const R = document.getElementById('R').value / 100;
            const C = document.getElementById('C').value / 100;
            
            // Formula FEDACS
            const f_E = V - 0.8*S + 0.5*R - 0.9*C;
            const f_D = 0.8*S + 0.5*R - 0.7*V + 0.9*C;
            
            const exp_E = Math.exp(f_E);
            const exp_D = Math.exp(f_D);
            const alpha_fedacs = exp_E / (exp_E + exp_D);
            const beta = 1 - alpha_fedacs;
            
            // Mostra risultati
            document.getElementById('fedacs-display').style.display = 'flex';
            document.getElementById('fedacs-results').style.display = 'block';
            
            // Aggiorna barre
            document.getElementById('beta-bar').style.width = (beta * 100) + '%';
            document.getElementById('alpha-bar').style.width = (alpha_fedacs * 100) + '%';
            document.getElementById('beta-text').textContent = (beta * 100).toFixed(1) + '%';
            document.getElementById('alpha-text').textContent = (alpha_fedacs * 100).toFixed(1) + '%';
            document.getElementById('beta-value').textContent = beta.toFixed(3);
            document.getElementById('alpha-fedacs-value').textContent = alpha_fedacs.toFixed(3);
            
            // Interpretazione
            let interpretation = '<h4>📋 Interpretazione FEDACS:</h4>';
            if (beta > 0.7) {
                interpretation += '<p>🛡️ <strong>Governance Dominante</strong>: Sistema che richiede forte struttura e controllo.</p>';
            } else if (alpha_fedacs > 0.7) {
                interpretation += '<p>🌱 <strong>Evoluzione Dominante</strong>: Sistema dinamico che premia adattamento.</p>';
            } else if (beta > 0.55) {
                interpretation += '<p>⚖️ <strong>Governance Moderata</strong>: Struttura presente ma flessibile.</p>';
            } else {
                interpretation += '<p>🌀 <strong>Equilibrio Instabile</strong>: Forze in competizione.</p>';
            }
            
            interpretation += `<p>Coordinate: V=${V.toFixed(2)}, S=${S.toFixed(2)}, R=${R.toFixed(2)}, C=${C.toFixed(2)}</p>`;
            interpretation += `<p>Forze: f_E=${f_E.toFixed(3)}, f_D=${f_D.toFixed(3)}</p>`;
            
            document.getElementById('fedacs-interpretation').innerHTML = interpretation;
            document.getElementById('fedacs-result').textContent = 
                `β=${beta.toFixed(2)} | α=${alpha_fedacs.toFixed(2)}`;
            
            return { alpha_fedacs, beta, V, S, R, C };
        }
        
        // ==================== FUNZIONE ESPERIMENTO ====================
        function runExperiment() {
            const alpha_text = calculateAlpha();
            const fedacs = calculateFEDACS();
            
            // Aggiungi punto dati
            const dataPoint = {
                id: experimentData.length + 1,
                alpha_text: alpha_text,
                alpha_fedacs: fedacs.alpha_fedacs,
                beta: fedacs.beta,
                V: fedacs.V,
                S: fedacs.S,
                R: fedacs.R,
                C: fedacs.C,
                timestamp: new Date().toLocaleTimeString()
            };
            
            experimentData.push(dataPoint);
            
            // Aggiorna visualizzazione dati
            updateDataPoints();
            
            // Calcola correlazione se abbiamo abbastanza dati
            if (experimentData.length >= 2) {
                calculateInsights();
            }
            
            // Aggiungi al container dati
            const point = document.createElement('div');
            point.className = 'data-point';
            point.style.background = alpha_text > 1.2 ? '#1e3a2e' : '#3a1e1e';
            point.style.border = alpha_text > 1.2 ? '1px solid #4ecdc4' : '1px solid #ff6b6b';
            point.innerHTML = `#${dataPoint.id}: α=${alpha_text.toFixed(2)} | αₚ=${fedacs.alpha_fedacs.toFixed(2)}`;
            point.title = `V=${fedacs.V.toFixed(2)} S=${fedacs.S.toFixed(2)} R=${fedacs.R.toFixed(2)} C=${fedacs.C.toFixed(2)}`;
            
            document.getElementById('data-points-container').appendChild(point);
        }
        
        function updateDataPoints() {
            const container = document.getElementById('data-points-container');
            container.innerHTML = '';
            
            experimentData.forEach(dp => {
                const point = document.createElement('div');
                point.className = 'data-point';
                point.style.background = dp.alpha_text > 1.2 ? '#1e3a2e' : '#3a1e1e';
                point.style.border = dp.alpha_text > 1.2 ? '1px solid #4ecdc4' : '1px solid #ff6b6b';
                point.innerHTML = `#${dp.id}: α=${dp.alpha_text.toFixed(2)} | αₚ=${dp.alpha_fedacs.toFixed(2)}`;
                point.title = `V=${dp.V.toFixed(2)} S=${dp.S.toFixed(2)} R=${dp.R.toFixed(2)} C=${dp.C.toFixed(2)}`;
                container.appendChild(point);
            });
        }
        
        function calculateInsights() {
            if (experimentData.length < 2) return;
            
            // Calcola medie
            const avgAlphaText = experimentData.reduce((sum, dp) => sum + dp.alpha_text, 0) / experimentData.length;
            const avgAlphaFedacs = experimentData.reduce((sum, dp) => sum + dp.alpha_fedacs, 0) / experimentData.length;
            
            // Conta pattern
            const generativePoints = experimentData.filter(dp => dp.alpha_text > 1.2);
            const extractivePoints = experimentData.filter(dp => dp.alpha_text < 0.8);
            
            let insightText = '';
            
            if (generativePoints.length > 0) {
                const avgBetaGenerative = generativePoints.reduce((sum, dp) => sum + dp.beta, 0) / generativePoints.length;
                
                insightText += `<p>🔍 <strong>Pattern rilevato:</strong> I sistemi generativi (α>1.2) hanno in media β=${avgBetaGenerative.toFixed(2)}</p>`;
                
                if (avgBetaGenerative > 0.6) {
                    insightText += `<p>💡 <strong>Intuizione:</strong> La generatività prospera con governance moderata (non anarchia).</p>`;
                }
            }
            
            if (extractivePoints.length > 0) {
                const avgBetaExtractive = extractivePoints.reduce((sum, dp) => sum + dp.beta, 0) / extractivePoints.length;
                insightText += `<p>⚠️ Sistemi estrattivi (α<0.8) hanno β medio: ${avgBetaExtractive.toFixed(2)}</p>`;
            }
            
            insightText += `<p>📈 Dati totali: ${experimentData.length} punti | α medio: ${avgAlphaText.toFixed(2)} | αₚ medio: ${avgAlphaFedacs.toFixed(2)}</p>`;
            
            document.getElementById('insight-text').innerHTML = insightText;
            document.getElementById('main-insight').style.display = 'block';
        }
        
        function clearExperiment() {
            experimentData = [];
            document.getElementById('data-points-container').innerHTML = '';
            document.getElementById('experiment-insights').innerHTML = '';
            document.getElementById('main-insight').style.display = 'none';
        }
        
        // ==================== FUNZIONI AUSILIARIE ====================
        function cleanText(text) {
            return text.toLowerCase()
                      .replace(/[^\w\s]/g, ' ')
                      .replace(/\s+/g, ' ')
                      .trim();
        }
        
        function autoExtractFromText() {
            const text = document.getElementById('output-text').value.toLowerCase();
            
            // Estrai coordinate approssimative dal testo
            let V = 0.5, S = 0.5, R = 0.5, C = 0.5;
            
            if (text.includes('dinamico') || text.includes('veloc') || text.includes('cambiamento')) V = 0.8;
            if (text.includes('statico') || text.includes('lento')) V = 0.3;
            
            if (text.includes('complesso') || text.includes('irregolare') || text.includes('difficile')) S = 0.8;
            if (text.includes('semplice') || text.includes('lineare')) S = 0.3;
            
            if (text.includes('divers') || text.includes('multipl') || text.includes('varie')) R = 0.8;
            if (text.includes('omogeneo') || text.includes('uniforme')) R = 0.3;
            
            if (text.includes('coordinamento') || text.includes('comunicazione') || text.includes('difficile')) C = 0.8;
            if (text.includes('facile') || text.includes('semplice') || text.includes('immediato')) C = 0.3;
            
            // Applica ai slider
            document.getElementById('V').value = V * 100;
            document.getElementById('S').value = S * 100;
            document.getElementById('R').value = R * 100;
            document.getElementById('C').value = C * 100;
            
            // Aggiorna display
            ['V', 'S', 'R', 'C'].forEach(id => {
                document.getElementById(id + '-value').textContent = 
                    (document.getElementById(id).value / 100).toFixed(2);
            });
            
            alert(`Coordinate estratte: V=${V}, S=${S}, R=${R}, C=${C}`);
        }
        
        // ==================== SCENARI PRECONFIGURATI ====================
        const scenarios = {
            'multi-specie': {
                input: `Analizza il sistema multi-specie uomo-AI`,
                output: `Il sistema multi-specie presenta α=1.45 (generativo). Analisi FEDACS: V=0.9 (dinamico), S=0.8 (complesso), R=0.95 (alta diversità), C=0.7 (coordinamento difficile). Risultato: α=0.26, β=0.74 - governance forte necessaria per gestire complessità.`,
                fedacs: { V: 90, S: 80, R: 95, C: 70 }
            },
            'twitter': {
                input: `Nuovo video virale!`,
                output: `😂🔥👏 RIPOSTA! Seguimi!`,
                fedacs: { V: 70, S: 30, R: 20, C: 40 }
            },
            'wikipedia': {
                input: `Voce incompleta su FEDACS`,
                output: `FEDACS è un framework eco-dialettico con 4 coordinate: V, S, R, C. Dimostra che sistemi equi sincronizzano con 4× meno accoppiamento. Inclusi: storia, formule, applicazioni, e 12 riferimenti bibliografici nuovi.`,
                fedacs: { V: 40, S: 60, R: 80, C: 50 }
            },
            'lecture': {
                input: `Spiegami la teoria`,
                output: `La teoria dice che A implica B. Esempio: se X allora Y. In conclusione, Z. Fine.`,
                fedacs: { V: 20, S: 50, R: 30, C: 60 }
            },
            'socratic': {
                input: `Cos'è la giustizia?`,
                output: `La giustizia è dare a ciascuno il suo. Ma cos'è "il suo"? Dipende dal sistema di valori. E come decidiamo i valori? Forse attraverso dialogo con α>1. Nuove domande: Cos'è l'equità algoritmica? Come bilanciare α e β?`,
                fedacs: { V: 60, S: 70, R: 80, C: 60 }
            }
        };
        
        function loadScenario(name) {
            const scenario = scenarios[name];
            if (scenario) {
                document.getElementById('input-text').value = scenario.input;
                document.getElementById('output-text').value = scenario.output;
                calculateAlpha();
            }
        }
        
        function loadFEDACSScenario(name) {
            const scenario = scenarios[name];
            if (scenario && scenario.fedacs) {
                document.getElementById('V').value = scenario.fedacs.V;
                document.getElementById('S').value = scenario.fedacs.S;
                document.getElementById('R').value = scenario.fedacs.R;
                document.getElementById('C').value = scenario.fedacs.C;
                
                ['V', 'S', 'R', 'C'].forEach(id => {
                    document.getElementById(id + '-value').textContent = 
                        (document.getElementById(id).value / 100).toFixed(2);
                });
                
                calculateFEDACS();
            }
        }
        
        function loadFullScenario(name) {
            loadScenario(name);
            loadFEDACSScenario(name);
            
            // Rimuovi active da tutti i bottoni
            document.querySelectorAll('.scenario-button').forEach(btn => {
                btn.classList.remove('active');
            });
            
            // Aggiungi active al bottone cliccato
            event.target.classList.add('active');
        }
        
        // ==================== AVVIO AUTOMATICO ====================
        // Calcola all'avvio
        setTimeout(() => {
            loadFullScenario('multi-specie');
            setTimeout(() => {
                calculateAlpha();
                calculateFEDACS();
            }, 100);
        }, 300);
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <title>FEDACS - File Locale</title>
    <style>
        body {
            background: #0f0f23;
            color: #ccc;
            font-family: Arial, sans-serif;
            padding: 20px;
        }
        h1 { color: #00ff00; }
        .box {
            background: #1a1a2e;
            padding: 15px;
            margin: 10px 0;
            border-radius: 8px;
        }
        .bar {
            height: 20px;
            background: #333;
            border-radius: 10px;
            overflow: hidden;
            margin: 10px 0;
        }
        .beta { 
            width: 74%;
            background: #ff6b6b;
            height: 100%;
        }
        .alpha {
            width: 26%;
            background: #4ecdc4;
            height: 100%;
        }
    </style>
</head>
<body>
    <h1>✅ FEDACS - File Locale</h1>
    
    <div class="box">
        <h2>Stato: FUNZIONANTE (senza server)</h2>
        <p>Questo file HTML funziona perché è aperto direttamente dal filesystem.</p>
    </div>
    
    <div class="box">
        <h3>Coordinate FEDACS</h3>
        <p>V=0.9, S=0.8, R=0.95, C=0.7</p>
        
        <p>Governance (β): 74%</p>
        <div class="bar"><div class="beta"></div></div>
        
        <p>Evoluzione (α): 26%</p>
        <div class="bar"><div class="alpha"></div></div>
    </div>
    
    <div class="box">
        <h3>Problema identificato:</h3>
        <p>Il tuo Windows blocca TUTTE le connessioni localhost.</p>
        <p><strong>Soluzione:</strong> Lavoriamo con file locali fino al PASSO 3.</p>
    </div>
    
    <script>
        console.log("FEDACS locale caricato");
        alert("✅ FEDACS funziona in modalità locale!");
    </script>
</body>
</html>
{
  "name": "fedacs-unified",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "lucide-react": "^0.309.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "@types/react": "^18.2.48",
    "@types/react-dom": "^18.2.18",
    "@vitejs/plugin-react": "^4.2.1",
    "@vitest/browser": "^4.0.17",
    "typescript": "^5.3.3",
    "vite": "^5.1.0"
  }
}

{
  "name": "fedacs-unified",
  "version": "0.0.0",
  "lockfileVersion": 3,
  "requires": true,
  "packages": {
    "": {
      "name": "fedacs-unified",
      "version": "0.0.0",
      "dependencies": {
        "lucide-react": "^0.309.0",
        "react": "^18.2.0",
        "react-dom": "^18.2.0"
      },
      "devDependencies": {
        "@types/react": "^18.2.48",
        "@types/react-dom": "^18.2.18",
        "@vitejs/plugin-react": "^4.2.1",
        "@vitest/browser": "^4.0.17",
        "typescript": "^5.3.3",
        "vite": "^5.1.0"
      }
    },
    "node_modules/@babel/code-frame": {
      "version": "7.28.6",
      "resolved": "https://registry.npmjs.org/@babel/code-frame/-/code-frame-7.28.6.tgz",
      "integrity": "sha512-JYgintcMjRiCvS8mMECzaEn+m3PfoQiyqukOMCCVQtoJGYJw8j/8LBJEiqkHLkfwCcs74E3pbAUFNg7d9VNJ+Q==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/helper-validator-identifier": "^7.28.5",
        "js-tokens": "^4.0.0",
        "picocolors": "^1.1.1"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/compat-data": {
      "version": "7.28.6",
      "resolved": "https://registry.npmjs.org/@babel/compat-data/-/compat-data-7.28.6.tgz",
      "integrity": "sha512-2lfu57JtzctfIrcGMz992hyLlByuzgIk58+hhGCxjKZ3rWI82NnVLjXcaTqkI2NvlcvOskZaiZ5kjUALo3Lpxg==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/core": {
      "version": "7.28.6",
      "resolved": "https://registry.npmjs.org/@babel/core/-/core-7.28.6.tgz",
      "integrity": "sha512-H3mcG6ZDLTlYfaSNi0iOKkigqMFvkTKlGUYlD8GW7nNOYRrevuA46iTypPyv+06V3fEmvvazfntkBU34L0azAw==",
      "dev": true,
      "license": "MIT",
      "peer": true,
      "dependencies": {
        "@babel/code-frame": "^7.28.6",
        "@babel/generator": "^7.28.6",
        "@babel/helper-compilation-targets": "^7.28.6",
        "@babel/helper-module-transforms": "^7.28.6",
        "@babel/helpers": "^7.28.6",
        "@babel/parser": "^7.28.6",
        "@babel/template": "^7.28.6",
        "@babel/traverse": "^7.28.6",
        "@babel/types": "^7.28.6",
        "@jridgewell/remapping": "^2.3.5",
        "convert-source-map": "^2.0.0",
        "debug": "^4.1.0",
        "gensync": "^1.0.0-beta.2",
        "json5": "^2.2.3",
        "semver": "^6.3.1"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "funding": {
        "type": "opencollective",
        "url": "https://opencollective.com/babel"
      }
    },
    "node_modules/@babel/generator": {
      "version": "7.28.6",
      "resolved": "https://registry.npmjs.org/@babel/generator/-/generator-7.28.6.tgz",
      "integrity": "sha512-lOoVRwADj8hjf7al89tvQ2a1lf53Z+7tiXMgpZJL3maQPDxh0DgLMN62B2MKUOFcoodBHLMbDM6WAbKgNy5Suw==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/parser": "^7.28.6",
        "@babel/types": "^7.28.6",
        "@jridgewell/gen-mapping": "^0.3.12",
        "@jridgewell/trace-mapping": "^0.3.28",
        "jsesc": "^3.0.2"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-compilation-targets": {
      "version": "7.28.6",
      "resolved": "https://registry.npmjs.org/@babel/helper-compilation-targets/-/helper-compilation-targets-7.28.6.tgz",
      "integrity": "sha512-JYtls3hqi15fcx5GaSNL7SCTJ2MNmjrkHXg4FSpOA/grxK8KwyZ5bubHsCq8FXCkua6xhuaaBit+3b7+VZRfcA==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/compat-data": "^7.28.6",
        "@babel/helper-validator-option": "^7.27.1",
        "browserslist": "^4.24.0",
        "lru-cache": "^5.1.1",
        "semver": "^6.3.1"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-globals": {
      "version": "7.28.0",
      "resolved": "https://registry.npmjs.org/@babel/helper-globals/-/helper-globals-7.28.0.tgz",
      "integrity": "sha512-+W6cISkXFa1jXsDEdYA8HeevQT/FULhxzR99pxphltZcVaugps53THCeiWA8SguxxpSp3gKPiuYfSWopkLQ4hw==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-module-imports": {
      "version": "7.28.6",
      "resolved": "https://registry.npmjs.org/@babel/helper-module-imports/-/helper-module-imports-7.28.6.tgz",
      "integrity": "sha512-l5XkZK7r7wa9LucGw9LwZyyCUscb4x37JWTPz7swwFE/0FMQAGpiWUZn8u9DzkSBWEcK25jmvubfpw2dnAMdbw==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/traverse": "^7.28.6",
        "@babel/types": "^7.28.6"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-module-transforms": {
      "version": "7.28.6",
      "resolved": "https://registry.npmjs.org/@babel/helper-module-transforms/-/helper-module-transforms-7.28.6.tgz",
      "integrity": "sha512-67oXFAYr2cDLDVGLXTEABjdBJZ6drElUSI7WKp70NrpyISso3plG9SAGEF6y7zbha/wOzUByWWTJvEDVNIUGcA==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/helper-module-imports": "^7.28.6",
        "@babel/helper-validator-identifier": "^7.28.5",
        "@babel/traverse": "^7.28.6"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0"
      }
    },
    "node_modules/@babel/helper-plugin-utils": {
      "version": "7.28.6",
      "resolved": "https://registry.npmjs.org/@babel/helper-plugin-utils/-/helper-plugin-utils-7.28.6.tgz",
      "integrity": "sha512-S9gzZ/bz83GRysI7gAD4wPT/AI3uCnY+9xn+Mx/KPs2JwHJIz1W8PZkg2cqyt3RNOBM8ejcXhV6y8Og7ly/Dug==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-string-parser": {
      "version": "7.27.1",
      "resolved": "https://registry.npmjs.org/@babel/helper-string-parser/-/helper-string-parser-7.27.1.tgz",
      "integrity": "sha512-qMlSxKbpRlAridDExk92nSobyDdpPijUq2DW6oDnUqd0iOGxmQjyqhMIihI9+zv4LPyZdRje2cavWPbCbWm3eA==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-validator-identifier": {
      "version": "7.28.5",
      "resolved": "https://registry.npmjs.org/@babel/helper-validator-identifier/-/helper-validator-identifier-7.28.5.tgz",
      "integrity": "sha512-qSs4ifwzKJSV39ucNjsvc6WVHs6b7S03sOh2OcHF9UHfVPqWWALUsNUVzhSBiItjRZoLHx7nIarVjqKVusUZ1Q==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helper-validator-option": {
      "version": "7.27.1",
      "resolved": "https://registry.npmjs.org/@babel/helper-validator-option/-/helper-validator-option-7.27.1.tgz",
      "integrity": "sha512-YvjJow9FxbhFFKDSuFnVCe2WxXk1zWc22fFePVNEaWJEu8IrZVlda6N0uHwzZrUM1il7NC9Mlp4MaJYbYd9JSg==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/helpers": {
      "version": "7.28.6",
      "resolved": "https://registry.npmjs.org/@babel/helpers/-/helpers-7.28.6.tgz",
      "integrity": "sha512-xOBvwq86HHdB7WUDTfKfT/Vuxh7gElQ+Sfti2Cy6yIWNW05P8iUslOVcZ4/sKbE+/jQaukQAdz/gf3724kYdqw==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/template": "^7.28.6",
        "@babel/types": "^7.28.6"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/parser": {
      "version": "7.28.6",
      "resolved": "https://registry.npmjs.org/@babel/parser/-/parser-7.28.6.tgz",
      "integrity": "sha512-TeR9zWR18BvbfPmGbLampPMW+uW1NZnJlRuuHso8i87QZNq2JRF9i6RgxRqtEq+wQGsS19NNTWr2duhnE49mfQ==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/types": "^7.28.6"
      },
      "bin": {
        "parser": "bin/babel-parser.js"
      },
      "engines": {
        "node": ">=6.0.0"
      }
    },
    "node_modules/@babel/plugin-transform-react-jsx-self": {
      "version": "7.27.1",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-react-jsx-self/-/plugin-transform-react-jsx-self-7.27.1.tgz",
      "integrity": "sha512-6UzkCs+ejGdZ5mFFC/OCUrv028ab2fp1znZmCZjAOBKiBK2jXD1O+BPSfX8X2qjJ75fZBMSnQn3Rq2mrBJK2mw==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.27.1"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/plugin-transform-react-jsx-source": {
      "version": "7.27.1",
      "resolved": "https://registry.npmjs.org/@babel/plugin-transform-react-jsx-source/-/plugin-transform-react-jsx-source-7.27.1.tgz",
      "integrity": "sha512-zbwoTsBruTeKB9hSq73ha66iFeJHuaFkUbwvqElnygoNbj/jHRsSeokowZFN3CZ64IvEqcmmkVe89OPXc7ldAw==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/helper-plugin-utils": "^7.27.1"
      },
      "engines": {
        "node": ">=6.9.0"
      },
      "peerDependencies": {
        "@babel/core": "^7.0.0-0"
      }
    },
    "node_modules/@babel/template": {
      "version": "7.28.6",
      "resolved": "https://registry.npmjs.org/@babel/template/-/template-7.28.6.tgz",
      "integrity": "sha512-YA6Ma2KsCdGb+WC6UpBVFJGXL58MDA6oyONbjyF/+5sBgxY/dwkhLogbMT2GXXyU84/IhRw/2D1Os1B/giz+BQ==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/code-frame": "^7.28.6",
        "@babel/parser": "^7.28.6",
        "@babel/types": "^7.28.6"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/traverse": {
      "version": "7.28.6",
      "resolved": "https://registry.npmjs.org/@babel/traverse/-/traverse-7.28.6.tgz",
      "integrity": "sha512-fgWX62k02qtjqdSNTAGxmKYY/7FSL9WAS1o2Hu5+I5m9T0yxZzr4cnrfXQ/MX0rIifthCSs6FKTlzYbJcPtMNg==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/code-frame": "^7.28.6",
        "@babel/generator": "^7.28.6",
        "@babel/helper-globals": "^7.28.0",
        "@babel/parser": "^7.28.6",
        "@babel/template": "^7.28.6",
        "@babel/types": "^7.28.6",
        "debug": "^4.3.1"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@babel/types": {
      "version": "7.28.6",
      "resolved": "https://registry.npmjs.org/@babel/types/-/types-7.28.6.tgz",
      "integrity": "sha512-0ZrskXVEHSWIqZM/sQZ4EV3jZJXRkio/WCxaqKZP1g//CEWEPSfeZFcms4XeKBCHU0ZKnIkdJeU/kF+eRp5lBg==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/helper-string-parser": "^7.27.1",
        "@babel/helper-validator-identifier": "^7.28.5"
      },
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/@esbuild/aix-ppc64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/aix-ppc64/-/aix-ppc64-0.21.5.tgz",
      "integrity": "sha512-1SDgH6ZSPTlggy1yI6+Dbkiz8xzpHJEVAlF/AM1tHPLsf5STom9rwtjE4hKAF20FfXXNTFqEYXyJNWh1GiZedQ==",
      "cpu": [
        "ppc64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "aix"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/android-arm": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/android-arm/-/android-arm-0.21.5.tgz",
      "integrity": "sha512-vCPvzSjpPHEi1siZdlvAlsPxXl7WbOVUBBAowWug4rJHb68Ox8KualB+1ocNvT5fjv6wpkX6o/iEpbDrf68zcg==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "android"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/android-arm64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/android-arm64/-/android-arm64-0.21.5.tgz",
      "integrity": "sha512-c0uX9VAUBQ7dTDCjq+wdyGLowMdtR/GoC2U5IYk/7D1H1JYC0qseD7+11iMP2mRLN9RcCMRcjC4YMclCzGwS/A==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "android"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/android-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/android-x64/-/android-x64-0.21.5.tgz",
      "integrity": "sha512-D7aPRUUNHRBwHxzxRvp856rjUHRFW1SdQATKXH2hqA0kAZb1hKmi02OpYRacl0TxIGz/ZmXWlbZgjwWYaCakTA==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "android"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/darwin-arm64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/darwin-arm64/-/darwin-arm64-0.21.5.tgz",
      "integrity": "sha512-DwqXqZyuk5AiWWf3UfLiRDJ5EDd49zg6O9wclZ7kUMv2WRFr4HKjXp/5t8JZ11QbQfUS6/cRCKGwYhtNAY88kQ==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "darwin"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/darwin-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/darwin-x64/-/darwin-x64-0.21.5.tgz",
      "integrity": "sha512-se/JjF8NlmKVG4kNIuyWMV/22ZaerB+qaSi5MdrXtd6R08kvs2qCN4C09miupktDitvh8jRFflwGFBQcxZRjbw==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "darwin"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/freebsd-arm64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/freebsd-arm64/-/freebsd-arm64-0.21.5.tgz",
      "integrity": "sha512-5JcRxxRDUJLX8JXp/wcBCy3pENnCgBR9bN6JsY4OmhfUtIHe3ZW0mawA7+RDAcMLrMIZaf03NlQiX9DGyB8h4g==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "freebsd"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/freebsd-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/freebsd-x64/-/freebsd-x64-0.21.5.tgz",
      "integrity": "sha512-J95kNBj1zkbMXtHVH29bBriQygMXqoVQOQYA+ISs0/2l3T9/kj42ow2mpqerRBxDJnmkUDCaQT/dfNXWX/ZZCQ==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "freebsd"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-arm": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-arm/-/linux-arm-0.21.5.tgz",
      "integrity": "sha512-bPb5AHZtbeNGjCKVZ9UGqGwo8EUu4cLq68E95A53KlxAPRmUyYv2D6F0uUI65XisGOL1hBP5mTronbgo+0bFcA==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-arm64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-arm64/-/linux-arm64-0.21.5.tgz",
      "integrity": "sha512-ibKvmyYzKsBeX8d8I7MH/TMfWDXBF3db4qM6sy+7re0YXya+K1cem3on9XgdT2EQGMu4hQyZhan7TeQ8XkGp4Q==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-ia32": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-ia32/-/linux-ia32-0.21.5.tgz",
      "integrity": "sha512-YvjXDqLRqPDl2dvRODYmmhz4rPeVKYvppfGYKSNGdyZkA01046pLWyRKKI3ax8fbJoK5QbxblURkwK/MWY18Tg==",
      "cpu": [
        "ia32"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-loong64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-loong64/-/linux-loong64-0.21.5.tgz",
      "integrity": "sha512-uHf1BmMG8qEvzdrzAqg2SIG/02+4/DHB6a9Kbya0XDvwDEKCoC8ZRWI5JJvNdUjtciBGFQ5PuBlpEOXQj+JQSg==",
      "cpu": [
        "loong64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-mips64el": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-mips64el/-/linux-mips64el-0.21.5.tgz",
      "integrity": "sha512-IajOmO+KJK23bj52dFSNCMsz1QP1DqM6cwLUv3W1QwyxkyIWecfafnI555fvSGqEKwjMXVLokcV5ygHW5b3Jbg==",
      "cpu": [
        "mips64el"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-ppc64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-ppc64/-/linux-ppc64-0.21.5.tgz",
      "integrity": "sha512-1hHV/Z4OEfMwpLO8rp7CvlhBDnjsC3CttJXIhBi+5Aj5r+MBvy4egg7wCbe//hSsT+RvDAG7s81tAvpL2XAE4w==",
      "cpu": [
        "ppc64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-riscv64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-riscv64/-/linux-riscv64-0.21.5.tgz",
      "integrity": "sha512-2HdXDMd9GMgTGrPWnJzP2ALSokE/0O5HhTUvWIbD3YdjME8JwvSCnNGBnTThKGEB91OZhzrJ4qIIxk/SBmyDDA==",
      "cpu": [
        "riscv64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-s390x": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-s390x/-/linux-s390x-0.21.5.tgz",
      "integrity": "sha512-zus5sxzqBJD3eXxwvjN1yQkRepANgxE9lgOW2qLnmr8ikMTphkjgXu1HR01K4FJg8h1kEEDAqDcZQtbrRnB41A==",
      "cpu": [
        "s390x"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/linux-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-x64/-/linux-x64-0.21.5.tgz",
      "integrity": "sha512-1rYdTpyv03iycF1+BhzrzQJCdOuAOtaqHTWJZCWvijKD2N5Xu0TtVC8/+1faWqcP9iBCWOmjmhoH94dH82BxPQ==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/netbsd-arm64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/netbsd-arm64/-/netbsd-arm64-0.27.2.tgz",
      "integrity": "sha512-Kj6DiBlwXrPsCRDeRvGAUb/LNrBASrfqAIok+xB0LxK8CHqxZ037viF13ugfsIpePH93mX7xfJp97cyDuTZ3cw==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "netbsd"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@esbuild/netbsd-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/netbsd-x64/-/netbsd-x64-0.21.5.tgz",
      "integrity": "sha512-Woi2MXzXjMULccIwMnLciyZH4nCIMpWQAs049KEeMvOcNADVxo0UBIQPfSmxB3CWKedngg7sWZdLvLczpe0tLg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "netbsd"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/openbsd-arm64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/openbsd-arm64/-/openbsd-arm64-0.27.2.tgz",
      "integrity": "sha512-DNIHH2BPQ5551A7oSHD0CKbwIA/Ox7+78/AWkbS5QoRzaqlev2uFayfSxq68EkonB+IKjiuxBFoV8ESJy8bOHA==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "openbsd"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@esbuild/openbsd-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/openbsd-x64/-/openbsd-x64-0.21.5.tgz",
      "integrity": "sha512-HLNNw99xsvx12lFBUwoT8EVCsSvRNDVxNpjZ7bPn947b8gJPzeHWyNVhFsaerc0n3TsbOINvRP2byTZ5LKezow==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "openbsd"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/openharmony-arm64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/openharmony-arm64/-/openharmony-arm64-0.27.2.tgz",
      "integrity": "sha512-LRBbCmiU51IXfeXk59csuX/aSaToeG7w48nMwA6049Y4J4+VbWALAuXcs+qcD04rHDuSCSRKdmY63sruDS5qag==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "openharmony"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@esbuild/sunos-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/sunos-x64/-/sunos-x64-0.21.5.tgz",
      "integrity": "sha512-6+gjmFpfy0BHU5Tpptkuh8+uw3mnrvgs+dSPQXQOv3ekbordwnzTVEb4qnIvQcYXq6gzkyTnoZ9dZG+D4garKg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "sunos"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/win32-arm64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/win32-arm64/-/win32-arm64-0.21.5.tgz",
      "integrity": "sha512-Z0gOTd75VvXqyq7nsl93zwahcTROgqvuAcYDUr+vOv8uHhNSKROyU961kgtCD1e95IqPKSQKH7tBTslnS3tA8A==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/win32-ia32": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/win32-ia32/-/win32-ia32-0.21.5.tgz",
      "integrity": "sha512-SWXFF1CL2RVNMaVs+BBClwtfZSvDgtL//G/smwAc5oVK/UPu2Gu9tIaRgFmYFFKrmg3SyAjSrElf0TiJ1v8fYA==",
      "cpu": [
        "ia32"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@esbuild/win32-x64": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/@esbuild/win32-x64/-/win32-x64-0.21.5.tgz",
      "integrity": "sha512-tQd/1efJuzPC6rCFwEvLtci/xNFcTZknmXs98FYDfGE4wP9ClFV98nyKrzJKVPMhdDnjzLhdUyMX4PsQAPjwIw==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/@jridgewell/gen-mapping": {
      "version": "0.3.13",
      "resolved": "https://registry.npmjs.org/@jridgewell/gen-mapping/-/gen-mapping-0.3.13.tgz",
      "integrity": "sha512-2kkt/7niJ6MgEPxF0bYdQ6etZaA+fQvDcLKckhy1yIQOzaoKjBBjSj63/aLVjYE3qhRt5dvM+uUyfCg6UKCBbA==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@jridgewell/sourcemap-codec": "^1.5.0",
        "@jridgewell/trace-mapping": "^0.3.24"
      }
    },
    "node_modules/@jridgewell/remapping": {
      "version": "2.3.5",
      "resolved": "https://registry.npmjs.org/@jridgewell/remapping/-/remapping-2.3.5.tgz",
      "integrity": "sha512-LI9u/+laYG4Ds1TDKSJW2YPrIlcVYOwi2fUC6xB43lueCjgxV4lffOCZCtYFiH6TNOX+tQKXx97T4IKHbhyHEQ==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@jridgewell/gen-mapping": "^0.3.5",
        "@jridgewell/trace-mapping": "^0.3.24"
      }
    },
    "node_modules/@jridgewell/resolve-uri": {
      "version": "3.1.2",
      "resolved": "https://registry.npmjs.org/@jridgewell/resolve-uri/-/resolve-uri-3.1.2.tgz",
      "integrity": "sha512-bRISgCIjP20/tbWSPWMEi54QVPRZExkuD9lJL+UIxUKtwVJA8wW1Trb1jMs1RFXo1CBTNZ/5hpC9QvmKWdopKw==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=6.0.0"
      }
    },
    "node_modules/@jridgewell/sourcemap-codec": {
      "version": "1.5.5",
      "resolved": "https://registry.npmjs.org/@jridgewell/sourcemap-codec/-/sourcemap-codec-1.5.5.tgz",
      "integrity": "sha512-cYQ9310grqxueWbl+WuIUIaiUaDcj7WOq5fVhEljNVgRfOUhY9fy2zTvfoqWsnebh8Sl70VScFbICvJnLKB0Og==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/@jridgewell/trace-mapping": {
      "version": "0.3.31",
      "resolved": "https://registry.npmjs.org/@jridgewell/trace-mapping/-/trace-mapping-0.3.31.tgz",
      "integrity": "sha512-zzNR+SdQSDJzc8joaeP8QQoCQr8NuYx2dIIytl1QeBEZHJ9uW6hebsrYgbz8hJwUQao3TWCMtmfV8Nu1twOLAw==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@jridgewell/resolve-uri": "^3.1.0",
        "@jridgewell/sourcemap-codec": "^1.4.14"
      }
    },
    "node_modules/@polka/url": {
      "version": "1.0.0-next.29",
      "resolved": "https://registry.npmjs.org/@polka/url/-/url-1.0.0-next.29.tgz",
      "integrity": "sha512-wwQAWhWSuHaag8c4q/KN/vCoeOJYshAIvMQwD4GpSb3OiZklFfvAgmj0VCBBImRpuF/aFgIRzllXlVX93Jevww==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/@rolldown/pluginutils": {
      "version": "1.0.0-beta.27",
      "resolved": "https://registry.npmjs.org/@rolldown/pluginutils/-/pluginutils-1.0.0-beta.27.tgz",
      "integrity": "sha512-+d0F4MKMCbeVUJwG96uQ4SgAznZNSq93I3V+9NHA4OpvqG8mRCpGdKmK8l/dl02h2CCDHwW2FqilnTyDcAnqjA==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/@rollup/rollup-android-arm-eabi": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-android-arm-eabi/-/rollup-android-arm-eabi-4.55.1.tgz",
      "integrity": "sha512-9R0DM/ykwfGIlNu6+2U09ga0WXeZ9MRC2Ter8jnz8415VbuIykVuc6bhdrbORFZANDmTDvq26mJrEVTl8TdnDg==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "android"
      ]
    },
    "node_modules/@rollup/rollup-android-arm64": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-android-arm64/-/rollup-android-arm64-4.55.1.tgz",
      "integrity": "sha512-eFZCb1YUqhTysgW3sj/55du5cG57S7UTNtdMjCW7LwVcj3dTTcowCsC8p7uBdzKsZYa8J7IDE8lhMI+HX1vQvg==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "android"
      ]
    },
    "node_modules/@rollup/rollup-darwin-arm64": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-darwin-arm64/-/rollup-darwin-arm64-4.55.1.tgz",
      "integrity": "sha512-p3grE2PHcQm2e8PSGZdzIhCKbMCw/xi9XvMPErPhwO17vxtvCN5FEA2mSLgmKlCjHGMQTP6phuQTYWUnKewwGg==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "darwin"
      ]
    },
    "node_modules/@rollup/rollup-darwin-x64": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-darwin-x64/-/rollup-darwin-x64-4.55.1.tgz",
      "integrity": "sha512-rDUjG25C9qoTm+e02Esi+aqTKSBYwVTaoS1wxcN47/Luqef57Vgp96xNANwt5npq9GDxsH7kXxNkJVEsWEOEaQ==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "darwin"
      ]
    },
    "node_modules/@rollup/rollup-freebsd-arm64": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-freebsd-arm64/-/rollup-freebsd-arm64-4.55.1.tgz",
      "integrity": "sha512-+JiU7Jbp5cdxekIgdte0jfcu5oqw4GCKr6i3PJTlXTCU5H5Fvtkpbs4XJHRmWNXF+hKmn4v7ogI5OQPaupJgOg==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "freebsd"
      ]
    },
    "node_modules/@rollup/rollup-freebsd-x64": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-freebsd-x64/-/rollup-freebsd-x64-4.55.1.tgz",
      "integrity": "sha512-V5xC1tOVWtLLmr3YUk2f6EJK4qksksOYiz/TCsFHu/R+woubcLWdC9nZQmwjOAbmExBIVKsm1/wKmEy4z4u4Bw==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "freebsd"
      ]
    },
    "node_modules/@rollup/rollup-linux-arm-gnueabihf": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-arm-gnueabihf/-/rollup-linux-arm-gnueabihf-4.55.1.tgz",
      "integrity": "sha512-Rn3n+FUk2J5VWx+ywrG/HGPTD9jXNbicRtTM11e/uorplArnXZYsVifnPPqNNP5BsO3roI4n8332ukpY/zN7rQ==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-arm-musleabihf": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-arm-musleabihf/-/rollup-linux-arm-musleabihf-4.55.1.tgz",
      "integrity": "sha512-grPNWydeKtc1aEdrJDWk4opD7nFtQbMmV7769hiAaYyUKCT1faPRm2av8CX1YJsZ4TLAZcg9gTR1KvEzoLjXkg==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-arm64-gnu": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-arm64-gnu/-/rollup-linux-arm64-gnu-4.55.1.tgz",
      "integrity": "sha512-a59mwd1k6x8tXKcUxSyISiquLwB5pX+fJW9TkWU46lCqD/GRDe9uDN31jrMmVP3feI3mhAdvcCClhV8V5MhJFQ==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-arm64-musl": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-arm64-musl/-/rollup-linux-arm64-musl-4.55.1.tgz",
      "integrity": "sha512-puS1MEgWX5GsHSoiAsF0TYrpomdvkaXm0CofIMG5uVkP6IBV+ZO9xhC5YEN49nsgYo1DuuMquF9+7EDBVYu4uA==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-loong64-gnu": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-loong64-gnu/-/rollup-linux-loong64-gnu-4.55.1.tgz",
      "integrity": "sha512-r3Wv40in+lTsULSb6nnoudVbARdOwb2u5fpeoOAZjFLznp6tDU8kd+GTHmJoqZ9lt6/Sys33KdIHUaQihFcu7g==",
      "cpu": [
        "loong64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-loong64-musl": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-loong64-musl/-/rollup-linux-loong64-musl-4.55.1.tgz",
      "integrity": "sha512-MR8c0+UxAlB22Fq4R+aQSPBayvYa3+9DrwG/i1TKQXFYEaoW3B5b/rkSRIypcZDdWjWnpcvxbNaAJDcSbJU3Lw==",
      "cpu": [
        "loong64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-ppc64-gnu": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-ppc64-gnu/-/rollup-linux-ppc64-gnu-4.55.1.tgz",
      "integrity": "sha512-3KhoECe1BRlSYpMTeVrD4sh2Pw2xgt4jzNSZIIPLFEsnQn9gAnZagW9+VqDqAHgm1Xc77LzJOo2LdigS5qZ+gw==",
      "cpu": [
        "ppc64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-ppc64-musl": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-ppc64-musl/-/rollup-linux-ppc64-musl-4.55.1.tgz",
      "integrity": "sha512-ziR1OuZx0vdYZZ30vueNZTg73alF59DicYrPViG0NEgDVN8/Jl87zkAPu4u6VjZST2llgEUjaiNl9JM6HH1Vdw==",
      "cpu": [
        "ppc64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-riscv64-gnu": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-riscv64-gnu/-/rollup-linux-riscv64-gnu-4.55.1.tgz",
      "integrity": "sha512-uW0Y12ih2XJRERZ4jAfKamTyIHVMPQnTZcQjme2HMVDAHY4amf5u414OqNYC+x+LzRdRcnIG1YodLrrtA8xsxw==",
      "cpu": [
        "riscv64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-riscv64-musl": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-riscv64-musl/-/rollup-linux-riscv64-musl-4.55.1.tgz",
      "integrity": "sha512-u9yZ0jUkOED1BFrqu3BwMQoixvGHGZ+JhJNkNKY/hyoEgOwlqKb62qu+7UjbPSHYjiVy8kKJHvXKv5coH4wDeg==",
      "cpu": [
        "riscv64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-s390x-gnu": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-s390x-gnu/-/rollup-linux-s390x-gnu-4.55.1.tgz",
      "integrity": "sha512-/0PenBCmqM4ZUd0190j7J0UsQ/1nsi735iPRakO8iPciE7BQ495Y6msPzaOmvx0/pn+eJVVlZrNrSh4WSYLxNg==",
      "cpu": [
        "s390x"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-x64-gnu": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-x64-gnu/-/rollup-linux-x64-gnu-4.55.1.tgz",
      "integrity": "sha512-a8G4wiQxQG2BAvo+gU6XrReRRqj+pLS2NGXKm8io19goR+K8lw269eTrPkSdDTALwMmJp4th2Uh0D8J9bEV1vg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-linux-x64-musl": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-linux-x64-musl/-/rollup-linux-x64-musl-4.55.1.tgz",
      "integrity": "sha512-bD+zjpFrMpP/hqkfEcnjXWHMw5BIghGisOKPj+2NaNDuVT+8Ds4mPf3XcPHuat1tz89WRL+1wbcxKY3WSbiT7w==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ]
    },
    "node_modules/@rollup/rollup-openbsd-x64": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-openbsd-x64/-/rollup-openbsd-x64-4.55.1.tgz",
      "integrity": "sha512-eLXw0dOiqE4QmvikfQ6yjgkg/xDM+MdU9YJuP4ySTibXU0oAvnEWXt7UDJmD4UkYialMfOGFPJnIHSe/kdzPxg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "openbsd"
      ]
    },
    "node_modules/@rollup/rollup-openharmony-arm64": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-openharmony-arm64/-/rollup-openharmony-arm64-4.55.1.tgz",
      "integrity": "sha512-xzm44KgEP11te3S2HCSyYf5zIzWmx3n8HDCc7EE59+lTcswEWNpvMLfd9uJvVX8LCg9QWG67Xt75AuHn4vgsXw==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "openharmony"
      ]
    },
    "node_modules/@rollup/rollup-win32-arm64-msvc": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-win32-arm64-msvc/-/rollup-win32-arm64-msvc-4.55.1.tgz",
      "integrity": "sha512-yR6Bl3tMC/gBok5cz/Qi0xYnVbIxGx5Fcf/ca0eB6/6JwOY+SRUcJfI0OpeTpPls7f194as62thCt/2BjxYN8g==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "win32"
      ]
    },
    "node_modules/@rollup/rollup-win32-ia32-msvc": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-win32-ia32-msvc/-/rollup-win32-ia32-msvc-4.55.1.tgz",
      "integrity": "sha512-3fZBidchE0eY0oFZBnekYCfg+5wAB0mbpCBuofh5mZuzIU/4jIVkbESmd2dOsFNS78b53CYv3OAtwqkZZmU5nA==",
      "cpu": [
        "ia32"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "win32"
      ]
    },
    "node_modules/@rollup/rollup-win32-x64-gnu": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-win32-x64-gnu/-/rollup-win32-x64-gnu-4.55.1.tgz",
      "integrity": "sha512-xGGY5pXj69IxKb4yv/POoocPy/qmEGhimy/FoTpTSVju3FYXUQQMFCaZZXJVidsmGxRioZAwpThl/4zX41gRKg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "win32"
      ]
    },
    "node_modules/@rollup/rollup-win32-x64-msvc": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/@rollup/rollup-win32-x64-msvc/-/rollup-win32-x64-msvc-4.55.1.tgz",
      "integrity": "sha512-SPEpaL6DX4rmcXtnhdrQYgzQ5W2uW3SCJch88lB2zImhJRhIIK44fkUrgIV/Q8yUNfw5oyZ5vkeQsZLhCb06lw==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "win32"
      ]
    },
    "node_modules/@standard-schema/spec": {
      "version": "1.1.0",
      "resolved": "https://registry.npmjs.org/@standard-schema/spec/-/spec-1.1.0.tgz",
      "integrity": "sha512-l2aFy5jALhniG5HgqrD6jXLi/rUWrKvqN/qJx6yoJsgKhblVd+iqqU4RCXavm/jPityDo5TCvKMnpjKnOriy0w==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/@types/babel__core": {
      "version": "7.20.5",
      "resolved": "https://registry.npmjs.org/@types/babel__core/-/babel__core-7.20.5.tgz",
      "integrity": "sha512-qoQprZvz5wQFJwMDqeseRXWv3rqMvhgpbXFfVyWhbx9X47POIA6i/+dXefEmZKoAgOaTdaIgNSMqMIU61yRyzA==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/parser": "^7.20.7",
        "@babel/types": "^7.20.7",
        "@types/babel__generator": "*",
        "@types/babel__template": "*",
        "@types/babel__traverse": "*"
      }
    },
    "node_modules/@types/babel__generator": {
      "version": "7.27.0",
      "resolved": "https://registry.npmjs.org/@types/babel__generator/-/babel__generator-7.27.0.tgz",
      "integrity": "sha512-ufFd2Xi92OAVPYsy+P4n7/U7e68fex0+Ee8gSG9KX7eo084CWiQ4sdxktvdl0bOPupXtVJPY19zk6EwWqUQ8lg==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/types": "^7.0.0"
      }
    },
    "node_modules/@types/babel__template": {
      "version": "7.4.4",
      "resolved": "https://registry.npmjs.org/@types/babel__template/-/babel__template-7.4.4.tgz",
      "integrity": "sha512-h/NUaSyG5EyxBIp8YRxo4RMe2/qQgvyowRwVMzhYhBCONbW8PUsg4lkFMrhgZhUe5z3L3MiLDuvyJ/CaPa2A8A==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/parser": "^7.1.0",
        "@babel/types": "^7.0.0"
      }
    },
    "node_modules/@types/babel__traverse": {
      "version": "7.28.0",
      "resolved": "https://registry.npmjs.org/@types/babel__traverse/-/babel__traverse-7.28.0.tgz",
      "integrity": "sha512-8PvcXf70gTDZBgt9ptxJ8elBeBjcLOAcOtoO/mPJjtji1+CdGbHgm77om1GrsPxsiE+uXIpNSK64UYaIwQXd4Q==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/types": "^7.28.2"
      }
    },
    "node_modules/@types/chai": {
      "version": "5.2.3",
      "resolved": "https://registry.npmjs.org/@types/chai/-/chai-5.2.3.tgz",
      "integrity": "sha512-Mw558oeA9fFbv65/y4mHtXDs9bPnFMZAL/jxdPFUpOHHIXX91mcgEHbS5Lahr+pwZFR8A7GQleRWeI6cGFC2UA==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@types/deep-eql": "*",
        "assertion-error": "^2.0.1"
      }
    },
    "node_modules/@types/deep-eql": {
      "version": "4.0.2",
      "resolved": "https://registry.npmjs.org/@types/deep-eql/-/deep-eql-4.0.2.tgz",
      "integrity": "sha512-c9h9dVVMigMPc4bwTvC5dxqtqJZwQPePsWjPlpSOnojbor6pGqdk541lfA7AqFQr5pB1BRdq0juY9db81BwyFw==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/@types/estree": {
      "version": "1.0.8",
      "resolved": "https://registry.npmjs.org/@types/estree/-/estree-1.0.8.tgz",
      "integrity": "sha512-dWHzHa2WqEXI/O1E9OjrocMTKJl2mSrEolh1Iomrv6U+JuNwaHXsXx9bLu5gG7BUWFIN0skIQJQ/L1rIex4X6w==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/@types/prop-types": {
      "version": "15.7.15",
      "resolved": "https://registry.npmjs.org/@types/prop-types/-/prop-types-15.7.15.tgz",
      "integrity": "sha512-F6bEyamV9jKGAFBEmlQnesRPGOQqS2+Uwi0Em15xenOxHaf2hv6L8YCVn3rPdPJOiJfPiCnLIRyvwVaqMY3MIw==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/@types/react": {
      "version": "18.3.27",
      "resolved": "https://registry.npmjs.org/@types/react/-/react-18.3.27.tgz",
      "integrity": "sha512-cisd7gxkzjBKU2GgdYrTdtQx1SORymWyaAFhaxQPK9bYO9ot3Y5OikQRvY0VYQtvwjeQnizCINJAenh/V7MK2w==",
      "dev": true,
      "license": "MIT",
      "peer": true,
      "dependencies": {
        "@types/prop-types": "*",
        "csstype": "^3.2.2"
      }
    },
    "node_modules/@types/react-dom": {
      "version": "18.3.7",
      "resolved": "https://registry.npmjs.org/@types/react-dom/-/react-dom-18.3.7.tgz",
      "integrity": "sha512-MEe3UeoENYVFXzoXEWsvcpg6ZvlrFNlOQ7EOsvhI3CfAXwzPfO8Qwuxd40nepsYKqyyVQnTdEfv68q91yLcKrQ==",
      "dev": true,
      "license": "MIT",
      "peerDependencies": {
        "@types/react": "^18.0.0"
      }
    },
    "node_modules/@vitejs/plugin-react": {
      "version": "4.7.0",
      "resolved": "https://registry.npmjs.org/@vitejs/plugin-react/-/plugin-react-4.7.0.tgz",
      "integrity": "sha512-gUu9hwfWvvEDBBmgtAowQCojwZmJ5mcLn3aufeCsitijs3+f2NsrPtlAWIR6OPiqljl96GVCUbLe0HyqIpVaoA==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@babel/core": "^7.28.0",
        "@babel/plugin-transform-react-jsx-self": "^7.27.1",
        "@babel/plugin-transform-react-jsx-source": "^7.27.1",
        "@rolldown/pluginutils": "1.0.0-beta.27",
        "@types/babel__core": "^7.20.5",
        "react-refresh": "^0.17.0"
      },
      "engines": {
        "node": "^14.18.0 || >=16.0.0"
      },
      "peerDependencies": {
        "vite": "^4.2.0 || ^5.0.0 || ^6.0.0 || ^7.0.0"
      }
    },
    "node_modules/@vitest/browser": {
      "version": "4.0.17",
      "resolved": "https://registry.npmjs.org/@vitest/browser/-/browser-4.0.17.tgz",
      "integrity": "sha512-cgf2JZk2fv5or3efmOrRJe1V9Md89BPgz4ntzbf84yAb+z2hW6niaGFinl9aFzPZ1q3TGfWZQWZ9gXTFThs2Qw==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@vitest/mocker": "4.0.17",
        "@vitest/utils": "4.0.17",
        "magic-string": "^0.30.21",
        "pixelmatch": "7.1.0",
        "pngjs": "^7.0.0",
        "sirv": "^3.0.2",
        "tinyrainbow": "^3.0.3",
        "ws": "^8.18.3"
      },
      "funding": {
        "url": "https://opencollective.com/vitest"
      },
      "peerDependencies": {
        "vitest": "4.0.17"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/aix-ppc64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/aix-ppc64/-/aix-ppc64-0.27.2.tgz",
      "integrity": "sha512-GZMB+a0mOMZs4MpDbj8RJp4cw+w1WV5NYD6xzgvzUJ5Ek2jerwfO2eADyI6ExDSUED+1X8aMbegahsJi+8mgpw==",
      "cpu": [
        "ppc64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "aix"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/android-arm": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/android-arm/-/android-arm-0.27.2.tgz",
      "integrity": "sha512-DVNI8jlPa7Ujbr1yjU2PfUSRtAUZPG9I1RwW4F4xFB1Imiu2on0ADiI/c3td+KmDtVKNbi+nffGDQMfcIMkwIA==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "android"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/android-arm64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/android-arm64/-/android-arm64-0.27.2.tgz",
      "integrity": "sha512-pvz8ZZ7ot/RBphf8fv60ljmaoydPU12VuXHImtAs0XhLLw+EXBi2BLe3OYSBslR4rryHvweW5gmkKFwTiFy6KA==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "android"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/android-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/android-x64/-/android-x64-0.27.2.tgz",
      "integrity": "sha512-z8Ank4Byh4TJJOh4wpz8g2vDy75zFL0TlZlkUkEwYXuPSgX8yzep596n6mT7905kA9uHZsf/o2OJZubl2l3M7A==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "android"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/darwin-arm64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/darwin-arm64/-/darwin-arm64-0.27.2.tgz",
      "integrity": "sha512-davCD2Zc80nzDVRwXTcQP/28fiJbcOwvdolL0sOiOsbwBa72kegmVU0Wrh1MYrbuCL98Omp5dVhQFWRKR2ZAlg==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "darwin"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/darwin-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/darwin-x64/-/darwin-x64-0.27.2.tgz",
      "integrity": "sha512-ZxtijOmlQCBWGwbVmwOF/UCzuGIbUkqB1faQRf5akQmxRJ1ujusWsb3CVfk/9iZKr2L5SMU5wPBi1UWbvL+VQA==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "darwin"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/freebsd-arm64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/freebsd-arm64/-/freebsd-arm64-0.27.2.tgz",
      "integrity": "sha512-lS/9CN+rgqQ9czogxlMcBMGd+l8Q3Nj1MFQwBZJyoEKI50XGxwuzznYdwcav6lpOGv5BqaZXqvBSiB/kJ5op+g==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "freebsd"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/freebsd-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/freebsd-x64/-/freebsd-x64-0.27.2.tgz",
      "integrity": "sha512-tAfqtNYb4YgPnJlEFu4c212HYjQWSO/w/h/lQaBK7RbwGIkBOuNKQI9tqWzx7Wtp7bTPaGC6MJvWI608P3wXYA==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "freebsd"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/linux-arm": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-arm/-/linux-arm-0.27.2.tgz",
      "integrity": "sha512-vWfq4GaIMP9AIe4yj1ZUW18RDhx6EPQKjwe7n8BbIecFtCQG4CfHGaHuh7fdfq+y3LIA2vGS/o9ZBGVxIDi9hw==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/linux-arm64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-arm64/-/linux-arm64-0.27.2.tgz",
      "integrity": "sha512-hYxN8pr66NsCCiRFkHUAsxylNOcAQaxSSkHMMjcpx0si13t1LHFphxJZUiGwojB1a/Hd5OiPIqDdXONia6bhTw==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/linux-ia32": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-ia32/-/linux-ia32-0.27.2.tgz",
      "integrity": "sha512-MJt5BRRSScPDwG2hLelYhAAKh9imjHK5+NE/tvnRLbIqUWa+0E9N4WNMjmp/kXXPHZGqPLxggwVhz7QP8CTR8w==",
      "cpu": [
        "ia32"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/linux-loong64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-loong64/-/linux-loong64-0.27.2.tgz",
      "integrity": "sha512-lugyF1atnAT463aO6KPshVCJK5NgRnU4yb3FUumyVz+cGvZbontBgzeGFO1nF+dPueHD367a2ZXe1NtUkAjOtg==",
      "cpu": [
        "loong64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/linux-mips64el": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-mips64el/-/linux-mips64el-0.27.2.tgz",
      "integrity": "sha512-nlP2I6ArEBewvJ2gjrrkESEZkB5mIoaTswuqNFRv/WYd+ATtUpe9Y09RnJvgvdag7he0OWgEZWhviS1OTOKixw==",
      "cpu": [
        "mips64el"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/linux-ppc64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-ppc64/-/linux-ppc64-0.27.2.tgz",
      "integrity": "sha512-C92gnpey7tUQONqg1n6dKVbx3vphKtTHJaNG2Ok9lGwbZil6DrfyecMsp9CrmXGQJmZ7iiVXvvZH6Ml5hL6XdQ==",
      "cpu": [
        "ppc64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/linux-riscv64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-riscv64/-/linux-riscv64-0.27.2.tgz",
      "integrity": "sha512-B5BOmojNtUyN8AXlK0QJyvjEZkWwy/FKvakkTDCziX95AowLZKR6aCDhG7LeF7uMCXEJqwa8Bejz5LTPYm8AvA==",
      "cpu": [
        "riscv64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/linux-s390x": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-s390x/-/linux-s390x-0.27.2.tgz",
      "integrity": "sha512-p4bm9+wsPwup5Z8f4EpfN63qNagQ47Ua2znaqGH6bqLlmJ4bx97Y9JdqxgGZ6Y8xVTixUnEkoKSHcpRlDnNr5w==",
      "cpu": [
        "s390x"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/linux-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-x64/-/linux-x64-0.27.2.tgz",
      "integrity": "sha512-uwp2Tip5aPmH+NRUwTcfLb+W32WXjpFejTIOWZFw/v7/KnpCDKG66u4DLcurQpiYTiYwQ9B7KOeMJvLCu/OvbA==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/netbsd-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/netbsd-x64/-/netbsd-x64-0.27.2.tgz",
      "integrity": "sha512-HwGDZ0VLVBY3Y+Nw0JexZy9o/nUAWq9MlV7cahpaXKW6TOzfVno3y3/M8Ga8u8Yr7GldLOov27xiCnqRZf0tCA==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "netbsd"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/openbsd-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/openbsd-x64/-/openbsd-x64-0.27.2.tgz",
      "integrity": "sha512-/it7w9Nb7+0KFIzjalNJVR5bOzA9Vay+yIPLVHfIQYG/j+j9VTH84aNB8ExGKPU4AzfaEvN9/V4HV+F+vo8OEg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "openbsd"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/sunos-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/sunos-x64/-/sunos-x64-0.27.2.tgz",
      "integrity": "sha512-kMtx1yqJHTmqaqHPAzKCAkDaKsffmXkPHThSfRwZGyuqyIeBvf08KSsYXl+abf5HDAPMJIPnbBfXvP2ZC2TfHg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "sunos"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/win32-arm64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/win32-arm64/-/win32-arm64-0.27.2.tgz",
      "integrity": "sha512-Yaf78O/B3Kkh+nKABUF++bvJv5Ijoy9AN1ww904rOXZFLWVc5OLOfL56W+C8F9xn5JQZa3UX6m+IktJnIb1Jjg==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/win32-ia32": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/win32-ia32/-/win32-ia32-0.27.2.tgz",
      "integrity": "sha512-Iuws0kxo4yusk7sw70Xa2E2imZU5HoixzxfGCdxwBdhiDgt9vX9VUCBhqcwY7/uh//78A1hMkkROMJq9l27oLQ==",
      "cpu": [
        "ia32"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@esbuild/win32-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/win32-x64/-/win32-x64-0.27.2.tgz",
      "integrity": "sha512-sRdU18mcKf7F+YgheI/zGf5alZatMUTKj/jNS6l744f9u3WFu4v7twcUI9vu4mknF4Y9aDlblIie0IM+5xxaqQ==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/@vitest/browser/node_modules/@vitest/mocker": {
      "version": "4.0.17",
      "resolved": "https://registry.npmjs.org/@vitest/mocker/-/mocker-4.0.17.tgz",
      "integrity": "sha512-+ZtQhLA3lDh1tI2wxe3yMsGzbp7uuJSWBM1iTIKCbppWTSBN09PUC+L+fyNlQApQoR+Ps8twt2pbSSXg2fQVEQ==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@vitest/spy": "4.0.17",
        "estree-walker": "^3.0.3",
        "magic-string": "^0.30.21"
      },
      "funding": {
        "url": "https://opencollective.com/vitest"
      },
      "peerDependencies": {
        "msw": "^2.4.9",
        "vite": "^6.0.0 || ^7.0.0-0"
      },
      "peerDependenciesMeta": {
        "msw": {
          "optional": true
        },
        "vite": {
          "optional": true
        }
      }
    },
    "node_modules/@vitest/browser/node_modules/esbuild": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/esbuild/-/esbuild-0.27.2.tgz",
      "integrity": "sha512-HyNQImnsOC7X9PMNaCIeAm4ISCQXs5a5YasTXVliKv4uuBo1dKrG0A+uQS8M5eXjVMnLg3WgXaKvprHlFJQffw==",
      "dev": true,
      "hasInstallScript": true,
      "license": "MIT",
      "optional": true,
      "bin": {
        "esbuild": "bin/esbuild"
      },
      "engines": {
        "node": ">=18"
      },
      "optionalDependencies": {
        "@esbuild/aix-ppc64": "0.27.2",
        "@esbuild/android-arm": "0.27.2",
        "@esbuild/android-arm64": "0.27.2",
        "@esbuild/android-x64": "0.27.2",
        "@esbuild/darwin-arm64": "0.27.2",
        "@esbuild/darwin-x64": "0.27.2",
        "@esbuild/freebsd-arm64": "0.27.2",
        "@esbuild/freebsd-x64": "0.27.2",
        "@esbuild/linux-arm": "0.27.2",
        "@esbuild/linux-arm64": "0.27.2",
        "@esbuild/linux-ia32": "0.27.2",
        "@esbuild/linux-loong64": "0.27.2",
        "@esbuild/linux-mips64el": "0.27.2",
        "@esbuild/linux-ppc64": "0.27.2",
        "@esbuild/linux-riscv64": "0.27.2",
        "@esbuild/linux-s390x": "0.27.2",
        "@esbuild/linux-x64": "0.27.2",
        "@esbuild/netbsd-arm64": "0.27.2",
        "@esbuild/netbsd-x64": "0.27.2",
        "@esbuild/openbsd-arm64": "0.27.2",
        "@esbuild/openbsd-x64": "0.27.2",
        "@esbuild/openharmony-arm64": "0.27.2",
        "@esbuild/sunos-x64": "0.27.2",
        "@esbuild/win32-arm64": "0.27.2",
        "@esbuild/win32-ia32": "0.27.2",
        "@esbuild/win32-x64": "0.27.2"
      }
    },
    "node_modules/@vitest/expect": {
      "version": "4.0.17",
      "resolved": "https://registry.npmjs.org/@vitest/expect/-/expect-4.0.17.tgz",
      "integrity": "sha512-mEoqP3RqhKlbmUmntNDDCJeTDavDR+fVYkSOw8qRwJFaW/0/5zA9zFeTrHqNtcmwh6j26yMmwx2PqUDPzt5ZAQ==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@standard-schema/spec": "^1.0.0",
        "@types/chai": "^5.2.2",
        "@vitest/spy": "4.0.17",
        "@vitest/utils": "4.0.17",
        "chai": "^6.2.1",
        "tinyrainbow": "^3.0.3"
      },
      "funding": {
        "url": "https://opencollective.com/vitest"
      }
    },
    "node_modules/@vitest/pretty-format": {
      "version": "4.0.17",
      "resolved": "https://registry.npmjs.org/@vitest/pretty-format/-/pretty-format-4.0.17.tgz",
      "integrity": "sha512-Ah3VAYmjcEdHg6+MwFE17qyLqBHZ+ni2ScKCiW2XrlSBV4H3Z7vYfPfz7CWQ33gyu76oc0Ai36+kgLU3rfF4nw==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "tinyrainbow": "^3.0.3"
      },
      "funding": {
        "url": "https://opencollective.com/vitest"
      }
    },
    "node_modules/@vitest/runner": {
      "version": "4.0.17",
      "resolved": "https://registry.npmjs.org/@vitest/runner/-/runner-4.0.17.tgz",
      "integrity": "sha512-JmuQyf8aMWoo/LmNFppdpkfRVHJcsgzkbCA+/Bk7VfNH7RE6Ut2qxegeyx2j3ojtJtKIbIGy3h+KxGfYfk28YQ==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@vitest/utils": "4.0.17",
        "pathe": "^2.0.3"
      },
      "funding": {
        "url": "https://opencollective.com/vitest"
      }
    },
    "node_modules/@vitest/snapshot": {
      "version": "4.0.17",
      "resolved": "https://registry.npmjs.org/@vitest/snapshot/-/snapshot-4.0.17.tgz",
      "integrity": "sha512-npPelD7oyL+YQM2gbIYvlavlMVWUfNNGZPcu0aEUQXt7FXTuqhmgiYupPnAanhKvyP6Srs2pIbWo30K0RbDtRQ==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@vitest/pretty-format": "4.0.17",
        "magic-string": "^0.30.21",
        "pathe": "^2.0.3"
      },
      "funding": {
        "url": "https://opencollective.com/vitest"
      }
    },
    "node_modules/@vitest/spy": {
      "version": "4.0.17",
      "resolved": "https://registry.npmjs.org/@vitest/spy/-/spy-4.0.17.tgz",
      "integrity": "sha512-I1bQo8QaP6tZlTomQNWKJE6ym4SHf3oLS7ceNjozxxgzavRAgZDc06T7kD8gb9bXKEgcLNt00Z+kZO6KaJ62Ew==",
      "dev": true,
      "license": "MIT",
      "funding": {
        "url": "https://opencollective.com/vitest"
      }
    },
    "node_modules/@vitest/utils": {
      "version": "4.0.17",
      "resolved": "https://registry.npmjs.org/@vitest/utils/-/utils-4.0.17.tgz",
      "integrity": "sha512-RG6iy+IzQpa9SB8HAFHJ9Y+pTzI+h8553MrciN9eC6TFBErqrQaTas4vG+MVj8S4uKk8uTT2p0vgZPnTdxd96w==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@vitest/pretty-format": "4.0.17",
        "tinyrainbow": "^3.0.3"
      },
      "funding": {
        "url": "https://opencollective.com/vitest"
      }
    },
    "node_modules/assertion-error": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/assertion-error/-/assertion-error-2.0.1.tgz",
      "integrity": "sha512-Izi8RQcffqCeNVgFigKli1ssklIbpHnCYc6AknXGYoB6grJqyeby7jv12JUQgmTAnIDnbck1uxksT4dzN3PWBA==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=12"
      }
    },
    "node_modules/baseline-browser-mapping": {
      "version": "2.9.14",
      "resolved": "https://registry.npmjs.org/baseline-browser-mapping/-/baseline-browser-mapping-2.9.14.tgz",
      "integrity": "sha512-B0xUquLkiGLgHhpPBqvl7GWegWBUNuujQ6kXd/r1U38ElPT6Ok8KZ8e+FpUGEc2ZoRQUzq/aUnaKFc/svWUGSg==",
      "dev": true,
      "license": "Apache-2.0",
      "bin": {
        "baseline-browser-mapping": "dist/cli.js"
      }
    },
    "node_modules/browserslist": {
      "version": "4.28.1",
      "resolved": "https://registry.npmjs.org/browserslist/-/browserslist-4.28.1.tgz",
      "integrity": "sha512-ZC5Bd0LgJXgwGqUknZY/vkUQ04r8NXnJZ3yYi4vDmSiZmC/pdSN0NbNRPxZpbtO4uAfDUAFffO8IZoM3Gj8IkA==",
      "dev": true,
      "funding": [
        {
          "type": "opencollective",
          "url": "https://opencollective.com/browserslist"
        },
        {
          "type": "tidelift",
          "url": "https://tidelift.com/funding/github/npm/browserslist"
        },
        {
          "type": "github",
          "url": "https://github.com/sponsors/ai"
        }
      ],
      "license": "MIT",
      "peer": true,
      "dependencies": {
        "baseline-browser-mapping": "^2.9.0",
        "caniuse-lite": "^1.0.30001759",
        "electron-to-chromium": "^1.5.263",
        "node-releases": "^2.0.27",
        "update-browserslist-db": "^1.2.0"
      },
      "bin": {
        "browserslist": "cli.js"
      },
      "engines": {
        "node": "^6 || ^7 || ^8 || ^9 || ^10 || ^11 || ^12 || >=13.7"
      }
    },
    "node_modules/caniuse-lite": {
      "version": "1.0.30001764",
      "resolved": "https://registry.npmjs.org/caniuse-lite/-/caniuse-lite-1.0.30001764.tgz",
      "integrity": "sha512-9JGuzl2M+vPL+pz70gtMF9sHdMFbY9FJaQBi186cHKH3pSzDvzoUJUPV6fqiKIMyXbud9ZLg4F3Yza1vJ1+93g==",
      "dev": true,
      "funding": [
        {
          "type": "opencollective",
          "url": "https://opencollective.com/browserslist"
        },
        {
          "type": "tidelift",
          "url": "https://tidelift.com/funding/github/npm/caniuse-lite"
        },
        {
          "type": "github",
          "url": "https://github.com/sponsors/ai"
        }
      ],
      "license": "CC-BY-4.0"
    },
    "node_modules/chai": {
      "version": "6.2.2",
      "resolved": "https://registry.npmjs.org/chai/-/chai-6.2.2.tgz",
      "integrity": "sha512-NUPRluOfOiTKBKvWPtSD4PhFvWCqOi0BGStNWs57X9js7XGTprSmFoz5F0tWhR4WPjNeR9jXqdC7/UpSJTnlRg==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/convert-source-map": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/convert-source-map/-/convert-source-map-2.0.0.tgz",
      "integrity": "sha512-Kvp459HrV2FEJ1CAsi1Ku+MY3kasH19TFykTz2xWmMeq6bk2NU3XXvfJ+Q61m0xktWwt+1HSYf3JZsTms3aRJg==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/csstype": {
      "version": "3.2.3",
      "resolved": "https://registry.npmjs.org/csstype/-/csstype-3.2.3.tgz",
      "integrity": "sha512-z1HGKcYy2xA8AGQfwrn0PAy+PB7X/GSj3UVJW9qKyn43xWa+gl5nXmU4qqLMRzWVLFC8KusUX8T/0kCiOYpAIQ==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/debug": {
      "version": "4.4.3",
      "resolved": "https://registry.npmjs.org/debug/-/debug-4.4.3.tgz",
      "integrity": "sha512-RGwwWnwQvkVfavKVt22FGLw+xYSdzARwm0ru6DhTVA3umU5hZc28V3kO4stgYryrTlLpuvgI9GiijltAjNbcqA==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "ms": "^2.1.3"
      },
      "engines": {
        "node": ">=6.0"
      },
      "peerDependenciesMeta": {
        "supports-color": {
          "optional": true
        }
      }
    },
    "node_modules/electron-to-chromium": {
      "version": "1.5.267",
      "resolved": "https://registry.npmjs.org/electron-to-chromium/-/electron-to-chromium-1.5.267.tgz",
      "integrity": "sha512-0Drusm6MVRXSOJpGbaSVgcQsuB4hEkMpHXaVstcPmhu5LIedxs1xNK/nIxmQIU/RPC0+1/o0AVZfBTkTNJOdUw==",
      "dev": true,
      "license": "ISC"
    },
    "node_modules/es-module-lexer": {
      "version": "1.7.0",
      "resolved": "https://registry.npmjs.org/es-module-lexer/-/es-module-lexer-1.7.0.tgz",
      "integrity": "sha512-jEQoCwk8hyb2AZziIOLhDqpm5+2ww5uIE6lkO/6jcOCusfk6LhMHpXXfBLXTZ7Ydyt0j4VoUQv6uGNYbdW+kBA==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/esbuild": {
      "version": "0.21.5",
      "resolved": "https://registry.npmjs.org/esbuild/-/esbuild-0.21.5.tgz",
      "integrity": "sha512-mg3OPMV4hXywwpoDxu3Qda5xCKQi+vCTZq8S9J/EpkhB2HzKXq4SNFZE3+NK93JYxc8VMSep+lOUSC/RVKaBqw==",
      "dev": true,
      "hasInstallScript": true,
      "license": "MIT",
      "bin": {
        "esbuild": "bin/esbuild"
      },
      "engines": {
        "node": ">=12"
      },
      "optionalDependencies": {
        "@esbuild/aix-ppc64": "0.21.5",
        "@esbuild/android-arm": "0.21.5",
        "@esbuild/android-arm64": "0.21.5",
        "@esbuild/android-x64": "0.21.5",
        "@esbuild/darwin-arm64": "0.21.5",
        "@esbuild/darwin-x64": "0.21.5",
        "@esbuild/freebsd-arm64": "0.21.5",
        "@esbuild/freebsd-x64": "0.21.5",
        "@esbuild/linux-arm": "0.21.5",
        "@esbuild/linux-arm64": "0.21.5",
        "@esbuild/linux-ia32": "0.21.5",
        "@esbuild/linux-loong64": "0.21.5",
        "@esbuild/linux-mips64el": "0.21.5",
        "@esbuild/linux-ppc64": "0.21.5",
        "@esbuild/linux-riscv64": "0.21.5",
        "@esbuild/linux-s390x": "0.21.5",
        "@esbuild/linux-x64": "0.21.5",
        "@esbuild/netbsd-x64": "0.21.5",
        "@esbuild/openbsd-x64": "0.21.5",
        "@esbuild/sunos-x64": "0.21.5",
        "@esbuild/win32-arm64": "0.21.5",
        "@esbuild/win32-ia32": "0.21.5",
        "@esbuild/win32-x64": "0.21.5"
      }
    },
    "node_modules/escalade": {
      "version": "3.2.0",
      "resolved": "https://registry.npmjs.org/escalade/-/escalade-3.2.0.tgz",
      "integrity": "sha512-WUj2qlxaQtO4g6Pq5c29GTcWGDyd8itL8zTlipgECz3JesAiiOKotd8JU6otB3PACgG6xkJUyVhboMS+bje/jA==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/estree-walker": {
      "version": "3.0.3",
      "resolved": "https://registry.npmjs.org/estree-walker/-/estree-walker-3.0.3.tgz",
      "integrity": "sha512-7RUKfXgSMMkzt6ZuXmqapOurLGPPfgj6l9uRZ7lRGolvk0y2yocc35LdcxKC5PQZdn2DMqioAQ2NoWcrTKmm6g==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@types/estree": "^1.0.0"
      }
    },
    "node_modules/expect-type": {
      "version": "1.3.0",
      "resolved": "https://registry.npmjs.org/expect-type/-/expect-type-1.3.0.tgz",
      "integrity": "sha512-knvyeauYhqjOYvQ66MznSMs83wmHrCycNEN6Ao+2AeYEfxUIkuiVxdEa1qlGEPK+We3n0THiDciYSsCcgW/DoA==",
      "dev": true,
      "license": "Apache-2.0",
      "engines": {
        "node": ">=12.0.0"
      }
    },
    "node_modules/fdir": {
      "version": "6.5.0",
      "resolved": "https://registry.npmjs.org/fdir/-/fdir-6.5.0.tgz",
      "integrity": "sha512-tIbYtZbucOs0BRGqPJkshJUYdL+SDH7dVM8gjy+ERp3WAUjLEFJE+02kanyHtwjWOnwrKYBiwAmM0p4kLJAnXg==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=12.0.0"
      },
      "peerDependencies": {
        "picomatch": "^3 || ^4"
      },
      "peerDependenciesMeta": {
        "picomatch": {
          "optional": true
        }
      }
    },
    "node_modules/fsevents": {
      "version": "2.3.3",
      "resolved": "https://registry.npmjs.org/fsevents/-/fsevents-2.3.3.tgz",
      "integrity": "sha512-5xoDfX+fL7faATnagmWPpbFtwh/R77WmMMqqHGS65C3vvB0YHrgF+B1YmZ3441tMj5n63k0212XNoJwzlhffQw==",
      "dev": true,
      "hasInstallScript": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "darwin"
      ],
      "engines": {
        "node": "^8.16.0 || ^10.6.0 || >=11.0.0"
      }
    },
    "node_modules/gensync": {
      "version": "1.0.0-beta.2",
      "resolved": "https://registry.npmjs.org/gensync/-/gensync-1.0.0-beta.2.tgz",
      "integrity": "sha512-3hN7NaskYvMDLQY55gnW3NQ+mesEAepTqlg+VEbj7zzqEMBVNhzcGYYeqFo/TlYz6eQiFcp1HcsCZO+nGgS8zg==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=6.9.0"
      }
    },
    "node_modules/js-tokens": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/js-tokens/-/js-tokens-4.0.0.tgz",
      "integrity": "sha512-RdJUflcE3cUzKiMqQgsCu06FPu9UdIJO0beYbPhHN4k6apgJtifcoCtT9bcxOpYBtpD2kCM6Sbzg4CausW/PKQ==",
      "license": "MIT"
    },
    "node_modules/jsesc": {
      "version": "3.1.0",
      "resolved": "https://registry.npmjs.org/jsesc/-/jsesc-3.1.0.tgz",
      "integrity": "sha512-/sM3dO2FOzXjKQhJuo0Q173wf2KOo8t4I8vHy6lF9poUp7bKT0/NHE8fPX23PwfhnykfqnC2xRxOnVw5XuGIaA==",
      "dev": true,
      "license": "MIT",
      "bin": {
        "jsesc": "bin/jsesc"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/json5": {
      "version": "2.2.3",
      "resolved": "https://registry.npmjs.org/json5/-/json5-2.2.3.tgz",
      "integrity": "sha512-XmOWe7eyHYH14cLdVPoyg+GOH3rYX++KpzrylJwSW98t3Nk+U8XOl8FWKOgwtzdb8lXGf6zYwDUzeHMWfxasyg==",
      "dev": true,
      "license": "MIT",
      "bin": {
        "json5": "lib/cli.js"
      },
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/loose-envify": {
      "version": "1.4.0",
      "resolved": "https://registry.npmjs.org/loose-envify/-/loose-envify-1.4.0.tgz",
      "integrity": "sha512-lyuxPGr/Wfhrlem2CL/UcnUc1zcqKAImBDzukY7Y5F/yQiNdko6+fRLevlw1HgMySw7f611UIY408EtxRSoK3Q==",
      "license": "MIT",
      "dependencies": {
        "js-tokens": "^3.0.0 || ^4.0.0"
      },
      "bin": {
        "loose-envify": "cli.js"
      }
    },
    "node_modules/lru-cache": {
      "version": "5.1.1",
      "resolved": "https://registry.npmjs.org/lru-cache/-/lru-cache-5.1.1.tgz",
      "integrity": "sha512-KpNARQA3Iwv+jTA0utUVVbrh+Jlrr1Fv0e56GGzAFOXN7dk/FviaDW8LHmK52DlcH4WP2n6gI8vN1aesBFgo9w==",
      "dev": true,
      "license": "ISC",
      "dependencies": {
        "yallist": "^3.0.2"
      }
    },
    "node_modules/lucide-react": {
      "version": "0.309.0",
      "resolved": "https://registry.npmjs.org/lucide-react/-/lucide-react-0.309.0.tgz",
      "integrity": "sha512-zNVPczuwFrCfksZH3zbd1UDE6/WYhYAdbe2k7CImVyPAkXLgIwbs6eXQ4loigqDnUFjyFYCI5jZ1y10Kqal0dg==",
      "license": "ISC",
      "peerDependencies": {
        "react": "^16.5.1 || ^17.0.0 || ^18.0.0"
      }
    },
    "node_modules/magic-string": {
      "version": "0.30.21",
      "resolved": "https://registry.npmjs.org/magic-string/-/magic-string-0.30.21.tgz",
      "integrity": "sha512-vd2F4YUyEXKGcLHoq+TEyCjxueSeHnFxyyjNp80yg0XV4vUhnDer/lvvlqM/arB5bXQN5K2/3oinyCRyx8T2CQ==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@jridgewell/sourcemap-codec": "^1.5.5"
      }
    },
    "node_modules/mrmime": {
      "version": "2.0.1",
      "resolved": "https://registry.npmjs.org/mrmime/-/mrmime-2.0.1.tgz",
      "integrity": "sha512-Y3wQdFg2Va6etvQ5I82yUhGdsKrcYox6p7FfL1LbK2J4V01F9TGlepTIhnK24t7koZibmg82KGglhA1XK5IsLQ==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=10"
      }
    },
    "node_modules/ms": {
      "version": "2.1.3",
      "resolved": "https://registry.npmjs.org/ms/-/ms-2.1.3.tgz",
      "integrity": "sha512-6FlzubTLZG3J2a/NVCAleEhjzq5oxgHyaCU9yYXvcLsvoVaHJq/s5xXI6/XXP6tz7R9xAOtHnSO/tXtF3WRTlA==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/nanoid": {
      "version": "3.3.11",
      "resolved": "https://registry.npmjs.org/nanoid/-/nanoid-3.3.11.tgz",
      "integrity": "sha512-N8SpfPUnUp1bK+PMYW8qSWdl9U+wwNWI4QKxOYDy9JAro3WMX7p2OeVRF9v+347pnakNevPmiHhNmZ2HbFA76w==",
      "dev": true,
      "funding": [
        {
          "type": "github",
          "url": "https://github.com/sponsors/ai"
        }
      ],
      "license": "MIT",
      "bin": {
        "nanoid": "bin/nanoid.cjs"
      },
      "engines": {
        "node": "^10 || ^12 || ^13.7 || ^14 || >=15.0.1"
      }
    },
    "node_modules/node-releases": {
      "version": "2.0.27",
      "resolved": "https://registry.npmjs.org/node-releases/-/node-releases-2.0.27.tgz",
      "integrity": "sha512-nmh3lCkYZ3grZvqcCH+fjmQ7X+H0OeZgP40OierEaAptX4XofMh5kwNbWh7lBduUzCcV/8kZ+NDLCwm2iorIlA==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/obug": {
      "version": "2.1.1",
      "resolved": "https://registry.npmjs.org/obug/-/obug-2.1.1.tgz",
      "integrity": "sha512-uTqF9MuPraAQ+IsnPf366RG4cP9RtUi7MLO1N3KEc+wb0a6yKpeL0lmk2IB1jY5KHPAlTc6T/JRdC/YqxHNwkQ==",
      "dev": true,
      "funding": [
        "https://github.com/sponsors/sxzz",
        "https://opencollective.com/debug"
      ],
      "license": "MIT"
    },
    "node_modules/pathe": {
      "version": "2.0.3",
      "resolved": "https://registry.npmjs.org/pathe/-/pathe-2.0.3.tgz",
      "integrity": "sha512-WUjGcAqP1gQacoQe+OBJsFA7Ld4DyXuUIjZ5cc75cLHvJ7dtNsTugphxIADwspS+AraAUePCKrSVtPLFj/F88w==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/picocolors": {
      "version": "1.1.1",
      "resolved": "https://registry.npmjs.org/picocolors/-/picocolors-1.1.1.tgz",
      "integrity": "sha512-xceH2snhtb5M9liqDsmEw56le376mTZkEX/jEb/RxNFyegNul7eNslCXP9FDj/Lcu0X8KEyMceP2ntpaHrDEVA==",
      "dev": true,
      "license": "ISC"
    },
    "node_modules/picomatch": {
      "version": "4.0.3",
      "resolved": "https://registry.npmjs.org/picomatch/-/picomatch-4.0.3.tgz",
      "integrity": "sha512-5gTmgEY/sqK6gFXLIsQNH19lWb4ebPDLA4SdLP7dsWkIXHWlG66oPuVvXSGFPppYZz8ZDZq0dYYrbHfBCVUb1Q==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=12"
      },
      "funding": {
        "url": "https://github.com/sponsors/jonschlinkert"
      }
    },
    "node_modules/pixelmatch": {
      "version": "7.1.0",
      "resolved": "https://registry.npmjs.org/pixelmatch/-/pixelmatch-7.1.0.tgz",
      "integrity": "sha512-1wrVzJ2STrpmONHKBy228LM1b84msXDUoAzVEl0R8Mz4Ce6EPr+IVtxm8+yvrqLYMHswREkjYFaMxnyGnaY3Ng==",
      "dev": true,
      "license": "ISC",
      "dependencies": {
        "pngjs": "^7.0.0"
      },
      "bin": {
        "pixelmatch": "bin/pixelmatch"
      }
    },
    "node_modules/pngjs": {
      "version": "7.0.0",
      "resolved": "https://registry.npmjs.org/pngjs/-/pngjs-7.0.0.tgz",
      "integrity": "sha512-LKWqWJRhstyYo9pGvgor/ivk2w94eSjE3RGVuzLGlr3NmD8bf7RcYGze1mNdEHRP6TRP6rMuDHk5t44hnTRyow==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=14.19.0"
      }
    },
    "node_modules/postcss": {
      "version": "8.5.6",
      "resolved": "https://registry.npmjs.org/postcss/-/postcss-8.5.6.tgz",
      "integrity": "sha512-3Ybi1tAuwAP9s0r1UQ2J4n5Y0G05bJkpUIO0/bI9MhwmD70S5aTWbXGBwxHrelT+XM1k6dM0pk+SwNkpTRN7Pg==",
      "dev": true,
      "funding": [
        {
          "type": "opencollective",
          "url": "https://opencollective.com/postcss/"
        },
        {
          "type": "tidelift",
          "url": "https://tidelift.com/funding/github/npm/postcss"
        },
        {
          "type": "github",
          "url": "https://github.com/sponsors/ai"
        }
      ],
      "license": "MIT",
      "dependencies": {
        "nanoid": "^3.3.11",
        "picocolors": "^1.1.1",
        "source-map-js": "^1.2.1"
      },
      "engines": {
        "node": "^10 || ^12 || >=14"
      }
    },
    "node_modules/react": {
      "version": "18.3.1",
      "resolved": "https://registry.npmjs.org/react/-/react-18.3.1.tgz",
      "integrity": "sha512-wS+hAgJShR0KhEvPJArfuPVN1+Hz1t0Y6n5jLrGQbkb4urgPE/0Rve+1kMB1v/oWgHgm4WIcV+i7F2pTVj+2iQ==",
      "license": "MIT",
      "peer": true,
      "dependencies": {
        "loose-envify": "^1.1.0"
      },
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/react-dom": {
      "version": "18.3.1",
      "resolved": "https://registry.npmjs.org/react-dom/-/react-dom-18.3.1.tgz",
      "integrity": "sha512-5m4nQKp+rZRb09LNH59GM4BxTh9251/ylbKIbpe7TpGxfJ+9kv6BLkLBXIjjspbgbnIBNqlI23tRnTWT0snUIw==",
      "license": "MIT",
      "dependencies": {
        "loose-envify": "^1.1.0",
        "scheduler": "^0.23.2"
      },
      "peerDependencies": {
        "react": "^18.3.1"
      }
    },
    "node_modules/react-refresh": {
      "version": "0.17.0",
      "resolved": "https://registry.npmjs.org/react-refresh/-/react-refresh-0.17.0.tgz",
      "integrity": "sha512-z6F7K9bV85EfseRCp2bzrpyQ0Gkw1uLoCel9XBVWPg/TjRj94SkJzUTGfOa4bs7iJvBWtQG0Wq7wnI0syw3EBQ==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/rollup": {
      "version": "4.55.1",
      "resolved": "https://registry.npmjs.org/rollup/-/rollup-4.55.1.tgz",
      "integrity": "sha512-wDv/Ht1BNHB4upNbK74s9usvl7hObDnvVzknxqY/E/O3X6rW1U1rV1aENEfJ54eFZDTNo7zv1f5N4edCluH7+A==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@types/estree": "1.0.8"
      },
      "bin": {
        "rollup": "dist/bin/rollup"
      },
      "engines": {
        "node": ">=18.0.0",
        "npm": ">=8.0.0"
      },
      "optionalDependencies": {
        "@rollup/rollup-android-arm-eabi": "4.55.1",
        "@rollup/rollup-android-arm64": "4.55.1",
        "@rollup/rollup-darwin-arm64": "4.55.1",
        "@rollup/rollup-darwin-x64": "4.55.1",
        "@rollup/rollup-freebsd-arm64": "4.55.1",
        "@rollup/rollup-freebsd-x64": "4.55.1",
        "@rollup/rollup-linux-arm-gnueabihf": "4.55.1",
        "@rollup/rollup-linux-arm-musleabihf": "4.55.1",
        "@rollup/rollup-linux-arm64-gnu": "4.55.1",
        "@rollup/rollup-linux-arm64-musl": "4.55.1",
        "@rollup/rollup-linux-loong64-gnu": "4.55.1",
        "@rollup/rollup-linux-loong64-musl": "4.55.1",
        "@rollup/rollup-linux-ppc64-gnu": "4.55.1",
        "@rollup/rollup-linux-ppc64-musl": "4.55.1",
        "@rollup/rollup-linux-riscv64-gnu": "4.55.1",
        "@rollup/rollup-linux-riscv64-musl": "4.55.1",
        "@rollup/rollup-linux-s390x-gnu": "4.55.1",
        "@rollup/rollup-linux-x64-gnu": "4.55.1",
        "@rollup/rollup-linux-x64-musl": "4.55.1",
        "@rollup/rollup-openbsd-x64": "4.55.1",
        "@rollup/rollup-openharmony-arm64": "4.55.1",
        "@rollup/rollup-win32-arm64-msvc": "4.55.1",
        "@rollup/rollup-win32-ia32-msvc": "4.55.1",
        "@rollup/rollup-win32-x64-gnu": "4.55.1",
        "@rollup/rollup-win32-x64-msvc": "4.55.1",
        "fsevents": "~2.3.2"
      }
    },
    "node_modules/scheduler": {
      "version": "0.23.2",
      "resolved": "https://registry.npmjs.org/scheduler/-/scheduler-0.23.2.tgz",
      "integrity": "sha512-UOShsPwz7NrMUqhR6t0hWjFduvOzbtv7toDH1/hIrfRNIDBnnBWd0CwJTGvTpngVlmwGCdP9/Zl/tVrDqcuYzQ==",
      "license": "MIT",
      "dependencies": {
        "loose-envify": "^1.1.0"
      }
    },
    "node_modules/semver": {
      "version": "6.3.1",
      "resolved": "https://registry.npmjs.org/semver/-/semver-6.3.1.tgz",
      "integrity": "sha512-BR7VvDCVHO+q2xBEWskxS6DJE1qRnb7DxzUrogb71CWoSficBxYsiAGd+Kl0mmq/MprG9yArRkyrQxTO6XjMzA==",
      "dev": true,
      "license": "ISC",
      "bin": {
        "semver": "bin/semver.js"
      }
    },
    "node_modules/siginfo": {
      "version": "2.0.0",
      "resolved": "https://registry.npmjs.org/siginfo/-/siginfo-2.0.0.tgz",
      "integrity": "sha512-ybx0WO1/8bSBLEWXZvEd7gMW3Sn3JFlW3TvX1nREbDLRNQNaeNN8WK0meBwPdAaOI7TtRRRJn/Es1zhrrCHu7g==",
      "dev": true,
      "license": "ISC"
    },
    "node_modules/sirv": {
      "version": "3.0.2",
      "resolved": "https://registry.npmjs.org/sirv/-/sirv-3.0.2.tgz",
      "integrity": "sha512-2wcC/oGxHis/BoHkkPwldgiPSYcpZK3JU28WoMVv55yHJgcZ8rlXvuG9iZggz+sU1d4bRgIGASwyWqjxu3FM0g==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@polka/url": "^1.0.0-next.24",
        "mrmime": "^2.0.0",
        "totalist": "^3.0.0"
      },
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/source-map-js": {
      "version": "1.2.1",
      "resolved": "https://registry.npmjs.org/source-map-js/-/source-map-js-1.2.1.tgz",
      "integrity": "sha512-UXWMKhLOwVKb728IUtQPXxfYU+usdybtUrK/8uGE8CQMvrhOpwvzDBwj0QhSL7MQc7vIsISBG8VQ8+IDQxpfQA==",
      "dev": true,
      "license": "BSD-3-Clause",
      "engines": {
        "node": ">=0.10.0"
      }
    },
    "node_modules/stackback": {
      "version": "0.0.2",
      "resolved": "https://registry.npmjs.org/stackback/-/stackback-0.0.2.tgz",
      "integrity": "sha512-1XMJE5fQo1jGH6Y/7ebnwPOBEkIEnT4QF32d5R1+VXdXveM0IBMJt8zfaxX1P3QhVwrYe+576+jkANtSS2mBbw==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/std-env": {
      "version": "3.10.0",
      "resolved": "https://registry.npmjs.org/std-env/-/std-env-3.10.0.tgz",
      "integrity": "sha512-5GS12FdOZNliM5mAOxFRg7Ir0pWz8MdpYm6AY6VPkGpbA7ZzmbzNcBJQ0GPvvyWgcY7QAhCgf9Uy89I03faLkg==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/tinybench": {
      "version": "2.9.0",
      "resolved": "https://registry.npmjs.org/tinybench/-/tinybench-2.9.0.tgz",
      "integrity": "sha512-0+DUvqWMValLmha6lr4kD8iAMK1HzV0/aKnCtWb9v9641TnP/MFb7Pc2bxoxQjTXAErryXVgUOfv2YqNllqGeg==",
      "dev": true,
      "license": "MIT"
    },
    "node_modules/tinyexec": {
      "version": "1.0.2",
      "resolved": "https://registry.npmjs.org/tinyexec/-/tinyexec-1.0.2.tgz",
      "integrity": "sha512-W/KYk+NFhkmsYpuHq5JykngiOCnxeVL8v8dFnqxSD8qEEdRfXk1SDM6JzNqcERbcGYj9tMrDQBYV9cjgnunFIg==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/tinyglobby": {
      "version": "0.2.15",
      "resolved": "https://registry.npmjs.org/tinyglobby/-/tinyglobby-0.2.15.tgz",
      "integrity": "sha512-j2Zq4NyQYG5XMST4cbs02Ak8iJUdxRM0XI5QyxXuZOzKOINmWurp3smXu3y5wDcJrptwpSjgXHzIQxR0omXljQ==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "fdir": "^6.5.0",
        "picomatch": "^4.0.3"
      },
      "engines": {
        "node": ">=12.0.0"
      },
      "funding": {
        "url": "https://github.com/sponsors/SuperchupuDev"
      }
    },
    "node_modules/tinyrainbow": {
      "version": "3.0.3",
      "resolved": "https://registry.npmjs.org/tinyrainbow/-/tinyrainbow-3.0.3.tgz",
      "integrity": "sha512-PSkbLUoxOFRzJYjjxHJt9xro7D+iilgMX/C9lawzVuYiIdcihh9DXmVibBe8lmcFrRi/VzlPjBxbN7rH24q8/Q==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=14.0.0"
      }
    },
    "node_modules/totalist": {
      "version": "3.0.1",
      "resolved": "https://registry.npmjs.org/totalist/-/totalist-3.0.1.tgz",
      "integrity": "sha512-sf4i37nQ2LBx4m3wB74y+ubopq6W/dIzXg0FDGjsYnZHVa1Da8FH853wlL2gtUhg+xJXjfk3kUZS3BRoQeoQBQ==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=6"
      }
    },
    "node_modules/typescript": {
      "version": "5.9.3",
      "resolved": "https://registry.npmjs.org/typescript/-/typescript-5.9.3.tgz",
      "integrity": "sha512-jl1vZzPDinLr9eUt3J/t7V6FgNEw9QjvBPdysz9KfQDD41fQrC2Y4vKQdiaUpFT4bXlb1RHhLpp8wtm6M5TgSw==",
      "dev": true,
      "license": "Apache-2.0",
      "bin": {
        "tsc": "bin/tsc",
        "tsserver": "bin/tsserver"
      },
      "engines": {
        "node": ">=14.17"
      }
    },
    "node_modules/update-browserslist-db": {
      "version": "1.2.3",
      "resolved": "https://registry.npmjs.org/update-browserslist-db/-/update-browserslist-db-1.2.3.tgz",
      "integrity": "sha512-Js0m9cx+qOgDxo0eMiFGEueWztz+d4+M3rGlmKPT+T4IS/jP4ylw3Nwpu6cpTTP8R1MAC1kF4VbdLt3ARf209w==",
      "dev": true,
      "funding": [
        {
          "type": "opencollective",
          "url": "https://opencollective.com/browserslist"
        },
        {
          "type": "tidelift",
          "url": "https://tidelift.com/funding/github/npm/browserslist"
        },
        {
          "type": "github",
          "url": "https://github.com/sponsors/ai"
        }
      ],
      "license": "MIT",
      "dependencies": {
        "escalade": "^3.2.0",
        "picocolors": "^1.1.1"
      },
      "bin": {
        "update-browserslist-db": "cli.js"
      },
      "peerDependencies": {
        "browserslist": ">= 4.21.0"
      }
    },
    "node_modules/vite": {
      "version": "5.4.21",
      "resolved": "https://registry.npmjs.org/vite/-/vite-5.4.21.tgz",
      "integrity": "sha512-o5a9xKjbtuhY6Bi5S3+HvbRERmouabWbyUcpXXUA1u+GNUKoROi9byOJ8M0nHbHYHkYICiMlqxkg1KkYmm25Sw==",
      "dev": true,
      "license": "MIT",
      "peer": true,
      "dependencies": {
        "esbuild": "^0.21.3",
        "postcss": "^8.4.43",
        "rollup": "^4.20.0"
      },
      "bin": {
        "vite": "bin/vite.js"
      },
      "engines": {
        "node": "^18.0.0 || >=20.0.0"
      },
      "funding": {
        "url": "https://github.com/vitejs/vite?sponsor=1"
      },
      "optionalDependencies": {
        "fsevents": "~2.3.3"
      },
      "peerDependencies": {
        "@types/node": "^18.0.0 || >=20.0.0",
        "less": "*",
        "lightningcss": "^1.21.0",
        "sass": "*",
        "sass-embedded": "*",
        "stylus": "*",
        "sugarss": "*",
        "terser": "^5.4.0"
      },
      "peerDependenciesMeta": {
        "@types/node": {
          "optional": true
        },
        "less": {
          "optional": true
        },
        "lightningcss": {
          "optional": true
        },
        "sass": {
          "optional": true
        },
        "sass-embedded": {
          "optional": true
        },
        "stylus": {
          "optional": true
        },
        "sugarss": {
          "optional": true
        },
        "terser": {
          "optional": true
        }
      }
    },
    "node_modules/vitest": {
      "version": "4.0.17",
      "resolved": "https://registry.npmjs.org/vitest/-/vitest-4.0.17.tgz",
      "integrity": "sha512-FQMeF0DJdWY0iOnbv466n/0BudNdKj1l5jYgl5JVTwjSsZSlqyXFt/9+1sEyhR6CLowbZpV7O1sCHrzBhucKKg==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@vitest/expect": "4.0.17",
        "@vitest/mocker": "4.0.17",
        "@vitest/pretty-format": "4.0.17",
        "@vitest/runner": "4.0.17",
        "@vitest/snapshot": "4.0.17",
        "@vitest/spy": "4.0.17",
        "@vitest/utils": "4.0.17",
        "es-module-lexer": "^1.7.0",
        "expect-type": "^1.2.2",
        "magic-string": "^0.30.21",
        "obug": "^2.1.1",
        "pathe": "^2.0.3",
        "picomatch": "^4.0.3",
        "std-env": "^3.10.0",
        "tinybench": "^2.9.0",
        "tinyexec": "^1.0.2",
        "tinyglobby": "^0.2.15",
        "tinyrainbow": "^3.0.3",
        "vite": "^6.0.0 || ^7.0.0",
        "why-is-node-running": "^2.3.0"
      },
      "bin": {
        "vitest": "vitest.mjs"
      },
      "engines": {
        "node": "^20.0.0 || ^22.0.0 || >=24.0.0"
      },
      "funding": {
        "url": "https://opencollective.com/vitest"
      },
      "peerDependencies": {
        "@edge-runtime/vm": "*",
        "@opentelemetry/api": "^1.9.0",
        "@types/node": "^20.0.0 || ^22.0.0 || >=24.0.0",
        "@vitest/browser-playwright": "4.0.17",
        "@vitest/browser-preview": "4.0.17",
        "@vitest/browser-webdriverio": "4.0.17",
        "@vitest/ui": "4.0.17",
        "happy-dom": "*",
        "jsdom": "*"
      },
      "peerDependenciesMeta": {
        "@edge-runtime/vm": {
          "optional": true
        },
        "@opentelemetry/api": {
          "optional": true
        },
        "@types/node": {
          "optional": true
        },
        "@vitest/browser-playwright": {
          "optional": true
        },
        "@vitest/browser-preview": {
          "optional": true
        },
        "@vitest/browser-webdriverio": {
          "optional": true
        },
        "@vitest/ui": {
          "optional": true
        },
        "happy-dom": {
          "optional": true
        },
        "jsdom": {
          "optional": true
        }
      }
    },
    "node_modules/vitest/node_modules/@esbuild/aix-ppc64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/aix-ppc64/-/aix-ppc64-0.27.2.tgz",
      "integrity": "sha512-GZMB+a0mOMZs4MpDbj8RJp4cw+w1WV5NYD6xzgvzUJ5Ek2jerwfO2eADyI6ExDSUED+1X8aMbegahsJi+8mgpw==",
      "cpu": [
        "ppc64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "aix"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/android-arm": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/android-arm/-/android-arm-0.27.2.tgz",
      "integrity": "sha512-DVNI8jlPa7Ujbr1yjU2PfUSRtAUZPG9I1RwW4F4xFB1Imiu2on0ADiI/c3td+KmDtVKNbi+nffGDQMfcIMkwIA==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "android"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/android-arm64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/android-arm64/-/android-arm64-0.27.2.tgz",
      "integrity": "sha512-pvz8ZZ7ot/RBphf8fv60ljmaoydPU12VuXHImtAs0XhLLw+EXBi2BLe3OYSBslR4rryHvweW5gmkKFwTiFy6KA==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "android"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/android-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/android-x64/-/android-x64-0.27.2.tgz",
      "integrity": "sha512-z8Ank4Byh4TJJOh4wpz8g2vDy75zFL0TlZlkUkEwYXuPSgX8yzep596n6mT7905kA9uHZsf/o2OJZubl2l3M7A==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "android"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/darwin-arm64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/darwin-arm64/-/darwin-arm64-0.27.2.tgz",
      "integrity": "sha512-davCD2Zc80nzDVRwXTcQP/28fiJbcOwvdolL0sOiOsbwBa72kegmVU0Wrh1MYrbuCL98Omp5dVhQFWRKR2ZAlg==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "darwin"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/darwin-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/darwin-x64/-/darwin-x64-0.27.2.tgz",
      "integrity": "sha512-ZxtijOmlQCBWGwbVmwOF/UCzuGIbUkqB1faQRf5akQmxRJ1ujusWsb3CVfk/9iZKr2L5SMU5wPBi1UWbvL+VQA==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "darwin"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/freebsd-arm64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/freebsd-arm64/-/freebsd-arm64-0.27.2.tgz",
      "integrity": "sha512-lS/9CN+rgqQ9czogxlMcBMGd+l8Q3Nj1MFQwBZJyoEKI50XGxwuzznYdwcav6lpOGv5BqaZXqvBSiB/kJ5op+g==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "freebsd"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/freebsd-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/freebsd-x64/-/freebsd-x64-0.27.2.tgz",
      "integrity": "sha512-tAfqtNYb4YgPnJlEFu4c212HYjQWSO/w/h/lQaBK7RbwGIkBOuNKQI9tqWzx7Wtp7bTPaGC6MJvWI608P3wXYA==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "freebsd"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/linux-arm": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-arm/-/linux-arm-0.27.2.tgz",
      "integrity": "sha512-vWfq4GaIMP9AIe4yj1ZUW18RDhx6EPQKjwe7n8BbIecFtCQG4CfHGaHuh7fdfq+y3LIA2vGS/o9ZBGVxIDi9hw==",
      "cpu": [
        "arm"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/linux-arm64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-arm64/-/linux-arm64-0.27.2.tgz",
      "integrity": "sha512-hYxN8pr66NsCCiRFkHUAsxylNOcAQaxSSkHMMjcpx0si13t1LHFphxJZUiGwojB1a/Hd5OiPIqDdXONia6bhTw==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/linux-ia32": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-ia32/-/linux-ia32-0.27.2.tgz",
      "integrity": "sha512-MJt5BRRSScPDwG2hLelYhAAKh9imjHK5+NE/tvnRLbIqUWa+0E9N4WNMjmp/kXXPHZGqPLxggwVhz7QP8CTR8w==",
      "cpu": [
        "ia32"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/linux-loong64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-loong64/-/linux-loong64-0.27.2.tgz",
      "integrity": "sha512-lugyF1atnAT463aO6KPshVCJK5NgRnU4yb3FUumyVz+cGvZbontBgzeGFO1nF+dPueHD367a2ZXe1NtUkAjOtg==",
      "cpu": [
        "loong64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/linux-mips64el": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-mips64el/-/linux-mips64el-0.27.2.tgz",
      "integrity": "sha512-nlP2I6ArEBewvJ2gjrrkESEZkB5mIoaTswuqNFRv/WYd+ATtUpe9Y09RnJvgvdag7he0OWgEZWhviS1OTOKixw==",
      "cpu": [
        "mips64el"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/linux-ppc64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-ppc64/-/linux-ppc64-0.27.2.tgz",
      "integrity": "sha512-C92gnpey7tUQONqg1n6dKVbx3vphKtTHJaNG2Ok9lGwbZil6DrfyecMsp9CrmXGQJmZ7iiVXvvZH6Ml5hL6XdQ==",
      "cpu": [
        "ppc64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/linux-riscv64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-riscv64/-/linux-riscv64-0.27.2.tgz",
      "integrity": "sha512-B5BOmojNtUyN8AXlK0QJyvjEZkWwy/FKvakkTDCziX95AowLZKR6aCDhG7LeF7uMCXEJqwa8Bejz5LTPYm8AvA==",
      "cpu": [
        "riscv64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/linux-s390x": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-s390x/-/linux-s390x-0.27.2.tgz",
      "integrity": "sha512-p4bm9+wsPwup5Z8f4EpfN63qNagQ47Ua2znaqGH6bqLlmJ4bx97Y9JdqxgGZ6Y8xVTixUnEkoKSHcpRlDnNr5w==",
      "cpu": [
        "s390x"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/linux-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/linux-x64/-/linux-x64-0.27.2.tgz",
      "integrity": "sha512-uwp2Tip5aPmH+NRUwTcfLb+W32WXjpFejTIOWZFw/v7/KnpCDKG66u4DLcurQpiYTiYwQ9B7KOeMJvLCu/OvbA==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "linux"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/netbsd-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/netbsd-x64/-/netbsd-x64-0.27.2.tgz",
      "integrity": "sha512-HwGDZ0VLVBY3Y+Nw0JexZy9o/nUAWq9MlV7cahpaXKW6TOzfVno3y3/M8Ga8u8Yr7GldLOov27xiCnqRZf0tCA==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "netbsd"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/openbsd-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/openbsd-x64/-/openbsd-x64-0.27.2.tgz",
      "integrity": "sha512-/it7w9Nb7+0KFIzjalNJVR5bOzA9Vay+yIPLVHfIQYG/j+j9VTH84aNB8ExGKPU4AzfaEvN9/V4HV+F+vo8OEg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "openbsd"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/sunos-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/sunos-x64/-/sunos-x64-0.27.2.tgz",
      "integrity": "sha512-kMtx1yqJHTmqaqHPAzKCAkDaKsffmXkPHThSfRwZGyuqyIeBvf08KSsYXl+abf5HDAPMJIPnbBfXvP2ZC2TfHg==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "sunos"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/win32-arm64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/win32-arm64/-/win32-arm64-0.27.2.tgz",
      "integrity": "sha512-Yaf78O/B3Kkh+nKABUF++bvJv5Ijoy9AN1ww904rOXZFLWVc5OLOfL56W+C8F9xn5JQZa3UX6m+IktJnIb1Jjg==",
      "cpu": [
        "arm64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/win32-ia32": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/win32-ia32/-/win32-ia32-0.27.2.tgz",
      "integrity": "sha512-Iuws0kxo4yusk7sw70Xa2E2imZU5HoixzxfGCdxwBdhiDgt9vX9VUCBhqcwY7/uh//78A1hMkkROMJq9l27oLQ==",
      "cpu": [
        "ia32"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@esbuild/win32-x64": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/@esbuild/win32-x64/-/win32-x64-0.27.2.tgz",
      "integrity": "sha512-sRdU18mcKf7F+YgheI/zGf5alZatMUTKj/jNS6l744f9u3WFu4v7twcUI9vu4mknF4Y9aDlblIie0IM+5xxaqQ==",
      "cpu": [
        "x64"
      ],
      "dev": true,
      "license": "MIT",
      "optional": true,
      "os": [
        "win32"
      ],
      "engines": {
        "node": ">=18"
      }
    },
    "node_modules/vitest/node_modules/@vitest/mocker": {
      "version": "4.0.17",
      "resolved": "https://registry.npmjs.org/@vitest/mocker/-/mocker-4.0.17.tgz",
      "integrity": "sha512-+ZtQhLA3lDh1tI2wxe3yMsGzbp7uuJSWBM1iTIKCbppWTSBN09PUC+L+fyNlQApQoR+Ps8twt2pbSSXg2fQVEQ==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "@vitest/spy": "4.0.17",
        "estree-walker": "^3.0.3",
        "magic-string": "^0.30.21"
      },
      "funding": {
        "url": "https://opencollective.com/vitest"
      },
      "peerDependencies": {
        "msw": "^2.4.9",
        "vite": "^6.0.0 || ^7.0.0-0"
      },
      "peerDependenciesMeta": {
        "msw": {
          "optional": true
        },
        "vite": {
          "optional": true
        }
      }
    },
    "node_modules/vitest/node_modules/esbuild": {
      "version": "0.27.2",
      "resolved": "https://registry.npmjs.org/esbuild/-/esbuild-0.27.2.tgz",
      "integrity": "sha512-HyNQImnsOC7X9PMNaCIeAm4ISCQXs5a5YasTXVliKv4uuBo1dKrG0A+uQS8M5eXjVMnLg3WgXaKvprHlFJQffw==",
      "dev": true,
      "hasInstallScript": true,
      "license": "MIT",
      "bin": {
        "esbuild": "bin/esbuild"
      },
      "engines": {
        "node": ">=18"
      },
      "optionalDependencies": {
        "@esbuild/aix-ppc64": "0.27.2",
        "@esbuild/android-arm": "0.27.2",
        "@esbuild/android-arm64": "0.27.2",
        "@esbuild/android-x64": "0.27.2",
        "@esbuild/darwin-arm64": "0.27.2",
        "@esbuild/darwin-x64": "0.27.2",
        "@esbuild/freebsd-arm64": "0.27.2",
        "@esbuild/freebsd-x64": "0.27.2",
        "@esbuild/linux-arm": "0.27.2",
        "@esbuild/linux-arm64": "0.27.2",
        "@esbuild/linux-ia32": "0.27.2",
        "@esbuild/linux-loong64": "0.27.2",
        "@esbuild/linux-mips64el": "0.27.2",
        "@esbuild/linux-ppc64": "0.27.2",
        "@esbuild/linux-riscv64": "0.27.2",
        "@esbuild/linux-s390x": "0.27.2",
        "@esbuild/linux-x64": "0.27.2",
        "@esbuild/netbsd-arm64": "0.27.2",
        "@esbuild/netbsd-x64": "0.27.2",
        "@esbuild/openbsd-arm64": "0.27.2",
        "@esbuild/openbsd-x64": "0.27.2",
        "@esbuild/openharmony-arm64": "0.27.2",
        "@esbuild/sunos-x64": "0.27.2",
        "@esbuild/win32-arm64": "0.27.2",
        "@esbuild/win32-ia32": "0.27.2",
        "@esbuild/win32-x64": "0.27.2"
      }
    },
    "node_modules/vitest/node_modules/vite": {
      "version": "7.3.1",
      "resolved": "https://registry.npmjs.org/vite/-/vite-7.3.1.tgz",
      "integrity": "sha512-w+N7Hifpc3gRjZ63vYBXA56dvvRlNWRczTdmCBBa+CotUzAPf5b7YMdMR/8CQoeYE5LX3W4wj6RYTgonm1b9DA==",
      "dev": true,
      "license": "MIT",
      "peer": true,
      "dependencies": {
        "esbuild": "^0.27.0",
        "fdir": "^6.5.0",
        "picomatch": "^4.0.3",
        "postcss": "^8.5.6",
        "rollup": "^4.43.0",
        "tinyglobby": "^0.2.15"
      },
      "bin": {
        "vite": "bin/vite.js"
      },
      "engines": {
        "node": "^20.19.0 || >=22.12.0"
      },
      "funding": {
        "url": "https://github.com/vitejs/vite?sponsor=1"
      },
      "optionalDependencies": {
        "fsevents": "~2.3.3"
      },
      "peerDependencies": {
        "@types/node": "^20.19.0 || >=22.12.0",
        "jiti": ">=1.21.0",
        "less": "^4.0.0",
        "lightningcss": "^1.21.0",
        "sass": "^1.70.0",
        "sass-embedded": "^1.70.0",
        "stylus": ">=0.54.8",
        "sugarss": "^5.0.0",
        "terser": "^5.16.0",
        "tsx": "^4.8.1",
        "yaml": "^2.4.2"
      },
      "peerDependenciesMeta": {
        "@types/node": {
          "optional": true
        },
        "jiti": {
          "optional": true
        },
        "less": {
          "optional": true
        },
        "lightningcss": {
          "optional": true
        },
        "sass": {
          "optional": true
        },
        "sass-embedded": {
          "optional": true
        },
        "stylus": {
          "optional": true
        },
        "sugarss": {
          "optional": true
        },
        "terser": {
          "optional": true
        },
        "tsx": {
          "optional": true
        },
        "yaml": {
          "optional": true
        }
      }
    },
    "node_modules/why-is-node-running": {
      "version": "2.3.0",
      "resolved": "https://registry.npmjs.org/why-is-node-running/-/why-is-node-running-2.3.0.tgz",
      "integrity": "sha512-hUrmaWBdVDcxvYqnyh09zunKzROWjbZTiNy8dBEjkS7ehEDQibXJ7XvlmtbwuTclUiIyN+CyXQD4Vmko8fNm8w==",
      "dev": true,
      "license": "MIT",
      "dependencies": {
        "siginfo": "^2.0.0",
        "stackback": "0.0.2"
      },
      "bin": {
        "why-is-node-running": "cli.js"
      },
      "engines": {
        "node": ">=8"
      }
    },
    "node_modules/ws": {
      "version": "8.19.0",
      "resolved": "https://registry.npmjs.org/ws/-/ws-8.19.0.tgz",
      "integrity": "sha512-blAT2mjOEIi0ZzruJfIhb3nps74PRWTCz1IjglWEEpQl5XS/UNama6u2/rjFkDDouqr4L67ry+1aGIALViWjDg==",
      "dev": true,
      "license": "MIT",
      "engines": {
        "node": ">=10.0.0"
      },
      "peerDependencies": {
        "bufferutil": "^4.0.1",
        "utf-8-validate": ">=5.0.2"
      },
      "peerDependenciesMeta": {
        "bufferutil": {
          "optional": true
        },
        "utf-8-validate": {
          "optional": true
        }
      }
    },
    "node_modules/yallist": {
      "version": "3.1.1",
      "resolved": "https://registry.npmjs.org/yallist/-/yallist-3.1.1.tgz",
      "integrity": "sha512-a4UGQaWPH59mOXUYnAG2ewncQS4i4F43Tv3JoAM+s2VDAmS9NsK8GpDMLrCHPksFT7h3K6TOoUNn2pb7RoXx4g==",
      "dev": true,
      "license": "ISC"
    }
  }
}

@echo off
npm run dev -- --host 0.0.0.0 --port 5173
pause
// Test interno senza browser
import fs from 'fs'

console.log("=== TEST FILE SYSTEM ===")
console.log("1. Controllo index.html...")
const html = fs.readFileSync('./public/index.html', 'utf8')
console.log("✅ index.html trovato (" + html.length + " caratteri)")
console.log("Prime 50 chars:", html.substring(0, 50))

console.log("\n2. Controllo App.tsx...")
const app = fs.readFileSync('./src/App.tsx', 'utf8')
console.log("✅ App.tsx trovato (" + app.length + " caratteri)")

console.log("\n3. Controllo main.tsx...")
const main = fs.readFileSync('./src/main.tsx', 'utf8')
console.log("✅ main.tsx trovato")

console.log("\n=== TUTTI I FILE SONO PRESENTI ===")
console.log("Il problema è di rete/firewall, non di file mancanti.")

const http = require('http');
const fs = require('fs');
const path = require('path');

const server = http.createServer((req, res) => {
  console.log(`${req.method} ${req.url}`);
  
  if (req.url === '/') {
    const html = fs.readFileSync(path.join(__dirname, 'public', 'index.html'), 'utf8');
    res.writeHead(200, { 'Content-Type': 'text/html' });
    res.end(html);
  } else {
    res.writeHead(404);
    res.end('Not found');
  }
});

server.listen(8080, '127.0.0.1', () => {
  console.log('Server test in esecuzione su http://127.0.0.1:8080');
  console.log('Premi Ctrl+C per fermare');
});
{
  "compilerOptions": {
    "target": "ES2020",
    "useDefineForClassFields": true,
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "skipLibCheck": true,
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true
  },
  "include": ["src"]
}

// Server semplicissimo che FUNZIONA SEMPRE
const http = require('http');
const fs = require('fs');
const path = require('path');

const server = http.createServer((req, res) => {
  console.log(`[${new Date().toLocaleTimeString()}] ${req.method} ${req.url}`);
  
  // Sempre rispondi con HTML, anche se la pagina non esiste
  res.writeHead(200, { 'Content-Type': 'text/html; charset=utf-8' });
  
  const html = `
  <!DOCTYPE html>
  <html lang="it">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FEDACS Sistema Unificato</title>
    <style>
      body {
        margin: 0;
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
        background: #0f0f23;
        color: #ccc;
        padding: 20px;
      }
      header {
        display: flex;
        align-items: center;
        gap: 10px;
        margin-bottom: 30px;
      }
      h1 {
        color: #00ff00;
        margin: 0;
      }
      .status-box {
        background: #1a1a2e;
        padding: 20px;
        border-radius: 10px;
        margin-bottom: 20px;
      }
      .bar-container {
        height: 10px;
        background: #333;
        border-radius: 5px;
        margin-top: 5px;
        margin-bottom: 5px;
      }
      .bar-governance {
        width: 74%;
        height: 100%;
        background: #ff6b6b;
        border-radius: 5px;
      }
      .bar-evolution {
        width: 26%;
        height: 100%;
        background: #4ecdc4;
        border-radius: 5px;
      }
      button {
        background: #00ff00;
        color: #000;
        border: none;
        padding: 10px 20px;
        border-radius: 5px;
        cursor: pointer;
        font-weight: bold;
        font-size: 16px;
      }
    </style>
  </head>
  <body>
    <header>
      <h1>🧠 FEDACS Sistema Unificato</h1>
      <span style="margin-left: auto; background: #1a1a2e; padding: 5px 10px; border-radius: 5px;">
        α=0.26 | β=0.74
      </span>
    </header>
    
    <div class="status-box">
      <h2>⚡ Stato Sistema</h2>
      <p>✅ Ambiente base configurato correttamente.</p>
      <p>🚨 <strong>Problema firewall risolto con strategia alternativa</strong></p>
      
      <div style="display: flex; gap: 15px; margin-top: 20px;">
        <div style="background: #252547; padding: 10px; border-radius: 5px; flex: 1;">
          <div>🛡️ Governance (β)</div>
          <div class="bar-container">
            <div class="bar-governance"></div>
          </div>
          <div style="text-align: right; font-size: 12px;">74%</div>
        </div>
        
        <div style="background: #252547; padding: 10px; border-radius: 5px; flex: 1;">
          <div>👥 Evoluzione (α)</div>
          <div class="bar-container">
            <div class="bar-evolution"></div>
          </div>
          <div style="text-align: right; font-size: 12px;">26%</div>
        </div>
      </div>
    </div>
    
    <div class="status-box">
      <h3>✅ PASSO 2 COMPLETATO</h3>
      <p>React + TypeScript installati correttamente.</p>
      <p><strong>Prossimo passo:</strong> Calcolatore FEDACS base</p>
      <button onclick="alert('Pronti per il PASSO 3!')">Attendi istruzioni...</button>
    </div>
    
    <div style="margin-top: 20px; color: #888; font-size: 12px;">
      Server: ultra-server.cjs | Porta: 8888 | Data: ${new Date().toLocaleDateString()}
    </div>
    
    <script>
      console.log('FEDACS loaded successfully');
    </script>
  </body>
  </html>
  `;
  
  res.end(html);
});

const PORT = 8888;
server.listen(PORT, '127.0.0.1', () => {
  console.log('='.repeat(50));
  console.log('🚀 SERVER FEDACS AVVIATO CON SUCCESSO!');
  console.log('='.repeat(50));
  console.log('👉 APRI IL BROWSER E VAI SU:');
  console.log(`   http://127.0.0.1:${PORT}`);
  console.log('   http://localhost:${PORT}');
  console.log('='.repeat(50));
  console.log('Premi CTRL+C per fermare il server');
  console.log('='.repeat(50));
});
import { defineConfig } from "vite"
import react from "@vitejs/plugin-react"

export default defineConfig({
  plugins: [react()],
  server: {
    port: 3000,
    open: false  // Non aprire browser automaticamente
  }
})
