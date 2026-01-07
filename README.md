# StarDiary-beta-
A beta version to memorise and record your moment with your stars (artistes/idols etc)

<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>StarDiary by Grafittiii</title>
    <link href="https://fonts.googleapis.com/css2?family=LXGW+WenKai+TC:wght@400;700&family=Noto+Sans+TC:wght@400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-font: 'LXGW WenKai TC', sans-serif;
            --glass: rgba(255, 255, 255, 0.2);
            --glass-border: rgba(255, 255, 255, 0.3);
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }
        body {
            font-family: var(--primary-font);
            height: 100vh; width: 100vw; overflow: hidden;
            display: flex; align-items: center; justify-content: center;
            transition: all 0.6s ease;
        }

        /* --- 背景模板 --- */
        .bg-sakura { background: linear-gradient(135deg, #fff0f3, #ffd6e0); color: #4a4a4a; }
        .bg-british { background: #1a2e1a; color: #f5f5dc; }
        .bg-stage { background: #1a0b2e; color: #fff; }
        .bg-clover { background: #e8f5e9; color: #2e7d32; }
        .bg-rainbow { background: linear-gradient(90deg, #ff9a9e, #fad0c4, #a1c4fd, #d4fc79); color: #444; }
        .bg-sunflower { background: #fff9c4; color: #5d4037; }
        .bg-starry { background: #0d1117; color: #c9d1d9; }

        .app-wrapper {
            width: 100%; height: 100%; display: flex; flex-direction: column;
            align-items: center; justify-content: space-evenly; padding: 10px;
        }

        /* --- 編輯卡片 --- */
        .note-card {
            background: var(--glass); backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
            border: 1px solid var(--glass-border); border-radius: 20px; padding: 20px;
            width: 100%; max-width: 360px; position: relative;
            display: flex; flex-direction: column; box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }
        .ratio-9-16 { aspect-ratio: 9 / 16; height: 52vh; }
        .ratio-square { aspect-ratio: 1 / 1; height: 42vh; }

        .question-display { font-size: 18px; font-weight: 700; margin-bottom: 15px; min-height: 3em; border-bottom: 1px solid rgba(0,0,0,0.1); padding-bottom: 10px; }

        /* 可編輯區域 */
        #answer-editor {
            flex: 1; outline: none; font-size: 16px; line-height: 1.6;
            overflow-y: auto; text-align: left;
        }
        #answer-editor:empty:before { content: "在此寫下妳的回憶..."; opacity: 0.5; }

        /* --- 工具欄 (格式/字體) --- */
        .toolbar {
            display: flex; gap: 5px; margin-bottom: 10px; width: 100%; max-width: 360px;
            overflow-x: auto; padding: 5px 0;
        }
        .tool-btn {
            background: var(--glass); border: 1px solid var(--glass-border);
            padding: 5px 10px; border-radius: 8px; font-size: 12px; cursor: pointer; color: inherit;
        }
        .font-select { background: var(--glass); border: 1px solid var(--glass-border); border-radius: 8px; font-size: 12px; padding: 5px; color: inherit; }

        /* --- 控制面板 --- */
        .control-panel { width: 100%; max-width: 380px; display: flex; flex-direction: column; gap: 8px; }
        .theme-selector { display: flex; justify-content: center; gap: 8px; margin-bottom: 5px; }
        .theme-dot { width: 22px; height: 22px; border-radius: 50%; cursor: pointer; border: 2px solid #fff; }

        .glass-btn {
            background: var(--glass); backdrop-filter: blur(10px); border: 1px solid var(--glass-border);
            padding: 12px; border-radius: 12px; font-size: 13px; font-weight: 700; cursor: pointer; color: inherit;
        }
        .btn-save { background: #222; color: #fff; border: none; }

        #exportCanvas { display: none; }
    </style>
</head>
<body class="bg-sakura">

    <div class="app-wrapper">
        <div class="toolbar">
            <button class="tool-btn" onclick="execCmd('bold')"><b>B</b></button>
            <button class="tool-btn" onclick="execCmd('italic')"><i>I</i></button>
            <button class="tool-btn" onclick="execCmd('underline')"><u>U</u></button>
            <select class="font-select" onchange="changeFont(this.value)">
                <option value="'LXGW WenKai TC'">霞鶩文楷 (手寫)</option>
                <option value="'Noto Sans TC'">思源黑體 (現代)</option>
                <option value="serif">標準明體 (經典)</option>
            </select>
        </div>

        <div class="card-container">
            <div id="capture-area" class="note-card ratio-9-16">
                <div class="question-display" id="question-text">妳準備好記錄關於他/她的瞬間了嗎？</div>
                <div id="answer-editor" contenteditable="true"></div>
                <div style="display: flex; justify-content: space-between; opacity: 0.6; font-size: 10px; margin-top: 10px;">
                    <div id="current-date"></div>
                    <div style="font-weight: 700;">StarDiary by Grafittiii</div>
                </div>
            </div>
        </div>

        <div class="control-panel">
            <div class="theme-selector">
                <div class="theme-dot" style="background:#ffd6e0" onclick="setTheme('sakura')"></div>
                <div class="theme-dot" style="background:#1a2e1a" onclick="setTheme('british')"></div>
                <div class="theme-dot" style="background:#4a148c" onclick="setTheme('stage')"></div>
                <div class="theme-dot" style="background:#a5d6a7" onclick="setTheme('clover')"></div>
                <div class="theme-dot" style="background:#ff9a9e" onclick="setTheme('rainbow')"></div>
                <div class="theme-dot" style="background:#fbc02d" onclick="setTheme('sunflower')"></div>
                <div class="theme-dot" style="background:#0d1117" onclick="setTheme('starry')"></div>
            </div>
            
            <button class="glass-btn" onclick="drawPrompt()">✦ 抽取題目 (他/她)</button>
            
            <div style="display: flex; gap: 8px;">
                <button class="glass-btn" style="flex:1" onclick="setRatio('ratio-9-16')">9:16</button>
                <button class="glass-btn" style="flex:1" onclick="setRatio('ratio-square')">1:1</button>
            </div>
            <button class="glass-btn btn-save" id="save-btn" onclick="handleSave()">📸 儲存圖片</button>
        </div>
    </div>

    <canvas id="exportCanvas"></canvas>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <script>
        const questions = [
            { cat: "初遇", txt: "第一次在螢幕上看到他/她時，心臟漏跳一拍的瞬間" },
            { cat: "日常", txt: "聽著他/她的歌，在那段難熬的日子裡得到的安慰" },
            { cat: "特質", txt: "他/她身上最吸引妳、讓妳想成為更好的人的優點" },
            { cat: "現場", txt: "如果能在現場對他/她說一句話，妳最想說什麼？" }
        ];

        let isDrawn = false;

        function execCmd(cmd) { document.execCommand(cmd, false, null); }
        
        function changeFont(font) {
            document.getElementById('answer-editor').style.fontFamily = font;
            document.getElementById('question-text').style.fontFamily = font;
        }

        function setTheme(t) { document.body.className = 'bg-' + t; }

        function drawPrompt() {
            const q = questions[Math.floor(Math.random() * questions.length)];
            document.getElementById('question-text').innerText = q.txt;
            isDrawn = true;
        }

        function setRatio(r) {
            const card = document.getElementById('capture-area');
            card.className = `note-card ${r}`;
        }

        async function handleSave() {
            if (!isDrawn) return alert("請先抽取題目！");
            const editor = document.getElementById('answer-editor');
            if (!editor.innerText.trim()) return alert("妳還沒寫下回憶呢！");

            const btn = document.getElementById('save-btn');
            btn.innerText = "生成中...";
            btn.disabled = true;

            try {
                // 使用 html2canvas 捕捉富文本樣式（粗體、斜體等）
                const canvas = await html2canvas(document.getElementById('capture-area'), {
                    backgroundColor: null,
                    scale: 3,
                    useCORS: true,
                    logging: false
                });

                const link = document.createElement('a');
                link.download = `StarDiary_${Date.now()}.png`;
                link.href = canvas.toDataURL("image/png");
                link.click();
                
                btn.innerText = "儲存成功！";
                setTimeout(() => { btn.innerText = "📸 儲存圖片"; btn.disabled = false; }, 2000);
            } catch (err) {
                alert("儲存失敗，請再試一次。文字已自動保留。");
                btn.disabled = false;
                btn.innerText = "📸 儲存圖片";
            }
        }

        document.getElementById('current-date').innerText = new Date().toLocaleDateString();
    </script>
</body>
</html>
