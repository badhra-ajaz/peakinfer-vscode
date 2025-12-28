# PeakInfer VS Code Extension - Project Overview

This is the **peakinfer-vscode** (VS Code Extension) repository.

## Key Information

- **Type:** VS Code Extension
- **Mode:** PeakInfer Token (Credits)
- **Analysis:** Calls peakinfer.com API

---

## Architecture

### What This Extension Does

1. User triggers analysis (command or on-save)
2. Reads PeakInfer token from settings or `PEAKINFER_TOKEN` env var
3. Calls `peakinfer.com/api/analyze` with code
4. Displays results as VS Code diagnostics
5. Shows results in webview panel

### Key Features

- **Inline Diagnostics:** Squiggly lines in editor
- **Results Panel:** Comprehensive analysis view
- **Credit System:** Uses PeakInfer credits (50 free, then $19-$499 packs)
- **Error/Loading States:** Spinner, retry button, help text

---

## Key Files

| File | Purpose |
|------|---------|
| `src/extension.ts` | Activation, command registration |
| `src/analysis.ts` | AnalysisRunner with API call |
| `src/diagnostics.ts` | VS Code diagnostics integration |
| `src/views/resultsPanel.ts` | Webview panel with states |
| `package.json` | Commands, settings, keybindings |

---

## Configuration Settings

| Setting | Default | Description |
|---------|---------|-------------|
| `peakinfer.token` | `""` | PeakInfer token (or use env var) |
| `peakinfer.analyzeOnSave` | `false` | Auto-analyze on save |
| `peakinfer.showInlineHints` | `true` | Show inline hints |
| `peakinfer.severityThreshold` | `warning` | Minimum severity |
| `peakinfer.includeBenchmarks` | `true` | Include benchmarks |

---

## Commands

| Command | Description |
|---------|-------------|
| `peakinfer.analyzeFile` | Analyze current file |
| `peakinfer.analyzeWorkspace` | Analyze entire workspace |
| `peakinfer.showResults` | Show results panel |
| `peakinfer.clearDiagnostics` | Clear diagnostics |
| `peakinfer.setToken` | Set PeakInfer token |

---

## Pricing

Same as GitHub Action:

| Pack | Price | Credits |
|------|-------|---------|
| Free | $0 | 50 (one-time, 6-month expiry) |
| Starter | $19 | 200 |
| Growth | $49 | 600 |
| Scale | $149 | 2,000 |
| Mega | $499 | 10,000 |

Credits are shared across VS Code and GitHub Action.

Get token at [peakinfer.com/dashboard](https://peakinfer.com/dashboard)

---

## Session Memory (Last Updated: December 29, 2025)

### Current State

**v1.9.5 Status:** ✅ 100% Complete - Ready for Release

### Work Completed This Session

**Strategy Change:**
- Changed from BYOK (Anthropic API key) to PeakInfer token (credits)
- Same pricing model as GitHub Action
- Credits shared across VS Code and GitHub Action

**Files Modified:**
- `README.md` - Updated setup and pricing sections
- `CLAUDE.md` - Updated to reflect token-based auth

### Cross-Repo Context

| Repository | Role | Auth Mode | Status |
|------------|------|-----------|--------|
| `peakinfer/` (CLI) | CLI | BYOK | ✅ Complete |
| `peakinfer-mcp/` | MCP Server | BYOK | ✅ Complete |
| `peakinfer-action/` | GitHub Action | PeakInfer Token | ✅ Complete |
| `peakinfer-site/` | API + Website | - | ✅ Complete |
| `peakinfer-vscode/` (this repo) | VS Code Extension | PeakInfer Token | ✅ Complete |
| `peakinfer_templates/` | Templates | - | ✅ Complete |

### Important Context

1. **PeakInfer Token** - calls peakinfer.com API (NOT local BYOK)
2. **Credit System** - same as GitHub Action (50 free, then paid)
3. **Token from** settings OR `PEAKINFER_TOKEN` env var
4. **Error states** - showLoading(), showError(), retry button

### Reference Documents

| Document | Location |
|----------|----------|
| Implementation Guide | `peakinfer/design/PeakInfer Implementation v1.9.5.md` |
| Main CLAUDE.md | `peakinfer/CLAUDE.md` |
| VS Code README | `README.md` |
