# OpenScrape CLI

Interactive CLI tool for web scraping with Puppeteer. Extract titles, descriptions, links, headings, paragraphs, and full text from any website.

## Installation

### Global Installation
```bash
npm install -g openscrape-cli
```

### Local Installation
```bash
npm install openscrape-cli
```

## Usage

### Interactive Mode
```bash
openscrape
```
Or if installed locally:
```bash
npx openscrape-cli
```

### Using the MCP Server
To use the MCP server capabilities, run:
```bash
node mcp-server.js
```

The MCP server provides two tools:
- `scrape_page`: Scrape a single web page
- `crawl_pages`: Crawl multiple pages starting from a URL

#### IDE Configuration (Windsurf)
To integrate the MCP server with Windsurf or other MCP-compatible IDEs, add the following to your MCP configuration file:

```json
{
  "open-scrape": {
    "args": [
      "/path/to/openscrape-cli/mcp-server.js",
      "--stdio"
    ],
    "command": "node"
  }
}
```

Replace `/path/to/openscrape-cli/` with the actual installation path of the package on your system.

### Auto-Starting the MCP Server

#### Windows
Create a batch file to start the MCP server automatically:

**start_mcp.bat**
```batch
@echo off
cd /d "%~dp0"
start /B node mcp-server.js
echo MCP server started in background.
pause
```

To run on startup, copy the batch file to your Windows startup folder:
```batch
copy "start_mcp.bat" "%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup\"
```

Replace `start_mcp.bat` with the full path to your batch file if needed.

#### macOS
Create a launch agent to auto-start the MCP server:

**~/Library/LaunchAgents/com.openscrape.mcp.plist**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.openscrape.mcp</string>
    <key>ProgramArguments</key>
    <array>
        <string>/usr/local/bin/node</string>
        <string>/path/to/openscrape-cli/mcp-server.js</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
</dict>
</plist>
```

Load the launch agent:
```bash
launchctl load ~/Library/LaunchAgents/com.openscrape.mcp.plist
```

Replace `/path/to/openscrape-cli/` with your installation path.

## Features

- **Interactive CLI**: User-friendly terminal interface with colorful prompts
- **Screenshot Support**: Capture full page or viewport screenshots
- **Multiple Output Formats**: Save results as Markdown, XML, or HTML
- **Comprehensive Extraction**: Extract titles, descriptions, links, headings, paragraphs, and full text
- **MCP Server**: Model Context Protocol server for integration with AI assistants

## Example

```
 ██████╗ ██████╗ ███████╗███╗   ██╗███████╗ ██████╗██████╗  █████╗ ██████╗ ███████╗
██╔═══██╗██╔══██╗██╔════╝████╗  ██║██╔════╝██╔════╝██╔══██╗██╔══██╗██╔══██╗██╔════╝
██║   ██║██████╔╝█████╗  ██╔██╗ ██║███████╗██║     ██████╔╝███████║██████╔╝█████╗
██║   ██║██╔═══╝ ██╔══╝  ██║╚██╗██║╚════██║██║     ██╔══██╗██╔══██║██╔═══╝ ██╔══╝
╚██████╔╝██║     ███████╗██║ ╚████║███████║╚██████╗██║  ██║██║  ██║██║     ███████╗
 ╚═════╝ ╚═╝     ╚══════╝╚═╝  ╚═══╝╚══════╝ ╚═════╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝     ╚══════╝

Current directory: /your/project/directory
────────────────────────────────────────────────────────────────────────────────
┌─ > Enter the URL to scrape:─┐
```

## Configuration

Create a `config/default.yaml` file to configure scraping options:

```yaml
urls:
  - https://example.com
  - https://example.org
screenshots:
  enabled: true
  dir: ./output/screenshots
output:
  format: md
  path: ./output/scraped.md
delay: 1000
```

## Requirements

- Node.js 18+
- npm

## License

ISC
