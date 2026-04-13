# B4n1Web

[![PyPI version](https://badge.fury.io/py/b4n1-web.svg)](https://pypi.org/project/b4n1-web/)
[![npm version](https://badge.fury.io/js/b4n1-web.svg)](https://www.npmjs.com/package/b4n1-web)
[![Go Reference](https://pkg.go.dev/badge/github.com/B4N1-com/b4n1web.svg)](https://pkg.go.dev/github.com/B4N1-com/b4n1web)
[![Maven Central](https://img.shields.io/maven-central/v/com.b4n1/b4n1-web.svg)](https://central.sonatype.com/artifact/com.b4n1/b4n1-web)
[![NuGet](https://img.shields.io/nuget/v/B4n1Web.svg)](https://www.nuget.org/packages/B4n1Web)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

> Ultra-lightweight agentic browser engine. Navigate URLs, extract content (markdown, links, screenshots), and build AI agent workflows.

## 🌐 [Website](https://web.b4n1.com)

## Install

### Option 1: SDK (Recommended)

| Language | Install |
|----------|---------|
| Python | `pip install b4n1-web` |
| JavaScript/TypeScript | `npm install b4n1-web` |
| Go | `go get github.com/B4N1-com/b4n1web` |
| C#/.NET | `dotnet add package B4n1Web` |
| Java | `com.b4n1:b4n1-web:0.4.0` |

### Option 2: Binary (Standalone)

For direct CLI usage, MCP server, or bulk operations:

```bash
curl -sL https://web.b4n1.com/install | bash
```

## Quick Start

### Python

```python
from b4n1web import AgentBrowser, BrowserMode

browser = AgentBrowser(mode=BrowserMode.LIGHT)
page = browser.goto("https://example.com")
print(page.markdown)
print(f"Found {len(page.links)} links")
browser.close()
```

### JavaScript

```javascript
import { AgentBrowser, BrowserMode } from 'b4n1-web';

const browser = new AgentBrowser({ mode: BrowserMode.LIGHT });
const page = await browser.goto('https://example.com');
console.log(page.markdown);
browser.close();
```

### Go

```go
import b4n1web "github.com/B4N1-com/b4n1web"

browser, _ := b4n1web.NewAgentBrowser(b4n1web.WithMode(b4n1web.ModeLight))
page, _ := browser.Goto("https://example.com")
fmt.Println(page.Markdown)
```

## Browser Modes

| Mode | Description | RAM | Speed |
|------|-------------|-----|-------|
| **Light** | HTTP fetch + HTML parsing | ~15MB | Instant |
| **JS** | Light + JavaScript extraction | ~15MB | Instant |
| **Render** | Full Chromium + screenshots | ~100MB | ~2s |

## Features

- **Ultra-lightweight**: Binary is ~5.5MB, compiled with LTO
- **Multi-language SDKs**: Python, JS, Go, Java, C#
- **MCP Server**: Native support for AI agent integration
- **Screenshots**: Render mode captures PNG screenshots as base64
- **Security**: Domain-level validation in the binary
- **Zero-config**: Install and use immediately

## MCP Server

Start the MCP server for AI agents (OpenCode, Cursor, etc.):

```bash
b4n1web mcp -p 8080
```

Available tools:
- `goto(url, mode)` — Navigate and extract content
- `get_links()` — Get all links from current page

## Screenshot Decoding

Render mode outputs screenshots as base64. Decode to PNG:

```bash
b4n1web goto https://example.com --mode render \
  | grep "Screenshot:" \
  | sed 's/Screenshot: //' \
  | base64 -d > screenshot.png
```

## Releases

| Platform | Status |
|----------|--------|
| Linux x86_64 | ✅ Available |
| macOS x86_64 | ⏳ Coming soon |
| macOS ARM64 | ⏳ Coming soon |
| Windows x86_64 | ⏳ Coming soon |

Download from [Releases](https://github.com/B4N1-com/b4n1web/releases).

## Tests

| Component | Tests | Status |
|-----------|-------|--------|
| Python SDK | 163 | ✅ Passing |
| JavaScript SDK | 34 | ✅ Passing |
| Java SDK | 49 | ✅ Passing |
| C# SDK | 34 | ✅ Passing |
| Go SDK | 37 | ✅ Passing |
| Rust Engine | 74 | ✅ Passing |
| Binary (bash) | 33 | ✅ Passing |
| E2E Podman | 6 SDKs | ✅ Passing |

**Total: 424+ tests, 0 failing**

---
*Built by B4N1 with ❤️ · All rights reserved.*
