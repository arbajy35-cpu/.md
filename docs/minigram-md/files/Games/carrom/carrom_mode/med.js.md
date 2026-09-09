# med.js

## 1. File Identity

- **File Name:** `med.js`
- **File Path:** `Games/carrom/carrom_mode/med.js`
- **Extension:** `.js`
- **Lines:** 77
- **Bytes:** 2677

## 2. What This File Does

- **[FACT]** This source file contains 77 lines and is part of the MiniGram source tree.

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

- **[INFERRED]** Static size: 2677 bytes; 77 lines. Runtime performance requires profiling for reliable measurement.

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

- **[INFERRED]** Start by inspecting Games/carrom/carrom_mode/med.js, then inspect its incoming and outgoing dependency relationships.

## 37. If File Is Deleted

- **[INFERRED]** No local dependent file was detected by the static graph.

## 38. If File Fails

- **[INFERRED]** No local caller was detected.

## 39. Change Impact

- **[INFERRED]** Changes should be reviewed against 0 incoming and 0 outgoing detected relationship(s).

## 40. Related Files

- None detected.

## 41. Real Code References

- `loadUserData` — line 55
- `click` — line 6
- `click` — line 11
- `click` — line 17
- `touchend` — line 71

## 42. Exact Line References

- `loadUserData` — line 55
- `click` — line 6
- `click` — line 11
- `click` — line 17
- `touchend` — line 71

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

Source file: Games/carrom/carrom_mode/med.js.

---

# SOURCE CODE

> Source: `Games/carrom/carrom_mode/med.js`
> Snapshot generated automatically.
> Secrets are redacted before documentation output.

```js
const backBtn = document.getElementById('backBtn');
const profileBtn = document.getElementById('profileBtn');
const modeCards = document.querySelectorAll('.mode-card');

// Back to home
backBtn?.addEventListener('click', () => {
  window.location.href = '../carrom_home.html';
});

// Profile click
profileBtn?.addEventListener('click', () => {
  alert('Profile Section\n👤 Player_01\n💰 Coins: 2500\n🏆 Wins: 12\n📊 Rank: #247\n\nComing Soon: Edit Profile, Stats, Achievements');
});

// Mode selection
modeCards.forEach(card => {
  card.addEventListener('click', () => {
    const mode = card.dataset.mode;

    if (navigator.vibrate) navigator.vibrate(50);

    card.style.transform = 'scale(0.95)';

    setTimeout(() => {
      if (mode === 'freestyle') {
        window.location.href = 'carrom_game/carrom.html?mode=freestyle';
      }
      else if (mode === 'classic') {
        let coins = parseInt(document.getElementById('coinsCount')?.textContent || '0');
        if (coins >= 100) {
          coins -= 100;
          localStorage.setItem('carromCoins', coins);
          window.location.href = 'carrom_game/carrom.html?mode=classic';
        } else {
          alert('❌ Not enough coins!\n\nYou need 100 coins to play Classic mode.');
        }
      }
      else if (mode === '2player') {
        // NEW: 2 Player mode - No AI, No coins needed
        window.location.href = 'carrom_game/carrom.html?mode=2player';
      }
      else if (mode === 'tournament') {
        let coins = parseInt(document.getElementById('coinsCount')?.textContent || '0');
        if (coins >= 500) {
          alert('🏆 TOURNAMENT MODE\n\nEntry Fee: ₹500\nPrize Pool: ₹5000\nTop 3 win!\n\nComing Soon!');
        } else {
          alert('❌ Not enough coins!\n\nYou need 500 coins for Tournament.');
        }
      }
      card.style.transform = 'scale(1)';
    }, 150);
  });
});

function loadUserData() {
  const savedCoins = localStorage.getItem('carromCoins') || '2500';
  const savedWins = localStorage.getItem('carromWins') || '12';

  const coinsEl = document.getElementById('coinsCount');
  const winsEl = document.getElementById('winsCount');
  const coinsHeaderEl = document.querySelector('.coins');

  if (coinsEl) coinsEl.textContent = savedCoins;
  if (winsEl) winsEl.textContent = savedWins;
  if (coinsHeaderEl) coinsHeaderEl.textContent = `💰 ${savedCoins}`;
}

loadUserData();

let lastTouchEnd = 0;
document.addEventListener('touchend', (e) => {
  const now = Date.now();
  if (now - lastTouchEnd <= 300) {
    e.preventDefault();
  }
  lastTouchEnd = now;
}, false);
```
