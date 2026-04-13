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

| Language | Install | Version |
|----------|---------|---------|
| Python | `pip install b4n1-web` | [0.5.0](https://pypi.org/project/b4n1-web/0.5.0/) |
| JavaScript/TypeScript | `npm install b4n1-web` | [0.5.0](https://www.npmjs.com/package/b4n1-web/v/0.5.0) |
| Go | `go get github.com/B4N1-com/b4n1web` | [0.5.0](https://pkg.go.dev/github.com/B4N1-com/b4n1web) |
| C#/.NET | `dotnet add package B4n1Web` | [0.5.0](https://www.nuget.org/packages/B4n1Web/0.5.0) |
| Java | See below | [0.5.0](https://central.sonatype.com/artifact/com.b4n1/b4n1-web) |

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

### JavaScript/TypeScript

```javascript
import { AgentBrowser, BrowserMode } from 'b4n1-web';

const browser = new AgentBrowser({ mode: BrowserMode.LIGHT });
const page = await browser.goto('https://example.com');
console.log(page.markdown);
console.log(page.links.length, 'links found');
browser.close();
```

### Go

```go
package main

import (
    "fmt"
    b4n1web "github.com/B4N1-com/b4n1web"
)

func main() {
    browser, _ := b4n1web.NewAgentBrowser(b4n1web.WithMode(b4n1web.ModeLight))
    defer browser.Close()
    
    page, _ := browser.Goto("https://example.com")
    fmt.Println(page.Markdown)
    fmt.Println(len(page.Links), "links found")
}
```

### Java

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.b4n1</groupId>
    <artifactId>b4n1-web</artifactId>
    <version>0.5.0</version>
</dependency>
```

```java
import com.b4n1.web.*;

AgentBrowser browser = new AgentBrowser(new BrowserOptions());
Page page = browser.goto_("https://example.com");
System.out.println(page.getMarkdown());
System.out.println(page.getLinks().size() + " links found");
browser.close();
```

### C#

```csharp
using B4N1Web;

var browser = new AgentBrowser(new BrowserOptions { Mode = BrowserMode.Light });
var page = browser.Goto("https://example.com");
Console.WriteLine(page.Markdown);
Console.WriteLine($"{page.Links.Count} links found");
browser.Close();
```

## Page Object

All SDKs return the same structured data:

| Property | Type | Description |
|----------|------|-------------|
| `Url` / `url` | string | Final URL after navigation |
| `Markdown` / `markdown` | string | Page content as markdown |
| `Links` / `links` | List\<string\> | All links found on page |
| `Screenshot` / `screenshot` | string? | Base64 PNG (render mode only) |

Methods:
- `getMainContent()` / `GetMainContent()` — Extract content without headers
- `findLinksByText(text)` / `FindLinksByText(text)` — Find links containing text

## Browser Modes

| Mode | Flag | Description | RAM | Speed |
|------|------|-------------|-----|-------|
| **Light** | `--mode light` | HTTP fetch + HTML parsing | ~15MB | Instant |
| **JS** | `--mode js` | Light + JavaScript extraction | ~15MB | Instant |
| **Render** | `--mode render` | Full Chromium + screenshots | ~100MB | ~2s |

## MCP Server

Start the MCP server for AI agents (OpenCode, Cursor, etc.):

```bash
b4n1web mcp -p 8080
```

Available tools:
- `goto(url, mode)` — Navigate and extract content
- `get_links()` — Get all links from current page

## Screenshot Decoding

Render mode outputs screenshots as base64 PNG. Decode to file:

```bash
b4n1web goto https://example.com --mode render \
  | grep "Screenshot:" \
  | sed 's/Screenshot: //' \
  | base64 -d > screenshot.png
```

## Features

- **Ultra-lightweight**: Binary is ~5.5MB, compiled with LTO
- **5 language SDKs**: Python, JS, Go, Java, C#
- **Bundled binary**: `pip install` includes everything
- **MCP Server**: Native AI agent integration
- **Screenshots**: Render mode captures PNG as base64
- **Security**: Domain-level validation
- **424+ tests**: All passing across all SDKs

---
*Built by B4N1 with ❤️ · All rights reserved.*
