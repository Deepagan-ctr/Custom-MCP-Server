<div align="center">

# Social Media Scraper - MCP Server

## 🛠️ Tech Stack

This project is built with a modern, asynchronous Python stack, designed for efficient API interactions.

### Core Technologies & Frameworks
![FastMCP](https://img.shields.io/badge/FastMCP-8A2BE2?&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white)
![HTTPX](https://img.shields.io/badge/httpx-003366?logo=python&logoColor=white)
![AsyncIO](https://img.shields.io/badge/AsyncIO-3776AB?logo=python&logoColor=white)

### Programming Language & Environment
![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![uv](https://img.shields.io/badge/uv-007ACC?logo=python&logoColor=white)
![dotenv](https://img.shields.io/badge/dotenv-ECD53F?logo=dotenv&logoColor=black)

### APIs & Data Formats
![REST API](https://img.shields.io/badge/REST_API-0277BD?&logoColor=white)
![RapidAPI](https://img.shields.io/badge/RapidAPI-3333FF?logo=apollographql&logoColor=white)
![JSON](https://img.shields.io/badge/JSON-000000?logo=json&logoColor=white)
</div>

A comprehensive Model Context Protocol (MCP) server that provides social media scraping capabilities for LinkedIn, Facebook, Instagram, and Google search functionality.

## What is MCP?

**[Model Context Protocol (MCP)](https://modelcontextprotocol.io/introduction)** is an open standard that enables AI assistants to securely connect with external data sources and tools. MCP servers act as bridges between AI models and various services, allowing for enhanced capabilities like real-time data access, API integrations, and custom tool execution.

## Features

- **LinkedIn Profile Scraping**: Extract personal and company profile data
- **Facebook Profile Scraping**: Fetch public profile information
- **Instagram Profile Scraping**: Get profile data and basic information
- **Google Search**: Perform web searches using Google Serper API

## Available Tools

### LinkedIn Tools
- `get_personal_profile(linkedin_url)` - Scrape LinkedIn personal profiles
- `get_company_profile(linkedin_url)` - Scrape LinkedIn company pages

### Social Media Tools
- `get_facebook_profile(profile_url)` - Scrape Facebook profile data
- `get_instagram_profile(username_or_url)` - Scrape Instagram profile information

### Web Search Tools
- `scrape_website(query, gl, num, page)` - Perform Google searches with customizable parameters

## Installation

### Adding MCP to your Python project

We recommend using [uv](https://docs.astral.sh/uv/) to manage your Python projects.

If you haven't created a uv-managed project yet, create one:

```bash
uv init custom-mcp-server
cd custom-mcp-server
```

Then add MCP to your project dependencies:

```bash
uv add "mcp[cli]"
```

### Install Additional Dependencies

```bash
uv add httpx python-dotenv fastmcp
```

## Configuration

### Environment Variables

Create a `.env` file in your project root with the following variables:

```env
RAPIDAPI_KEY=your_rapidapi_key_here
SERPER_API_KEY=your_serper_api_key_here
```

### API Keys Setup

1. **RapidAPI Key**: 
   - Sign up at [RapidAPI](https://rapidapi.com/)
   - Subscribe to the following APIs (Most Important):
     - Fresh LinkedIn Profile Data
     - Facebook Scraper3
     - Instagram Scraper Stable API

2. **Google Serper API Key**:
   - Sign up at [Serper.dev](https://serper.dev/)
   - Get your API key from the dashboard

## Usage

### Running with Claude Desktop

You can install this server in [Claude Desktop](https://claude.ai/download) and interact with it right away by running:

```bash
mcp install main.py
```

### Testing with MCP Inspector

Alternatively, you can test it with the MCP Inspector:

```bash
mcp dev main.py
```

## Project Structure

```
custom-mcp-server/
├── main.py              # Main MCP server implementation
├── .env                 # Environment variables (create this)
├── .env.example         # Example environment file
├── pyproject.toml       # Project configuration
├── README.md           # This file
└── requirements.txt    # Dependencies (if not using uv)
```

## Response Format

All tools return JSON-formatted strings containing the scraped data. Example response structure:

```json
{
  "success": true,
  "data": {
    "profile": {
      "name": "John Doe",
      "title": "Software Engineer",
      "location": "San Francisco, CA",
      "bio": "Passionate about technology..."
    }
  },
  "timestamp": "2024-01-15T10:30:00Z"
}
```
But using these tools via Claude makes it readable.
## Error Handling

The server includes comprehensive error handling:

- **Network Errors**: Automatic retry logic with exponential backoff
- **API Rate Limits**: Graceful handling of rate limit responses
- **Invalid URLs**: Validation and helpful error messages
- **Missing Data**: Clear indication when profile data is unavailable

## Rate Limiting

To avoid being blocked by APIs:

- Requests are limited to reasonable intervals
- Concurrent requests are managed
- API usage is monitored and logged

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request
