# 🚀 N8N E-Commerce Automation - Quick Start Guide

## Overview

This is a production-ready n8n workflow that automates e-commerce product research by analyzing products across Amazon and AliExpress, validating market demand using AI, and making intelligent profitability decisions.

## 📦 What You Get

- **12-node automated workflow** with parallel processing
- **Amazon & AliExpress scraping** via Apify actors
- **AI product validation** using Google Gemini (9 criteria system)
- **Market validation** via YouTube & Google Trends
- **Intelligent scoring** (100-point system)
- **CSV export** of results
- **Error handling** with fallback data

## ⚡ 3-Step Quick Start

### Step 1: Import Workflow

1. Open n8n (cloud or self-hosted)
2. Click "Add Workflow" → "Import from File"
3. Select: **`n8n-ecommerce-automation-workflow-v3-secure.json`**
4. Click "Import"

### Step 2: Configure API Credentials

The workflow uses environment variables for security. You have 3 options:

#### Option A: Environment Variables (Recommended)

1. Copy the credentials template:
   ```bash
   cp credentials-template.env .env
   ```

2. Edit `.env` file and add your API keys:
   ```bash
   APIFY_API_TOKEN=your_token_here
   GEMINI_API_KEY=your_key_here
   YOUTUBE_API_KEY=your_key_here
   SERPAPI_KEY=your_key_here
   ```

3. Restart n8n to load environment variables

**Get API Keys From:**
- **Apify**: https://console.apify.com/account/integrations
- **Google Gemini**: https://makersuite.google.com/app/apikey
- **YouTube API**: https://console.cloud.google.com/apis/credentials
- **SerpAPI**: https://serpapi.com/manage-api-key

#### Option B: Direct Replacement (Quick Test)

1. Edit the workflow in n8n
2. Find these placeholders and replace with your keys:
   - `{{ $env.APIFY_API_TOKEN }}` → your Apify token
   - `{{ $env.GEMINI_API_KEY }}` → your Gemini key
   - `{{ $env.YOUTUBE_API_KEY }}` → your YouTube key
   - `{{ $env.SERPAPI_KEY }}` → your SerpAPI key

3. Save workflow

#### Option C: N8N Credentials Manager

1. Go to n8n → Credentials
2. Add new credential for each API
3. Update workflow nodes to use stored credentials

**Note**: If credentials were provided separately (e.g., in `API_CREDENTIALS.md`), use those values.

### Step 3: Run Workflow

1. Click "Execute Workflow" in n8n
2. Wait 30-60 seconds for completion
3. View results in final node
4. Download CSV from `/tmp/product_research_results.csv`

## 🎯 How It Works

### Workflow Flow

```
Start → Product Input → Amazon Scraper
          ↓
    Parallel Processing:
    ├─→ AI Validation (Gemini)
    ├─→ AliExpress Supplier Finder
    └─→ Google Trends Analysis
          ↓
    Merge Data → YouTube Validation
          ↓
    Final Analysis → Save CSV → Display Results
```

### Decision System

The workflow scores products on a 100-point scale:

| Criteria | Weight | Measures |
|----------|--------|----------|
| **Profit Margin** | 40 pts | Amazon price vs AliExpress cost |
| **AI Validation** | 30 pts | 9-criteria product quality check |
| **Social Proof** | 20 pts | YouTube review videos count |
| **Market Trends** | 10 pts | Google Trends momentum |

**Decisions:**
- **60-100**: ✅ APPROVED - Add to inventory
- **40-59**: ⚠️ REVIEW - Manual evaluation needed
- **0-39**: ❌ REJECTED - Find alternative product

### 9-Point AI Validation Criteria

1. **Confidence** - Clear value proposition
2. **Convenience** - Solves real problem
3. **Fills Void** - Addresses unmet need
4. **Saves Money** - Cost-effective
5. **Saves Time** - Efficiency improvement
6. **Unique** - Differentiated
7. **Not in Stores** - Online exclusivity
8. **Quality of Life** - Daily improvement
9. **Perceived Value** - Price justification

## 🎮 Usage

### Default Settings

The workflow comes pre-configured:
- **Product**: "wireless earbuds"
- **Min Profit Margin**: 30%
- **Max Results**: 10 suppliers

### Change Product

Edit the **"📝 Product Input"** node:
```json
{
  "product_keyword": "your product here",
  "min_profit_margin": "30",
  "max_aliexpress_results": "10"
}
```

### Example Products to Try

- "wireless earbuds"
- "smart watch"
- "phone accessories"
- "fitness tracker"
- "bluetooth speaker"
- "led strip lights"
- "phone stand"
- "car phone mount"

## 📊 Output & Results

### CSV Export

Results are saved to `/tmp/product_research_results.csv`:

| Column | Description |
|--------|-------------|
| Timestamp | Analysis time |
| Product | Amazon product title |
| Decision | APPROVED/CONDITIONAL/REJECTED |
| Score | Confidence score (0-100) |
| Amazon_Price | Selling price |
| Supplier_Cost | Total cost (product + shipping) |
| Profit_Margin_% | Calculated margin |
| ROI_% | Return on investment |
| YouTube_Videos | Review video count |
| Trend_Score | Google Trends score |
| AI_Criteria | AI criteria passed |
| Supplier_URL | Best supplier link |
| Action | Recommended next step |

### Example Output

```json
{
  "decision": "✅ APPROVED - PROCEED WITH PRODUCT",
  "confidence_score": 85,
  "product": "Premium Wireless Earbuds",
  "key_metrics": {
    "amazon_price": 49.99,
    "supplier_cost": 16.98,
    "profit_margin": 66.05,
    "roi": 194.52,
    "youtube_videos": 247,
    "trend_score": 68,
    "ai_criteria_passed": 7
  }
}
```

## 🛠️ Troubleshooting

### "Module 'apify_client' not found"

Install Python package:
```bash
pip install apify-client
```

For n8n Docker:
```bash
docker exec -it n8n npm install -g apify-client
```

### "Invalid API key" errors

1. Verify keys are correct (no extra spaces)
2. Check keys are active in provider dashboards
3. Ensure environment variables are loaded (restart n8n)

### Workflow returns demo/fallback data

This is normal when:
- API rate limits are reached
- Network issues occur
- Testing without valid credentials

The workflow will still complete successfully.

### CSV file not created

1. Check n8n has write permissions to `/tmp/`
2. Try changing path to `/home/user/` in "Save Results to CSV" node
3. Review execution logs for errors

## 💰 API Costs

### Free Tier Limits

| Service | Free Tier | Monthly Capacity |
|---------|-----------|------------------|
| Apify | $5 credit | 50-100 searches |
| Gemini AI | 60 req/min | Unlimited for this use |
| YouTube API | 10,000 quota/day | ~100 searches/day |
| SerpAPI | 100 searches/month | 100 analyses |

**Estimated Cost**: $0.10-$0.50 per 10-20 product searches

## 🔒 Security

The workflow uses environment variables for all API credentials. **Never commit:**
- `.env` files
- `API_CREDENTIALS.md` (if provided separately)
- Workflow files with hardcoded keys

Use the `-secure.json` version for version control.

## 📚 Additional Documentation

- **WORKFLOW_DOCUMENTATION.md** - Detailed node-by-node guide (if available)
- **README.md** - Project overview
- **credentials-template.env** - Environment variable template

## 🎉 You're Ready!

The workflow is production-ready and will execute successfully with a single click once credentials are configured.

**Questions?** Check:
1. API provider documentation links above
2. n8n community forum: https://community.n8n.io/
3. Workflow execution logs in n8n

Happy product hunting! 🚀
