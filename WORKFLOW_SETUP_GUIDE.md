# N8N E-Commerce Automation Workflow - Setup Guide

## Overview
This n8n workflow automates product research for dropshipping by validating Amazon products against AliExpress suppliers, using AI analysis, trend data, and YouTube validation.

## Features
- ✅ Amazon product scraping and data extraction
- ✅ AI-powered validation using Google Gemini (9 criteria analysis)
- ✅ Google Trends analysis via SerpAPI
- ✅ AliExpress product matching via Apify
- ✅ YouTube validation (reviews/unboxing videos)
- ✅ Advanced profit margin calculations
- ✅ Automated decision making (PASS/FAIL/REVIEW)
- ✅ CSV export with detailed metrics
- ✅ HTML report generation
- ✅ Error handling and logging

## Prerequisites

### Required Software
- n8n installed (version 0.200.0 or higher)
- Node.js v16+ (for running n8n)

### API Keys Required
The workflow requires the following API keys (you need to configure these):

1. **Gemini API** (Free tier available)
   - Get your key from: https://makersuite.google.com/app/apikey
   - Used for: AI product validation

2. **YouTube Data API v3** (Free tier: 10,000 units/day)
   - Get your key from: https://console.cloud.google.com/apis/library/youtube.googleapis.com
   - Used for: Finding product review videos

3. **SerpAPI** (Free trial: 100 searches)
   - Get your key from: https://serpapi.com/users/sign_up
   - Used for: Google Trends data

4. **Apify** (Free tier: $5 credit)
   - Get your key from: https://console.apify.com/account/integrations
   - Used for: AliExpress product scraping

5. **ScraperAPI** (Free tier: 1,000 requests)
   - Get your key from: https://www.scraperapi.com/signup
   - Used for: Amazon product scraping

## Installation Steps

### 1. Import the Workflow

```bash
# Option A: Import via n8n UI
1. Open n8n (http://localhost:5678)
2. Click "Workflows" in the left sidebar
3. Click "Import from File"
4. Select "n8n-ecommerce-automation-workflow.json"
5. Click "Import"

# Option B: Import via CLI
n8n import:workflow --input=n8n-ecommerce-automation-workflow.json
```

### 2. Configure ScraperAPI Key

After importing, you need to add your ScraperAPI key:

1. Open the workflow in n8n
2. Click on the "Amazon Product Scraper" node
3. Find the query parameter with name `api_key`
4. Replace `SCRAPER_API_KEY_PLACEHOLDER` with your actual ScraperAPI key
5. Save the workflow

**Get ScraperAPI Key:**
- Visit: https://www.scraperapi.com/
- Sign up for free account
- Copy your API key from dashboard
- Free tier includes 1,000 requests/month

### 3. Verify Node Dependencies

The workflow requires these n8n nodes (all are built-in):
- Manual Trigger
- HTTP Request
- Code (JavaScript)
- Set
- IF (Conditional)
- Merge

No additional node installations needed!

### 4. Test the Workflow

```bash
# Start n8n
n8n start

# Or if using Docker:
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
```

## Usage Guide

### Basic Workflow Execution

1. **Open the workflow** in n8n editor
2. **Click "Execute Workflow"** button
3. **Fill in the form:**
   - **Amazon URL**: Full Amazon product URL (e.g., `https://www.amazon.com/dp/B08XYZ123`)
   - **Search Term**: Alternative search term (optional)
   - **Category**: Select from dropdown (Electronics, Home, Beauty, Sports, Pets)
4. **Click "Execute"** and wait for results

### Input Options

#### Amazon URL Format
```
https://www.amazon.com/product-name/dp/B08XYZ123
https://www.amazon.com/dp/B08XYZ123
```

#### Categories
- **Electronics**: Gadgets, accessories, tech products
- **Home**: Home decor, kitchen items, organization
- **Beauty**: Skincare, makeup, personal care
- **Sports**: Fitness equipment, outdoor gear
- **Pets**: Pet supplies, toys, accessories

### Understanding the Output

#### CSV Output
Location: `/tmp/product_research_results.csv`

Columns include:
- Product identification (name, ASIN, URLs)
- Pricing data (Amazon, AliExpress, profit margins)
- AI validation scores (9 criteria)
- Trend analysis
- YouTube metrics
- Final decision (PASS/FAIL/REVIEW)

#### HTML Report
Location: `/tmp/product_report_[ASIN]_[timestamp].html`

Contains:
- Visual status indicator (color-coded)
- Detailed profit breakdown
- AI score visualization
- Market analysis charts
- Final verdict with reasoning

### Workflow Execution Flow

```
1. Manual Trigger
   ↓
2. Form Input Collection
   ↓
3. Amazon Product Scraper → Parse Data → Validate
   ↓ (if valid)
4. Parallel API Calls:
   ├─ Gemini AI Validation
   ├─ Google Trends Analysis
   ├─ AliExpress Product Search
   └─ YouTube Validation
   ↓
5. Merge All Data
   ↓
6. Final Aggregation & Decision Logic
   ↓
7. Outputs:
   ├─ Save to CSV
   └─ Generate HTML Report
```

## Validation Criteria

### AI Validation (9 Criteria)
Each scored 0-10:

1. **Profit Potential**: Price point analysis ($15-$150 ideal)
2. **Shipping Feasibility**: Size and weight considerations
3. **Brand Risk**: Generic vs branded products
4. **Market Saturation**: Competition level
5. **Visual Appeal**: Product photography quality
6. **Problem Solving**: Clear value proposition
7. **Impulse Buy Factor**: Spontaneous purchase likelihood
8. **Durability Concerns**: Product quality expectations
9. **Seasonal Dependency**: Year-round vs seasonal demand

### Pass/Fail Logic

**PASS Requirements:**
- ✅ AI average score ≥ 6/10
- ✅ Profit margin ≥ 30%
- ✅ Profit dollar amount ≥ $5
- ✅ Trend not declining
- ✅ YouTube videos found (market validation)
- ✅ Price range $15-$150
- ✅ AliExpress suppliers available
- ✅ At least 5 out of 6 checks passed

**REVIEW Status:**
- 4 out of 6 checks passed
- Total score ≥ 5/10
- Borderline cases needing manual review

**FAIL Status:**
- Less than 4 checks passed
- Total score < 5/10

## Troubleshooting

### Common Issues

#### 1. Amazon Scraper Returns No Data
**Symptoms:** "N/A" values for product title/price

**Solutions:**
- Check if Amazon URL is valid
- Verify ScraperAPI key is configured
- Try alternative scraping method (see alternatives below)
- Amazon may be blocking - wait and retry

**Alternative Amazon Scraping:**
```javascript
// Use Apify's Amazon Scraper instead
// Replace Amazon Product Scraper node with:
URL: https://api.apify.com/v2/acts/vaclavrut~amazon-crawler/run-sync
Method: POST
Body: {
  "productUrls": ["YOUR_AMAZON_URL"],
  "maxItems": 1,
  "country": "US"
}
```

#### 2. Gemini API Errors
**Symptoms:** AI validation fails

**Solutions:**
- Verify API key is valid
- Check quota limits (free tier restrictions)
- Reduce request frequency
- Check response parsing in "Parse Gemini Response" node

#### 3. AliExpress No Results
**Symptoms:** 0 matches found

**Solutions:**
- Product title may be too specific - try simplifying
- Check Apify credits balance
- Try manual search on AliExpress to verify product exists
- Adjust search parameters in node configuration

#### 4. YouTube API Quota Exceeded
**Symptoms:** 403 error from YouTube API

**Solutions:**
- Free tier allows 10,000 units/day
- Each search costs ~100 units
- Wait 24 hours for quota reset
- Use alternative YouTube Data API key

#### 5. SerpAPI Rate Limit
**Symptoms:** 429 error from SerpAPI

**Solutions:**
- Free trial has 100 searches total
- Upgrade to paid plan or
- Use alternative Google Trends method (see below)

**Alternative Trends Method:**
```javascript
// Use unofficial Google Trends endpoint
URL: https://trends.google.com/trends/api/dailytrends
Method: GET
Parameters: {
  geo: "US",
  hl: "en-US"
}
```

### Error Logging

All errors are logged to: `/tmp/product_research_errors.csv`

Columns:
- timestamp
- error_type
- error_message
- amazon_url
- search_term

## Advanced Configuration

### Adjusting Timeout Values

For slower APIs, increase timeout in HTTP Request nodes:
```json
"options": {
  "timeout": 60000,  // 60 seconds
  "retry": {
    "maxRetries": 3,
    "retryInterval": 2000
  }
}
```

### Modifying AI Prompt

Edit the Gemini AI Validation node to customize scoring criteria:
```javascript
// In the jsonBody parameter
"text": "Your custom prompt here..."
```

### Changing Profit Thresholds

Edit "Final Aggregation & Decision" node:
```javascript
// Line ~45
const profitPct = aliexpressData.profit_analysis.profit_percentage;
if (profitPct >= 50) scores.profit_score = 10;  // Adjust threshold
else if (profitPct >= 40) scores.profit_score = 8;
// ... etc
```

### Adding Custom Criteria

1. Modify "Gemini AI Validation" to add new criteria
2. Update "Parse Gemini Response" to extract new scores
3. Adjust "Final Aggregation & Decision" to include in total score
4. Update CSV headers in "Save to CSV" node

## Performance Optimization

### Parallel Execution
The workflow runs these in parallel for speed:
- Gemini AI Validation
- Google Trends
- AliExpress Search
- YouTube Validation

Total execution time: ~30-60 seconds per product

### Batch Processing

To process multiple products:
1. Create a spreadsheet with Amazon URLs
2. Add "Spreadsheet File" trigger node
3. Connect to existing workflow
4. Results will accumulate in CSV

### Caching

To avoid redundant API calls:
```javascript
// Add to "Parse Amazon Data" node
const cache = {}; // Store in workflow static data
if (cache[asin]) {
  return cache[asin];
}
// ... scrape logic
cache[asin] = productData;
```

## API Rate Limits & Costs

| Service | Free Tier | Rate Limit | Cost After |
|---------|-----------|------------|------------|
| ScraperAPI | 1,000 req/mo | 5 req/sec | $29/mo (10K) |
| Gemini API | 60 req/min | - | Free (limits apply) |
| YouTube API | 10,000 units/day | 100 units/search | Pay-as-you-go |
| SerpAPI | 100 searches | - | $50/mo (5K) |
| Apify | $5 credit | Varies | Pay-as-you-go |

**Daily Capacity (Free Tier):**
- ~1,000 products/month (limited by ScraperAPI)
- ~100 products/day (limited by YouTube quota)
- ~100 products total (limited by SerpAPI trial)

## Security Best Practices

1. **API Keys**: Store in environment variables
```bash
# In n8n settings, use environment variables
GEMINI_API_KEY={{ $env.GEMINI_API_KEY }}
```

2. **Never commit workflow JSON with real API keys**
3. **Use n8n credentials manager** for production
4. **Rotate API keys regularly**
5. **Monitor API usage** to detect abuse

## Workflow Customization

### For Different Marketplaces

**eBay instead of Amazon:**
- Replace Amazon scraper with eBay scraper
- Adjust parsing logic for eBay HTML structure

**Walmart, Target, etc:**
- Same approach as eBay
- May need different scraping service

**Different AliExpress alternatives:**
- DHgate
- Banggood
- 1688.com (Chinese wholesale)

### For Different Business Models

**Print on Demand:**
- Remove shipping cost calculations
- Add design validation
- Check Printful/Printify pricing

**Wholesale:**
- Adjust profit margin requirements (lower)
- Focus on bulk order pricing
- Check MOQ (Minimum Order Quantity)

**Retail Arbitrage:**
- Compare multiple retailer prices
- Factor in sales tax
- Include Amazon FBA fees

## Support & Resources

### Official Documentation
- n8n Docs: https://docs.n8n.io/
- Workflow Templates: https://n8n.io/workflows

### API Documentation
- Gemini API: https://ai.google.dev/docs
- YouTube Data API: https://developers.google.com/youtube/v3
- SerpAPI: https://serpapi.com/google-trends-api
- Apify: https://docs.apify.com/

### Community
- n8n Community: https://community.n8n.io/
- n8n Discord: https://discord.gg/n8n

### Troubleshooting Resources
- Check `/tmp/product_research_errors.csv` for logged errors
- Review n8n execution logs
- Test individual nodes with sample data

## License
This workflow is provided as-is for educational and commercial use.

## Version History
- v1.0.0 (2025-11-17): Initial release
  - Full automation pipeline
  - 9-criteria AI validation
  - Multi-source data aggregation
  - CSV and HTML outputs
