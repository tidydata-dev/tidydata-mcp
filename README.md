# TidyData MCP Server

**49 read-only tools for AI assistants**: public holidays and business days for 100+ countries, currency conversion (ECB rates), time zones, sunrise & moon, DNS / WHOIS / domain availability, web page inspection (status, redirects, SEO, links, tables, tech stack), geodata (cities, airports, postal codes, distances), nutrition facts, dictionary, spell check, summaries and calculators.

Remote server, nothing to install. Works with Claude, ChatGPT, Cursor, VS Code, Windsurf and any MCP client.

```
https://tidydata-api.tidydata.workers.dev/mcp
```

- Transport: Streamable HTTP (stateless JSON)
- Authentication: none
- **Free: 100 tool calls per day per user.** Need more? Use the same APIs with a plan on RapidAPI, Zyla or api.market → [pricing](https://developers.tidydata.workers.dev/pricing/)

## Connect

**Claude (claude.ai / Claude Desktop):** Settings → Connectors → *Add custom connector* → paste the URL above.

**Claude Code:**
```bash
claude mcp add --transport http tidydata https://tidydata-api.tidydata.workers.dev/mcp
```

**ChatGPT:** Settings → Apps & Connectors → *Create* (developer mode) → paste the URL above, authentication *None*.

**Cursor** (`~/.cursor/mcp.json`) · **Windsurf** · **Cline**:
```json
{
  "mcpServers": {
    "tidydata": { "url": "https://tidydata-api.tidydata.workers.dev/mcp" }
  }
}
```

**VS Code** (`.vscode/mcp.json`):
```json
{
  "servers": {
    "tidydata": { "type": "http", "url": "https://tidydata-api.tidydata.workers.dev/mcp" }
  }
}
```

Clients that only speak stdio:
```bash
npx -y mcp-remote https://tidydata-api.tidydata.workers.dev/mcp
```

## Example prompts

- *"Is 8 December 2026 a public holiday in Spain, and how many business days are there in December?"*
- *"Convert 250 USD to EUR at today's ECB rate."*
- *"Check the DNS, SSL redirects and security headers of example.com."*
- *"Is tidyplanner.com available? If not, who owns it?"*
- *"Sunrise and golden hour in Lisbon tomorrow."*
- *"Calories and protein of 200 g chicken breast, 100 g rice and 1 tbsp olive oil."*

## Tools

### 📅 Dates & time

| Tool | What it does |
|---|---|
| `public_holidays` | Public holidays of a country |
| `is_public_holiday` | Is this date a public holiday? |
| `business_days_between` | Business days between two dates |
| `add_business_days` | Add business days to a date |
| `convert_time_zone` | Time zone converter / world clock |
| `timezone_by_coordinates` | Time zone of a latitude/longitude |
| `sunrise_sunset` | Sunrise, sunset, twilight and golden hour |
| `moon_phase` | Moon phase and illumination |
| `convert_calendar_date` | Convert a date to Islamic, Hebrew, Chinese… calendars |

### 💱 Money

| Tool | What it does |
|---|---|
| `convert_currency` | Convert currency (ECB rates) |
| `exchange_rates` | Latest exchange rates |
| `validate_iban` | Validate and parse an IBAN |
| `loan_calculator` | Loan / mortgage payments and schedule |

### 🌐 Web & domains

| Tool | What it does |
|---|---|
| `dns_lookup` | DNS records of a domain |
| `dns_propagation` | DNS propagation across global resolvers |
| `domain_whois` | Domain registration info (WHOIS/RDAP) |
| `domain_availability` | Is a domain name available? |
| `check_url_status` | HTTP status and redirect chain of a URL |
| `expand_short_url` | Expand a shortened link |
| `link_preview` | Title, description and image of a web page |
| `website_technologies` | Technologies used by a website |
| `seo_audit` | On-page SEO audit of a URL |
| `security_headers_check` | Security headers grade of a website |
| `extract_links` | Links found on a web page |
| `extract_html_tables` | Tables of a web page as JSON |
| `sitemap_urls` | URLs listed in a website's sitemap |
| `robots_txt_check` | Is a URL allowed by robots.txt? |
| `ip_lookup` | Owner, network and country of an IP address |

### 🗺️ Places

| Tool | What it does |
|---|---|
| `country_info` | Country data (capital, currency, languages…) |
| `airport_info` | Airport by IATA/ICAO code |
| `airport_search` | Search airports by name or city |
| `airport_distance` | Distance between two airports |
| `city_search` | Find a city (coordinates, population, country) |
| `reverse_geocode` | Nearest city to a latitude/longitude |
| `distance_between_places` | Distance between two places or coordinates |
| `postal_code_lookup` | Place of a postal / ZIP code |

### 📝 Text & language

| Tool | What it does |
|---|---|
| `dictionary_define` | English definitions of a word |
| `synonyms` | Synonyms of an English word |
| `rhymes` | Rhymes of an English word |
| `spell_check` | English spell check with suggestions |
| `summarize` | Summarize a text or web page |
| `extract_keywords` | Keywords of a text (58 languages) |
| `detect_language` | Language of a text |

### 🧮 Other

| Tool | What it does |
|---|---|
| `nutrition_search` | Nutrition facts of foods (USDA) |
| `nutrition_calculate` | Calories and macros of a list of ingredients |
| `decode_vin` | Decode a vehicle VIN |
| `convert_units` | Convert units of measure |
| `hash_text` | MD5 / SHA hashes of a text |
| `generate_password` | Secure random passwords |

All tools are read-only (`readOnlyHint: true`). Full API documentation: [developers.tidydata.workers.dev](https://developers.tidydata.workers.dev/)

## Data sources

European Central Bank reference rates · date-holidays (CC BY 3.0) · GeoNames (CC BY 4.0) · OurAirports (public domain) · USDA FoodData Central (public domain) · WordNet / CMU dictionaries · SCOWL word lists · public DNS resolvers and RDAP.

## More from TidyData

- Printables shop: [etsy.com/shop/TidyData](https://www.etsy.com/shop/TidyData)
- Free web tools: [tidydata-tools.tidydata.workers.dev](https://tidydata-tools.tidydata.workers.dev/about/)
- Apify actors: [apify.com/tidydata](https://apify.com/tidydata?fpr=wtg6qt)

## License

MIT for this repository (documentation and configuration). The hosted service is free within the daily limit above.

💻 Code examples (curl, Python, JavaScript, Postman, OpenAPI) for every API: [tidydata-api-examples](https://github.com/tidydata-dev/tidydata-api-examples)

---
<sub>Links to apify.com include our affiliate ID: if you start a paid Apify plan through them, Apify pays TidyData a commission at no extra cost to you.</sub>
