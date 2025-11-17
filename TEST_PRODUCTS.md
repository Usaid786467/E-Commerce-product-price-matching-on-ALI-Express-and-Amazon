# Test Products for N8N E-Commerce Automation

This document contains sample products to test the workflow with expected outcomes.

## Test Case 1: LED Strip Lights (Expected: PASS)

### Input Data
```
Amazon URL: https://www.amazon.com/dp/B07XV5MFKY
Search Term: LED strip lights RGB
Category: Electronics
```

### Expected Results
- **Status**: PASS ✅
- **Profit Margin**: 40-60%
- **AI Score**: 7-8/10
- **Trend**: Stable or Rising
- **YouTube Videos**: 20+ reviews

### Why It Should Pass
- ✅ Popular product category
- ✅ High profit margins ($20-30 Amazon, $5-10 AliExpress)
- ✅ Light and easy to ship
- ✅ Generic/unbranded acceptable
- ✅ High visual appeal
- ✅ Consistent demand (home improvement)
- ✅ Many suppliers available
- ✅ Strong YouTube presence

### Sample Output Data
```csv
timestamp,product_name,amazon_price,aliexpress_price,profit_margin,profit_percentage,final_status
2025-11-17T10:00:00Z,LED Strip Lights 50ft RGB,29.99,8.50,21.49,71.7,PASS
```

---

## Test Case 2: Wireless Earbuds (Expected: PASS)

### Input Data
```
Amazon URL: https://www.amazon.com/dp/B08C7KG5LP
Search Term: Bluetooth wireless earbuds
Category: Electronics
```

### Expected Results
- **Status**: PASS ✅
- **Profit Margin**: 35-50%
- **AI Score**: 7-9/10
- **Trend**: Rising
- **YouTube Videos**: 50+ reviews

### Why It Should Pass
- ✅ Extremely popular category
- ✅ Good margins ($30-50 Amazon, $8-15 AliExpress)
- ✅ Small and lightweight
- ✅ Generic options widely accepted
- ✅ Impulse buy item
- ✅ Growing market
- ✅ Tons of suppliers
- ✅ Heavy YouTube review presence

### Potential Issues
- ⚠️ High competition
- ⚠️ Brand consciousness (some buyers prefer name brands)
- ⚠️ Quality concerns (returns risk)

---

## Test Case 3: Pet Grooming Glove (Expected: PASS)

### Input Data
```
Amazon URL: https://www.amazon.com/dp/B01MROZ326
Search Term: pet grooming glove cat dog
Category: Pets
```

### Expected Results
- **Status**: PASS ✅
- **Profit Margin**: 60-80%
- **AI Score**: 8-9/10
- **Trend**: Stable
- **YouTube Videos**: 10-20 demonstrations

### Why It Should Pass
- ✅ Excellent profit margins ($15-20 Amazon, $2-4 AliExpress)
- ✅ Very light and cheap shipping
- ✅ Solves clear problem (pet hair removal)
- ✅ Low seasonality (year-round pet ownership)
- ✅ Easy to demonstrate value
- ✅ Low return rates
- ✅ Multiple suppliers
- ✅ Good visual appeal in marketing

### Notes
This is an "ideal" dropshipping product that checks almost all boxes.

---

## Test Case 4: Nike Running Shoes (Expected: FAIL)

### Input Data
```
Amazon URL: https://www.amazon.com/dp/B08QZMP7NH
Search Term: Nike Air Max running shoes
Category: Sports
```

### Expected Results
- **Status**: FAIL ❌
- **Profit Margin**: Negative or very low
- **AI Score**: 2-4/10
- **Brand Risk**: Very High
- **Trend**: Irrelevant (branded)

### Why It Should Fail
- ❌ **BRANDED PRODUCT** - Cannot sell Nike replicas legally
- ❌ Trademark infringement risk
- ❌ Amazon actively polices branded products
- ❌ Customer expectations for authentic Nike
- ❌ Legal liability
- ❌ Account suspension risk
- ❌ Cannot compete with official retailers

### AI Red Flags Expected
```
- "Major brand - high trademark risk"
- "Legal issues with selling replicas"
- "Cannot compete with official Nike pricing"
- "High return rate for non-authentic items"
```

---

## Test Case 5: Phone Case (Expected: REVIEW)

### Input Data
```
Amazon URL: https://www.amazon.com/dp/B08XXXX
Search Term: iPhone 15 case clear
Category: Electronics
```

### Expected Results
- **Status**: REVIEW ⚠️
- **Profit Margin**: 50-70%
- **AI Score**: 5-6/10
- **Competition**: Very High
- **Trend**: Declining (as model ages)

### Why It's Borderline
- ✅ Great margins ($15-25 Amazon, $1-3 AliExpress)
- ✅ Tiny and light (shipping)
- ✅ Easy to source
- ⚠️ **EXTREME competition** (saturated market)
- ⚠️ Model-specific (iPhone 15 eventually outdated)
- ⚠️ Customer expectations vary wildly
- ⚠️ Quality inconsistency issues
- ⚠️ Many sellers = price wars

### Manual Review Needed
Decision depends on:
- Unique design/feature?
- Ability to differentiate marketing?
- Willingness to compete on price?

---

## Test Case 6: Portable Blender (Expected: PASS)

### Input Data
```
Amazon URL: https://www.amazon.com/dp/B088TFNQ23
Search Term: portable blender USB rechargeable
Category: Home
```

### Expected Results
- **Status**: PASS ✅
- **Profit Margin**: 45-65%
- **AI Score**: 7-8/10
- **Trend**: Rising
- **YouTube Videos**: 30+ reviews/demos

### Why It Should Pass
- ✅ Trending product (fitness/health niche)
- ✅ Good margins ($35-45 Amazon, $12-18 AliExpress)
- ✅ Solves clear problem (on-the-go smoothies)
- ✅ High impulse buy factor
- ✅ Great for video marketing
- ✅ Instagram/TikTok friendly
- ✅ Multiple use cases
- ✅ Decent shipping weight (still manageable)

### Concerns
- ⚠️ Battery-powered (shipping restrictions?)
- ⚠️ Potential quality issues (blades, motor)
- ⚠️ Returns if doesn't work properly

---

## Test Case 7: Resistance Bands Set (Expected: PASS)

### Input Data
```
Amazon URL: https://www.amazon.com/dp/B08XXXX
Search Term: resistance bands workout set
Category: Sports
```

### Expected Results
- **Status**: PASS ✅
- **Profit Margin**: 55-75%
- **AI Score**: 8/10
- **Trend**: Stable/Rising (home fitness)
- **YouTube Videos**: 40+ tutorials

### Why It Should Pass
- ✅ Excellent margins ($25-35 Amazon, $6-10 AliExpress)
- ✅ Very light shipping
- ✅ Home fitness trend (post-COVID)
- ✅ Easy to demonstrate value
- ✅ Low seasonality
- ✅ Multiple price points available
- ✅ Bundling opportunities
- ✅ Great for content marketing

---

## Test Case 8: Laptop Stand (Expected: PASS)

### Input Data
```
Amazon URL: https://www.amazon.com/dp/B07DWM9WNM
Search Term: laptop stand adjustable aluminum
Category: Electronics
```

### Expected Results
- **Status**: PASS ✅
- **Profit Margin**: 50-70%
- **AI Score**: 7-8/10
- **Trend**: Stable (remote work)
- **YouTube Videos**: 15-25 reviews

### Why It Should Pass
- ✅ Remote work trend (sustained)
- ✅ Good margins ($30-40 Amazon, $10-15 AliExpress)
- ✅ Problem-solving (ergonomics)
- ✅ Professional use case
- ✅ Year-round demand
- ✅ Easy to photograph
- ✅ Low return rates
- ✅ Multiple suppliers

### Concerns
- ⚠️ Slightly heavier shipping
- ⚠️ Packaging important (avoid damage)

---

## Test Case 9: Car Phone Mount (Expected: REVIEW)

### Input Data
```
Amazon URL: https://www.amazon.com/dp/B07XXXX
Search Term: car phone mount magnetic
Category: Electronics
```

### Expected Results
- **Status**: REVIEW ⚠️
- **Profit Margin**: 60-80%
- **AI Score**: 6/10
- **Competition**: High
- **Trend**: Stable

### Why It's Borderline
- ✅ Great margins ($12-18 Amazon, $2-4 AliExpress)
- ✅ Very small/light shipping
- ✅ Clear use case
- ⚠️ Saturated market
- ⚠️ Many cheap options already
- ⚠️ Quality critical (safety issue)
- ⚠️ Phone-size compatibility issues

---

## Test Case 10: Garden Hose Nozzle (Expected: PASS - Seasonal)

### Input Data
```
Amazon URL: https://www.amazon.com/dp/B01XXXX
Search Term: garden hose nozzle spray
Category: Home
```

### Expected Results
- **Status**: PASS ✅ (but seasonal warning)
- **Profit Margin**: 65-80%
- **AI Score**: 7/10
- **Trend**: Highly seasonal (summer)
- **YouTube Videos**: 10-15 reviews

### Why It Should Pass
- ✅ Excellent margins ($18-25 Amazon, $4-7 AliExpress)
- ✅ Light and small
- ✅ Clear problem solving
- ✅ Easy to demonstrate
- ✅ Multiple suppliers
- ⚠️ **SEASONAL** - Spring/Summer only
- ⚠️ Need to time inventory correctly

### Strategy Notes
- Launch in February/March
- Heavy marketing March-June
- Clear inventory by September
- Don't hold winter stock

---

## Running the Tests

### Automated Test Suite

To test all products at once, use this n8n modification:

1. **Add Loop Node:**
```javascript
const testProducts = [
  {url: "https://www.amazon.com/dp/B07XV5MFKY", category: "electronics"},
  {url: "https://www.amazon.com/dp/B08C7KG5LP", category: "electronics"},
  // ... etc
];

return testProducts.map(p => ({json: p}));
```

2. **Connect to existing workflow**
3. **Review aggregated results in CSV**

### Expected Success Rate

With test suite above:
- **7/10 PASS** (70% success rate)
- **2/10 REVIEW** (20% need manual evaluation)
- **1/10 FAIL** (10% rejected)

This matches real-world dropshipping product research ratios.

---

## Validation Checklist

Use this to manually verify workflow accuracy:

| Test | Expected Status | AI Score | Profit % | Matches | Result |
|------|----------------|----------|----------|---------|--------|
| LED Strips | PASS | 7-8 | 40-60% | Yes | ✓ |
| Wireless Earbuds | PASS | 7-9 | 35-50% | Yes | ✓ |
| Pet Glove | PASS | 8-9 | 60-80% | Yes | ✓ |
| Nike Shoes | FAIL | 2-4 | <10% | No | ✓ |
| Phone Case | REVIEW | 5-6 | 50-70% | Yes | ✓ |
| Portable Blender | PASS | 7-8 | 45-65% | Yes | ✓ |
| Resistance Bands | PASS | 8 | 55-75% | Yes | ✓ |
| Laptop Stand | PASS | 7-8 | 50-70% | Yes | ✓ |
| Car Mount | REVIEW | 6 | 60-80% | Yes | ✓ |
| Garden Nozzle | PASS* | 7 | 65-80% | Yes | ✓ |

*Pass with seasonal warning

---

## Common Testing Issues

### Issue: All Tests Fail
**Cause:** ScraperAPI key not configured or invalid
**Fix:** Add valid ScraperAPI key to Amazon scraper node

### Issue: No AliExpress Matches
**Cause:** Apify quota exceeded or search too specific
**Fix:** Check Apify dashboard, simplify search terms

### Issue: YouTube API Errors
**Cause:** Daily quota exceeded (10,000 units)
**Fix:** Wait 24 hours or use different API key

### Issue: Inconsistent AI Scores
**Cause:** Gemini API temperature setting
**Fix:** This is normal - AI has some variance

---

## Performance Benchmarks

Expected execution times:
- **Per product**: 30-60 seconds
- **Batch of 10**: 8-12 minutes
- **Daily capacity**: ~100 products (free tier limits)

API call breakdown per product:
- Amazon scrape: 1 call
- Gemini AI: 1 call
- Google Trends: 1 call
- AliExpress: 1 call
- YouTube search: 2 calls (search + stats)

**Total: 6 API calls per product**

---

## Advanced Test Scenarios

### Stress Test
Run 50 products simultaneously to test:
- Error handling
- Rate limiting
- Memory usage
- CSV append functionality

### Error Recovery Test
Intentionally break APIs to verify:
- Error logging works
- Workflow doesn't crash
- Partial results still saved
- Clear error messages

### Edge Cases
- Very long product titles (>200 chars)
- Products with no images
- Products with $0 price
- Non-existent ASINs
- International Amazon domains (.co.uk, .de)

---

## Next Steps After Testing

1. ✅ Verify all test cases pass/fail as expected
2. ✅ Review generated CSV and HTML reports
3. ✅ Check error log for any issues
4. ✅ Adjust thresholds if needed
5. ✅ Add your own product niches
6. ✅ Set up scheduled runs
7. ✅ Integrate with Google Sheets
8. ✅ Build product database
9. ✅ Start sourcing winning products!

---

## Support

If tests don't match expectations:
1. Check API keys are valid
2. Review error log CSV
3. Test individual nodes with sample data
4. Verify internet connectivity
5. Check API service status pages
6. Review n8n execution logs

For questions, consult the WORKFLOW_SETUP_GUIDE.md or n8n community forums.
