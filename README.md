<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>YouTube टैग जनरेटर</title>
    <style>
        /* Loading Screen Styling */
        #loading-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #fff;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 24px;
            color: #ff0000;
            z-index: 1000;
            flex-direction: column;
        }

        /* Instagram Link Styling */
        .instagram-link {
            position: fixed;
            top: 20px;
            right: 20px;
            background: #E1306C;
            color: white;
            padding: 8px 15px;
            border-radius: 5px;
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        /* Main Container Styling */
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            min-height: 100vh;
            position: relative;
        }
        .container {
            background-color: #fff;
            padding: 25px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
            max-width: 600px;
            width: 100%;
            display: none;
        }
        h1 {
            color: #ff0000;
            margin-bottom: 25px;
            text-align: center;
        }
        .input-group {
            margin-bottom: 25px;
        }
        input[type="text"] {
            width: 100%;
            padding: 12px;
            border: 2px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }
        button {
            width: 100%;
            padding: 12px;
            background-color: #ff0000;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #cc0000;
        }
        .tags-container {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            margin-top: 25px;
        }
        .tag {
            background-color: #f0f0f0;
            color: #333;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 14px;
            border: 1px solid #ddd;
            cursor: pointer;
            transition: all 0.3s;
        }
        .tag:hover {
            background-color: #ddd;
            transform: scale(1.05);
        }
    </style>
</head>
<body>

<!-- Loading Screen -->
<div id="loading-screen">
    <div>टैग जनरेट हो रहे हैं...</div>
    <div style="font-size:14px;margin-top:10px;">Developed by: royal_kushwaha2</div>
</div>

<!-- Instagram Link -->
<a href="https://www.instagram.com/royal_kushwaha2" class="instagram-link" target="_blank">
    <img src="https://upload.wikimedia.org/wikipedia/commons/a/a5/Instagram_icon.png" width="20" height="20" alt="Instagram">
    royal_kushwaha2
</a>

<!-- Main Container -->
<div class="container">
    <h1>YouTube टैग जनरेटर</h1>
    <div class="input-group">
        <input type="text" id="keyword" placeholder="विषय-शब्द दर्ज करें..." autofocus>
    </div>
    <button onclick="generateTags()">टैग जनरेट करें</button>
    <div class="tags-container" id="tags"></div>
</div>

<script>
    // Page load पर सही तरीके से initialize
    window.addEventListener('load', () => {
        setTimeout(() => {
            document.getElementById('loading-screen').style.display = 'none';
            document.querySelector('.container').style.display = 'block';
            document.getElementById('keyword').focus();
        }, 2000);
    });

    // Tags generate function
    function generateTags() {
        const keyword = document.getElementById('keyword').value.trim();
        const tagsContainer = document.getElementById('tags');
        
        if (!keyword) {
            alert('⚠️ कृपया कोई कीवर्ड दर्ज करें');
            return;
        }

        tagsContainer.innerHTML = '';
        
        // Updated Trending Words 2024
        const trendingWords = [
            "2024", "latest update", "viral trends", "breaking news", 
            "tech review", "hindi tutorial", "top hacks", "secret tips",
            "beginner guide", "exclusive", "unboxing", "comparison",
            "life hacks", "money saving", "pro tricks", "latest features"
        ];

        // Unique tags generate करने के लिए
        const uniqueTags = new Set();
        while(uniqueTags.size < 10) {
            const randomWord = trendingWords[Math.floor(Math.random()*trendingWords.length)];
            uniqueTags.add(`${keyword} ${randomWord}`);
        }

        // Tags create करें
        uniqueTags.forEach(tag => {
            const tagElement = document.createElement('div');
            tagElement.className = 'tag';
            tagElement.textContent = tag;
            tagElement.onclick = () => copyToClipboard(tag);
            tagsContainer.appendChild(tagElement);
        });
    }

    // Clipboard copy function
    function copyToClipboard(text) {
        navigator.clipboard.writeText(text)
            .then(() => {
                alert('✅ कॉपी हो गया: ' + text);
            })
            .catch(() => {
                alert('❌ कॉपी करने में त्रुटि!');
            });
    }
</script>

</body>
</html>
