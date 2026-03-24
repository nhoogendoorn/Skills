# App Store Optimization Guide

## Table of Contents

1. Platform-Specific Requirements
2. Keyword Research
3. Metadata Optimization
4. Visual Asset Optimization
5. Review & Rating Management
6. Launch Strategy
7. Localization
8. ASO Scripts Reference
9. Input/Output Formats
10. Limitations

---

## 1. Platform-Specific Requirements

### Apple App Store
| Field | Limit |
|-------|-------|
| Title | 30 characters |
| Subtitle | 30 characters |
| Promotional Text | 170 characters (editable without app update) |
| Description | 4,000 characters |
| Keywords | 100 characters (comma-separated, no spaces) |
| What's New | 4,000 characters |

### Google Play Store
| Field | Limit |
|-------|-------|
| Title | 50 characters |
| Short Description | 80 characters |
| Full Description | 4,000 characters |
| No separate keyword field | Keywords extracted from title and description |

---

## 2. Keyword Research

1. **Volume vs. Competition**: Balance high-volume keywords with achievable rankings
2. **Relevance First**: Only target keywords genuinely relevant to your app
3. **Long-Tail Strategy**: Include 3-4 word phrases with lower competition
4. **Continuous Research**: Keyword trends change -- research quarterly
5. **Competitor Keywords**: Don't copy blindly; ensure relevance to your features

---

## 3. Metadata Optimization

1. **Front-Load Keywords**: Place most important keywords early in title/description
2. **Natural Language**: Write for humans first, SEO second
3. **Feature Benefits**: Focus on user benefits, not just features
4. **A/B Test Everything**: Test titles, descriptions, screenshots systematically
5. **Update Regularly**: Refresh metadata every major update
6. **Character Limits**: Use every character -- don't waste valuable space
7. **Apple Keyword Field**: No plurals, duplicates, or spaces between commas

---

## 4. Visual Asset Optimization

1. **Icon**: Must be recognizable at small sizes (60x60px). Single most important visual element.
2. **Screenshots**: First 2-3 are critical -- most users don't scroll
3. **Captions**: Use screenshot captions to tell your value story
4. **Consistency**: Match visual style to app design
5. **A/B Test Icons**: Test icon variations before committing
6. **Preview Video**: Keep under 30 seconds, show core value in first 5 seconds

---

## 5. Review & Rating Management

1. **Respond Quickly**: Reply to reviews within 24-48 hours
2. **Professional Tone**: Always courteous, even with negative reviews
3. **Address Issues**: Show you're actively fixing reported problems
4. **Thank Supporters**: Acknowledge positive reviews
5. **Prompt Strategically**: Ask for ratings after positive experiences (completed a task, achieved a goal)

---

## 6. Launch Strategy

1. **Soft Launch**: Consider launching in smaller markets first
2. **PR Timing**: Coordinate press coverage with launch
3. **Update Frequently**: Initial updates signal active development
4. **Monitor Closely**: Track metrics daily for first 2 weeks
5. **Iterate Quickly**: Fix critical issues immediately

---

## 7. Localization

1. **Priority Markets**: Start with English, Spanish, Chinese, French, German
2. **Native Speakers**: Use professional translators, not machine translation
3. **Cultural Adaptation**: Some features resonate differently by culture
4. **Test Locally**: Have native speakers review before publishing
5. **Measure ROI**: Track downloads by locale to assess impact

---

## 8. ASO Scripts Reference

All scripts are in the `scripts/` directory. Run with Python 3.

### keyword_analyzer.py
Analyzes keywords for search volume, competition, and relevance.
- `analyze_keyword()` -- Analyze single keyword metrics
- `compare_keywords()` -- Compare multiple keywords
- `find_long_tail()` -- Discover long-tail opportunities
- `calculate_keyword_difficulty()` -- Assess competition level

### metadata_optimizer.py
Optimizes titles, descriptions, and keyword fields with platform-specific validation.
- `optimize_title()` -- Create keyword-rich titles
- `optimize_description()` -- Generate conversion-focused descriptions
- `optimize_keyword_field()` -- Maximize Apple's 100-char keyword field
- `validate_character_limits()` -- Ensure platform compliance
- `calculate_keyword_density()` -- Analyze keyword usage

### competitor_analyzer.py
Analyzes top competitors' ASO strategies.
- `get_top_competitors()` -- Identify category leaders
- `analyze_competitor_metadata()` -- Extract competitor keywords
- `compare_visual_assets()` -- Evaluate icons and screenshots
- `identify_gaps()` -- Find competitive opportunities

### aso_scorer.py
Calculates comprehensive ASO health score (0-100).
- `calculate_overall_score()` -- Compute ASO score
- `score_metadata_quality()` -- Evaluate title, description, keywords
- `score_ratings_reviews()` -- Assess rating quality and volume
- `generate_recommendations()` -- Provide prioritized action items

### ab_test_planner.py
Plans and tracks A/B tests for metadata and visual assets.
- `design_test()` -- Create test hypothesis and variables
- `calculate_sample_size()` -- Determine required test duration
- `calculate_significance()` -- Assess statistical significance

### localization_helper.py
Manages multi-language ASO optimization.
- `identify_target_markets()` -- Recommend localization priorities
- `translate_metadata()` -- Generate localized metadata
- `adapt_keywords()` -- Research locale-specific keywords
- `calculate_localization_roi()` -- Estimate impact

### review_analyzer.py
Analyzes user reviews for sentiment, issues, and feature requests.
- `analyze_sentiment()` -- Calculate positive/negative/neutral ratios
- `extract_common_themes()` -- Identify frequent topics
- `identify_issues()` -- Surface bugs and complaints
- `find_feature_requests()` -- Extract desired features

### launch_checklist.py
Generates comprehensive pre-launch and update checklists.
- `generate_prelaunch_checklist()` -- Complete submission validation
- `validate_app_store_compliance()` -- Check Apple guidelines
- `validate_play_store_compliance()` -- Check Google policies
- `optimize_launch_timing()` -- Recommend release dates

---

## 9. Input/Output Formats

### Keyword Research Input
```json
{
  "app_name": "MyApp",
  "category": "Productivity",
  "target_keywords": ["task manager", "productivity", "todo list"],
  "competitors": ["Todoist", "Any.do"],
  "language": "en-US"
}
```

### Metadata Optimization Input
```json
{
  "platform": "apple",
  "app_info": {
    "name": "MyApp",
    "category": "Productivity",
    "target_audience": "Professionals aged 25-45",
    "key_features": ["Task management", "AI assistance"],
    "unique_value": "AI-powered task prioritization"
  },
  "target_keywords": ["productivity", "task manager"]
}
```

---

## 10. Limitations

- Keyword search volume estimates are approximate (no official data from Apple/Google)
- Competitor data may be incomplete for private apps
- A/B testing requires significant traffic for statistical significance
- Store algorithms are proprietary and change without notice
- ASO benchmarks vary significantly by category
- Does not include paid user acquisition (Apple Search Ads, Google Ads)
