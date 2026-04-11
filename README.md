# B4n1Web

[![PyPI version](https://badge.fury.io/py/b4n1-web.svg)](https://pypi.org/project/b4n1-web/)
[![npm version](https://badge.fury.io/js/b4n1-web.svg)](https://www.npmjs.com/package/b4n1-web)
[![Go Reference](https://pkg.go.dev/badge/github.com/B4N1-com/b4n1web.svg)](https://pkg.go.dev/github.com/B4N1-com/b4n1web)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

> Ultra-lightweight agentic browser engine. Navigate URLs, extract content (markdown, links, screenshots), and build AI agent workflows.

## 🌐 [Website](https://web.b4n1.com)

## Install SDK

Choose your language:

| Language | Install |
|----------|---------|
| Python | `pip install b4n1-web` |
| JavaScript/TypeScript | `npm install b4n1-web` |
| Go | `go get github.com/B4N1-com/b4n1web` |
| C#/.NET | `dotnet add package B4n1Web` |
| Java | `com.b4n1:b4n1-web:0.4.0` |

All SDKs include the b4n1web binary — no separate installation needed.

## Install Binary (Standalone)

For direct CLI usage, MCP server, or bulk operations:

```bash
curl -sL https://web.b4n1.com/install | bash
b4n1web --version
b4n1web mcp -p 8080
```

## Quick Start

```python
from b4n1web import AgentBrowser

browser = AgentBrowser()
page = browser.goto("https://example.com")
print(page.markdown)
```

## Features

- **Light Mode**: HTTP fetch + HTML parsing (~15MB RAM, instant startup)
- **JS Mode**: JavaScript extraction from pages
- **Render Mode**: Full Chromium rendering with screenshots
- **SecurityShield**: Domain-level safety validation
- **MCP Support**: Model Context Protocol for AI agents

## Releases

Binary releases disponibles:

| Plataforma | Estado |
|------------|--------|
| Linux x86_64 | ✅ Disponible |
| macOS x86_64 | ⏳ Coming soon |
| macOS ARM64 | ⏳ Coming soon |
| Windows x86_64 | ⏳ Coming soon |

Ver [Releases](https://github.com/B4N1-com/b4n1web/releases) para descargas.

---
*Built by B4N1 with ❤️ · All rights reserved.*
