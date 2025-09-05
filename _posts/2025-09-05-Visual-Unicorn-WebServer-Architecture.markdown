---
layout: post
title:  "Visual-Unicorn-WebServer-Architecture"
date:   2025-09-05
categories: server
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Unicorn Web Server Architecture</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
            background: #0d1117;
            color: #c9d1d9;
            line-height: 1.6;
            padding: 20px;
            min-height: 100vh;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            background: #161b22;
            border: 1px solid #30363d;
            border-radius: 12px;
            padding: 30px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
        }

        h1 {
            text-align: center;
            color: #58a6ff;
            margin-bottom: 30px;
            font-size: 2.2em;
            font-weight: 600;
        }

        h1::before {
            content: "// ";
            color: #7c3aed;
        }

        .architecture {
            display: flex;
            flex-direction: column;
            gap: 25px;
            margin: 30px 0;
        }

        .layer {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            padding: 20px;
            border-radius: 8px;
            position: relative;
            border: 1px solid;
        }

        .clients-layer {
            background: #0f172a;
            border-color: #1e293b;
        }

        .load-balancer {
            background: #0f1419;
            border-color: #21262d;
        }

        .unicorn-layer {
            background: #0d1117;
            border-color: #30363d;
            flex-direction: column;
            gap: 20px;
        }

        .client {
            background: #1f2937;
            border: 1px solid #374151;
            color: #10b981;
            padding: 12px 18px;
            border-radius: 6px;
            font-family: 'Monaco', monospace;
            font-size: 0.9em;
            position: relative;
            transition: all 0.3s ease;
        }

        .client:hover {
            background: #374151;
            border-color: #10b981;
        }

        .client::before {
            content: "$ ";
            color: #7c3aed;
            font-weight: bold;
        }

        .lb {
            background: #1e293b;
            border: 1px solid #475569;
            color: #06b6d4;
            padding: 18px 28px;
            border-radius: 6px;
            font-family: 'Monaco', monospace;
            font-weight: 600;
            position: relative;
        }

        .lb::before {
            content: "nginx ";
            color: #22c55e;
        }

        .unicorn-server {
            border: 2px solid #7c3aed;
            border-radius: 8px;
            padding: 25px;
            background: #0d1117;
            width: 100%;
            max-width: 900px;
            position: relative;
        }

        .unicorn-server::before {
            content: "unicorn.rb";
            position: absolute;
            top: -12px;
            left: 20px;
            background: #0d1117;
            color: #7c3aed;
            padding: 0 8px;
            font-size: 0.8em;
        }

        .master-process {
            background: #dc2626;
            border: 1px solid #ef4444;
            color: #fecaca;
            padding: 15px 25px;
            border-radius: 6px;
            text-align: center;
            font-family: 'Monaco', monospace;
            margin-bottom: 20px;
            position: relative;
        }

        .master-process::before {
            content: "class Master < Process";
            display: block;
            font-size: 0.7em;
            opacity: 0.8;
            margin-bottom: 5px;
        }

        .workers-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 15px;
        }

        .worker {
            background: #1e293b;
            border: 1px solid #059669;
            color: #d1fae5;
            padding: 15px;
            border-radius: 6px;
            text-align: center;
            font-family: 'Monaco', monospace;
            position: relative;
            transition: all 0.3s ease;
        }

        .worker::before {
            content: "def handle_request";
            display: block;
            font-size: 0.6em;
            opacity: 0.7;
            margin-bottom: 5px;
        }

        .worker.crashed {
            background: #7f1d1d;
            border-color: #dc2626;
            color: #fecaca;
            animation: shake 0.5s;
        }

        .worker.crashed::before {
            content: "rescue => error";
            color: #fca5a5;
        }

        .socket-indicator {
            position: absolute;
            bottom: -8px;
            left: 50%;
            transform: translateX(-50%);
            background: #0891b2;
            border: 1px solid #0e7490;
            color: #e0f7fa;
            padding: 2px 8px;
            border-radius: 4px;
            font-size: 0.6em;
            font-family: 'Monaco', monospace;
        }

        .arrow {
            font-size: 1.5em;
            color: #6b7280;
            animation: pulse 2s infinite;
        }

        .feature-box {
            background: #0f172a;
            border: 1px solid #1e293b;
            padding: 25px;
            border-radius: 8px;
            margin: 25px 0;
            border-left: 4px solid #7c3aed;
        }

        .feature-title {
            font-weight: 600;
            color: #58a6ff;
            margin-bottom: 15px;
            font-size: 1.1em;
        }

        .feature-title::before {
            content: "# ";
            color: #7c3aed;
        }

        .comparison {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 25px;
            margin: 30px 0;
        }

        .comparison-box {
            padding: 25px;
            border-radius: 8px;
            border: 1px solid;
        }

        .good {
            background: #0f1419;
            border-color: #22c55e;
        }

        .good h3 {
            color: #22c55e;
        }

        .good h3::before {
            content: "✓ ";
            color: #16a34a;
        }

        .tradeoff {
            background: #1c1917;
            border-color: #f59e0b;
        }

        .tradeoff h3 {
            color: #f59e0b;
        }

        .tradeoff h3::before {
            content: "⚠ ";
            color: #d97706;
        }

        .comparison-box ul {
            list-style: none;
            margin-top: 15px;
        }

        .comparison-box li {
            margin: 8px 0;
            padding-left: 20px;
            position: relative;
            font-family: 'Monaco', monospace;
            font-size: 0.9em;
        }

        .good li::before {
            content: "→";
            position: absolute;
            left: 0;
            color: #22c55e;
        }

        .tradeoff li::before {
            content: "→";
            position: absolute;
            left: 0;
            color: #f59e0b;
        }

        .interactive-demo {
            margin: 30px 0;
            text-align: center;
            background: #0f172a;
            border: 1px solid #1e293b;
            border-radius: 8px;
            padding: 25px;
        }

        .demo-title {
            color: #58a6ff;
            margin-bottom: 15px;
            font-weight: 600;
        }

        .demo-title::before {
            content: "#!/bin/bash\n";
            color: #7c3aed;
            display: block;
            font-size: 0.8em;
        }

        .demo-button {
            background: #1e293b;
            border: 1px solid #374151;
            color: #d1d5db;
            padding: 12px 24px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.9em;
            font-family: 'Monaco', monospace;
            margin: 8px;
            transition: all 0.3s ease;
        }

        .demo-button:hover {
            background: #374151;
            border-color: #58a6ff;
            color: #58a6ff;
            transform: translateY(-1px);
        }

        .demo-button::before {
            content: "$ ";
            color: #7c3aed;
        }

        .code-snippet {
            background: #0d1117;
            border: 1px solid #21262d;
            border-radius: 6px;
            padding: 20px;
            margin: 20px 0;
            font-family: 'Monaco', monospace;
            font-size: 0.85em;
            overflow-x: auto;
        }

        .code-snippet::before {
            content: "config/unicorn.rb";
            display: block;
            color: #7c3aed;
            font-size: 0.8em;
            margin-bottom: 10px;
            border-bottom: 1px solid #21262d;
            padding-bottom: 5px;
        }

        .keyword { color: #ff7b72; }
        .string { color: #a5d6ff; }
        .comment { color: #8b949e; }
        .number { color: #79c0ff; }
        .variable { color: #ffa657; }

        @keyframes pulse {
            0%, 100% { opacity: 0.6; }
            50% { opacity: 1; }
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-3px); }
            75% { transform: translateX(3px); }
        }

        @media (max-width: 768px) {
            .workers-container {
                grid-template-columns: 1fr;
            }
            
            .comparison {
                grid-template-columns: 1fr;
            }

            .container {
                padding: 15px;
            }
        }

        .terminal-output {
            background: #0d1117;
            border: 1px solid #21262d;
            border-radius: 6px;
            padding: 15px;
            margin: 15px 0;
            font-family: 'Monaco', monospace;
            font-size: 0.8em;
        }

        .terminal-output::before {
            content: "$ ps aux | grep unicorn";
            display: block;
            color: #7c3aed;
            margin-bottom: 8px;
        }

        .process-line {
            color: #22c55e;
            margin: 3px 0;
        }

        .process-line .pid {
            color: #58a6ff;
        }

        .process-line .master {
            color: #dc2626;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Unicorn Web Server Architecture</h1>
        
        <div class="architecture">
            <!-- Clients Layer -->
            <div class="layer clients-layer">
                <div class="client">curl -X GET /api/users</div>
                <div class="client">fetch('/api/posts')</div>
                <div class="client">HTTParty.get('/health')</div>
                <div class="client">axios.post('/login')</div>
            </div>

            <div class="arrow">⬇</div>

            <!-- Load Balancer -->
            <div class="layer load-balancer">
                <div class="lb">upstream unicorn_backend</div>
            </div>

            <div class="arrow">⬇</div>

            <!-- Unicorn Server -->
            <div class="layer unicorn-layer">
                <div class="unicorn-server">
                    <div class="master-process">
                        Master Process (PID: 1234)
                        <div style="font-size: 0.8em; margin-top: 8px; opacity: 0.9;">
                            fork() workers • listen on socket • graceful restarts
                        </div>
                    </div>
                    
                    <div class="workers-container" id="workersContainer">
                        <div class="worker">
                            Worker 1 (PID: 1235)
                            <div class="socket-indicator">:8080</div>
                        </div>
                        <div class="worker">
                            Worker 2 (PID: 1236)
                            <div class="socket-indicator">:8080</div>
                        </div>
                        <div class="worker">
                            Worker 3 (PID: 1237)
                            <div class="socket-indicator">:8080</div>
                        </div>
                        <div class="worker">
                            Worker 4 (PID: 1238)
                            <div class="socket-indicator">:8080</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="interactive-demo">
            <div class="demo-title">Process Management Demo</div>
            <button class="demo-button" onclick="simulateCrash()">kill -9 [worker_pid]</button>
            <button class="demo-button" onclick="resetWorkers()">systemctl restart unicorn</button>
            <button class="demo-button" onclick="showProcessList()">ps aux | grep unicorn</button>
        </div>

        <div class="terminal-output" id="terminalOutput" style="display: none;">
            <div class="process-line">
                <span class="master">unicorn master</span> <span class="pid">1234</span> 0.1 2.3 rails_app
            </div>
            <div class="process-line">
                unicorn worker[0] <span class="pid">1235</span> 0.2 1.8 rails_app
            </div>
            <div class="process-line">
                unicorn worker[1] <span class="pid">1236</span> 0.1 1.9 rails_app
            </div>
            <div class="process-line">
                unicorn worker[2] <span class="pid">1237</span> 0.3 1.7 rails_app
            </div>
            <div class="process-line">
                unicorn worker[3] <span class="pid">1238</span> 0.2 1.8 rails_app
            </div>
        </div>

        <div class="code-snippet">
<span class="comment"># Unicorn configuration</span>
<span class="variable">worker_processes</span> <span class="number">4</span>  <span class="comment"># One per CPU core</span>
<span class="variable">listen</span> <span class="string">":8080"</span>
<span class="variable">timeout</span> <span class="number">30</span>

<span class="keyword">before_fork</span> <span class="keyword">do</span> |server, worker|
  <span class="comment"># Disconnect database before fork</span>
  <span class="variable">ActiveRecord::Base</span>.connection.disconnect!
<span class="keyword">end</span>

<span class="keyword">after_fork</span> <span class="keyword">do</span> |server, worker|
  <span class="comment"># Reconnect database in worker</span>
  <span class="variable">ActiveRecord::Base</span>.establish_connection
<span class="keyword">end</span>
        </div>

        <div class="feature-box">
            <div class="feature-title">How Fork Magic Works</div>
            <strong>1. fork() system call:</strong> Creates identical process copy<br>
            <strong>2. Copy-on-write:</strong> Memory shared until modified<br>
            <strong>3. Socket inheritance:</strong> All workers listen on same port<br>
            <strong>4. Kernel load balancing:</strong> accept() distributes requests<br>
            <strong>5. Process isolation:</strong> Crash = kill -9 one worker only
        </div>

        <div class="comparison">
            <div class="comparison-box good">
                <h3>Production Benefits</h3>
                <ul>
                    <li><strong>Zero downtime deploys:</strong> Rolling worker restarts</li>
                    <li><strong>Memory leak immunity:</strong> Workers recycled periodically</li>
                    <li><strong>CPU affinity:</strong> Workers pinned to specific cores</li>
                    <li><strong>Predictable RAM usage:</strong> No thread overhead</li>
                    <li><strong>Signal handling:</strong> SIGUSR2 for graceful restart</li>
                    <li><strong>Process monitoring:</strong> Easy with tools like monit</li>
                </ul>
            </div>
            
            <div class="comparison-box tradeoff">
                <h3>Engineering Trade-offs</h3>
                <ul>
                    <li><strong>Memory per worker:</strong> Full Rails app loaded</li>
                    <li><strong>Cold boot time:</strong> Workers start sequentially</li>
                    <li><strong>Horizontal scaling:</strong> More servers vs more threads</li>
                    <li><strong>Connection limits:</strong> worker_connections * workers</li>
                    <li><strong>Database connections:</strong> Pool per worker process</li>
                    <li><strong>Shared state:</strong> Redis/Memcached required</li>
                </ul>
            </div>
        </div>

        <div class="feature-box">
            <div class="feature-title">Why GitHub, Shopify, Stripe Choose This</div>
            <strong>Operational Excellence over Raw Performance:</strong><br>
            • Failure isolation prevents cascading crashes<br>
            • Memory leaks auto-heal via worker recycling<br>
            • Zero shared state = zero race conditions<br>
            • Battle-tested Unix primitives (1970s tech still works)<br>
            • Simple mental model for debugging production issues<br><br>
            <em>"The best system is the one that fails predictably and recovers automatically."</em>
        </div>
    </div>

    <script>
        let crashedWorkers = new Set();

        function simulateCrash() {
            const workers = document.querySelectorAll('.worker');
            const randomIndex = Math.floor(Math.random() * workers.length);
            const worker = workers[randomIndex];
            const pid = 1235 + randomIndex;
            
            // Simulate crash
            worker.classList.add('crashed');
            worker.innerHTML = `
                Worker ${randomIndex + 1} (CRASHED)
                <div style="font-size: 0.7em; margin-top: 5px;">
                    exit status: 1
                </div>
                <div class="socket-indicator">:8080</div>
            `;
            crashedWorkers.add(randomIndex);
            
            // Show terminal output
            showTerminalMessage(`[ERROR] Worker ${pid} crashed with signal 9`);
            
            // Simulate recovery after 2 seconds
            setTimeout(() => {
                worker.classList.remove('crashed');
                const newPid = pid + 1000;
                worker.innerHTML = `
                    Worker ${randomIndex + 1} (PID: ${newPid})
                    <div style="font-size: 0.7em; margin-top: 5px;">
                        freshly forked
                    </div>
                    <div class="socket-indicator">:8080</div>
                `;
                crashedWorkers.delete(randomIndex);
                
                showTerminalMessage(`[INFO] Spawned worker ${newPid}`);
            }, 2000);
        }

        function resetWorkers() {
            const workers = document.querySelectorAll('.worker');
            workers.forEach((worker, index) => {
                worker.classList.remove('crashed');
                const pid = 1235 + index;
                worker.innerHTML = `
                    Worker ${index + 1} (PID: ${pid})
                    <div class="socket-indicator">:8080</div>
                `;
            });
            crashedWorkers.clear();
            showTerminalMessage('[INFO] All workers restarted successfully');
        }

        function showProcessList() {
            const terminal = document.getElementById('terminalOutput');
            terminal.style.display = terminal.style.display === 'none' ? 'block' : 'none';
        }

        function showTerminalMessage(message) {
            // Create temporary terminal message
            const msgDiv = document.createElement('div');
            msgDiv.style.cssText = `
                background: #0d1117;
                border: 1px solid #21262d;
                border-radius: 6px;
                padding: 10px;
                margin: 10px 0;
                font-family: Monaco, monospace;
                font-size: 0.8em;
                color: #22c55e;
            `;
            msgDiv.textContent = message;
            
            const container = document.querySelector('.interactive-demo');
            container.appendChild(msgDiv);
            
            setTimeout(() => {
                msgDiv.remove();
            }, 3000);
        }

        // Add periodic worker activity animation
        setInterval(() => {
            const workers = document.querySelectorAll('.worker:not(.crashed)');
            const randomWorker = workers[Math.floor(Math.random() * workers.length)];
            if (randomWorker) {
                const original = randomWorker.style.background;
                randomWorker.style.background = '#1f2937';
                randomWorker.style.borderColor = '#10b981';
                setTimeout(() => {
                    randomWorker.style.background = original;
                    randomWorker.style.borderColor = '#059669';
                }, 300);
            }
        }, 2000);

        // Simulate terminal cursor blink in code snippets
        setInterval(() => {
            const codeSnippets = document.querySelectorAll('.code-snippet');
            codeSnippets.forEach(snippet => {
                if (Math.random() < 0.1) {
                    snippet.style.borderColor = '#7c3aed';
                    setTimeout(() => {
                        snippet.style.borderColor = '#21262d';
                    }, 200);
                }
            });
        }, 1500);
    </script>
</body>
</html>
