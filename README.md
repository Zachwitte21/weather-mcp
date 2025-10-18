# Weather MCP Server

An MCP (Model Context Protocol) server that provides weather information tools using the National Weather Service (NWS) API.

## Features

This MCP server exposes two tools for accessing weather data:

- **`get_alerts`**: Get active weather alerts for any US state
- **`get_forecast`**: Get detailed weather forecast for a specific location (latitude/longitude)

## Requirements

- Python >= 3.14
- uv (recommended for dependency management)

## Setup

1. Clone this repository or download the source code

2. Install dependencies using uv:
```bash
uv sync
```

## Running the Server

The server runs using stdio transport for MCP communication:

```bash
uv run weather.py
```

## Using with MCP Clients

To use this server with an MCP client (like Claude Desktop), add it to your MCP client configuration:

```json
{
  "mcpServers": {
    "weather": {
      "command": "uv",
      "args": [
        "--directory",
        "c:\\Users\\Zachary\\Dev\\weather",
        "run",
        "weather.py"
      ]
    }
  }
}
```

## Available Tools

### get_alerts

Get active weather alerts for a US state.

**Parameters:**
- `state` (string): Two-letter US state code (e.g., "CA", "NY", "TX")

**Example:**
```
get_alerts(state="CA")
```

### get_forecast

Get weather forecast for a specific location.

**Parameters:**
- `latitude` (float): Latitude of the location
- `longitude` (float): Longitude of the location

**Example:**
```
get_forecast(latitude=37.7749, longitude=-122.4194)
```

## Data Source

This server uses the [National Weather Service API](https://www.weather.gov/documentation/services-web-api), which provides free weather data for US locations.

## License

Add your license information here.
