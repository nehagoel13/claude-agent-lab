# Product Manager Documentation Guidelines

## Purpose
Generate product documentation that helps PMs, stakeholders, and business users understand what the product does and its business value.

## Target Audience
- Product Managers
- Product Owners
- Business Stakeholders
- Executive Leadership
- Sales & Marketing teams
- Customer Success teams

## Documentation Structure

### 1. Product Overview
````markdown
# [Product Name] - Product Documentation

## What is [Product Name]?
[Product Name] is a [brief description] that helps [target users] to [main value proposition].

## Key Value Propositions
- **For Users**: [How it helps end users]
- **For Business**: [Business benefits and ROI]
- **Competitive Advantage**: [What makes it unique]

## Target Users
- **Primary**: [Main user persona]
- **Secondary**: [Additional user personas]
````

### 2. Features & Capabilities
````markdown
## Core Features

### 1. [Feature Name]
**What it does:** [User-friendly description]

**User Benefit:** [How this helps users accomplish their goals]

**Use Cases:**
- [Scenario 1]: User can [action] to achieve [outcome]
- [Scenario 2]: User can [action] to achieve [outcome]

**Status:** ✅ Live | 🚧 In Development | 📋 Planned

---

### 2. [Feature Name]
**What it does:** [Description]

**User Benefit:** [Benefit explanation]

**Use Cases:**
- [Scenario 1]
- [Scenario 2]

**Status:** ✅ Live
````

### 3. User Journeys
````markdown
## Key User Journeys

### Journey 1: [User Goal]
**User Type:** [Persona]
**Goal:** [What they want to accomplish]

**Steps:**
1. User logs in to the dashboard
2. User navigates to [section]
3. User creates/edits [entity]
4. User reviews and confirms
5. System processes and confirms success

**Success Metrics:**
- Time to complete: < 2 minutes
- Success rate: > 95%
- User satisfaction: 4.5/5

---

### Journey 2: [User Goal]
[Similar structure]
````

### 4. Product Metrics
````markdown
## Success Metrics & KPIs

### User Engagement
- **Daily Active Users (DAU)**: [Current: X, Target: Y]
- **Monthly Active Users (MAU)**: [Current: X, Target: Y]
- **Feature Adoption Rate**: [Current: X%, Target: Y%]

### Business Metrics
- **Conversion Rate**: [Current: X%, Target: Y%]
- **Revenue Impact**: [Current: $X, Target: $Y]
- **Customer Retention**: [Current: X%, Target: Y%]

### Performance Metrics
- **Page Load Time**: < 2 seconds
- **API Response Time**: < 200ms
- **Uptime**: 99.9%
````

### 5. Release History
````markdown
## Release History

### Version 2.1.0 - January 15, 2026
**New Features:**
- ✨ Advanced search with filters
- ✨ Bulk export to CSV
- ✨ Custom dashboard widgets

**Improvements:**
- ⚡ 40% faster page load times
- 🎨 Updated UI with better accessibility
- 📱 Mobile responsive design

**Impact:**
- Expected to increase user productivity by 25%
- Addresses top 3 customer requests

---

### Version 2.0.0 - December 1, 2025
[Similar structure]
````

### 6. Roadmap & Upcoming Features
````markdown
## Product Roadmap

### Q1 2026 (Current)
- ✅ Advanced search (Completed)
- 🚧 Real-time collaboration (In Progress)
- 📋 Mobile app (Planned)

### Q2 2026
- 📋 AI-powered recommendations
- 📋 Integration with Salesforce
- 📋 Advanced analytics dashboard

### Future Considerations
- Multi-language support
- White-label solution
- Enterprise SSO
````

### 7. Integration & Ecosystem
````markdown
## Integrations

### Available Integrations
- **Slack**: Receive notifications and updates
- **Google Workspace**: Single sign-on and calendar sync
- **Stripe**: Payment processing
- **Zapier**: Connect to 1000+ apps

### API Access
**For Customers:**
- REST API available for Enterprise plan
- Webhooks for real-time events
- SDKs available for JavaScript and Python

**Documentation:** [Link to API docs]
````

### 8. User Feedback & Insights
````markdown
## User Feedback Summary

### Top Requested Features
1. **Mobile app** (250 requests) - 📋 Q1 2026
2. **Dark mode** (180 requests) - ✅ Shipped in v2.0
3. **Bulk operations** (150 requests) - ✅ Shipped in v2.1

### Recent Customer Quotes
> "This feature saved our team 10 hours per week" - Enterprise Customer

> "The new dashboard is exactly what we needed" - Mid-market Customer

### Pain Points Being Addressed
- Loading time on large datasets → Fixed in v2.1
- Complex navigation → Redesigned in v2.0
- Limited export options → Enhanced in v2.1
````

### 9. Competitive Analysis
````markdown
## Competitive Positioning

### Key Competitors
| Feature | Our Product | Competitor A | Competitor B |
|---------|------------|--------------|--------------|
| Real-time collaboration | ✅ | ❌ | ✅ |
| Advanced search | ✅ | ✅ | ❌ |
| Mobile app | 🚧 Q1 | ✅ | ✅ |
| API access | ✅ Enterprise | ✅ All plans | ❌ |
| Price/user/month | $15 | $20 | $12 |

### Our Unique Advantages
- Only solution with [specific capability]
- Best-in-class [specific feature]
- Superior [specific metric]
````

### 10. Getting Started Guide
````markdown
## Getting Started (For End Users)

### Step 1: Create Account
Visit [URL] and sign up with your email or Google account.

### Step 2: Complete Setup
1. Set up your profile
2. Invite team members (optional)
3. Import existing data (optional)

### Step 3: Start Using Core Features
- **Create your first [entity]**: Click "New" button
- **Organize with [feature]**: Use tags and folders
- **Collaborate**: Share with team members

### Resources
- 📚 Knowledge Base: [link]
- 🎥 Video Tutorials: [link]
- 💬 Support Chat: Available in app
- 📧 Email Support: support@example.com
````

## Content Guidelines

### What to Include
✅ Product features and capabilities
✅ User benefits and value propositions
✅ Use cases and user journeys
✅ Business metrics and KPIs
✅ Release notes and roadmap
✅ Competitive positioning
✅ User feedback and testimonials
✅ Getting started guides

### What to Exclude
❌ Technical implementation details
❌ Code examples
❌ Database schemas
❌ API endpoints (link to dev docs instead)
❌ Deployment procedures
❌ Architecture diagrams

## Tone & Style
- **Business-focused and accessible**
- **Use plain language, avoid jargon**
- **Focus on outcomes and value**
- **Include metrics and data**
- **Tell the story of the product**
- **Assume non-technical audience**

## Update Triggers
Update PM documentation when:
- New features are released
- Product metrics change significantly
- Roadmap is updated
- User feedback trends emerge
- Competitive landscape changes
- Pricing or packaging changes

