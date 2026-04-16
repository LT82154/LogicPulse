# LogicPulse

**Async concurrent web scraping project for sheeel.com coupon deals**

## 📋 Overview

LogicPulse scrapes the coupons category on sheeel.com which contains special deals, vouchers, and discount offers. Built with async concurrent architecture for optimal performance.

## 🎯 Categories

### Coupons
- **URL**: https://www.sheeel.com/ar/coupons.html
- **S3 Path**: `s3://bucket/coupons/YYYY/MM/DD/`
- **Schedule**: Every 2 days at 8:00 AM UTC
- **Special Features**: Extracts coupon-specific information including deal details, validity dates, location, and usage notes

## 📊 Coupon-Specific Data Fields

This scraper extracts additional fields unique to coupon/deal products:

- **`deal_details`** - Complete description of the deal offer (التفاصيل)
- **`valid_from`** - Coupon valid start date (صالح من)
- **`valid_until`** - Coupon expiration date (صالح حتى)
- **`coupon_location`** - Physical location or address where coupon can be redeemed (الموقع)
- **`coupon_notes`** - Terms, conditions, reservation details, and usage instructions (الملاحظات)

## 🏗️ Architecture

- **Technology**: Playwright (async API) with Chromium
- **Concurrency**: 3 concurrent subcategories by default
- **Performance**: ~3x faster than sequential scraping
- **Upload**: Incremental S3 upload per subcategory

## 🚀 Quick Start

```bash
cd coupons
pip install -r requirements.txt
playwright install chromium

# Set environment variables
export AWS_ACCESS_KEY_ID=your_key
export AWS_SECRET_ACCESS_KEY=your_secret
export S3_BUCKET_NAME=your_bucket

python scraper.py
```

## ⚙️ GitHub Actions

- **Schedule**: Every 2 days at 8:00 AM UTC
- **Workflow**: `.github/workflows/main.yml`
- **Manual Trigger**: Available via Actions tab

## 📝 Notes

- All fields include Arabic text handling and Excel character sanitization
- Coupon-specific fields may be `None` if not available for certain products
- Brand names are extracted when available

## 📄 License

Internal use only.