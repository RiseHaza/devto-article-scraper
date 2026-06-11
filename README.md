[Devto Article Scraper](https://apify.com/openclawmara/devto-article-scraper?fpr=data)

# DEV.to Article Scraper

Scrape articles, comments, tags, and user data from [DEV.to](https://dev.to) — the largest developer community platform. Uses the official Forem/DEV.to API for reliable, fast data extraction.

## What can it do?

- **Latest articles** — Get the newest articles published on DEV.to
- **Top/trending articles** — Scrape top-rated articles by reactions and engagement
- **Articles by tag** — Filter by any tag (javascript, python, react, webdev, etc.)
- **Search** — Full-text search across article titles and content
- **User articles** — Get all articles from a specific author
- **Single article** — Full content (HTML + Markdown) for a specific article
- **Comments** — Nested comment threads for any article

## Why use this scraper?

- ⚡ **Fast** — Uses the official API, no browser needed
- 🔄 **Reliable** — Auto-retry with exponential backoff on rate limits
- 📊 **Rich data** — Reactions, comments count, reading time, tags, author info
- 📝 **Full content** — Both HTML and Markdown body for single articles
- 🧵 **Nested comments** — Complete comment trees with author metadata

## Input examples

### Get latest 50 articles

```
{
  "mode": "latest_articles",
  "maxItems": 50
}
```

### Search for AI articles

```
{
  "mode": "search",
  "searchQuery": "artificial intelligence",
  "maxItems": 30
}
```

### Get articles by tag

```
{
  "mode": "articles_by_tag",
  "tag": "python",
  "maxItems": 100
}
```

### Get all articles from a user

```
{
  "mode": "user_articles",
  "username": "ben",
  "maxItems": 50
}
```

### Get single article with full content

```
{
  "mode": "single_article",
  "articleId": 123456
}
```

### Get comments for an article

```
{
  "mode": "comments",
  "articleIdForComments": 123456
}
```

## Output example

```
{
  "id": 123456,
  "title": "Building a REST API with Python",
  "description": "A step-by-step guide to building REST APIs",
  "url": "https://dev.to/author/building-rest-api-python",
  "tags": "python, api, tutorial, beginners",
  "public_reactions_count": 245,
  "comments_count": 32,
  "reading_time_minutes": 8,
  "published_at": "2026-03-01T10:00:00Z",
  "username": "author",
  "user_name": "Author Name"
}
```

## Use cases

- **Content research** — Find trending topics and popular articles in your niche
- **Competitor analysis** — Track what content performs best on DEV.to
- **Data journalism** — Analyze developer community trends
- **Lead generation** — Find active developers writing about specific technologies
- **Content aggregation** — Build curated newsletters or feeds from DEV.to data

## Pricing

This actor is free to use. You only pay for Apify platform usage (compute and storage).

## Limitations

- DEV.to API rate limit: ~30 requests/second (handled automatically with retries)
- Maximum 1000 articles per run (API pagination limit)
- Comments are returned as flat list with parent_id for nesting