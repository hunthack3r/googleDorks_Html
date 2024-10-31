# googleDorks_Html


```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dark Hacker Theme - Bug Bounty & Dorks</title>
    <style>
        body {
            font-family: 'Courier New', monospace;
            max-width: 800px;
            margin: 0 auto;
            background-color: #000000;
            color: #33FF33;
            padding: 20px;
            box-sizing: border-box;
        }
        h1, h2, h3 {
            color: #33FF33;
            text-align: center;
            margin-bottom: 20px;
            text-transform: uppercase;
        }
        label {
            font-size: 1.2em;
            color: #33FF33;
        }
        input, button {
            font-size: 1em;
            padding: 5px;
            margin-left: 5px;
            background-color: #000000;
            color: #33FF33;
            border: 1px solid #33FF33;
        }
        button {
            cursor: pointer;
            transition: 0.2s;
        }
        button:hover {
            background-color: #33FF33;
            color: #000000;
        }
        ul {
            list-style-type: none;
            padding: 0;
        }
        li {
            margin-bottom: 10px;
        }
        a {
            text-decoration: none;
            color: #33FF33;
        }
        a:hover {
            text-decoration: underline;
        }
        .profile-container {
            border-top: 1px solid #33FF33;
            padding-top: 20px;
            margin-top: 20px;
        }
        .icon-links img {
            margin-right: 10px;
        }
        .stats-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-top: 20px;
        }
        #tooltip {
            position: absolute;
            background-color: #000000;
            color: #33FF33;
            padding: 5px;
            border: 1px solid #33FF33;
            border-radius: 3px;
            display: none;
        }
    </style>
</head>
<body>
    <h1>Welcome to DedCrowd's Bug Bounty Toolkit</h1>
    <h3>Exploit Google Dorks for Maximum Impact</h3>

    <p>
        <a href="https://twitter.com/recursivedefer" target="_blank">
            <img src="https://img.shields.io/twitter/follow/recursivedefer?logo=twitter&style=for-the-badge&color=33FF33" alt="Twitter Follow Badge">
        </a>
        <a href="https://github.com/hunthack3r" target="_blank" style="color: #33FF33; text-decoration: none; font-weight: bold;">GitHub Repository</a>
    </p>

    <label for="domainInput">Target Domain:</label>
    <input type="text" id="domainInput" placeholder="example.com" oninput="updateDomain()">
    <div id="tooltip" class="hidden">Enter multiple domains separated by a comma. e.g., example1.com, example2.com</div>

    <ul id="dorkList"></ul>

    <section class="profile-container">
        <h2>Essential Resources</h2>
        <ul class="link-list">
            <li><a href="https://github.com/hunthack3r" target="_blank">Advanced Google Dorks</a></li>
            <li><a href="https://thegrayarea.tech/5-google-dorks-every-hacker-needs-to-know-fed21022a906" target="_blank">Top 5 Dorks for Hackers</a></li>
            <li><a href="https://infosecwriteups.com/uncover-hidden-gems-in-the-cloud-with-google-dorks-8621e56a329d" target="_blank">Hidden Gems with Dorks</a></li>
            <li><a href="https://infosecwriteups.com/10-google-dorks-for-sensitive-data-9454b09edc12" target="_blank">Dorks for Sensitive Data</a></li>
        </ul>

        <h3>Get in Touch</h3>
        <p class="icon-links">
            <a href="https://twitter.com/recursivedefer" target="_blank"><img src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/twitter.svg" alt="Twitter" height="30" width="40"></a>
            <a href="https://linkedin.com/in/hacker--" target="_blank"><img src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="LinkedIn" height="30" width="40"></a>
            <a href="https://kaggle.com/akifsayin" target="_blank"><img src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/kaggle.svg" alt="Kaggle" height="30" width="40"></a>
            <a href="https://instagram.com/4kif_x" target="_blank"><img src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/instagram.svg" alt="Instagram" height="30" width="40"></a>
        </p>

        <h3>Languages & Tools</h3>
        <p class="icon-links">
            <img src="https://cdn.worldvectorlogo.com/logos/arduino-1.svg" alt="Arduino" width="40" height="40">
            <img src="https://www.vectorlogo.zone/logos/gnu_bash/gnu_bash-icon.svg" alt="Bash" width="40" height="40">
            <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg" alt="Docker" width="40" height="40">
            <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="Python" width="40" height="40">
        </p>

        <div class="stats-container">
            <img src="https://github-readme-stats.vercel.app/api/top-langs?username=hunthack3r&show_icons=true&locale=en&layout=compact" alt="Top Languages">
            <img src="https://github-readme-stats.vercel.app/api?username=hunthack3r&show_icons=true&locale=en" alt="GitHub Stats">
            <img src="https://github-readme-streak-stats.herokuapp.com/?user=hunthack3r&" alt="GitHub Streak Stats">
        </div>
    </section>

    <script>
        const domainInput = document.getElementById('domainInput');
        const tooltip = document.getElementById('tooltip');

        domainInput.addEventListener('mouseover', function() {
            tooltip.style.display = 'block';
            tooltip.style.left = domainInput.offsetLeft + 'px';
            tooltip.style.top = (domainInput.offsetTop + domainInput.offsetHeight + 5) + 'px';
        });

        domainInput.addEventListener('mouseout', function() {
            tooltip.style.display = 'none';
        });

        let originalDorks = [];
        
        async function fetchDorks() {
            const url = "https://raw.githubusercontent.com/TakSec/google-dorks-bug-bounty/main/README.md";
            const response = await fetch(url);
            const text = await response.text();

            const dorkList = document.getElementById("dorkList");
            const regex = /(?:^### (.+)|```([^`]+)```)/gm;
            let match;
            let title = '';
            let firstDork = true;

            while ((match = regex.exec(text)) !== null) {
                if (match[1]) {
                    title = match[1];
                } else if (match[2]) {
                    const dork = match[2].trim();
                    originalDorks.push(dork);
                    const listItem = createDorkListItem(dork, title);
                    dorkList.appendChild(listItem);
                }
            }
            filterDorks();
        }
            
        let prevTitle = '';

        function createDorkListItem(dork, description) {
            const googleLink = `https://www.google.com/search?q=${encodeURIComponent(dork)}`;
            const listItem = document.createElement("li");

            if (description && description !== prevTitle) {
                const desc = document.createElement("p");
                desc.textContent = description;
                desc.classList.add("description");
                listItem.appendChild(desc);
                prevTitle = description;
            }

            const link = document.createElement("a");
            link.href = googleLink;
            link.textContent = dork;
            link.classList.add("dorkLink");
            link.target = "_blank";

            listItem.appendChild(link);
            return listItem;
        }

        function updateDomain() {
            const domains = domainInput.value.split(",").map(domain => domain.trim());
        
            if (domains.length === 0) return;

            const dorkLinks = document.querySelectorAll(".dorkLink");
            dorkLinks.forEach((link, index) => {
                let originalDork = originalDorks[index];
                if (originalDork.includes("Drupal")) return;

                if (/site:"?example\[?\.\]?com"?/i.test(originalDork)) {
                    const joinedDomains = domains.map(d => `site:${d}`).join(" | ");
                    originalDork = originalDork.replace(/site:"?example\[?\.\]?com"?/gi, joinedDomains);
                } else if (/["']example\[?\.\]?com["']/i.test(originalDork)) {
                    const joinedDomains = domains.map(d => `"${d}"`).join(" | ");
                    originalDork = originalDork.replace(/["']example\[?\.\]?com["']/gi, joinedDomains);
                }

                const intextPattern = /intext:"example\.com"/gi;
                if (intextPattern.test(originalDork)) {
                    const joinedDomains = domains.map(d => `intext:"${d}"`).join(" | ");
                    originalDork = originalDork.replace(intextPattern, joinedDomains);
                }

                link.textContent = originalDork;
                link.href = `https://www.google.com/search?q=${encodeURIComponent(originalDork)}`;
            });
        }
        
        fetchDorks();

        function filterDorks() {
            const dorkItems = document.querySelectorAll("#dorkList li");
            dorkItems.forEach(item => {
                if (item.textContent.toLowerCase().includes("omit")) {
                    item.style.display = "none";
                }
            });
        }
    </script>
</body>
</html>


```
