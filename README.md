# StarDiary-beta-

<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>StarDiary by Grafittiii</title>
    <link href="https://fonts.googleapis.com/css2?family=LXGW+WenKai+TC:wght@400;700&family=Noto+Sans+TC:wght@400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-font: 'LXGW WenKai TC', sans-serif;
            --glass: rgba(255, 255, 255, 0.8);
            --accent-color: #ff748c;
            --accent-text: #fff;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }
        
        /* 1. 模板套用在全屏 (Body) */
        body {
            font-family: var(--primary-font);
            height: 100vh; width: 100vw; overflow: hidden;
            display: flex; align-items: center; justify-content: center;
            transition: 0.5s ease;
        }

        /* --- 七大全屏模板 --- */
        .theme-sakura { background: linear-gradient(135deg, #fff0f3, #ffd6e0); background-image: url("data:image/svg+xml,%3Csvg width='40' height='40' viewBox='0 0 40 40' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M20 10c2-5 8-5 10 0s-3 8-10 12c-7-4-12-7-10-12s8-5 10 0z' fill='%23ffb7c5' fill-opacity='0.4'/%3E%3C/svg%3E"); }
        .theme-british { background-color: #1a2e1a; background-image: repeating-linear-gradient(45deg, rgba(212,175,55,0.1) 0, rgba(212,175,55,0.1) 1px, transparent 1px, transparent 30px); }
        .theme-stage { background: #1a0b2e radial-gradient(circle at 50% 10%, rgba(255,255,255,0.2) 0%, transparent 80%); }
        .theme-clover { background: linear-gradient(135deg, #e8f5e9, #a5d6a7); background-image: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M30 30c5-10 15-10 15 0s-10 5-15 5c-5 0-15-5-15-5s10-10 15 0z' fill='%232e7d32' fill-opacity='0.1'/%3E%3C/svg%3E"); }
        .theme-rainbow { background: linear-gradient(135deg, #ff9a9e, #fad0c4, #ffecd2, #a1c4fd, #c2e9fb, #d4fc79); }
        /* 2. 向日葵：回歸黃橙漸變 */
        .theme-sunflower { background: linear-gradient(135deg, #ffd773, #fbc02d); background-image: radial-gradient(circle at top-left, rgba(255,255,255,0.2) 0%, transparent 70%); }
        /* 3. 星空：隨機散落感 */
        .theme-starry { 
            background: #0d1117; 
            background-image: 
                radial-gradient(1px 1px at 10% 20%, white, transparent),
                radial-gradient(2px 2px at 25% 45%, white, transparent),
                radial-gradient(1px 1px at 50% 80%, white, transparent),
                radial-gradient(2px 2px at 70% 30%, white, transparent),
                radial-gradient(1px 1px at 85% 65%, white, transparent),
                radial-gradient(1.5px 1.5px at 15% 90%, white, transparent);
            background-size: 250px 250px; /* 增加尺寸讓排列感消失 */
        }

        /* --- 介面佈局 --- */
        .app-wrapper {
            width: 100%; height: 100%; display: flex; flex-direction: column;
            align-items: center; justify-content: space-evenly; padding: 20px; z-index: 10;
        }

        .top-controls { width: 100%; max-width: 360px; display: flex; flex-direction: column; gap: 10px; }
        .toolbar-row { display: flex; gap: 8px; align-items: stretch; }
        .format-group { display: flex; gap: 4px; background: rgba(255,255,255,0.6); padding: 5px 10px; border-radius: 12px; }
        .tool-btn { border: none; background: none; font-size: 16px; cursor: pointer; color: #333; }

        .font-select, .btn-draw { height: 40px; border-radius: 12px; border: none; font-family: inherit; font-size: 13px; font-weight: 700; }
        .font-select { flex: 1.2; background: white; padding: 0 10px; }
        .btn-draw { flex: 1; background: var(--accent-color); color: var(--accent-text); cursor: pointer; box-shadow: 0 4px 10px rgba(0,0,0,0.15); }

        /* 畫布區域 */
        .card-container { width: 100%; display: flex; justify-content: center; }
        .note-card {
            width: 100%; max-width: 360px; border-radius: 24px; padding: 25px;
            display: flex; flex-direction: column; position: relative;
            box-shadow: 0 30px 60px rgba(0,0,0,0.2); 
            background: var(--glass); /* 卡片本身是半透明磨砂 */
            transition: aspect-ratio 0.4s ease, height 0.4s ease;
        }
        
        /* 比例設定 */
        .ratio-9-16 { aspect-ratio: 9 / 16; height: 55vh; }
        .ratio-square { aspect-ratio: 1 / 1; height: 45vh; }

        #answer-editor { flex: 1; outline: none; font-size: 18px; line-height: 1.8; margin-top: 15px; color: #111; overflow-y: auto; }
        #answer-editor:empty:before { content: "在此寫下關於他/她的文字..."; opacity: 0.3; }

        /* 底部控制 */
        .control-panel { width: 100%; max-width: 400px; display: flex; flex-direction: column; gap: 15px; }
        .theme-selector { display: flex; justify-content: center; gap: 10px; }
        .theme-dot { width: 30px; height: 30px; border-radius: 50%; cursor: pointer; border: 2px solid white; box-shadow: 0 2px 6px rgba(0,0,0,0.1); }
        
        .action-btns { display: flex; gap: 10px; }
        .glass-btn { background: white; border: none; padding: 14px; border-radius: 15px; font-size: 14px; font-weight: 700; cursor: pointer; flex: 1; }
        .btn-save { background: #000; color: white; flex: 2; }

        /* 隱藏的 Canvas */
        #exportCanvas { display: none; }
    </style>
</head>
<body class="theme-sakura" id="full-body">

    <div class="app-wrapper">
        <div class="top-controls">
            <div class="toolbar-row">
                <div class="format-group">
                    <button class="tool-btn" onclick="document.execCommand('bold')">B</button>
                    <button class="tool-btn" onclick="document.execCommand('italic')">I</button>
                    <button class="tool-btn" onclick="document.execCommand('underline')">U</button>
                </div>
                <select class="font-select" onchange="changeFont(this.value)">
                    <option value="'LXGW WenKai TC'">霞鶩文楷 (手寫)</option>
                    <option value="'Noto Sans TC'">思源黑體 (現代)</option>
                </select>
                <button class="btn-draw" id="draw-trigger" onclick="drawPrompt()">✦ 抽取題目</button>
            </div>
        </div>

        <div class="card-container">
            <div id="capture-area" class="note-card ratio-9-16">
                <div id="category-badge" style="font-size: 10px; opacity: 0.5; letter-spacing: 2px; font-weight: 700;">STAR DIARY</div>
                <div id="question-text" style="font-size: 20px; font-weight: 700; margin-top: 10px; line-height: 1.5;">點擊右上按鈕抽取題目 記錄關於他/她的瞬間</div>
                <div id="answer-editor" contenteditable="true"></div>
                <div style="display: flex; justify-content: space-between; align-items: flex-end; margin-top: 15px;">
                    <div id="current-date" style="font-size: 10px; opacity: 0.5;"></div>
                    <div style="font-size: 11px; font-weight: 700; opacity: 0.8; text-align: right; line-height: 1.2;">
                        StarDiary<br><span style="font-size: 9px; font-weight: 400;">by Grafittiii</span>
                    </div>
                </div>
            </div>
        </div>

        <div class="control-panel">
            <div class="theme-selector">
                <div class="theme-dot" style="background:#ffd6e0" onclick="setTheme('sakura', '#ff748c')"></div>
                <div class="theme-dot" style="background:#1a2e1a" onclick="setTheme('british', '#d4af37')"></div>
                <div class="theme-dot" style="background:#4a148c" onclick="setTheme('stage', '#ffeb3b')"></div>
                <div class="theme-dot" style="background:#a5d6a7" onclick="setTheme('clover', '#2e7d32')"></div>
                <div class="theme-dot" style="background:linear-gradient(45deg, #ff9a9e, #a1c4fd)" onclick="setTheme('rainbow', '#333')"></div>
                <div class="theme-dot" style="background:#fbc02d" onclick="setTheme('sunflower', '#5d4037')"></div>
                <div class="theme-dot" style="background:#0d1117" onclick="setTheme('starry', '#00bcd4')"></div>
            </div>
            
            <div class="action-btns">
                <button class="glass-btn" onclick="setRatio('ratio-9-16')">9:16</button>
                <button class="glass-btn" onclick="setRatio('ratio-square')">1:1</button>
                <button class="glass-btn btn-save" id="save-btn" onclick="handleSave()">📸 儲存圖片</button>
            </div>
        </div>
    </div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <script>
        Random questions = [
            { cat: "初遇", txt: "第一次在螢幕上看到他/她時，被吸引的一幕"},
            { cat: "初遇", txt:"第一次線下看到他/她，心臟漏跳一拍的瞬間"},
            { cat: "陪伴", txt: "聽著他/她的歌，在那段難熬的日子裡得到的安慰"},
            { cat: "陪伴", txt:"已經關注他/她_年_月_日了"},
            { cat: "特質", txt: "他/她身上最吸引妳、讓妳想成為更好的人的優點"},
            { cat: "特質", txt: "他/她怎樣的一面，應該要有更多人知道？"},
            { cat: "語錄", txt: "他/她曾經說過哪句話，讓妳至今依然記憶猶新？"},
            { cat: "語錄", txt:"你最喜歡他/她的哪句歌詞/對白？"}
        ];

        let isDrawn = false;

        function setTheme(themeName, accentColor) {
            document.getElementById('full-body').className = 'theme-' + themeName;
            document.documentElement.style.setProperty('--accent-color', accentColor);
            // 英倫主題特殊處理：卡片邊框
            const card = document.getElementById('capture-area');
            if(themeName === 'british') {
                card.style.border = "3px solid #d4af37";
            } else {
                card.style.border = "none";
            }
        }

        function changeFont(font) {
            document.getElementById('capture-area').style.fontFamily = font;
        }

        function drawPrompt() {
            const q = questions[Math.floor(Math.random() * questions.length)];
            document.getElementById('question-text').innerText = q.txt;
            document.getElementById('category-badge').innerText = q.cat;
            isDrawn = true;
        }

        function setRatio(r) {
            const card = document.getElementById('capture-area');
            card.classList.remove('ratio-9-16', 'ratio-square');
            card.classList.add(r);
        }

        // 核心儲存邏輯修正
        async function handleSave() {
            if (!isDrawn) return alert("請先抽取題目！");
            if (!document.getElementById('answer-editor').innerText.trim()) return alert("請寫下你的心情記錄。");

            const btn = document.getElementById('save-btn');
            const originalText = btn.innerText;
            btn.innerText = "生成中...";
            btn.disabled = true;

            try {
                // 修正：截取全屏 (body)，而不只是卡片
                const canvas = await html2canvas(document.body, {
                    scale: 2, // 為了相容性使用 2 倍率
                    useCORS: true,
                    allowTaint: true,
                    backgroundColor: null,
                    // 確保截取當前視窗大小
                    width: window.innerWidth,
                    height: window.innerHeight
                });

                const link = document.createElement('a');
                link.download = `StarDiary_${Date.now()}.png`;
                link.href = canvas.toDataURL("image/png");
                document.body.appendChild(link); // 確保在 iOS 上能觸發
                link.click();
                document.body.removeChild(link);
                
                btn.innerText = "儲存成功！";
                setTimeout(() => { btn.innerText = originalText; btn.disabled = false; }, 2000);
            } catch (err) {
                console.error("Save Error:", err);
                alert("儲存失敗，可能是瀏覽器權限問題。請嘗試截圖或換個瀏覽器。");
                btn.innerText = originalText;
                btn.disabled = false;
            }
        }

        document.getElementById('current-date').innerText = new Date().toLocaleDateString();
    </script>
</body>
</html>
