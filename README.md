# ScraperAPI Tutorial: Complete Beginner's Guide to Web Scraping Without Getting Blocked — How to Set Up, Send Your First Request, Avoid Credit Traps, and Pick the Right Plan (With Full Pricing Breakdown and Real User Insights)

If you've ever tried to scrape a website and gotten hit with a 403 error, a CAPTCHA wall, or a mysteriously empty response, you already know the pain. You write what feels like perfectly good Python. You test it on one page. It works. You run it on a thousand pages. Half of them fail, your IP gets banned, and suddenly your weekend project has turned into a proxy management nightmare.

That's the exact problem ScraperAPI was built to solve — and this tutorial walks you through everything: how to get started, how the API actually works, what the credit system really means for your wallet, and where the platform genuinely shines versus where you should look elsewhere.

Let's get into it.

---

## **What ScraperAPI Actually Does (And Why Developers Keep Using It)**

At its core, ScraperAPI is a middleman between your code and the websites you want to scrape. Instead of sending your request directly to a target site, you send it through ScraperAPI's endpoint. On the backend, ScraperAPI handles all the messy stuff: rotating proxies across a pool of 40 million+ IPs in 50+ countries, solving CAPTCHAs, rendering JavaScript with a headless browser, and retrying failed requests automatically.

What you get back is the page HTML — clean, reliable, without any of the infrastructure overhead. For someone who's spent hours babysitting proxy lists and handling rate limits, this feels like magic.

The company was founded in 2018, grew entirely bootstrapped to around 10,000 customers and ~$3M in revenue, then was acquired by SaaS.group in 2020. Today it processes over 36 billion API requests per month and counts Deloitte, Sony, and Alibaba among its users. Not bad for what started as a solo developer's side project.

> The simplest way to think about it: you send a URL, ScraperAPI sends back the HTML. Everything between those two steps — proxies, CAPTCHAs, bot detection — is their problem, not yours.

👉 [Try ScraperAPI free — 1,000 credits with no credit card required](https://www.scraperapi.com/?fp_ref=coupons)

---

## **ScraperAPI Tutorial: From Zero to First Request in 10 Minutes**

This is the part you actually came for. Let's walk through setup step by step.

### **Step 1: Create Your Account and Get Your API Key**

Head over to ScraperAPI and sign up for free. You'll immediately get 1,000 API credits per month at no cost, plus a 7-day trial with an additional 5,000 credits to test at scale. No credit card required for the free tier.

Once you're in, find your API Key in the dashboard. It looks like a long alphanumeric string. Keep it somewhere safe — you'll need it for every request.

### **Step 2: Install the Requests Library (Python)**

If you're using Python (the most common choice for web scraping), you'll need the `requests` library:

bash
pip install requests


That's literally all the setup you need. No SDKs, no special packages. ScraperAPI works through a standard HTTP GET request.

### **Step 3: Send Your First Request**

Here's the simplest possible ScraperAPI call in Python:

python
import requests

api_key = 'YOUR_API_KEY'
target_url = 'https://www.example.com'

request_url = f'https://api.scraperapi.com?api_key={api_key}&url={target_url}'
response = requests.get(request_url)

print(response.text)


That's it. Run that, and you'll get the full HTML of `example.com` back in your terminal. ScraperAPI automatically selected a proxy, made the request, and returned the result — all in one line.

For Node.js users, the same basic pattern applies:

javascript
import request from 'node-fetch';

const url = 'http://api.scraperapi.com/?api_key=YOUR_API_KEY&url=https://example.com/';

request(url)
  .then(response => response.text())
  .then(body => console.log(body))
  .catch(error => console.error(error));


### **Step 4: Use Parameters to Handle Harder Sites**

The basic request above works great for simple, static HTML pages. But when you hit JavaScript-rendered sites, geo-locked content, or pages with aggressive bot detection, you need to add parameters.

Here are the most important ones:

| Parameter | What It Does | Credit Cost |
|---|---|---|
| `render=true` | Enables headless browser JS rendering | +10 credits |
| `premium=true` | Uses residential proxies (better bypass) | +10 credits |
| `ultra_premium=true` | Premium residential pool for hardest sites | +30 credits |
| `country_code=us` | Targets a specific country | Free |
| `session_number=123` | Reuses the same IP for 15 minutes | Free |
| `autoparse=true` | Returns structured JSON instead of HTML | Free |

Here's an example with JavaScript rendering enabled:

python
import requests

api_key = 'YOUR_API_KEY'
target_url = 'https://www.example.com'

request_url = f'https://api.scraperapi.com?api_key={api_key}&render=true&url={target_url}'
response = requests.get(request_url)

print(response.text)


**Important note:** Always put ScraperAPI parameters *before* the `url` parameter. If your target URL has its own query parameters, putting ScraperAPI's params after `url` can cause conflicts.

### **Step 5: Test on Your Actual Target Sites Before Committing**

Before you pick a paid plan, use your free 1,000 credits to test against the specific sites you need to scrape. Run 10–20 requests with the actual parameters you plan to use. Check the success rate and the credit consumption. This tells you your real monthly cost — not the number on the pricing page.

---

## **The Credit System Explained: The Most Important Thing No One Tells You**

Here's where a lot of people get burned, and it's worth spending real time on this.

When ScraperAPI says a plan comes with "100,000 API credits," most people read that as "100,000 requests." It's not. One credit is only the cost of one *standard* request — plain HTTP, no JavaScript, not on a premium domain. The moment you add any parameters or scrape certain domains, the credit cost goes up. Sometimes dramatically.

### **The Credit Multiplier Table**

| Request Type | Credits Per Request |
|---|---|
| Standard request (plain HTML) | 1 |
| `render=true` (JS rendering) | 10 |
| `premium=true` (premium proxy) | 10 |
| `screenshot=true` | 10 |
| `premium=true` + `render=true` combined | **25** (not 20) |
| `ultra_premium=true` | 30 |
| `ultra_premium=true` + `render=true` combined | **75** (not 40) |
| Cloudflare / bot-protection bypass | +10 (automatic) |

And certain high-value domains carry their own fixed multipliers that apply automatically — you don't opt in to them:

| Domain | Credits Per Request |
|---|---|
| Regular websites | 1 |
| Amazon | 5 |
| Google / Bing SERP | 25 |
| LinkedIn | 30 |

The combination multipliers are the part that catches people off guard. Premium proxy plus JavaScript rendering logically *seems* like it should cost 10 + 10 = 20 credits extra. ScraperAPI charges 25. Ultra-premium plus rendering logically feels like 30 + 10 = 40 credits extra. It's actually 75. That's nearly double what the math suggests.

### **What Your Plan Actually Gets You**

Here's what 100,000 Hobby-plan credits really means depending on how you use them:

| Use Case | Credits Per Request | Actual Requests |
|---|---|---|
| Basic HTML (news, blogs) | 1 | 100,000 |
| JS-rendered pages | 10 | 10,000 |
| Amazon product pages | 5 | 20,000 |
| Google SERP queries | 25 | 4,000 |
| Ultra-premium + JS render | 75 | ~1,333 |

If you're building a Google SERP monitoring tool and assumed you'd get 100,000 searches per month on the Hobby plan — you're actually getting 4,000. That math matters a lot before you pick a pricing tier.

---

## **Full ScraperAPI Plans Comparison**

Here's every current plan, with pricing, credits, concurrency limits, and what you actually get:

| Plan | Monthly Price | Annual (per/mo) | API Credits | Concurrent Threads | Geotargeting | Pay-As-You-Go | Purchase |
|---|---|---|---|---|---|---|---|
| **Free** | $0 | — | 1,000 | 5 | No | No |  [Get Free Plan](https://www.scraperapi.com/?fp_ref=coupons) |
| **Hobby** | $49 | ~$44 | 100,000 | 20 | US & EU only | No |  [Get Hobby Plan](https://www.scraperapi.com/?fp_ref=coupons) |
| **Startup** | $149 | ~$134 | 1,000,000 | 50 | US & EU only | No |  [Get Startup Plan](https://www.scraperapi.com/?fp_ref=coupons) |
| **Business** | $299 | ~$269 | 3,000,000 | 100 | Global (50+ countries) | No |  [Get Business Plan](https://www.scraperapi.com/?fp_ref=coupons) |
| **Scaling** | $475 | ~$427 | 5,000,000 | 200 | Global | Yes |  [Get Scaling Plan](https://www.scraperapi.com/?fp_ref=coupons) |
| **Professional** | $975 | — | 10,500,000 | 300 | Global | Yes |  [Get Professional Plan](https://www.scraperapi.com/?fp_ref=coupons) |
| **Advanced** | $1,975 | — | 21,500,000 | 500 | Global | Yes |  [Get Advanced Plan](https://www.scraperapi.com/?fp_ref=coupons) |
| **Enterprise** | Custom | Custom | 22,000,000+ | 500+ | Global + dedicated support | Yes |  [Contact Sales](https://www.scraperapi.com/?fp_ref=coupons) |

**A few things worth knowing:**

- Annual billing saves roughly 10% across all plans — worth it if you know you'll use ScraperAPI consistently
- Pay-As-You-Go overage (where the API keeps working when you run out of credits, billing at a per-credit rate) is only available on Scaling and above. If you're on Hobby, Startup, or Business and exhaust your credits mid-month, scraping stops until your plan renews
- Credits do **not** roll over month to month — unused credits expire
- Global geotargeting (beyond US and EU) requires at least the Business plan

---

## **Where ScraperAPI Genuinely Shines**

Based on independent benchmarks (Scrapeway, April 2026) and real user data, ScraperAPI has genuinely strong performance in some categories and significant gaps in others.

The platform does best on **e-commerce and real estate**. Amazon scraping hits a 98% success rate. Zillow is at 100%. Etsy sits at 99%. Walmart at 93%. For these targets — especially via ScraperAPI's Structured Data Endpoints (SDEs), which return pre-parsed JSON rather than raw HTML — the tool is legitimately excellent.

The structured data endpoints cover Amazon (product details, search results, competitor offers), Google (SERP, Shopping, Maps, News, Jobs), Walmart, eBay, and Redfin. If your workflow involves pulling Amazon product data by ASIN or monitoring Google search rankings, these endpoints save real development time and return clean, structured data you can use directly.

For SERP data specifically — monitoring keyword rankings, competitor analysis, tracking featured snippets — the Google SERP endpoint is one of the cleaner implementations on the market.

### **Where It Struggles**

Social media is essentially a dead zone for ScraperAPI. Independent testing shows 0% success rates on Instagram, Twitter/X, and Booking.com. LinkedIn technically works at 95%, but at 30 credits per request, the cost at scale gets steep fast.

Login-required sites are explicitly off-limits per ScraperAPI's terms of service. The API supports session persistence (keeping the same IP across requests via `session_number`), but it won't help you get past an authentication wall. For sites requiring a login, you'd need a browser-based tool that operates within an actual user session.

---

## **Real Users: What People Actually Say**

Ratings across major platforms tell a pretty consistent story:

- **Trustpilot**: 4.5/5 (42 reviews)
- **Capterra**: 4.6/5 (62 reviews) — Ease of Use specifically rated 4.9/5
- **G2**: 4.4/5 (16 reviews)

The praise clusters around a few themes: setup is genuinely fast (most developers report being up and running in under an hour), documentation is thorough, and the proxy infrastructure holds up on well-supported targets.

The complaints are more specific. Credit system transparency comes up repeatedly — the gap between "100,000 credits" and actual usable requests catches people off guard. One Capterra reviewer noted that "breakdown of credit costs can be confusing, especially as you use premium parameters." A Reddit thread documented a user who was quoted pricing based on 1-credit Amazon requests, only to discover the 5-credit multiplier applied automatically after purchase.

There's also a note about reliability at high volume. ScraperAPI works well for moderate scraping jobs. Under heavy concurrent load on harder targets, consistency can drop. For continuous, large-scale data pipelines, the higher tiers with Pay-As-You-Go overage and priority support (Professional and above) are meaningfully different from the entry tiers.

---

## **ScraperAPI vs. Alternatives: When to Look Elsewhere**

ScraperAPI isn't always the right tool. Here's an honest comparison for common scenarios:

| Scenario | Best Tool | Why |
|---|---|---|
| Scraping Amazon/Walmart at scale | ScraperAPI | Structured Data Endpoints, 98%+ success rate |
| SERP monitoring (Google/Bing) | ScraperAPI | Strong SERP endpoint, 25 credits per query |
| JavaScript-heavy SPAs on a budget | ScrapingBee or Scrapfly | JS rendering costs 5x credits on ScraperAPI vs. 5–6 on others |
| Sites requiring login | Browser-based tools | ScraperAPI explicitly forbids login-wall scraping |
| Instagram / Twitter / Booking.com | Alternative tools | 0% success rate on ScraperAPI |
| Non-technical users needing quick data | No-code tools | ScraperAPI requires code; no point-and-click |
| Protected sites needing flat-rate billing | Bright Data | Bright Data charges same rate regardless of rendering |

For developers who want deep customization, high concurrency, and support for well-known e-commerce and SERP targets, ScraperAPI is competitive. For anyone who can't write Python and needs data from a website by Thursday afternoon, it's the wrong tool for the job.

---

## **Practical Tips to Avoid Wasting Credits**

Running a ScraperAPI tutorial without a "don't blow your credits" section would be irresponsible. Here's what experienced users have learned:

**Test your target sites before buying a plan.** The 7-day trial gives you 5,000 credits to play with. Use them on your actual targets with your actual parameters. Build a credit-cost spreadsheet before you commit to a monthly plan.

**Only enable premium features when necessary.** ScraperAPI does not auto-enable `render=true`, `premium=true`, or `ultra_premium=true`. You explicitly set these. Domain multipliers (Amazon 5x, Google 25x, LinkedIn 30x) and bot-bypass credits (+10 for Cloudflare, DataDome, PerimeterX) apply automatically — but rendering and premium proxies don't. Start with the default and escalate only if you see failures.

**Check your dashboard daily for the first month.** There are no proactive credit alerts. No email when you hit 80% usage. You have to log in and check manually. Analytics history is limited to 2 weeks on the lower tiers. Set a reminder.

**Understand the 404 situation.** ScraperAPI charges credits for both 200 (success) and 404 (not found) responses. Only completely failed requests — where the page couldn't be retrieved at all — are free. Budget for a certain percentage of 404s in your credit estimate.

**Consider the DataPipeline credit multiplier separately.** If you use ScraperAPI's no-code DataPipeline feature for scheduled scraping, the credit costs are different from the standard API. A basic request costs 6 DataPipeline credits versus 1 standard API credit. This is documented but easy to miss.

---

## **Getting Started: Free Trial and Current Offers**

ScraperAPI offers a permanent free tier with 1,000 API credits per month and 5 concurrent connections — enough for small experiments or testing whether the tool fits your workflow. New signups also get a 7-day trial with 5,000 credits to test at larger scale, no credit card required.

Annual billing saves approximately 10% across all plans. For example, the Hobby plan drops from $49/month to around $44/month when billed annually.

If you're unsure which plan fits your use case, the free tier and 7-day trial are genuinely useful for figuring that out before spending money. Run your actual target URLs, with the actual parameters your production scraper will use, and let the credit consumption tell you which tier makes sense.

> There's also a 7-day no-questions-asked refund policy for paid plans. If you sign up, discover the tool doesn't meet your needs, and contact support within 7 days, you'll get your money back.

👉 [Start free — no credit card needed](https://www.scraperapi.com/?fp_ref=coupons)

---

## **Quick Recap: Is ScraperAPI the Right Tool for You?**

After walking through all of this, here's the honest summary:

If you're a developer who needs to scrape Amazon, Google, Walmart, Zillow, or similar well-supported targets at moderate to high volume — ScraperAPI is worth serious consideration. The structured data endpoints are genuinely good. The proxy infrastructure is large. The documentation is above-average. Setup time is measured in minutes, not days.

If the credit multiplier math works out for your specific use case, the pricing is competitive in the market, especially at the Business tier and above where per-credit cost drops significantly.

If you're on the Hobby or Startup plan and your scraping involves any rendering or premium proxies, do the math carefully before assuming the headline credit number maps to your actual request volume. It almost certainly doesn't.

And if you're not a developer, if you just need data from a website and don't want to write code — ScraperAPI isn't designed for you. That's not a criticism; it's just a clear-eyed read of who the product is built for.

👉 [Get started with ScraperAPI — free plan available](https://www.scraperapi.com/?fp_ref=coupons)

---

*All pricing data reflects ScraperAPI's plans as of mid-2026. Plan details and credit multipliers are subject to change — verify current pricing on the official site before purchasing.*
