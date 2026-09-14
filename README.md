# Google Analytics 4 MCP Server (GA4) by Insightful Pipe

[![MCP Compatible](https://img.shields.io/badge/MCP-Compatible-blue)](https://insightfulpipe.com/mcp-servers/google-analytics)
[![Insightful Pipe](https://img.shields.io/badge/Insightful_Pipe-MCP_Servers-purple)](https://insightfulpipe.com/mcp-servers)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> **Connect Google Analytics 4 to AI assistants for website analytics and property management.**

Part of the [Insightful Pipe MCP Server Collection](https://insightfulpipe.com/mcp-servers) — Connect Google Analytics 4 to Claude, ChatGPT, Cursor, and other AI assistants using the Model Context Protocol. Query website traffic, analyze user behavior, and get AI-driven insights conversationally.

[![Explore All MCP Servers](https://img.shields.io/badge/Explore_All-MCP_Servers-blue?style=for-the-badge)](https://insightfulpipe.com/mcp-servers)

![Google Analytics MCP Server](https://insightfulpipe.com/images/google-analytics.svg)

## MCP Server URL

```
https://google-analytics.insightfulmcp.com/
```

## What is Google Analytics 4 MCP?

Google Analytics 4 MCP is a **remote Model Context Protocol server** that enables AI assistants to query and analyze your GA4 data. This powerful integration allows you to:

- Ask questions about website traffic in natural language
- Analyze user behavior, conversions, and engagement
- Generate custom reports through conversation
- Get AI-powered insights and recommendations
- Access traffic sources, pages, events, and demographics

## Installation

### Claude

1. Copy the MCP Server URL: `https://google-analytics.insightfulmcp.com/`
2. Open [Claude Connectors Settings](https://claude.ai/settings/connectors)
3. Scroll to the bottom and click **Add custom connector**
4. Paste the URL and click **Add**
5. Click **Connect** on the connector to start authorization
6. Click **Authorize access** in the browser to complete the connection

### ChatGPT

Custom MCP servers are added through ChatGPT's **Developer mode**. Availability depends on your ChatGPT plan, and workspace admins may need to allow it.

1. Turn on **Developer mode** in ChatGPT settings
2. Create a new app for a remote MCP server and paste the URL: `https://google-analytics.insightfulmcp.com/`
3. Authorize with your InsightfulPipe account

See OpenAI's guide: [Developer mode and MCP apps in ChatGPT](https://help.openai.com/en/articles/12584461-developer-mode-and-mcp-apps-in-chatgpt)

### Claude Code

```bash
claude mcp add --transport http google-analytics https://google-analytics.insightfulmcp.com/
```

### Cursor

Add the server to `~/.cursor/mcp.json` (all projects) or `.cursor/mcp.json` (one project):

```json
{
  "mcpServers": {
    "google-analytics": {
      "url": "https://google-analytics.insightfulmcp.com/"
    }
  }
}
```

Then authorize the connection when Cursor prompts you.

## Available Actions

62 actions: 26 read, 36 write.

### Read Actions (26)

<details>
<summary>Show all 26 read actions</summary>

| Action | Description |
|--------|-------------|
| `ecommerce` | E-commerce performance data including transactions, revenue, and product metrics |
| `events` | Event tracking data including event names, counts, and user engagement |
| `geo` | Geographic performance data including country, region, city, and language |
| `get_audience` | Get one audience, including its filter clauses |
| `get_bigquery_link` | Get one BigQuery export link |
| `get_channel_group` | Get one channel group, including its grouping rules |
| `get_custom_dimension` | Get a single GA4 custom dimension by id |
| `get_custom_metric` | Get a single GA4 custom metric by id |
| `get_data_retention_settings` | Read a GA4 property's event and user data retention settings |
| `get_data_stream` | Fetch one data stream, including its Measurement ID |
| `get_enhanced_measurement_settings` | Read the enhanced measurement settings of a web data stream |
| `get_key_event` | Get a single GA4 key event by id |
| `get_property` | Fetch a GA4 property's settings (name, time zone, currency, industry) |
| `get_report` | Execute GA4 runReport with arbitrary metrics and dimensions |
| `list_audiences` | List the audiences on a property |
| `list_bigquery_links` | List the BigQuery export links on a property |
| `list_channel_groups` | List the channel groups on a property |
| `list_custom_dimensions` | List the GA4 custom dimensions on a property |
| `list_custom_metrics` | List the GA4 custom metrics on a property |
| `list_data_streams` | List a GA4 property's data streams (web, Android, iOS) |
| `list_google_ads_links` | List the Google Ads accounts linked to a GA4 property |
| `list_key_events` | List the GA4 key events (conversions) on a property |
| `pages` | Page-level performance data including views, engagement, and user behavior |
| `tech` | Technology breakdown data including browser, device, OS, and platform |
| `traffic_sources` | Traffic acquisition data including source, medium, campaign, and channel groupings |
| `user_demographics` | User demographic data including age, gender, interests, and user type |

</details>

### Write Actions (36)

<details>
<summary>Show all 36 write actions</summary>

| Action | Description |
|--------|-------------|
| `acknowledge_user_data_collection` | Attest the User Data Collection acknowledgement on a property, which GA4 requires before Measurement Protocol secrets can be created |
| `archive_audience` | Archive an audience so it stops collecting members |
| `archive_custom_dimension` | Archive a GA4 custom dimension (frees a slot; not a hard delete) |
| `archive_custom_metric` | Archive a GA4 custom metric (frees a slot; not a hard delete) |
| `create_audience` | Create an audience from a set of filter clauses |
| `create_bigquery_link` | Link a GA4 property to a BigQuery project for raw event export |
| `create_channel_group` | Create a custom channel group from grouping rules |
| `create_custom_dimension` | Create a GA4 custom dimension from an event parameter |
| `create_custom_metric` | Create a GA4 custom metric from an event parameter |
| `create_data_stream` | Create a web, Android or iOS data stream on a GA4 property |
| `create_google_ads_link` | Link a Google Ads account to a GA4 property |
| `create_key_event` | Create a GA4 key event (conversion) for an event name |
| `create_measurement_protocol_secret` | Create a Measurement Protocol secret so server-side events can be sent to a stream |
| `create_property` | Create a new GA4 property under an account |
| `delete_bigquery_link` | Remove a BigQuery export link |
| `delete_channel_group` | Delete a custom channel group |
| `delete_data_stream` | Delete a data stream from a GA4 property |
| `delete_google_ads_link` | Unlink a Google Ads account from a GA4 property |
| `delete_key_event` | Delete a GA4 key event (conversion) |
| `delete_measurement_protocol_secret` | Delete a Measurement Protocol secret, revoking server-side sends that use it |
| `delete_property` | Soft-delete (trash) the connected GA4 property |
| `get_measurement_protocol_secret` | Get one Measurement Protocol secret, including its secret value |
| `list_accounts` | List the GA4 accounts this connection can administer |
| `list_measurement_protocol_secrets` | List the Measurement Protocol secrets on a data stream |
| `update_audience` | Rename an audience or change its description |
| `update_bigquery_link` | Change what a BigQuery export link exports |
| `update_channel_group` | Change a channel group's name, description, rules, or primary flag |
| `update_custom_dimension` | Update a GA4 custom dimension's display name / description |
| `update_custom_metric` | Update a GA4 custom metric's display name / description |
| `update_data_retention_settings` | Set how long a GA4 property retains event and user data |
| `update_data_stream` | Update a data stream's display name or default URI |
| `update_enhanced_measurement_settings` | Turn enhanced measurement events (scrolls, outbound clicks, site search, video, downloads) on or off |
| `update_google_ads_link` | Update a Google Ads link's personalized-advertising setting |
| `update_key_event` | Update a GA4 key event's counting method or default value |
| `update_measurement_protocol_secret` | Rename a Measurement Protocol secret |
| `update_property` | Update a GA4 property's display name, time zone, currency or industry |

</details>

## Control What Your AI Can Do

You decide what AI agents can do with each connected account:

- **Turn individual actions on or off** for every connected account, so agents only see the actions you allow.
- **Connect as Read-only or Read & Write.** A read-only connection can only enable read actions.
- **Destructive actions stay off by default.** Actions such as deletes are disabled until an admin enables them.
- **Team access per account.** Restricted team members only use the accounts they are granted, with the read actions enabled on them.

## Usage Examples

### Traffic Analysis

```
"Show me website traffic for the last 30 days compared to the previous period"
```

### Acquisition Insights

```
"Which traffic sources have the highest conversion rate?"
```

### Page Performance

```
"What are my top 10 landing pages by engagement rate?"
```

### E-commerce Analytics

```
"What's our revenue trend this quarter and which products are selling best?"
```

### User Behavior

```
"How do mobile users behave differently from desktop users?"
```

### Custom Reports

```
"Run a report showing sessions by country and device category"
```

## Supported Metrics

| Metric | Description |
|--------|-------------|
| Users | Unique visitors to your site |
| Sessions | Total website visits |
| Pageviews | Total page views |
| Engagement Rate | Percentage of engaged sessions |
| Average Session Duration | Time spent on site |
| Bounce Rate | Single-page sessions |
| Conversions | Goal completions |
| Revenue | E-commerce revenue (if applicable) |

## Why Google Analytics 4 MCP?

### For Digital Marketers
- **Instant answers** - No more complex report building
- **Natural language** - Ask questions like you're talking to an analyst
- **Cross-channel insights** - Combine with ad platform data

### For Website Owners
- **Understand your audience** - Deep user behavior insights
- **Track goals** - Monitor what matters to your business
- **Identify opportunities** - AI-powered recommendations

### For Analysts
- **Faster exploration** - Query data conversationally
- **Automated insights** - AI surfaces important patterns
- **Flexible reporting** - Generate any report through chat

## Security & Privacy

- **Official Google Analytics API** - Direct integration with Google's API
- **OAuth 2.0** - Secure Google authentication
- **Data encryption** - Secure data transmission

## Ready-Made Skills and Prompts

- [Claude skills for measurement and analytics](https://insightfulpipe.com/marketing-claude-skills/measurement) — ready-made skills that run on your connected data

## Explore More MCP Servers by Insightful Pipe

Visit **[insightfulpipe.com/mcp-servers](https://insightfulpipe.com/mcp-servers)** to discover our full collection of MCP servers for marketing and analytics.

### Google MCP Servers
- [Google Search Console MCP](https://insightfulpipe.com/mcp-servers/google-search-console) - SEO analytics
- [Google Ads MCP](https://insightfulpipe.com/mcp-servers/google-ads) - Advertising data
- [Google My Business MCP](https://insightfulpipe.com/mcp-servers/google-my-business) - Local SEO

### SEO & Performance MCP Servers
- [PageSpeed MCP](https://insightfulpipe.com/mcp-servers/pagespeed) - Core Web Vitals
- [Web Crawler MCP](https://insightfulpipe.com/mcp-servers/crawler) - SEO auditing

**[View All MCP Servers →](https://insightfulpipe.com/mcp-servers)**

## Resources

- [Documentation](https://insightfulpipe.com/docs/connectors-google-analytics)
- [Video Tutorial](https://www.youtube.com/playlist?list=PLJNzvjxzI5Xwe__BJJLAelSF0ewO3mEFk)
- [InsightfulPipe Blog](https://insightfulpipe.com/blog)

## Support

- **Documentation**: [insightfulpipe.com/docs](https://insightfulpipe.com/docs)
- **All MCP Servers**: [insightfulpipe.com/mcp-servers](https://insightfulpipe.com/mcp-servers)
- **Email**: support@insightfulpipe.com

---

**[Insightful Pipe](https://insightfulpipe.com)** — AI-powered marketing analytics through MCP servers. [Explore all integrations →](https://insightfulpipe.com/mcp-servers)

## License

MIT License - see [LICENSE](LICENSE) for details.
