# doctor.html

## 1. File Identity

- **File Name:** `doctor.html`
- **File Path:** `doctor.html`
- **Extension:** `.html`
- **Lines:** 198
- **Bytes:** 6917

## 2. What This File Does

- **[FACT]** This source file contains 198 lines and is part of the MiniGram source tree.

## 3. 5th-Standard Explanation

- **[INFERRED]** The file can be understood by examining its executable code, references, functions, events and relationships with other source files.

## 4. When It Runs

- **[UNKNOWN]** Not determinable from static source analysis.

## 5. Called By

- None detected.

## 6. Calls / Uses

- None detected.

## 7. Imports

- None detected.

## 8. Exports

- None detected.

## 9. Globals Read

- None detected.

## 10. Globals Written

- None detected.

## 11. Inputs

- **[INFERRED]** Inputs are derived from function parameters, events, referenced globals, DOM APIs and external resources when detectable.

## 12. Outputs

- **[INFERRED]** Outputs are derived from return statements, DOM mutations, exported values and external effects when detectable.

## 13. Exact Execution Flow

- **[INFERRED]** Static execution order is represented by discovered declarations, references and dependency relationships. Runtime branch order may require execution tracing.

## 14. Forward Flow

- None detected.

## 15. Reverse Flow

- None detected.

## 16. Data Flow

- **[INFERRED]** Data flow is reconstructed only from statically detectable references. Runtime values that depend on user input or network responses may remain unknown.

## 17. UI Flow

- **[INFERRED]** UI interaction points are reported when DOM APIs, event listeners or HTML references are detected.

## 18. Network Flow

- **[UNKNOWN]** Not determinable from static source analysis.

## 19. Cache Flow

- **[UNKNOWN]** Not determinable from static source analysis.

## 20. Supabase Flow

- **[UNKNOWN]** Not determinable from static source analysis.

## 21. Error Flow

- **[INFERRED]** Potential error paths are identified from detectable error handling constructs; complete runtime error behavior cannot be proven statically.

## 22. Fallback Flow

- **[UNKNOWN]** Not determinable from static source analysis.

## 23. Dependency Graph

### Incoming
- None detected.

### Outgoing
- None detected.

## 24. Before This File

- [object Object]

## 25. After This File

- [object Object]

## 26. Parallel Files

- **[TODO]** Runtime parallelism requires execution tracing or explicit asynchronous scheduling analysis.

## 27. Blocking Files

- **[TODO]** Blocking behavior cannot always be proven from static source analysis.

## 28. Required Files

- None detected.

## 29. Optional Files

- **[TODO]** Optionality requires runtime/build configuration evidence.

## 30. Performance Impact

- **[INFERRED]** Static size: 6917 bytes; 198 lines. Runtime performance requires profiling for reliable measurement.

## 31. Memory Impact

- **[UNKNOWN]** Not determinable from static source analysis.

## 32. Network Impact

- **[UNKNOWN]** Not determinable from static source analysis.

## 33. Low-End Behavior

- **[UNKNOWN]** Not determinable from static source analysis.

## 34. Security

- **[WARNING]** Static analysis is not a complete security audit. Secrets, dangerous sinks and sensitive configuration should be reviewed separately.

## 35. Common Bugs

- **[TODO]** Potential bugs require combining static findings with tests and runtime reports.

## 36. Debugging

- **[INFERRED]** Start by inspecting doctor.html, then inspect its incoming and outgoing dependency relationships.

## 37. If File Is Deleted

- **[INFERRED]** No local dependent file was detected by the static graph.

## 38. If File Fails

- **[INFERRED]** No local caller was detected.

## 39. Change Impact

- **[INFERRED]** Changes should be reviewed against 0 incoming and 0 outgoing detected relationship(s).

## 40. Related Files

- None detected.

## 41. Real Code References

- `click` — line 190

## 42. Exact Line References

- `click` — line 190

## 43. Tests

- **[TODO]** No test result is claimed unless tests are actually executed.

## 44. Developer Checklist

- Verify source behavior before changing it.
- Check incoming dependencies.
- Check outgoing dependencies.
- Run relevant tests.
- Review generated documentation after changes.

## 45. Simple Example

- **[INFERRED]** Use the detected functions, events and dependency graph as the starting point for understanding this file.

## 46. Confidence / Evidence

- Static facts: **HIGH**
- Runtime behavior: **LIMITED**
- Inferred behavior: **MEDIUM**
- Unknown areas: **EXPLICIT**

The system does not present unknown runtime behavior as proven fact.

## 47. One-Line Summary

Source file: doctor.html.

---

# SOURCE CODE

> Source: `doctor.html`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

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
