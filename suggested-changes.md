# Suggested Changes for ATS for Candidates Project
*Based on Fall 2025 Retrospective Feedback*
*Date: December 23, 2025*

---

## Executive Summary

This document outlines comprehensive changes to address feedback from 78 student retrospectives and professor observations from the Fall 2025 semester. The proposed changes focus on six critical areas: improving UI/UX design guidance, reducing scope while maintaining learning outcomes, replacing impractical third-party APIs, restructuring sprints for better timing, eliminating redundancies, and providing clearer integration guidance across sprints.

**Key Priorities:**
1. **Start project earlier** - Move from Week 3 to Week 1
2. **Reduce sprint scope** - Cut 25-30% of use cases per sprint
3. **Replace AI-generated requirements** - Use human-written, clearer specifications
4. **Add comprehensive UI/UX vision** - Provide detailed design guidance upfront
5. **Eliminate API blockers** - Replace commercial APIs with free alternatives
6. **Integrate features coherently** - Show how each sprint builds on previous work

---

## 1. UI/UX Design and Architecture

### Problem
*"Of the 14 groups attacking this project none of them successfully designed an easy to use app. They treated each sprint as separate projects and bolted on features using buttons and menus."* - Professor Feedback

*"Many tickets overlapped or were redundant within and across sprints."* - Student Feedback

### Root Causes
- No unified UI/UX vision provided at project start
- Students treated each sprint as independent rather than iterative
- PRDs didn't explain how new features integrate with existing UI
- Lack of clear information architecture guidance

### Proposed Solutions

#### 1.1 Add Comprehensive UI/UX Vision Document (New Sprint 0 Deliverable)

**Create "UI-UX-Vision.md" document that includes:**

```markdown
# ATS for Candidates - UI/UX Vision

## Core User Journeys

### Primary Navigation Structure
┌─────────────────────────────────────────┐
│  Dashboard (Home)                       │
│  ├── Profile Section (Sprint 1)        │
│  ├── Jobs Pipeline (Sprint 2)          │
│  ├── Interview Prep (Sprint 3)         │
│  └── Analytics & Insights (Sprint 3-4) │
└─────────────────────────────────────────┘

### Job Detail Page Architecture
- Integrates: Job tracking (Sprint 2), Resume/Cover Letter (Sprint 2),
  Interview Prep (Sprint 3), Company Research (Sprint 2-3),
  Salary Data (Sprint 4), Network Contacts (Sprint 3)

All job-related features accessible from ONE unified job detail view.

### Profile Page Architecture
- Integrates: Basic Info (Sprint 1), Employment (Sprint 1),
  Skills (Sprint 1), GitHub Portfolio (Sprint 4),
  Certifications (Sprint 4), Network Stats (Sprint 3)

All profile features accessible from tabs/sections on ONE profile page.
```

**Benefits:**
- Students understand the final vision from Day 1
- Features naturally integrate rather than bolt-on
- Reduces redundant navigation patterns
- Creates cohesive user experience

#### 1.2 Add Required Wireframes to Each Sprint PRD

**Add wireframe section to each sprint showing:**
- How new features integrate with existing pages
- Specific placement of new UI elements
- Navigation flow between related features
- Mobile-first responsive behavior

**Example for Sprint 2 - Job Detail Page:**
```
Job Detail Wireframe (builds on Sprint 1 navigation):

┌──────────────────────────────────────┐
│ [← Back to Pipeline]    [⋮ Menu]    │
├──────────────────────────────────────┤
│ Software Engineer - Google           │
│ $120k-150k │ Applied │ 5 days ago   │
├──────────────────────────────────────┤
│ [Overview] [Materials] [Research]    │ ← New tabs (Sprint 2)
├──────────────────────────────────────┤
│ Materials Tab:                       │
│ Resume: [Version 2.1] [Edit] [View] │ ← Sprint 2 UC-042
│ Cover Letter: [Generate with AI...] │ ← Sprint 2 UC-053
│                                      │
│ [Interview Prep →]                   │ ← Placeholder for Sprint 3
└──────────────────────────────────────┘
```

#### 1.3 Replace Separate Navigation with Integrated Workflows

**Change in PRDs:**

❌ **Don't Say:** "Add a button to access salary analytics"
✅ **Do Say:** "Display salary range in the job card header, link to full analytics modal from job detail page"

❌ **Don't Say:** "Create network management page"
✅ **Do Say:** "Add 'Contacts' tab to job detail page showing connections at this company from your network (built in Sprint 3)"

#### 1.4 Add UI Integration Requirements to Each Use Case

**Example - UC-046 Resume Template Management (Sprint 2):**

```markdown
**UI Integration Requirements:**
- Access from: Profile page → "Documents" tab → "Resumes" section
- Also accessible from: Job Detail → "Materials" tab → "Create Resume"
- Navigation: Reuse left sidebar from Sprint 1, add "Documents" icon
- States: Empty state shows template gallery, populated shows resume list
- DO NOT create separate standalone resume page disconnected from profile
```

---

## 2. Project Timing and Sprint Structure

### Problem
*"Project should start earlier in the semester. Having to finish during finals week when students are busiest."* - Student Feedback (35+ mentions)

*"Sprints were too short for the amount of work required. Not adequate time given to complete required tasks."* - Student Feedback

### Proposed Solutions

#### 2.1 Revised Semester Timeline

**Current Timeline Issues:**
- Weeks 1-3: Lectures and setup (project starts Week 3)
- Week 15: Finals week conflict
- 4 sprints in 12 weeks = 3 weeks per sprint (inadequate)

**Proposed New Timeline:**

| Week | Activity | Notes |
|------|----------|-------|
| 1 | Project Kickoff, Team Formation, UI/UX Vision Review | Condense intro lectures to 2 days |
| 2-5 | Sprint 1 (4 weeks) | Authentication, Profile, Brand Identity |
| 6-9 | Sprint 2 (4 weeks) | Job Tracking, AI Resume/Cover Letter |
| 10-13 | Sprint 3 (4 weeks) | Interview Prep, Networking |
| 14 | Sprint 4 (1 week) | Deployment, Testing, Final Demo |
| 15 | Finals Week | No project work |

**Benefits:**
- Project starts Week 1 (2 weeks earlier)
- 4-week sprints for complex development
- Deployment sprint focused and short
- Avoids finals week entirely
- Total: 13 weeks instead of 12

#### 2.2 Compress Early Lectures

**Current: 3 weeks of lectures before project**
**Proposed: 1 week of lectures, concurrent with project setup**

**Week 1 Schedule:**
- Monday: Project overview, team formation, technology stack intro
- Wednesday: Git workflows, CI/CD pipeline setup hands-on
- Friday: UI/UX vision walkthrough, design system review

Students begin project setup concurrently during Week 1.

#### 2.3 Add In-Class Work Time

*"More efficient use of in-class time. Some class days should be set aside for just working on the project."* - Student Feedback

**Proposed: Dedicate 1 class per week to project work**
- Monday/Wednesday: Lecture, code review, technical topics
- Friday: In-class sprint work, professor available for questions

**Particularly valuable for:**
- Sprint 1 Week 1: Project setup, environment configuration
- Sprint 2 Week 1: API integration troubleshooting
- Sprint 3 Week 1: Complex feature planning
- Final week: Deployment support

---

## 3. Sprint Scope Reduction

### Problem
*"Too many tickets per sprint - felt overwhelming even with AI tools. The scope should be reduced."* - Student Feedback (40+ mentions)

*"Several features built and debugged never made it into the demo."* - Student Feedback

### Analysis of Current Scope

| Sprint | Current Use Cases | Demo Actions | Completion Rate |
|--------|------------------|--------------|-----------------|
| Sprint 1 | 35 use cases | 47 demo actions | Many skipped |
| Sprint 2 | 35 use cases | 52 demo actions | Many skipped |
| Sprint 3 | 30 use cases | 61 demo actions | Many skipped |
| Sprint 4 | 26 use cases | 48 demo actions | Many skipped |
| **Total** | **126 use cases** | **208 demo actions** | **Overwhelming** |

### Proposed Scope Reduction

#### 3.1 Target: 15-20 Use Cases Per Sprint

**Reduction Strategy:**
1. **Merge redundant use cases** (e.g., combine CRUD operations)
2. **Remove "nice-to-have" features** that aren't core to learning
3. **Simplify complex features** to focus on key functionality
4. **Eliminate features that duplicate across sprints**

#### 3.2 Sprint 1 Reduction: 35 → 18 Use Cases

**Keep (Core Authentication & Profile):**
- UC-001 to UC-009: Authentication (9 use cases) - KEEP ALL
- UC-010 to UC-012: Database & API (3 use cases) - KEEP ALL
- UC-013: Design System - KEEP
- UC-016: Profile Information - KEEP
- UC-020: Employment History - KEEP
- UC-022: Skills Management - KEEP
- UC-026: Education History - KEEP
- UC-030: Project Portfolio - KEEP

**Remove or Defer:**
- UC-014: Logo Design - REMOVE (provide logo)
- UC-015: Responsive Design Testing - MERGE with UC-013
- UC-017 to UC-019: Redundant profile views - MERGE into UC-016
- UC-021: Employment display - MERGE into UC-020
- UC-023 to UC-025: Skills organization/display - MERGE into UC-022
- UC-027 to UC-029: Education display - MERGE into UC-026
- UC-031 to UC-032: Project display - MERGE into UC-030
- UC-033 to UC-035: Resume upload - DEFER to Sprint 2

**Result: 18 focused use cases, all demonstrable**

#### 3.3 Sprint 2 Reduction: 35 → 20 Use Cases

**Keep (Core Job Tracking & AI):**
- UC-036 to UC-045: Job Entry & Tracking (10 use cases) - KEEP ALL
- UC-046 to UC-048: Resume Templates (3 use cases) - MERGE to 1
- UC-049 to UC-051: AI Resume Generation (3 use cases) - MERGE to 2
- UC-052 to UC-056: Cover Letter (5 use cases) - MERGE to 3
- UC-057 to UC-058: Company Research (2 use cases) - KEEP
- UC-061: Job Matching - KEEP
- UC-062: Application Quality Score - KEEP

**Remove or Simplify:**
- UC-059 to UC-060: Market insights - DEFER to Sprint 3/4
- UC-063 to UC-070: Advanced AI features - REMOVE (too ambitious)

**Result: 20 focused use cases**

#### 3.4 Sprint 3 Reduction: 30 → 18 Use Cases

**Keep (Core Interview & Network):**
- UC-074 to UC-077: Interview Prep Core (4 use cases) - KEEP
- UC-078: Technical Interview Prep - SIMPLIFY
- UC-079 to UC-082: Interview Calendar & Follow-up (4 use cases) - MERGE to 2
- UC-083: Salary Negotiation - KEEP
- UC-086 to UC-089: Network Management (4 use cases) - KEEP
- UC-094 to UC-097: Analytics (4 use cases) - MERGE to 2
- UC-102 to UC-105: Collaboration (4 use cases) - KEEP

**Remove:**
- UC-084 to UC-085: Advanced interview features - REMOVE
- UC-090 to UC-093: Complex networking features - REMOVE
- UC-098 to UC-101: Gamification - REMOVE (not core learning)
- UC-106 to UC-111: Advanced collaboration - DEFER

**Result: 18 focused use cases**

#### 3.5 Sprint 4 Reduction: 26 → 15 Use Cases

**Keep (Core Deployment & APIs):**
- UC-112 to UC-117: External APIs (6 use cases) - KEEP
- UC-118 to UC-120: AI Automation Core (3 use cases) - KEEP
- UC-129 to UC-136: Cloud Deployment (8 use cases) - MERGE to 6

**Remove:**
- UC-121 to UC-128: Advanced AI features - REMOVE (many already simplified)
- UC-137 to UC-138: User testing - SIMPLIFY to feedback collection

**Result: 15 focused use cases**

**New Total: ~71 use cases (down from 126) - 44% reduction**

---

## 4. API and Third-Party Integration Fixes

### Problem
*"The PRD requested features from LinkedIn, Indeed, and other companies that do not have robust public APIs that are freely available."* - Professor Feedback

*"Students were prompting with AI instead of using free APIs from national labor bureaus, news.org, etc."* - Professor Feedback

### Current Problematic APIs

| Feature | Current API | Issue | Student Workaround |
|---------|------------|-------|-------------------|
| Job Import | LinkedIn/Indeed | No free API | Web scraping / AI prompts |
| Salary Data | Glassdoor | Requires partnership | AI hallucinated data |
| Company Info | LinkedIn Company | No free API | Manual entry / AI |
| Skills Assessment | HackerRank | No free tier | AI prompts |
| Email Integration | Gmail API | Complex OAuth | Skipped entirely |
| Market Trends | Premium services | Expensive | AI prompts |

### Proposed API Replacements

#### 4.1 Replace Commercial APIs with Free Alternatives

**UC-112: Salary Data Integration**

❌ **Current:** "Integrate with Glassdoor API" (not available)
✅ **Proposed:**
- Primary: [US Bureau of Labor Statistics API](https://www.bls.gov/developers/) - Free, comprehensive
- Secondary: [H1B Salary Database](https://h1bdata.info/api.php) - Free, tech-focused
- Fallback: Manual entry with optional AI estimation

**Example Implementation:**
```javascript
// BLS API - Free, unlimited
GET https://api.bls.gov/publicAPI/v2/timeseries/data/
// Returns: occupation code, median salary, percentiles
// Coverage: All US job categories
```

**UC-041: Job Import from URL**

❌ **Current:** "Support for major job boards (LinkedIn, Indeed, Glassdoor)" (no APIs)
✅ **Proposed:**
- Remove automatic import feature entirely
- Replace with simple URL storage and manual entry
- Provide browser extension (optional) for copy-paste assist
- Focus on job organization, not import automation

**UC-114: GitHub Repository Showcase**

✅ **Current approach is good** - GitHub API is free and robust
**Enhancement:** Add code snippet to PRD showing exact API call

**UC-116: Location and Geo-coding**

✅ **Proposed replacement is already good:**
- OpenStreetMap Nominatim (free)
- Keep current Sprint 4 specification

#### 4.2 Add Specific API Documentation to PRDs

**Add to each Use Case requiring API:**

```markdown
**API Integration Details:**

API Provider: US Bureau of Labor Statistics
Endpoint: https://api.bls.gov/publicAPI/v2/timeseries/data/
Authentication: Free API key (register at bls.gov/developers)
Rate Limits: 500 requests/day (free tier)
Cost: $0
Documentation: https://www.bls.gov/developers/api_signature_v2.htm

**Example Request:**
GET https://api.bls.gov/publicAPI/v2/timeseries/data/OEUN00000000000000003
Returns: Unemployment rate time series

**Expected Response Format:**
{
  "status": "REQUEST_SUCCEEDED",
  "responseTime": 123,
  "Results": {
    "series": [
      {
        "seriesID": "OEUN00000000000000003",
        "data": [...]
      }
    ]
  }
}

**Student Tasks:**
1. Register for free API key
2. Store key in .env file
3. Implement API call with axios/fetch
4. Parse response and display in UI
5. Implement error handling and caching
```

#### 4.3 Replace AI-Dependent Features with API-First Approach

**Current Problem Areas:**

| Use Case | Current Spec | Proposed Change |
|----------|--------------|-----------------|
| UC-057: Company Research | "Use AI to generate company information" | "Use [Clearbit Logo API](https://clearbit.com/logo) (free) for logos, [Wikipedia API](https://www.mediawiki.org/wiki/API:Main_page) for company info" |
| UC-059: Market Trends | "AI analysis of market trends" | "Use [BLS Employment API](https://www.bls.gov/developers/) for real employment trends" |
| UC-074: Company Research | "AI-powered research" | "Use [News API](https://newsapi.org/) (free tier: 100 req/day) for recent company news" |

**Benefits:**
- Real, accurate data instead of AI hallucinations
- Lower costs (no AI API usage)
- Better learning outcomes (students use REST APIs)
- More impressive demos (real-time data)

---

## 5. Eliminate Redundancies and Duplications

### Problem
*"The PRD frequently had duplicate or conflicting requirements. Salary features are part of three different sprints."* - Professor Feedback

*"Many tickets overlapped or were redundant within and across sprints."* - Student Feedback

### Current Redundancies Identified

#### 5.1 Salary Information (Appears in 3 Sprints)

**Current:**
- **Sprint 2 - UC-036:** Job salary range field (basic entry)
- **Sprint 3 - UC-083:** Salary negotiation preparation
- **Sprint 4 - UC-112:** Salary data API integration

**Issues:**
- Students confused about which sprint "owns" salary
- UI had 3 different places showing salary
- Redundant database fields and API calls

**Proposed Consolidation:**

**Sprint 2 - UC-036:** Job Entry Form
- Add: Basic salary range field (text input: "$100k-120k")
- Display: On job card and detail page

**Sprint 3 - UC-083:** Salary Negotiation Tab (builds on Sprint 2)
- Location: Job Detail → "Salary" tab (NEW)
- Display: Entered salary range from Sprint 2
- Add: Negotiation notes, talking points, offer tracking
- NO new database fields

**Sprint 4 - UC-112:** Salary API Enhancement (enriches Sprint 2 data)
- Location: Same "Salary" tab from Sprint 3
- Add: Market benchmark data from BLS API
- Display: "Your range: $100k-120k | Market median: $115k"
- Enhancement, not replacement

**Single UI Location:** Job Detail → Salary Tab
- Sprint 2: Basic range input
- Sprint 3: Add negotiation tools
- Sprint 4: Add market data

#### 5.2 Company Information (Appears in 2 Sprints)

**Current:**
- **Sprint 2 - UC-043:** Company Information Display
- **Sprint 3 - UC-074:** Company Research for Interviews

**Proposed Consolidation:**

**Sprint 2 - UC-043:** Company Profile (Basic)
- Create: Company database table
- Display: Company name, industry, website, logo
- Location: Job Detail → "Company" tab

**Sprint 3 - UC-074:** Company Research (Enhancement)
- Same Location: Job Detail → "Company" tab
- Add: Recent news, interviewer info, research notes
- Builds on Sprint 2 foundation, doesn't duplicate

**Delete:** Separate company research page

#### 5.3 Profile Display (Multiple Use Cases Per Section)

**Current Pattern (Example: Skills):**
- UC-022: Add/Edit Skills
- UC-023: Display Skills
- UC-024: Organize Skills by Category
- UC-025: Skills Proficiency Indicators

**Issue:** Students created 4 separate features instead of 1 cohesive skills section

**Proposed Consolidation:**

**UC-022: Skills Management (Combined)**
- Add skills with name and proficiency level
- Auto-organize by category (frontend/backend/etc)
- Display with visual proficiency indicators
- All in ONE component, not 4 separate UIs

**Apply pattern to:**
- Employment History (merge UC-020, UC-021)
- Education (merge UC-026, UC-027, UC-028, UC-029)
- Projects (merge UC-030, UC-031, UC-032)

**Reduction:** ~12 fewer use cases

#### 5.4 Resume/Cover Letter (Overlapping Features)

**Current:**
- UC-046 to UC-054: Resume features (9 use cases)
- UC-055 to UC-056: Cover letter features (overlapping)

**Proposed Consolidation:**

**Merge Similar Operations:**
- UC-046 + UC-055: Template Management (both resume and cover letter templates)
- UC-048 + UC-056: Export/Download (unified export system)
- UC-051 + UC-053: AI Generation (same AI engine, different templates)

**Result:** 9 use cases → 6 use cases (33% reduction)

#### 5.5 Analytics Dashboards (Multiple Overlapping Dashboards)

**Current:**
- UC-044: Job Statistics
- UC-080: Interview Performance Analytics
- UC-094: Career Analytics Dashboard
- UC-095: Network Analytics
- UC-119: Application Success Optimization Dashboard

**Issue:** 5 separate dashboards with overlapping data

**Proposed Consolidation:**

**UC-094: Unified Analytics Dashboard (Tabbed Interface)**
- Tab 1: Job Search (UC-044 data)
- Tab 2: Interview Performance (UC-080 data)
- Tab 3: Network Growth (UC-095 data)
- Tab 4: Optimization (UC-119 data)

**Result:** 1 dashboard URL, 4 feature tabs instead of 5 separate pages

---

## 6. Clear Sprint Integration and Dependencies

### Problem
*"Not clear how subsequent sprints build on earlier work. The PRDs did not make it clear how subsequent features should be added to existing UX."* - Professor Feedback

### Proposed Solutions

#### 6.1 Add "Builds On" Section to Each Use Case

**Template:**

```markdown
## UC-XXX: Feature Name

**Builds On (Previous Sprint Dependencies):**
- Sprint 1, UC-016: Uses existing Profile page layout
- Sprint 1, UC-020: Displays employment history from database
- Adds: New "Skills Match" tab to existing Job Detail page (from Sprint 2)

**UI Integration:**
- Location: Job Detail page → NEW "Skills Match" tab
- Reuses: Existing tab navigation component from Sprint 2
- Data: Pulls from skills (Sprint 1) and job requirements (Sprint 2)
- DO NOT: Create separate skills matching page
```

**Example for Sprint 3, UC-074 (Company Research):**

```markdown
**Builds On:**
- Sprint 2, UC-043: Extends existing Company tab on Job Detail page
- Sprint 2, UC-036: Uses company name from job entry
- Sprint 1 Database: Stores research in new table with job_id foreign key

**UI Integration:**
- Location: Job Detail → Company tab (created in Sprint 2)
- Add to existing tab: "Research Notes" section below company info
- Add: "Generate Interview Research" button
- Display: Collapsible sections for history, news, leadership
- Reuse: Same card styling and layout from Sprint 2
```

#### 6.2 Add "Integration Checklist" to Demo Scripts

**Add to each sprint demo:**

```markdown
## Pre-Demo Integration Verification

Before running the demo, verify these integrations from previous sprints:

**Sprint 2 Demo Integration Checklist:**
□ Sprint 1 navigation menu includes new "Jobs" link
□ Profile page (Sprint 1) links to generated resumes (Sprint 2)
□ Sidebar (Sprint 1) maintained across all new pages
□ User authentication (Sprint 1) protects all new job features
□ Same design system colors/fonts used throughout

**Navigation Flow Test:**
Profile → Jobs → Job Detail → Generate Resume → View Profile
(Should flow smoothly without broken links or style inconsistencies)
```

#### 6.3 Provide "Feature Integration Map" for Each Sprint

**Add to PRD:**

```markdown
## Sprint 2 Feature Integration Map

This sprint's features integrate as follows:

┌─────────────────────────────────────────┐
│ Existing: Profile Page (Sprint 1)      │
│ ├── NEW: "Documents" tab               │ ← UC-046
│ │   ├── Resumes section                │
│ │   └── Cover Letters section          │
└─────────────────────────────────────────┘

┌─────────────────────────────────────────┐
│ NEW: Jobs Page                          │
│ ├── Pipeline View                       │ ← UC-037
│ ├── List View                           │ ← UC-039
│ └── Calendar View                       │ ← UC-040
│                                         │
│ Job Detail (click any job):             │
│ ├── Overview tab (job info)            │ ← UC-038
│ ├── Materials tab                       │ ← UC-042
│ │   ├── Link Resume (from UC-046)      │
│ │   └── Generate Cover Letter          │ ← UC-053
│ ├── Company tab                         │ ← UC-043
│ └── Analytics tab                       │ ← UC-044
└─────────────────────────────────────────┘

Navigation hierarchy:
Dashboard → Jobs → Job Detail → Materials → Generate Resume
                                           ↓
                                    Opens: Resume Editor (UC-046)
                                    Returns to: Job Detail Materials tab
```

#### 6.4 Add Database Schema Evolution Documentation

**Add to each sprint PRD:**

```markdown
## Database Changes (Evolution from Previous Sprints)

**New Tables Created This Sprint:**
- `jobs` (stores job entries from UC-036)
- `resumes` (stores resume versions from UC-046)
- `companies` (stores company info from UC-043)

**Foreign Key Relationships:**
- `resumes.user_id` → `users.id` (from Sprint 1)
- `jobs.user_id` → `users.id` (from Sprint 1)
- `jobs.company_id` → `companies.id` (new this sprint)
- `job_applications.job_id` → `jobs.id`
- `job_applications.resume_id` → `resumes.id`

**Modified Tables (from Sprint 1):**
- `users` table: NO CHANGES (maintains Sprint 1 compatibility)

**Migration Path:**
Sprint 1 database continues to work. New features add tables without modifying existing schema.
```

---

## 7. Demo Script Alignment with PRD

### Problem
*"What was expected on demo day often differed from what the sprint PRD specified. Many UCs implemented were not shown on demo day."* - Student Feedback

*"PRD included far more features than could be demonstrated in 15 minutes."* - Professor Feedback

### Proposed Solutions

#### 7.1 Align Demo Actions with Reduced Use Case Count

**Current Issue:**
- Sprint 1: 35 use cases → 47 demo actions (impossible to demo all)
- Sprint 2: 35 use cases → 52 demo actions

**Proposed:**
- Sprint 1: 18 use cases → 22 demo actions (achievable in 15 min)
- Sprint 2: 20 use cases → 24 demo actions

**Rule:** Maximum 25 demo actions per 15-minute demo (36 seconds per action)

#### 7.2 Mark "Demo Priority" on Each Use Case

**Add to each use case:**

```markdown
**Demo Priority:** CRITICAL | HIGH | MEDIUM | LOW

**Demo Inclusion:**
- CRITICAL: Must demonstrate (core learning objective)
- HIGH: Should demonstrate if time permits
- MEDIUM: Can demonstrate in extended demo
- LOW: Verify in testing, not required for demo
```

**Example:**

```markdown
## UC-001: User Registration
**Demo Priority:** CRITICAL
**Rationale:** Core authentication flow, demonstrates database persistence and validation

## UC-009: Account Deletion
**Demo Priority:** LOW
**Rationale:** Edge case feature, can verify in testing without live demo
```

#### 7.3 Provide Two Demo Scripts

**15-Minute Demo (Required):**
- CRITICAL priority use cases only
- Demonstrates core learning objectives
- Used for grading and presentation

**30-Minute Extended Demo (Optional):**
- Includes HIGH and MEDIUM priority features
- For teams who want to showcase extra work
- Can be recorded and submitted, not presented live

#### 7.4 Add "Demo Data Setup Guide" to Each Sprint

**Add to Demo Script:**

```markdown
## Demo Data Preparation (Complete 24 Hours Before Demo)

**Required Test Data:**
1. User account: demo@example.com / Password123!
2. Profile: Complete with photo, 2 jobs, 5 skills
3. Jobs: Minimum 8 jobs across all pipeline stages
   - 2 in "Interested"
   - 2 in "Applied"
   - 2 in "Interview"
   - 1 in "Offer"
   - 1 in "Rejected"
4. Resumes: 2 versions (Version A, Version B)
5. Cover letters: 1 template, 1 generated letter

**Paste-Ready Content File:**
Create `demo-content.txt` with:
- Job descriptions (ready to paste)
- Company names and details
- Interview questions and responses
- All text content pre-written

**Visual Assets:**
- Professional profile photo (not placeholder)
- Company logos for 3+ companies
- Screenshots of external references
```

---

## 8. Deployment and Testing Improvements

### Problem
*"CI/CD Pipeline wasn't fully working. Difficult transition from locally hosted website to one with permanent URL."* - Student Feedback

*"Database changes late in sprint complicated testing and integration."* - Student Feedback

### Proposed Solutions

#### 8.1 Move Deployment Earlier in Project

**Current:** Deployment is entirely Sprint 4 (final week)

**Proposed:**
- **Sprint 1 End:** Deploy basic authentication + profile to production
- **Sprint 2 End:** Deploy with job tracking features
- **Sprint 3 End:** Deploy with interview features
- **Sprint 4:** Final production hardening only

**Benefits:**
- Continuous deployment practice throughout project
- Identify deployment issues early (not during finals)
- Students experience iterative deployment (real-world practice)
- Less stress in final week

#### 8.2 Simplify Sprint 4 Deployment Requirements

**Current Sprint 4:** 26 use cases including complex monitoring, security, testing

**Proposed Sprint 4:** 8 core use cases

**Keep:**
- UC-129: Production deployment to Vercel + Render (or similar)
- UC-130: Environment variable management
- UC-131: Database migration to production
- UC-132: CI/CD pipeline (GitHub Actions)
- UC-133: Basic error monitoring (Sentry free tier)
- UC-134: Performance testing (Lighthouse)
- UC-112 to UC-117: External API integrations (6 use cases, already simplified)

**Remove:**
- UC-135 to UC-136: Advanced security (covered in Sprint 1 requirements)
- UC-137 to UC-138: User testing (too much for final week)

**Sprint 4 Focus:** Deploy what you built in Sprints 1-3, verify it works in production

#### 8.3 Add "Deployment Cutoff" Dates

**Add to Sprint 4 PRD:**

```markdown
## Deployment Timeline and Cutoffs

**Week 1 (Days 1-3):**
- Deploy frontend to Vercel
- Deploy backend to Render
- Configure environment variables
- Verify basic functionality in production

**DEPLOYMENT CUTOFF: End of Day 3**
No new features after this point. Production deployment is frozen.

**Week 1 (Days 4-7):**
- Bug fixes only
- Performance optimization
- Monitoring setup
- Demo preparation

**BUG FIX CUTOFF: Day Before Demo**
No changes to production after this point.
```

---

## 9. Requirements Clarity and AI-Generated Content

### Problem
*"Sprint guidelines should not be AI-generated - they were often unclear, convoluted, or contradictory."* - Student Feedback (40+ mentions)

*"UC explanations were vague and caused confusion on demo day."* - Student Feedback

### Proposed Solutions

#### 9.1 Replace AI-Generated Use Cases with Human-Written Specifications

**Current Issue:** Use cases appear to be AI-generated with:
- Verbose acceptance criteria
- Ambiguous requirements
- Inconsistent terminology
- Overlapping functionality

**Proposed:**
- Manually review and rewrite all 126 → 71 use cases
- Use consistent template
- Clear, concise acceptance criteria (5-7 bullets max)
- Specific, testable requirements

**Template:**

```markdown
## UC-XXX: [Specific Feature Name]

**User Story:** As a [specific user type], I want to [specific action] so I can [specific benefit].

**Acceptance Criteria (Maximum 7 bullets):**
1. [Specific, testable requirement with clear success condition]
2. [UI element with exact location: "Dashboard → Jobs → Add Job button"]
3. [Data validation with specific rules: "Email must contain @ symbol"]
4. [Error handling with exact message: "Display 'Invalid email' in red text"]
5. [API interaction: "POST /api/jobs returns 201 status code"]

**Definition of Done:**
- Feature works in production environment
- Automated tests pass for all acceptance criteria
- Demonstrates successfully in demo script
- Matches wireframe design

**Common Mistakes to Avoid:**
- Don't create separate page; add tab to Job Detail
- Don't duplicate Sprint 1 navigation; reuse existing component
```

#### 9.2 Add "Example Implementation" to Complex Use Cases

**For technically challenging use cases, add:**

```markdown
## UC-046: Resume Template Management

[Standard use case content...]

**Example Implementation Guidance:**

**Database Schema:**
```sql
CREATE TABLE resumes (
  id UUID PRIMARY KEY,
  user_id UUID REFERENCES users(id),
  template_type VARCHAR(50), -- 'chronological', 'functional', 'hybrid'
  title VARCHAR(100),
  content JSONB, -- Stores resume sections
  created_at TIMESTAMP DEFAULT NOW()
);
```

**API Endpoint:**
```javascript
// POST /api/resumes
{
  "template_type": "chronological",
  "title": "Software Engineer Resume v1",
  "content": {
    "sections": ["experience", "education", "skills"]
  }
}
```

**UI Component Hierarchy:**
```
<ResumePage>
  <TemplateSelector templates={templates} onSelect={handleSelect} />
  <ResumeEditor content={resume.content} />
  <ResumePreview content={resume.content} />
</ResumePage>
```

**Testing Checklist:**
□ Can create resume from each template type
□ Resume appears in profile documents list
□ Can export to PDF
□ Can edit and save changes
```

#### 9.3 Add Glossary and Consistent Terminology

**Add to PRD Introduction:**

```markdown
## Project Terminology (Use Consistently)

| Term | Definition | Example |
|------|------------|---------|
| **Job Entry** | A saved job opportunity in the system | "Add new job entry for Google SWE role" |
| **Job Detail Page** | The full view of a single job | "Navigate to job detail page" |
| **Pipeline Stage** | Status category for job | "Interested", "Applied", "Interview", "Offer", "Rejected" |
| **Application Materials** | Resume and cover letter | "Link application materials to job" |
| **Profile Section** | Component of user profile | "Employment history profile section" |
| **Dashboard** | Main landing page after login | "User redirected to dashboard after login" |

**Avoid These Ambiguous Terms:**
- ❌ "Job page" (unclear: list? detail? entry form?)
- ❌ "Profile" (unclear: view? edit? specific section?)
- ❌ "Resume page" (unclear: editor? list? viewer?)

**Use These Specific Terms:**
- ✅ "Job detail page" or "Jobs list page" or "Add job form"
- ✅ "Profile overview page" or "Employment section" or "Skills section"
- ✅ "Resume editor" or "Resume list" or "Resume preview"
```

---

## 10. Implementation Roadmap

### Phase 1: Immediate Changes (Before Spring 2026)

**Week 1-2: Document Updates**
- [ ] Create UI-UX-Vision.md with complete design system
- [ ] Rewrite all use cases (remove AI-generated content)
- [ ] Add wireframes to each sprint PRD
- [ ] Add API documentation with free alternatives
- [ ] Create glossary and terminology guide

**Week 3-4: Sprint Restructuring**
- [ ] Reduce use cases from 126 → 71
- [ ] Merge redundant features (salary, company info, etc.)
- [ ] Mark demo priorities on each use case
- [ ] Rewrite demo scripts to match reduced scope
- [ ] Add "Builds On" sections to each use case

**Week 5-6: Timeline Adjustments**
- [ ] Condense Week 1 lectures to 3 days
- [ ] Extend sprints from 3 weeks to 4 weeks each
- [ ] Add in-class work time (Fridays)
- [ ] Move final demo before finals week

### Phase 2: Testing with Small Group (Spring 2026 - Optional Pilot)

**If possible, pilot with 1-2 teams:**
- Test revised Sprint 1 PRD
- Gather feedback on UI/UX vision clarity
- Validate reduced scope is achievable
- Iterate on use case clarity

### Phase 3: Full Rollout (Fall 2026)

**Implement all changes with full class:**
- All 4 sprints with revised PRDs
- New timeline starting Week 1
- Continuous deployment practice
- Reduced scope, clearer requirements

### Phase 4: Continuous Improvement (Ongoing)

**After each sprint:**
- Collect student feedback on clarity
- Adjust use cases based on completion rates
- Refine API recommendations
- Update wireframes based on successful implementations

---

## 11. Success Metrics

### How to Measure Improvement

**Project Completion:**
- **Current:** ~60% of teams complete all features
- **Target:** 90%+ of teams complete all features

**UI/UX Quality:**
- **Current:** 0/14 teams created cohesive navigation
- **Target:** 80%+ of teams have integrated, intuitive navigation

**API Usage:**
- **Current:** Heavy reliance on AI prompts instead of APIs
- **Target:** 90%+ of teams successfully use real APIs

**Demo Alignment:**
- **Current:** Many features built but not demonstrated
- **Target:** 95%+ of completed features demonstrated

**Student Satisfaction:**
- **Current:** Significant complaints about scope, timing, clarity
- **Target:** 80%+ positive feedback on scope and clarity

**Finals Week Stress:**
- **Current:** High stress due to overlap with finals
- **Target:** 0% project work during finals week

---

## 12. Quick Reference Summary

### Top 10 Changes

1. **Start Week 1** (not Week 3) - 2 weeks earlier
2. **Reduce 126 → 71 use cases** - 44% scope reduction
3. **Add UI/UX Vision document** - Show final design upfront
4. **Replace commercial APIs** - Use free BLS, GitHub, OSM, News APIs
5. **Consolidate salary features** - One location, progressive enhancement
6. **4-week sprints** (not 3) - More time per sprint
7. **Finish before finals** - Week 14 final demo
8. **Add wireframes to PRDs** - Show exactly where features go
9. **Human-written requirements** - No more AI-generated use cases
10. **Continuous deployment** - Deploy after each sprint, not just Sprint 4

### Critical Documents to Create

1. **UI-UX-Vision.md** - Complete design system and navigation hierarchy
2. **API-Integration-Guide.md** - Free API documentation and examples
3. **Demo-Data-Setup.md** - Required test data for each sprint
4. **Terminology-Glossary.md** - Consistent vocabulary across PRDs

### Files to Modify

- ✏️ Sprint1PRD.md - Reduce 35 → 18 use cases, add wireframes
- ✏️ Sprint2PRD.md - Reduce 35 → 20 use cases, consolidate salary/company
- ✏️ Sprint3PRD.md - Reduce 30 → 18 use cases, remove gamification
- ✏️ Sprint4PRD.md - Reduce 26 → 15 use cases, focus on deployment
- ✏️ Sprint1Demo.md - Align with 18 use cases
- ✏️ Sprint2Demo.md - Align with 20 use cases
- ✏️ Sprint3Demo.md - Align with 18 use cases
- ✏️ Sprint4Demo.md - Simplify to deployment focus
- ✏️ README.md - Update semester timeline

---

## Conclusion

The Fall 2025 semester provided valuable insights into how students approach a complex, multi-sprint capstone project. The feedback consistently points to six key areas: overwhelming scope, poor timing, unclear UI/UX vision, impractical API requirements, redundant features, and insufficient integration guidance.

By implementing these suggested changes, the Spring/Fall 2026 semesters should see:
- Higher completion rates
- Better quality UI/UX design
- More successful API integrations
- Less stress during finals week
- Clearer understanding of how sprints build on each other
- More cohesive final applications

The project will remain challenging and comprehensive, but the scope will be achievable within the semester timeline, requirements will be crystal clear, and students will build genuinely integrated applications rather than collections of bolted-on features.

**Estimated Implementation Effort:** 40-60 hours of documentation work before Spring 2026

**Expected Student Impact:** Reduction in stress, increase in learning outcomes, better final products

---

*Document prepared by: GitHub Copilot*
*Date: December 23, 2025*
*Based on: 78 student retrospectives and professor feedback from Fall 2025*
