# doctor.html

> MiniGram MD Intelligence V6

## 1. File Identity

| Property | Value |
|---|---|
| Source | `doctor.html` |
| Extension | `.html` |
| Bytes | 6917 |
| Lines | 198 |
| SHA-256 | `7d27d4a61a609b88e705b2dff57622d5b8b61a5dcc29eec0b23b62b030c8b0fe` |
| Dependency Depth | 0 |

## 2. Project Understanding

Project understanding generated from the local intelligence engine.

## 3. Architecture Context

Architecture derived from the complete local relation graph.

## 4. File Role

This file belongs to:

`doctor.html`

The local intelligence engine detected
0 direct dependencies
and 1 consumers.

## 5. Dependencies

- None

## 6. Used By

- `report.json`

## 7. Exact Relation Flow

- No local relation detected

## 8. Local Symbols

- None

## 9. Exports

- None

## 10. Unresolved References

- None

## 11. Error / Problem Detection

- No detected errors

## 12. Project Systems

- None

## 13. Project Risks

- None

## 14. Recommendations

- None

## 15. Execution / Architecture Flow

See the generated relation graph and file-level flows.

---

# ORIGINAL SOURCE CODE

The following is the **exact local source content**
read from:

`/storage/emulated/0/MINIGRAM1/doctor.html`

It is NOT AI generated or rewritten.

```html
<!DOCTYPE html>
<html>
<head>
    <title>MINIGRAM DOCTOR</title>
</head>
<body>
    <h2>🩺 MINIGRAM PROJECT DOCTOR v3.0</h2>
    <button id="startBtn" style="padding:15px 30px;font-size:18px;background:#ff4757;color:white;border:none;border-radius:8px;">
        START PROFILING
    </button>
    <pre id="output" style="background:#1e1e1e;color:#0f0;padding:20px;margin-top:20px;white-space:pre-wrap;font-family:monospace;"></pre>

<script>
const Doctor = {
    results: [],
    startTime: 0,

    log(msg) {
        document.getElementById('output').textContent += msg + '\n';
    },

    async start() {
        this.log('🩺 MINIGRAM PROJECT DOCTOR v3.0 - BROWSER MODE\n');
        this.log('='.repeat(50));
        this.startTime = performance.now();

        // 1. Hook saare functions ko
        this.hookFunctions();

        // 2. DOM ops count karo
        this.hookDOM();

        // 3. Network monitor
        this.hookNetwork();

        this.log('\nMonitoring started... Reload page to capture full load time\n');
        this.log('Waiting 5 sec then generating report...\n');

        setTimeout(() => this.generateReport(), 5000);
    },

    hookFunctions() {
        const self = this;
        const originalSetTimeout = window.setTimeout;
        const originalFetch = window.fetch;

        // SetTimeout wrap
        window.setTimeout = function(fn, delay,...args) {
            const wrapped = function() {
                const start = performance.now();
                fn.apply(this, arguments);
                const time = performance.now() - start;
                if (time > 5) { // Only log slow ones
                    self.log(`PERF: ${fn.name || 'anonymous'} | ${time.toFixed(0)}ms`);
                }
            };
            return originalSetTimeout(wrapped, delay,...args);
        };

        // Fetch wrap
        window.fetch = function(...args) {
            const start = performance.now();
            const url = args[0];
            return originalFetch.apply(this, args).then(res => {
                const time = performance.now() - start;
                self.log(`NET: ${url} | ${time.toFixed(0)}ms`);
                return res;
            });
        };
    },

    hookDOM() {
        let domOps = 0;
        const originalCreate = document.createElement;
        const originalAppend = Element.prototype.appendChild;

        document.createElement = function(...args) {
            domOps++;
            return originalCreate.apply(this, args);
        };

        Element.prototype.appendChild = function(...args) {
            domOps++;
            return originalAppend.apply(this, args);
        };

        setInterval(() => {
            window.__domOps = domOps;
        }, 1000);
    },

    hookNetwork() {
        const observer = new PerformanceObserver((list) => {
            for (const entry of list.getEntries()) {
                if (entry.entryType === 'resource' && entry.name.endsWith('.js')) {
                    this.results.push({
                        file: entry.name.split('/').pop(),
                        duration: entry.duration,
                        size: entry.transferSize,
                        type: 'script'
                    });
                }
                if (entry.entryType === 'measure') {
                    this.results.push({
                        file: entry.name,
                        duration: entry.duration,
                        size: 0,
                        type: 'function'
                    });
                }
            }
        });
        observer.observe({ entryTypes: ['resource', 'measure', 'navigation'] });
    },

    generateReport() {
        const nav = performance.getEntriesByType('navigation')[0];
        const totalTime = performance.now() - this.startTime;

        this.log('\n' + '='.repeat(50));
        this.log('\n🚀 MINIGRAM PERFORMANCE REPORT - REAL BROWSER\n');
        this.log('='.repeat(50));

        if (nav) {
            this.log(`\nTotal Page Load: ${nav.loadEventEnd.toFixed(0)}ms`);
            this.log(`DOM Content Loaded: ${nav.domContentLoadedEventEnd.toFixed(0)}ms`);
            this.log(`DOM Interactive: ${nav.domInteractive.toFixed(0)}ms`);
        }

        this.log(`Total DOM Operations: ${window.__domOps || 0}\n`);
        this.log('='.repeat(50));

        // JS Files
        const jsFiles = this.results.filter(r => r.type === 'script')
          .sort((a, b) => b.duration - a.duration);

        this.log('\n🔥 SLOW FILES - REAL LOAD TIME\n');
        jsFiles.slice(0, 10).forEach((f, i) => {
            this.log(`${i+1} ${f.file.padEnd(25)} ${f.duration.toFixed(0)}ms | ${(f.size/1024).toFixed(1)}KB`);
        });

        if (jsFiles.length) {
            const slowest = jsFiles[0];
            this.log('\n' + '='.repeat(50));
            this.log('\nBOTTLENECK\n');
            this.log(`${slowest.file}`);
            this.log('↓');
            this.log(`Load Time: ${slowest.duration.toFixed(0)}ms`);
            this.log('↓');
            this.log(`Size: ${(slowest.size/1024).toFixed(1)}KB`);
        }

        // Functions
        const funcs = this.results.filter(r => r.type === 'function')
          .sort((a, b) => b.duration - a.duration);

        if (funcs.length) {
            this.log('\n⏱️ SLOW FUNCTIONS\n');
            funcs.slice(0, 5).forEach(f => {
                this.log(`${f.file.padEnd(25)} ${f.duration.toFixed(0)}ms`);
            });
        }

        this.log('\n' + '='.repeat(50));
        this.log('\nSuggestions\n');

        if (window.__domOps > 200) {
            this.log(`⚠ High DOM operations: ${window.__domOps}`);
            this.log('→ Suggestion: Use DocumentFragment, batch updates');
            this.log('→ Estimated Gain: 30-45%\n');
        }

        if (jsFiles[0] && jsFiles[0].size > 100 * 1024) {
            this.log(`⚠ ${jsFiles[0].file} is heavy: ${(jsFiles[0].size/1024).toFixed(0)}KB`);
            this.log('→ Suggestion: Code split, lazy load, minify');
            this.log('→ Estimated Gain: 20-35%\n');
        }

        if (nav && nav.loadEventEnd > 3000) {
            this.log(`⚠ Total load > 3s: ${nav.loadEventEnd.toFixed(0)}ms`);
            this.log('→ Suggestion: Defer non-critical JS, optimize images');
            this.log('→ Estimated Gain: 40-60%\n');
        }

        this.log('='.repeat(50));
        this.log('\n💡 TIP: Open DevTools > Performance tab for flame graph\n');
    }
};

document.getElementById('startBtn').onclick = () => Doctor.start();

// Auto start agar?doctor=true URL me hai
if (location.search.includes('doctor=true')) {
    Doctor.start();
}
</script>
</body>
</html>
```

---

Generated by MiniGram MD Intelligence V6.
