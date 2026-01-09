# StarDiary-beta-

<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>StarDiary by Grafittiii</title>
    <!-- 預加載主要字體 -->
    <link rel="preload" href="https://cdn.jsdelivr.net/gh/max32002/pop-gothic@2.143/webfont/CJK%20TC/PopGothicCjkTc-Regular.woff2" as="font" type="font/woff2" crossorigin>
    <link rel="preload" href="https://cdn.jsdelivr.net/gh/max32002/JasonHandWritingFonts@20240409/webfont/JasonHandwriting1-Regular.woff2" as="font" type="font/woff2" crossorigin>
    <link rel="preload" href="https://cdn.jsdelivr.net/gh/max32002/JasonHandWritingFonts@20240409/webfont/JasonHandwriting3-Regular.woff2" as="font" type="font/woff2" crossorigin>
    <link rel="preload" href="https://cdn.jsdelivr.net/gh/max32002/JasonHandWritingFonts@20240409/webfont/JasonHandwriting5-Regular-P.woff2" as="font" type="font/woff2" crossorigin>
    <link rel="preload" href="https://cdn.jsdelivr.net/gh/max32002/naikaifont@1.89/webfont/NaikaiFont-Regular.woff2" as="font" type="font/woff2" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=LXGW+WenKai+TC:wght@400;700&family=Noto+Sans+TC:wght@400;700&family=Noto+Serif+TC:wght@400;700&display=swap" rel="stylesheet">
    <style>
        /* 大波浪圓體 - 可愛圓潤 */
        @font-face {
            font-family: 'PopGothic';
            src: url('https://cdn.jsdelivr.net/gh/max32002/pop-gothic@2.143/webfont/CJK%20TC/PopGothicCjkTc-Regular.woff2') format('woff2');
            font-weight: 400;
            font-display: swap;
        }
        @font-face {
            font-family: 'PopGothic';
            src: url('https://cdn.jsdelivr.net/gh/max32002/pop-gothic@2.143/webfont/CJK%20TC/PopGothicCjkTc-Bold.woff2') format('woff2');
            font-weight: 700;
            font-display: swap;
        }
        /* 清松手寫體1 - 圓潤手寫 */
        @font-face {
            font-family: 'JasonHandwriting1';
            src: url('https://cdn.jsdelivr.net/gh/max32002/JasonHandWritingFonts@20240409/webfont/JasonHandwriting1-Regular.woff2') format('woff2');
            font-weight: 400;
            font-display: swap;
        }
        /* 清松手寫體3 - 呆萌手寫 */
        @font-face {
            font-family: 'JasonHandwriting3';
            src: url('https://cdn.jsdelivr.net/gh/max32002/JasonHandWritingFonts@20240409/webfont/JasonHandwriting3-Regular.woff2') format('woff2');
            font-weight: 400;
            font-display: swap;
        }
        /* 清松手寫體5 - 行楷 (變動寬版本) */
        @font-face {
            font-family: 'JasonHandwriting5';
            src: url('https://cdn.jsdelivr.net/gh/max32002/JasonHandWritingFonts@20240409/webfont/JasonHandwriting5-Regular-P.woff2') format('woff2');
            font-weight: 400;
            font-display: swap;
        }
        /* 內海字體 - 可愛手寫 */
        @font-face {
            font-family: 'NaikaiFont';
            src: url('https://cdn.jsdelivr.net/gh/max32002/naikaifont@1.89/webfont/NaikaiFont-Regular.woff2') format('woff2');
            font-weight: 400;
            font-display: swap;
        }
    </style>
    <style>
        :root {
            --primary-font: 'LXGW WenKai TC', sans-serif;
            --glass: rgba(255, 255, 255, 0.8);
            --accent-color: #ff748c;
            --accent-text: #fff;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }
        
        /* 1. 模板套用在全屏 (Body) */
        html, body {
            overflow-x: hidden;
            max-width: 100%;
        }
        body {
            font-family: var(--primary-font);
            min-height: 100vh;
            min-height: 100dvh; /* 動態視口高度，適應鍵盤 */
            width: 100%;
            overflow-y: auto;
            display: flex; align-items: center; justify-content: center;
            transition: 0.5s ease;
            background-attachment: fixed;
        }

        /* --- 七大全屏模板 --- */
        .theme-sakura { background: linear-gradient(135deg, #fff0f3, #ffd6e0); background-image: url("data:image/svg+xml,%3Csvg width='40' height='40' viewBox='0 0 40 40' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M20 10c2-5 8-5 10 0s-3 8-10 12c-7-4-12-7-10-12s8-5 10 0z' fill='%23ffb7c5' fill-opacity='0.4'/%3E%3C/svg%3E"); }
        .theme-british { background-color: #1a2e1a; background-image: repeating-linear-gradient(45deg, rgba(212,175,55,0.1) 0, rgba(212,175,55,0.1) 1px, transparent 1px, transparent 30px); }
        .theme-stage {
            background: #0d0618;
            background-image:
                /* 中央主光束 - 明艷洋紅 */
                linear-gradient(180deg, rgba(255, 0, 127, 0.6) 0%, rgba(255, 0, 127, 0.15) 35%, transparent 70%),
                /* 左側光束 - 亮紫 */
                linear-gradient(165deg, transparent 20%, rgba(180, 0, 255, 0.5) 30%, rgba(180, 0, 255, 0.1) 50%, transparent 65%),
                /* 右側光束 - 亮粉 */
                linear-gradient(195deg, transparent 20%, rgba(255, 20, 180, 0.5) 30%, rgba(255, 20, 180, 0.1) 50%, transparent 65%),
                /* 頂部聚光燈源點 */
                radial-gradient(circle at 50% 0%, rgba(255, 255, 255, 0.9) 0%, rgba(255, 0, 127, 0.8) 3%, transparent 8%),
                radial-gradient(circle at 25% 0%, rgba(255, 255, 255, 0.7) 0%, rgba(180, 0, 255, 0.7) 3%, transparent 7%),
                radial-gradient(circle at 75% 0%, rgba(255, 255, 255, 0.7) 0%, rgba(255, 20, 180, 0.7) 3%, transparent 7%),
                /* 氛圍光暈 */
                radial-gradient(ellipse 100% 60% at 50% 0%, rgba(255, 0, 127, 0.25) 0%, transparent 60%),
                radial-gradient(ellipse 80% 50% at 25% 5%, rgba(180, 0, 255, 0.2) 0%, transparent 50%),
                radial-gradient(ellipse 80% 50% at 75% 5%, rgba(255, 20, 180, 0.2) 0%, transparent 50%);
        }
        .theme-clover {
            background: linear-gradient(135deg, #e8f5e9 0%, #a5d6a7 100%);
        }
        .theme-rainbow { background: linear-gradient(135deg, #ff9a9e, #fad0c4, #ffecd2, #a1c4fd, #c2e9fb, #d4fc79); }
        .theme-sunflower {
            background: linear-gradient(135deg, #ffd773 0%, #fbc02d 100%);
        }
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
            width: 100%;
            min-height: 100vh;
            min-height: 100dvh;
            display: flex; flex-direction: column;
            align-items: center; justify-content: space-evenly; padding: 20px; z-index: 10;
        }

        .top-controls { width: 100%; max-width: 360px; display: flex; flex-direction: column; gap: 10px; margin-bottom: 20px; flex-shrink: 0; }
        .toolbar-row { display: flex; gap: 6px; align-items: stretch; height: 44px; }
        .format-group { display: flex; gap: 2px; background: rgba(255,255,255,0.6); padding: 0 6px; border-radius: 12px; flex-shrink: 0; align-items: center; }
        .tool-btn { border: none; background: none; font-size: 16px; cursor: pointer; color: #333; padding: 0 10px; height: 100%; border-radius: 6px; transition: background 0.2s; display: flex; align-items: center; justify-content: center; }
        .tool-btn:hover { background: rgba(0,0,0,0.08); }
        .tool-btn:active { background: rgba(0,0,0,0.15); }

        .font-select, .btn-draw { height: 100%; border-radius: 12px; border: none; font-family: inherit; font-size: 12px; font-weight: 700; }
        .font-select { flex: 1; background: white; padding: 0 8px; min-width: 0; }
        .btn-draw { flex: 0 0 auto; padding: 0 12px; background: var(--accent-color); color: var(--accent-text); cursor: pointer; box-shadow: 0 4px 10px rgba(0,0,0,0.15); white-space: nowrap; }

        /* 畫布區域 */
        .card-container { width: 100%; display: flex; justify-content: center; flex-shrink: 0; }
        .note-card {
            width: 100%; max-width: 360px; border-radius: 24px; padding: 25px;
            display: flex; flex-direction: column; position: relative;
            box-shadow: 0 30px 60px rgba(0,0,0,0.2);
            background: var(--glass); /* 卡片本身是半透明磨砂 */
            transition: aspect-ratio 0.4s ease, height 0.4s ease;
        }

        /* 比例設定 */
        .ratio-9-16 { aspect-ratio: 9 / 16; height: 55vh; height: 55dvh; }
        .ratio-square { aspect-ratio: 1 / 1; height: 45vh; height: 45dvh; }

        #answer-editor { flex: 1; outline: none; font-size: 18px; line-height: 1.8; margin-top: 15px; color: #111; overflow-y: auto; min-height: 80px; }
        #answer-editor:empty:before { content: "在此寫下關於他/她的文字..."; opacity: 0.3; }

        /* 底部控制 */
        .control-panel { width: 100%; max-width: 400px; display: flex; flex-direction: column; gap: 15px; margin-top: 20px; flex-shrink: 0; padding-bottom: 20px; }
        .theme-selector { display: flex; justify-content: center; gap: 10px; }
        .theme-dot { width: 30px; height: 30px; border-radius: 50%; cursor: pointer; border: 2px solid white; box-shadow: 0 2px 6px rgba(0,0,0,0.1); }
        
        .action-btns { display: flex; gap: 10px; }
        .glass-btn { background: white; border: none; padding: 14px; border-radius: 15px; font-size: 14px; font-weight: 700; cursor: pointer; flex: 1; }
        .btn-save { background: #000; color: white; flex: 2; }

        /* 隱藏的 Canvas */
        #exportCanvas { display: none; }

        /* 背景裝飾 Canvas */
        #bgCanvas {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            pointer-events: none;
            z-index: 1;
        }
        .app-wrapper { z-index: 10; position: relative; }

        /* Custom Modal */
        .modal-overlay {
            position: fixed; inset: 0; background: rgba(0,0,0,0.5);
            display: flex; align-items: center; justify-content: center; z-index: 1000;
            animation: fadeIn 0.2s ease;
        }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        .modal-box {
            background: white; padding: 24px 28px; border-radius: 16px;
            max-width: 300px; text-align: center; box-shadow: 0 10px 40px rgba(0,0,0,0.2);
        }
        .modal-box p { font-size: 15px; color: #333; margin-bottom: 18px; line-height: 1.6; }
        .modal-box button {
            background: var(--accent-color); color: white; border: none;
            padding: 10px 28px; border-radius: 10px; font-size: 14px;
            font-weight: 700; cursor: pointer; font-family: inherit;
        }

        /* 字體載入提示 */
        .font-loading-toast {
            position: fixed;
            bottom: 100px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(0, 0, 0, 0.85);
            color: white;
            padding: 12px 24px;
            border-radius: 20px;
            font-size: 14px;
            z-index: 1000;
            display: flex;
            align-items: center;
            gap: 10px;
            animation: toastIn 0.3s ease;
            box-shadow: 0 4px 20px rgba(0,0,0,0.3);
        }
        @keyframes toastIn {
            from { opacity: 0; transform: translateX(-50%) translateY(20px); }
            to { opacity: 1; transform: translateX(-50%) translateY(0); }
        }
        .font-loading-toast.hide {
            animation: toastOut 0.3s ease forwards;
            pointer-events: none;
        }
        @keyframes toastOut {
            from { opacity: 1; transform: translateX(-50%) translateY(0); }
            to { opacity: 0; transform: translateX(-50%) translateY(20px); }
        }
        .font-loading-spinner {
            width: 16px;
            height: 16px;
            border: 2px solid rgba(255,255,255,0.3);
            border-top-color: white;
            border-radius: 50%;
            animation: spin 0.8s linear infinite;
        }
        @keyframes spin {
            to { transform: rotate(360deg); }
        }

        /* 字體選單選項載入狀態 */
        .font-select option.loading {
            color: #999;
        }
    </style>
</head>
<body class="theme-sakura" id="full-body">
    <canvas id="bgCanvas"></canvas>

    <div class="app-wrapper">
        <div class="top-controls">
            <div class="toolbar-row">
                <div class="format-group">
                    <button class="tool-btn" onclick="document.execCommand('bold')">B</button>
                    <button class="tool-btn" onclick="document.execCommand('italic')">I</button>
                    <button class="tool-btn" onclick="document.execCommand('underline')">U</button>
                </div>
                <select class="font-select" onchange="changeFont(this.value)">
                    <option value="'LXGW WenKai TC'">霞鶩文楷 (硬筆楷書)</option>
                    <option value="'PopGothic'">大波浪圓體 (可愛圓潤)</option>
                    <option value="'JasonHandwriting1'">清松手寫體1 (圓潤)</option>
                    <option value="'JasonHandwriting3'">清松手寫體3 (呆萌)</option>
                    <option value="'JasonHandwriting5'">清松手寫體5 (行楷)</option>
                    <option value="'NaikaiFont'">內海字體 (可愛手寫)</option>
                    <option value="'Noto Serif TC'">思源宋體 (優雅襯線)</option>
                    <option value="'Noto Sans TC'">思源黑體 (現代簡潔)</option>
                </select>
                <button class="btn-draw" id="draw-trigger" onclick="drawPrompt()">✦ 抽取題目</button>
            </div>
        </div>

        <div class="card-container">
            <div id="capture-area" class="note-card ratio-9-16">
                <div id="category-badge" style="font-size: 10px; opacity: 0.5; letter-spacing: 2px; font-weight: 700;">STAR DIARY</div>
                <div id="question-text" style="font-size: 20px; font-weight: 700; margin-top: 10px; line-height: 1.5;">你準備好記錄關於他/她的瞬間了嗎？</div>
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
                <div class="theme-dot" style="background:linear-gradient(180deg, #ff007f, #0d0618)" onclick="setTheme('stage', '#ff007f')"></div>
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

    <script>
        function showAlert(message) {
            const overlay = document.createElement('div');
            overlay.className = 'modal-overlay';
            overlay.innerHTML = `
                <div class="modal-box">
                    <p>${message}</p>
                    <button onclick="this.closest('.modal-overlay').remove()">確定</button>
                </div>
            `;
            document.body.appendChild(overlay);
            overlay.addEventListener('click', (e) => { if (e.target === overlay) overlay.remove(); });
        }

        const questions = [
            { cat: "初遇", txt: "第一次在螢幕上看到他/她時，被吸引的一幕"},
            { cat: "初遇", txt:"第一次線下看到他/她時，心臟漏跳一拍的瞬間"},
            { cat: "陪伴", txt: "聽著他/她的歌，在那段難熬的日子裡得到的安慰"},
            { cat: "陪伴", txt:"已經關注他/她_年_月_日了"},
            { cat: "特質", txt: "他/她身上最吸引妳、讓妳想成為更好的人的優點"},
            { cat: "特質", txt: "他/她怎樣的一面，應該要有更多人知道？"},
            { cat: "語錄", txt: "他/她曾經說過哪句話，讓妳至今依然記憶猶新？"},
            { cat: "語錄", txt:"你最喜歡他/她的哪句歌詞/對白？"}
        ];

        let isDrawn = false;
        let currentFont = 'LXGW WenKai TC';
        let currentThemeName = 'sakura';

        // 字體載入狀態追蹤
        const fontLoadStatus = {
            'LXGW WenKai TC': false,
            'PopGothic': false,
            'JasonHandwriting1': false,
            'JasonHandwriting3': false,
            'JasonHandwriting5': false,
            'NaikaiFont': false,
            'Noto Serif TC': false,
            'Noto Sans TC': false
        };
        let currentToast = null;

        // 顯示字體載入提示
        function showFontLoadingToast(fontName) {
            hideToast();
            const toast = document.createElement('div');
            toast.className = 'font-loading-toast';
            toast.innerHTML = `<div class="font-loading-spinner"></div><span>正在下載「${fontName}」字體...</span>`;
            document.body.appendChild(toast);
            currentToast = toast;
            return toast;
        }

        // 隱藏提示
        function hideToast() {
            if (currentToast) {
                const toastToRemove = currentToast;
                toastToRemove.classList.add('hide');
                currentToast = null;
                setTimeout(() => {
                    if (toastToRemove && toastToRemove.parentNode) {
                        toastToRemove.parentNode.removeChild(toastToRemove);
                    }
                }, 300);
            }
        }

        // 顯示成功提示
        function showFontReadyToast(fontName) {
            hideToast();
            const toast = document.createElement('div');
            toast.className = 'font-loading-toast';
            toast.innerHTML = `<span>✓「${fontName}」載入完成</span>`;
            document.body.appendChild(toast);
            currentToast = toast;
            setTimeout(() => {
                if (currentToast === toast) {
                    hideToast();
                }
            }, 1500);
        }

        // 檢查字體是否已載入
        async function checkFontLoaded(fontFamily) {
            const cleanName = fontFamily.replace(/'/g, '');
            if (fontLoadStatus[cleanName]) return true;

            try {
                const loaded = await document.fonts.check(`16px "${cleanName}"`);
                if (loaded) {
                    fontLoadStatus[cleanName] = true;
                    return true;
                }
                return false;
            } catch (e) {
                return false;
            }
        }

        // 獲取字體顯示名稱
        function getFontDisplayName(fontFamily) {
            const names = {
                'LXGW WenKai TC': '霞鶩文楷',
                'PopGothic': '大波浪圓體',
                'JasonHandwriting1': '清松手寫體1',
                'JasonHandwriting3': '清松手寫體3',
                'JasonHandwriting5': '清松手寫體5',
                'NaikaiFont': '內海字體',
                'Noto Serif TC': '思源宋體',
                'Noto Sans TC': '思源黑體'
            };
            return names[fontFamily] || fontFamily;
        }

        async function changeFont(font) {
            const cleanFont = font.replace(/'/g, '');
            const displayName = getFontDisplayName(cleanFont);

            // 先檢查字體是否已載入
            const isLoaded = await checkFontLoaded(cleanFont);

            if (!isLoaded) {
                // 顯示載入中提示
                showFontLoadingToast(displayName);

                // 設定超時保護（最多顯示 2.5 秒）
                const timeoutId = setTimeout(() => {
                    currentFont = cleanFont;
                    document.getElementById('capture-area').style.fontFamily = font;
                    hideToast();
                }, 2500);

                try {
                    // 嘗試載入字體
                    await document.fonts.load(`16px "${cleanFont}"`);
                    clearTimeout(timeoutId);
                    fontLoadStatus[cleanFont] = true;

                    // 套用字體
                    currentFont = cleanFont;
                    document.getElementById('capture-area').style.fontFamily = font;

                    // 顯示成功提示
                    showFontReadyToast(displayName);
                } catch (e) {
                    clearTimeout(timeoutId);
                    // 即使載入失敗也嘗試套用（瀏覽器可能會 fallback）
                    currentFont = cleanFont;
                    document.getElementById('capture-area').style.fontFamily = font;
                    hideToast();
                }
            } else {
                // 字體已載入，直接套用
                currentFont = cleanFont;
                document.getElementById('capture-area').style.fontFamily = font;
            }
        }

        // 預先開始載入所有字體
        document.fonts.ready.then(() => {
            // 標記已載入的字體
            Object.keys(fontLoadStatus).forEach(font => {
                if (document.fonts.check(`16px "${font}"`)) {
                    fontLoadStatus[font] = true;
                }
            });
        });

        // 處理鍵盤彈出時的滾動 - 確保輸入區域可見
        const answerEditor = document.getElementById('answer-editor');
        answerEditor.addEventListener('focus', () => {
            // 短暫延遲等待鍵盤完全彈出
            setTimeout(() => {
                answerEditor.scrollIntoView({ behavior: 'smooth', block: 'center' });
            }, 300);
        });

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
            // 更新背景裝飾
            currentThemeName = themeName;
            renderBgDecorations(themeName);
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

        // 背景顏色映射 (用於導出)
        const themeColors = {
            'theme-sakura': ['#fff0f3', '#ffd6e0'],
            'theme-british': ['#1a2e1a', '#1a2e1a'],
            'theme-stage': ['#0d0618', '#1a0d2e'],
            'theme-clover': ['#e8f5e9', '#a5d6a7'],
            'theme-rainbow': ['#ff9a9e', '#a1c4fd'],
            'theme-sunflower': ['#ffd773', '#fbc02d'],
            'theme-starry': ['#0d1117', '#1a1f29']
        };

        // 繪製圓角矩形
        function roundRect(ctx, x, y, w, h, r) {
            ctx.beginPath();
            ctx.moveTo(x + r, y);
            ctx.lineTo(x + w - r, y);
            ctx.quadraticCurveTo(x + w, y, x + w, y + r);
            ctx.lineTo(x + w, y + h - r);
            ctx.quadraticCurveTo(x + w, y + h, x + w - r, y + h);
            ctx.lineTo(x + r, y + h);
            ctx.quadraticCurveTo(x, y + h, x, y + h - r);
            ctx.lineTo(x, y + r);
            ctx.quadraticCurveTo(x, y, x + r, y);
            ctx.closePath();
        }

        // 文字換行處理
        function wrapText(ctx, text, maxWidth) {
            const lines = [];
            const paragraphs = text.split('\n');
            for (const para of paragraphs) {
                if (!para) { lines.push(''); continue; }
                let line = '';
                for (const char of para) {
                    const testLine = line + char;
                    if (ctx.measureText(testLine).width > maxWidth && line) {
                        lines.push(line);
                        line = char;
                    } else {
                        line = testLine;
                    }
                }
                if (line) lines.push(line);
            }
            return lines;
        }

        // 繪製愛心
        function drawHeart(ctx, x, y, size, color) {
            ctx.save();
            ctx.translate(x, y);
            ctx.scale(size / 20, size / 20);
            ctx.beginPath();
            ctx.moveTo(0, -5);
            ctx.bezierCurveTo(-5, -15, -15, -5, 0, 10);
            ctx.bezierCurveTo(15, -5, 5, -15, 0, -5);
            ctx.closePath();
            ctx.fillStyle = color;
            ctx.fill();
            ctx.restore();
        }

        // 繪製四葉草（無莖，只有4片葉子）
        function drawClover(ctx, x, y, size, color) {
            ctx.save();
            ctx.translate(x, y);
            ctx.fillStyle = color;
            for (let i = 0; i < 4; i++) {
                ctx.beginPath();
                ctx.ellipse(0, -size * 0.4, size * 0.35, size * 0.5, 0, 0, Math.PI * 2);
                ctx.fill();
                ctx.rotate(Math.PI / 2);
            }
            ctx.restore();
        }

        // 繪製向日葵
        function drawSunflower(ctx, x, y, size, petalColor, centerColor) {
            ctx.save();
            ctx.translate(x, y);
            // 花瓣
            ctx.fillStyle = petalColor;
            for (let i = 0; i < 12; i++) {
                ctx.beginPath();
                ctx.ellipse(0, -size * 0.6, size * 0.15, size * 0.4, 0, 0, Math.PI * 2);
                ctx.fill();
                ctx.rotate(Math.PI / 6);
            }
            // 花心
            ctx.beginPath();
            ctx.arc(0, 0, size * 0.35, 0, Math.PI * 2);
            ctx.fillStyle = centerColor;
            ctx.fill();
            ctx.restore();
        }

        // 核心儲存邏輯 - 純 Canvas 繪製
        function handleSave() {
            if (!isDrawn) { showAlert("請先抽取題目！"); return; }
            const answerText = document.getElementById('answer-editor').innerText.trim();
            if (!answerText) { showAlert("請寫下你的心情記錄。"); return; }

            const btn = document.getElementById('save-btn');
            const originalText = btn.innerText;
            btn.innerText = "生成中...";
            btn.disabled = true;

            try {
                const captureArea = document.getElementById('capture-area');
                const bodyClass = document.getElementById('full-body').className;
                const colors = themeColors[bodyClass] || ['#ffffff', '#f0f0f0'];
                const isSquare = captureArea.classList.contains('ratio-square');

                // 設置畫布尺寸
                const outputWidth = 1080;
                const outputHeight = isSquare ? 1080 : 1920;

                const canvas = document.createElement('canvas');
                canvas.width = outputWidth;
                canvas.height = outputHeight;
                const ctx = canvas.getContext('2d');

                // 1. 繪製漸變背景
                if (bodyClass === 'theme-rainbow') {
                    // 彩虹漸變特殊處理
                    const rainbowGradient = ctx.createLinearGradient(0, 0, outputWidth, outputHeight);
                    rainbowGradient.addColorStop(0, '#ff9a9e');
                    rainbowGradient.addColorStop(0.2, '#fad0c4');
                    rainbowGradient.addColorStop(0.4, '#ffecd2');
                    rainbowGradient.addColorStop(0.6, '#a1c4fd');
                    rainbowGradient.addColorStop(0.8, '#c2e9fb');
                    rainbowGradient.addColorStop(1, '#d4fc79');
                    ctx.fillStyle = rainbowGradient;
                    ctx.fillRect(0, 0, outputWidth, outputHeight);
                } else if (bodyClass === 'theme-stage') {
                    // 舞台仿真聚光燈光束效果
                    ctx.fillStyle = '#0d0618';
                    ctx.fillRect(0, 0, outputWidth, outputHeight);

                    // 繪製光束函數
                    function drawSpotlightBeam(ctx, startX, startY, endX, endY, topWidth, bottomWidth, color1, color2, opacity) {
                        ctx.save();
                        ctx.beginPath();
                        ctx.moveTo(startX - topWidth/2, startY);
                        ctx.lineTo(startX + topWidth/2, startY);
                        ctx.lineTo(endX + bottomWidth/2, endY);
                        ctx.lineTo(endX - bottomWidth/2, endY);
                        ctx.closePath();

                        const beamGrad = ctx.createLinearGradient(startX, startY, endX, endY);
                        beamGrad.addColorStop(0, color1.replace(')', `, ${opacity * 1.2})`).replace('rgba', 'rgba').replace('rgb', 'rgba'));
                        beamGrad.addColorStop(0.3, color1.replace(')', `, ${opacity})`).replace('rgba', 'rgba').replace('rgb', 'rgba'));
                        beamGrad.addColorStop(0.7, color2.replace(')', `, ${opacity * 0.4})`).replace('rgba', 'rgba').replace('rgb', 'rgba'));
                        beamGrad.addColorStop(1, 'rgba(0,0,0,0)');
                        ctx.fillStyle = beamGrad;
                        ctx.fill();
                        ctx.restore();
                    }

                    // 中央主光束 - 明艷洋紅
                    drawSpotlightBeam(ctx, outputWidth * 0.5, 0, outputWidth * 0.5, outputHeight * 0.85,
                        outputWidth * 0.08, outputWidth * 0.55, 'rgba(255, 0, 127', 'rgba(255, 0, 127', 0.6);

                    // 左側光束 - 亮紫色
                    drawSpotlightBeam(ctx, outputWidth * 0.25, 0, outputWidth * 0.35, outputHeight * 0.75,
                        outputWidth * 0.06, outputWidth * 0.4, 'rgba(180, 0, 255', 'rgba(140, 0, 200', 0.5);

                    // 右側光束 - 亮粉色
                    drawSpotlightBeam(ctx, outputWidth * 0.75, 0, outputWidth * 0.65, outputHeight * 0.75,
                        outputWidth * 0.06, outputWidth * 0.4, 'rgba(255, 20, 180', 'rgba(255, 50, 150', 0.5);

                    // 頂部光源亮點
                    const lights = [
                        { x: 0.5, color: 'rgba(255, 0, 127, 0.95)', size: 45 },
                        { x: 0.25, color: 'rgba(180, 0, 255, 0.9)', size: 35 },
                        { x: 0.75, color: 'rgba(255, 20, 180, 0.9)', size: 35 }
                    ];
                    lights.forEach(light => {
                        // 外暈
                        const outerGlow = ctx.createRadialGradient(
                            outputWidth * light.x, 0, 0,
                            outputWidth * light.x, 0, light.size * 3
                        );
                        outerGlow.addColorStop(0, light.color);
                        outerGlow.addColorStop(0.3, light.color.replace(/[\d.]+\)$/, '0.5)'));
                        outerGlow.addColorStop(1, 'transparent');
                        ctx.fillStyle = outerGlow;
                        ctx.fillRect(0, 0, outputWidth, outputHeight * 0.2);

                        // 中心白芯
                        const coreGlow = ctx.createRadialGradient(
                            outputWidth * light.x, 0, 0,
                            outputWidth * light.x, 0, light.size * 0.8
                        );
                        coreGlow.addColorStop(0, 'rgba(255, 255, 255, 1)');
                        coreGlow.addColorStop(0.4, 'rgba(255, 255, 255, 0.8)');
                        coreGlow.addColorStop(1, 'transparent');
                        ctx.fillStyle = coreGlow;
                        ctx.fillRect(0, 0, outputWidth, outputHeight * 0.1);
                    });

                    // 環境氛圍光
                    const ambientGlow = ctx.createRadialGradient(
                        outputWidth / 2, outputHeight * 0.3, 0,
                        outputWidth / 2, outputHeight * 0.3, outputHeight * 0.6
                    );
                    ambientGlow.addColorStop(0, 'rgba(255, 0, 127, 0.08)');
                    ambientGlow.addColorStop(0.5, 'rgba(140, 0, 200, 0.05)');
                    ambientGlow.addColorStop(1, 'transparent');
                    ctx.fillStyle = ambientGlow;
                    ctx.fillRect(0, 0, outputWidth, outputHeight);
                } else if (bodyClass === 'theme-sunflower') {
                    // 向日葵漸變 + 光暈
                    const sunGradient = ctx.createLinearGradient(0, 0, outputWidth, outputHeight);
                    sunGradient.addColorStop(0, '#ffd773');
                    sunGradient.addColorStop(1, '#fbc02d');
                    ctx.fillStyle = sunGradient;
                    ctx.fillRect(0, 0, outputWidth, outputHeight);
                    const sunGlow = ctx.createRadialGradient(0, 0, 0, 0, 0, outputHeight * 0.7);
                    sunGlow.addColorStop(0, 'rgba(255,255,255,0.3)');
                    sunGlow.addColorStop(1, 'transparent');
                    ctx.fillStyle = sunGlow;
                    ctx.fillRect(0, 0, outputWidth, outputHeight);
                } else {
                    const gradient = ctx.createLinearGradient(0, 0, outputWidth, outputHeight);
                    gradient.addColorStop(0, colors[0]);
                    gradient.addColorStop(1, colors[1]);
                    ctx.fillStyle = gradient;
                    ctx.fillRect(0, 0, outputWidth, outputHeight);
                }

                // 2. 繪製各主題裝飾元素
                if (bodyClass === 'theme-sakura') {
                    // 櫻花主題：散落愛心
                    for (let i = 0; i < 25; i++) {
                        const x = Math.random() * outputWidth;
                        const y = Math.random() * outputHeight;
                        const size = Math.random() * 25 + 15;
                        const opacity = Math.random() * 0.3 + 0.2;
                        drawHeart(ctx, x, y, size, `rgba(255, 183, 197, ${opacity})`);
                    }
                } else if (bodyClass === 'theme-british') {
                    // 英倫主題：金色斜線格紋
                    ctx.strokeStyle = 'rgba(212, 175, 55, 0.15)';
                    ctx.lineWidth = 2;
                    const spacing = 80;
                    for (let i = -outputHeight; i < outputWidth + outputHeight; i += spacing) {
                        ctx.beginPath();
                        ctx.moveTo(i, 0);
                        ctx.lineTo(i + outputHeight, outputHeight);
                        ctx.stroke();
                    }
                } else if (bodyClass === 'theme-clover') {
                    // 四葉草主題：不同大小散落四葉草（無莖，不重疊）
                    const placedClovers = [];
                    const cloverSizes = [
                        { count: 4, minSize: 45, maxSize: 60, opacity: 0.12 },   // 大
                        { count: 5, minSize: 30, maxSize: 45, opacity: 0.10 },   // 中
                        { count: 6, minSize: 18, maxSize: 30, opacity: 0.08 }    // 小
                    ];
                    cloverSizes.forEach(config => {
                        for (let i = 0; i < config.count; i++) {
                            let x, y, size, attempts = 0;
                            do {
                                x = Math.random() * outputWidth;
                                y = Math.random() * outputHeight;
                                size = Math.random() * (config.maxSize - config.minSize) + config.minSize;
                                attempts++;
                            } while (attempts < 50 && placedClovers.some(p => Math.hypot(p.x - x, p.y - y) < (p.size + size) * 1.2));
                            if (attempts < 50) {
                                placedClovers.push({ x, y, size });
                                drawClover(ctx, x, y, size, `rgba(46, 125, 50, ${config.opacity})`);
                            }
                        }
                    });
                } else if (bodyClass === 'theme-sunflower') {
                    // 向日葵主題：不同���小向日葵裝飾（不重疊）
                    const placedSunflowers = [];
                    const sunflowerSizes = [
                        { count: 3, minSize: 90, maxSize: 130, petalOpacity: 0.12, centerOpacity: 0.15 },   // 大
                        { count: 4, minSize: 55, maxSize: 90, petalOpacity: 0.10, centerOpacity: 0.12 },    // 中
                        { count: 5, minSize: 30, maxSize: 55, petalOpacity: 0.08, centerOpacity: 0.10 }     // 小
                    ];
                    sunflowerSizes.forEach(config => {
                        for (let i = 0; i < config.count; i++) {
                            let x, y, size, attempts = 0;
                            do {
                                x = Math.random() * outputWidth;
                                y = Math.random() * outputHeight;
                                size = Math.random() * (config.maxSize - config.minSize) + config.minSize;
                                attempts++;
                            } while (attempts < 50 && placedSunflowers.some(p => Math.hypot(p.x - x, p.y - y) < (p.size + size) * 1.3));
                            if (attempts < 50) {
                                placedSunflowers.push({ x, y, size });
                                drawSunflower(ctx, x, y, size, `rgba(230, 81, 0, ${config.petalOpacity})`, `rgba(62, 39, 35, ${config.centerOpacity})`);
                            }
                        }
                    });
                } else if (bodyClass === 'theme-starry') {
                    // 星空主題：閃爍星星
                    for (let i = 0; i < 180; i++) {
                        const x = Math.random() * outputWidth;
                        const y = Math.random() * outputHeight;
                        const r = Math.random() * 2.5 + 0.5;
                        const opacity = Math.random() * 0.7 + 0.3;
                        ctx.beginPath();
                        ctx.arc(x, y, r, 0, Math.PI * 2);
                        ctx.fillStyle = `rgba(255, 255, 255, ${opacity})`;
                        ctx.fill();
                    }
                    // 少量大亮星
                    for (let i = 0; i < 8; i++) {
                        const x = Math.random() * outputWidth;
                        const y = Math.random() * outputHeight;
                        ctx.beginPath();
                        ctx.arc(x, y, 4, 0, Math.PI * 2);
                        ctx.fillStyle = 'rgba(255, 255, 255, 0.9)';
                        ctx.fill();
                    }
                }
                // 彩虹主題不需要額外裝飾，六色漸變背景已足夠

                // 3. 繪製卡片
                const cardWidth = outputWidth * 0.85;
                const cardHeight = isSquare ? cardWidth : cardWidth * (16/9);
                const cardX = (outputWidth - cardWidth) / 2;
                const cardY = (outputHeight - cardHeight) / 2;
                const cardRadius = 60;
                const cardPadding = 60;

                // 卡片陰影
                ctx.shadowColor = 'rgba(0,0,0,0.25)';
                ctx.shadowBlur = 60;
                ctx.shadowOffsetY = 30;

                // 卡片背景
                roundRect(ctx, cardX, cardY, cardWidth, cardHeight, cardRadius);
                ctx.fillStyle = 'rgba(255, 255, 255, 0.9)';
                ctx.fill();

                // 英倫主題金色邊框
                if (bodyClass === 'theme-british') {
                    ctx.strokeStyle = '#d4af37';
                    ctx.lineWidth = 6;
                    ctx.stroke();
                }

                // 重置陰影
                ctx.shadowColor = 'transparent';
                ctx.shadowBlur = 0;
                ctx.shadowOffsetY = 0;

                // 3. 繪製內容
                const contentX = cardX + cardPadding;
                const contentWidth = cardWidth - cardPadding * 2;
                let currentY = cardY + cardPadding;

                // 類別標籤
                const category = document.getElementById('category-badge').innerText;
                ctx.font = `bold 24px "${currentFont}", sans-serif`;
                ctx.fillStyle = 'rgba(0,0,0,0.4)';
                ctx.letterSpacing = '4px';
                ctx.fillText(category, contentX, currentY + 20);
                currentY += 50;

                // 問題文字
                const question = document.getElementById('question-text').innerText;
                ctx.font = `bold 48px "${currentFont}", sans-serif`;
                ctx.fillStyle = '#111';
                const questionLines = wrapText(ctx, question, contentWidth);
                for (const line of questionLines) {
                    currentY += 60;
                    ctx.fillText(line, contentX, currentY);
                }
                currentY += 50;

                // 答案文字
                ctx.font = `normal 42px "${currentFont}", sans-serif`;
                ctx.fillStyle = '#111';
                const answerLines = wrapText(ctx, answerText, contentWidth);
                const lineHeight = 75;
                for (const line of answerLines) {
                    currentY += lineHeight;
                    ctx.fillText(line, contentX, currentY);
                }

                // 4. 底部信息
                const bottomY = cardY + cardHeight - cardPadding;

                // 日期
                ctx.font = `normal 24px "${currentFont}", sans-serif`;
                ctx.fillStyle = 'rgba(0,0,0,0.4)';
                ctx.fillText(document.getElementById('current-date').innerText, contentX, bottomY);

                // 品牌
                ctx.textAlign = 'right';
                ctx.font = `bold 28px "${currentFont}", sans-serif`;
                ctx.fillStyle = 'rgba(0,0,0,0.7)';
                ctx.fillText('StarDiary', cardX + cardWidth - cardPadding, bottomY - 24);
                ctx.font = `normal 22px "${currentFont}", sans-serif`;
                ctx.fillStyle = 'rgba(0,0,0,0.5)';
                ctx.fillText('by Grafittiii', cardX + cardWidth - cardPadding, bottomY);
                ctx.textAlign = 'left';

                // 5. 下載圖片
                const link = document.createElement('a');
                link.download = `StarDiary_${Date.now()}.png`;
                link.href = canvas.toDataURL('image/png');
                document.body.appendChild(link);
                link.click();
                document.body.removeChild(link);

                btn.innerText = "儲存成功！";
                setTimeout(() => { btn.innerText = originalText; btn.disabled = false; }, 2000);
            } catch (err) {
                console.error("Save Error:", JSON.stringify(err.message || err));
                showAlert("儲存失敗：" + (err.message || "未知錯誤"));
                btn.innerText = originalText;
                btn.disabled = false;
            }
        }

        document.getElementById('current-date').innerText = new Date().toLocaleDateString();

        // === 背景裝飾繪製（與儲存圖片使用相同參數） ===
        const bgCanvas = document.getElementById('bgCanvas');
        const bgCtx = bgCanvas.getContext('2d');

        // 統一的裝飾參數配置
        const decorConfig = {
            clover: [
                { count: 4, minSize: 45, maxSize: 60, opacity: 0.12 },
                { count: 5, minSize: 30, maxSize: 45, opacity: 0.10 },
                { count: 6, minSize: 18, maxSize: 30, opacity: 0.08 }
            ],
            sunflower: [
                { count: 3, minSize: 90, maxSize: 130, petalOpacity: 0.12, centerOpacity: 0.15 },
                { count: 4, minSize: 55, maxSize: 90, petalOpacity: 0.10, centerOpacity: 0.12 },
                { count: 5, minSize: 30, maxSize: 55, petalOpacity: 0.08, centerOpacity: 0.10 }
            ]
        };

        function resizeBgCanvas() {
            bgCanvas.width = window.innerWidth * window.devicePixelRatio;
            bgCanvas.height = window.innerHeight * window.devicePixelRatio;
            bgCtx.scale(window.devicePixelRatio, window.devicePixelRatio);
        }

        function drawBgClover(ctx, x, y, size, color) {
            ctx.save();
            ctx.translate(x, y);
            ctx.fillStyle = color;
            for (let i = 0; i < 4; i++) {
                ctx.beginPath();
                ctx.ellipse(0, -size * 0.4, size * 0.35, size * 0.5, 0, 0, Math.PI * 2);
                ctx.fill();
                ctx.rotate(Math.PI / 2);
            }
            ctx.restore();
        }

        function drawBgSunflower(ctx, x, y, size, petalColor, centerColor) {
            ctx.save();
            ctx.translate(x, y);
            ctx.fillStyle = petalColor;
            for (let i = 0; i < 12; i++) {
                ctx.beginPath();
                ctx.ellipse(0, -size * 0.6, size * 0.15, size * 0.4, 0, 0, Math.PI * 2);
                ctx.fill();
                ctx.rotate(Math.PI / 6);
            }
            ctx.beginPath();
            ctx.arc(0, 0, size * 0.35, 0, Math.PI * 2);
            ctx.fillStyle = centerColor;
            ctx.fill();
            ctx.restore();
        }

        function renderBgDecorations(themeName) {
            resizeBgCanvas();
            bgCtx.clearRect(0, 0, bgCanvas.width, bgCanvas.height);

            const w = window.innerWidth;
            const h = window.innerHeight;

            if (themeName === 'clover') {
                const placed = [];
                decorConfig.clover.forEach(config => {
                    for (let i = 0; i < config.count; i++) {
                        let x, y, size, attempts = 0;
                        do {
                            x = Math.random() * w;
                            y = Math.random() * h;
                            size = Math.random() * (config.maxSize - config.minSize) + config.minSize;
                            attempts++;
                        } while (attempts < 50 && placed.some(p => Math.hypot(p.x - x, p.y - y) < (p.size + size) * 1.2));
                        if (attempts < 50) {
                            placed.push({ x, y, size });
                            drawBgClover(bgCtx, x, y, size, `rgba(46, 125, 50, ${config.opacity})`);
                        }
                    }
                });
            } else if (themeName === 'sunflower') {
                const placed = [];
                decorConfig.sunflower.forEach(config => {
                    for (let i = 0; i < config.count; i++) {
                        let x, y, size, attempts = 0;
                        do {
                            x = Math.random() * w;
                            y = Math.random() * h;
                            size = Math.random() * (config.maxSize - config.minSize) + config.minSize;
                            attempts++;
                        } while (attempts < 50 && placed.some(p => Math.hypot(p.x - x, p.y - y) < (p.size + size) * 1.3));
                        if (attempts < 50) {
                            placed.push({ x, y, size });
                            drawBgSunflower(bgCtx, x, y, size, `rgba(230, 81, 0, ${config.petalOpacity})`, `rgba(62, 39, 35, ${config.centerOpacity})`);
                        }
                    }
                });
            }
            // 其他主題不需要額外裝飾
        }

        // 初始化背景裝飾
        renderBgDecorations(currentThemeName);

        // 監聽視窗大小變化
        window.addEventListener('resize', () => renderBgDecorations(currentThemeName));
    </script>
</body>
</html>
