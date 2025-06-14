# Social Media Scraper MCP Server

A comprehensive Model Context Protocol (MCP) server that provides social media scraping capabilities for LinkedIn, Facebook, Instagram, and Google search functionality.

## Features

- **LinkedIn Profile Scraping**: Extract personal and company profile data
- **Facebook Profile Scraping**: Fetch public profile information
- **Instagram Profile Scraping**: Get profile data and basic information
- **Google Search**: Perform web searches using Google Serper API
- **Async Operations**: Built with async/await for efficient concurrent processing
- **Error Handling**: Robust error handling with detailed logging

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

We recommend using uv to manage your Python projects.

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
   - Subscribe to the following APIs:
     - Fresh LinkedIn Profile Data
     - Facebook Scraper3
     - Instagram Scraper Stable API

2. **Google Serper API Key**:
   - Sign up at [Serper.dev](https://serper.dev/)
   - Get your API key from the dashboard

## Usage

### Running with Claude Desktop

You can install this server in Claude Desktop and interact with it right away by running:

```bash
mcp install main.py
```

### Testing with MCP Inspector

Alternatively, you can test it with the MCP Inspector:

```bash
mcp dev main.py
```

### Direct Execution

Run the server directly:

```bash
python main.py
```

## Example Usage

### LinkedIn Profile Scraping
```python
# Personal profile
result = await get_personal_profile("https://linkedin.com/in/username")

# Company profile  
result = await get_company_profile("https://linkedin.com/company/company-name")
```

### Social Media Scraping
```python
# Facebook profile
result = await get_facebook_profile("https://facebook.com/username")

# Instagram profile
result = await get_instagram_profile("username")
# or
result = await get_instagram_profile("https://instagram.com/username")
```

### Web Search
```python
# Basic search
result = await scrape_website("python programming")

# Advanced search with parameters
result = await scrape_website(
    query="social media marketing",
    gl="us",  # Country code
    num=20,   # Number of results
    page=1    # Page number
)
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

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Disclaimer

This tool is for educational and research purposes only. Please ensure you:

- Comply with the terms of service of each platform
- Respect privacy and data protection laws
- Only scrape publicly available information
- Use the data responsibly and ethically

## Support

For issues and questions:

- Check the [Issues](https://github.com/yourusername/custom-mcp-server/issues) page
- Create a new issue if your problem isn't already reported
- Include relevant error messages and configuration details

## Changelog

### v1.0.0
- Initial release
- LinkedIn, Facebook, Instagram scraping support
- Google Search integration
- Async operations support
- Comprehensive error handling
