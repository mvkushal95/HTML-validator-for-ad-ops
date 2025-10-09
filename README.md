# All-In-One Creative Validator PRD(Internal Tool):

**Problem Statement:**

Third-party HTML5 creative validation tools often impose strict usage limits (e.g., 5–10 previews per session) or require paid access. However, our creative and ad operations teams frequently need to validate **20–30 creatives at a time** during campaign launches and QA cycles.

These restrictions create workflow bottlenecks, forcing teams to either:

- Split validation across multiple sessions (time-consuming), or
- Skip thorough QA checks (risking trafficking errors in CM360).

As a result, the current process is **inefficient, repetitive, and error-prone**, slowing down campaign delivery and increasing the risk of issues being caught late.

### **Goals & Objectives**

### **Business Goal:**

Ensure thorough and efficient QA checks for HTML5 creatives by reducing reliance on restricted third-party tools and eliminating the need for multiple validation sessions. This will speed up campaign delivery and minimize trafficking errors.

### **Product Objective:**

Develop an internal HTML5 Creative Validator that:

- Automatically extracts the **landing page URL** from any platform type (e.g., Google Web Designer, custom JavaScript implementations).
- Accurately **renders the creative** in its intended dimensions.
- Validates critical behaviors:
    - Proper rendering of creative frames
    - Presence of click handler
    - Redirect functionality (click opens the extracted landing page)
- Provides a single, reliable workflow for creative and ad ops teams to QA large volumes of creatives without interruption.

### **Hypothesis**

If we build an internal HTML5 Creative Validator that can extract landing page URLs, validate click Tags, and render creatives exactly as they appear in CM360/Ad Manager, then:

- The creative and ad ops teams will be able to QA **20–30 creatives in a single session** without external tool restrictions.
- This will **reduce trafficking errors** caused by missing or misconfigured click Tags.
- QA time per campaign will decrease significantly, enabling **faster campaign launches** and **greater confidence** in creative quality.

### **Proposed Solution**

We will develop a lightweight, browser-based **HTML5 Creative Validator** that allows the creative and ad ops teams to validate zipped HTML5 creatives quickly and without usage restrictions.

Key elements of the solution:

1. **Zip Upload & Extraction**
    - Users can upload creative .zip files directly in the browser.
    - Tool extracts assets (HTML, JS, CSS, images) using JSZip.
2. **HTML File Detection**
    - Automatically identifies the main entry point (index.html or equivalent).
3. **ClickTag Validation & Extraction**
    - Detects whether a valid clickTag or GWD exit event is present.
    - Extracts and displays the landing page URL for review.
4. **Creative Rendering**
    - Rebuilds creative with Blob asset references for secure preview.
    - Renders in an iframe with correct dimensions (from ad.size meta or fallback).
    - Removes scrollbars to match actual ad serving environment.
5. **Clickability Check**
    - Ensures creatives are fully clickable by injecting an anchor overlay if required.
    - Validates that clicks redirect to the **extracted landing page** in a new tab.
6. **Results Dashboard**
    - Displays clear pass/fail checks for:
        - Click handler presence
        - Landing page extraction
        - Creative preview rendering
        - Click-through behavior

By providing this in-house solution, the team will be able to **validate unlimited creatives in one session**, reduce dependency on third-party tools, and ensure high QA standards before trafficking.

### **Constraints:**

- **File Size Limitations**
    - Large creatives (e.g., >50MB zips) may cause browser performance issues during extraction and rendering.
- **Browser Dependency**
    - Tool is optimized for Chrome/Edge. Other browsers (e.g., Safari, IE) may have limited compatibility and this specific validator is built on Github public server so can crash at anytime.
- **ClickTag Variations**
    - While standard clicktag and GWD exits are supported, non-standard custom scripts may not always be detected.
- **No Real Ad Server Environment**
    - The validator replicates CM360 behavior as closely as possible, but it does not simulate ad serving conditions (e.g., impressions, viewability, tracking pixels).
- **Security Restrictions**
    - External scripts (e.g., CDN-hosted JS libraries) may not load in preview mode due to cross-origin or CSP restrictions.

### **User Impact**

**For Creative Team:**

- Can validate multiple creatives (20–30+) in one go without hitting usage caps.
- Saves time by instantly previewing creatives in their correct dimensions.
- Confirms creatives are clickable and redirect correctly, avoiding back-and-forth with ad ops.

**For Ad Ops Team:**

- Reduces trafficking errors by verifying clickTags before upload to CM360.
- Eliminates dependency on third-party preview tools.
- Speeds up campaign QA → faster campaign launches.

**For Business:**

- Minimizes campaign delays caused by QA bottlenecks.
- Reduces the risk of serving non-compliant or broken creatives.
- Improves trust and collaboration between creative and ad ops teams.

### **Success Metrics**

- 100% of creatives uploaded render at their correct ad size.
- 90%+ of clickTags automatically detected and extracted correctly.
- Average QA time per campaign reduced by **50%** (e.g., from 1 hour → 30 mins).
- 0 trafficking errors related to missing/broken clickTags after rollout.
- Adoption: Creative and Ad Ops teams use the tool for **all campaigns within 1 month** of launch.

### **Timeline**

- **Week 1–2**: Finalize requirements, design PRD, align with stakeholders.
- **Week 3–4**: Develop MVP (upload, render, clickTag extraction).
- **Week 5**: Internal QA + feedback loop with Creative & Ad Ops teams.
- **Week 6**: Rollout to full team, document usage guidelines.
- **Post-launch (Ongoing)**: Enhancements (multi-clickTag detection, asset size validation, exportable reports).

### **Owner / Stakeholders**

- **Product Owner**: M.V.Kusal
- **Primary Users**: Creative Team, Ad Ops Team
- **Stakeholders**:
    - Marketing Ops
    - Campaign Management

### **Dependencies**

- **JSZip Library** (for file extraction)
- **Modern Browser Support** (Chrome/Edge preferred)
- **GitHub Hosting / GitHub Pages** (for accessibility)
- **Creative Team Input** (test cases with real zips)

### **TL;DR**

Third-party HTML5 validators are restrictive and inefficient for high-volume QA. We’re building an internal HTML5 Creative Validator that extracts clickTags, validates landing pages, and renders creatives in their correct dimensions. This tool will eliminate external tool limits, reduce trafficking errors, and cut QA time by half — empowering Creative and Ad Ops teams to move faster and with greater confidence.

Current third-party HTML5 and asset validation tools still impose strict session-based limits (5–10 creatives) or require paid accounts. However, creative, ad ops, and programmatic teams regularly need to **validate 20–30+ creatives** across different formats (HTML5, static image, and video) during campaign QA and launch.

These limitations result in:

- Repetitive, time-consuming split sessions
- Inconsistent QA coverage
- Delays in campaign activation and potential trafficking errors in CM360 or DSPs

This leads to **inefficient workflows and avoidable campaign risks**.

---

## **Goals & Objectives**

### **Business Goal**

Accelerate campaign delivery by streamlining and automating creative QA across all asset types — HTML5, image, and video — while reducing dependency on external tools.

### **Product Objective**

Develop an enhanced, browser-based **Internal Creative Validator** that:

- Allows **multi-asset uploads (up to 12 files)** across formats (HTML5, image, video)
- Performs **revenue-impact-based validations** (file size, dimensions, redirect checks)
- Provides a **centralized, single-session validation workflow** for Creative, Ad Ops, and Programmatic teams
- Supports **client-facing previews** through the **Native Preview Validator tab** for Account Managers

---

## **Hypothesis**

If we provide an all-format internal validator with automated rule checks (size, landing page, click handler, and dimensions) and native preview capability, then:

- Teams can QA 20–30 creatives in a single session without tool restrictions.
- The validator will eliminate manual size checks and reduce trafficking errors caused by non-compliant assets.
- Overall QA time per campaign will drop by **50% or more**, enabling faster and more accurate launches.

---

## **Proposed Solution**

We will enhance the existing internal HTML5 Validator into a **multi-format Creative Validator** with integrated revenue-impact checks and native preview support.

### **Core Features**

### **1. Multi-File Upload (Up to 12 Assets)**

- Supports mixed asset uploads: `.zip`, `.jpg`, `.png`, `.mp4`, `.webm`
- Files processed simultaneously within a single validation session

### **2. Revenue Impact Rulebook**

- Automatic validation against file size thresholds:
    - **HTML & Image Files:** ≤ 5 MB → ✅ *Accepted by Exchange*
    - **Video Files:** ≤ 1 GB → ✅ *Accepted by Exchange*
- Returns clear **status messages** (green success or red error) indicating compliance
- Helps teams proactively identify heavy or non-compliant creatives before trafficking

### **3. HTML5 Creative Analysis**

- Extracts **landing page URL** and validates click handlers (`clickTag`, `GWD.exit`, etc.)
- Displays:
    - Landing page link (clickable)
    - Creative dimensions
    - Creative preview within the tool
    - **Refresh button** to re-render and check multiple frames or animation behavior

### **4. Image & Video Validation**

- Displays file dimensions and playback (for video)
- Applies the same revenue impact validation logic
- Ensures exchange-ready compliance without additional manual checks

### **5. Report Generation**

- Generates validation reports
- Allows **export as CSV or PDF** for documentation, sharing, or client review

### **6. Native Preview Validator (Client-Facing Tab)**

- Dedicated interface for **Account Managers** to:
    - Upload and preview native ad components (headline, body text, logo, CTA)
    - Render **live ad mockups** with client branding
    - Share real-time previews with clients during review calls or presentations

---

## **User Impact**

### **Creative Team**

- Validate large creative batches quickly (12+ at once)
- Check landing pages and dimensions without external tools
- Confirm exchange readiness instantly

### **Ad Ops & Programmatic Teams**

- Avoid trafficking errors due to oversize creatives or missing click handlers
- Ensure all creatives are compliant before trafficking
- Save hours per campaign with instant validation reports

### **Account Managers**

- Use the **Native Preview Validator** for polished client previews
- Quickly upload, edit, and showcase native ad designs during review

### **External Stakeholders (Clients)**

- Receive live previews that reflect how ads will appear across placements
- Gain confidence in ad quality and brand alignment

---

## **Business Impact**

- **Reduced QA turnaround:** Campaign validation time cut by 50%+
- **Fewer trafficking errors:** Near-zero non-compliant uploads to CM360/DSPs
- **Improved collaboration:** Creative, Ad Ops, and AM teams work from one unified tool
- **Client confidence boost:** Faster previews and validated creatives

---

## **Success Metrics**

| Metric | Target |
| --- | --- |
| 100% creatives render correctly at intended ad sizes | ✅ |
| 95%+ clickTags and landing pages extracted accurately | ✅ |
| Average QA time per campaign reduced by ≥50% | ✅ |
| 0 trafficking errors related to missing/broken clickTags | ✅ |
| Adoption by all internal teams within 1 month of release | ✅ |

---

## **Timeline**

| Phase | Timeline | Deliverables |
| --- | --- | --- |
| **Week 1–2** | Requirements Finalization & UI Design | Align on multi-file logic + rulebook thresholds |
| **Week 3–4** | Development | Upload engine, validation logic, rendering & reporting |
| **Week 5** | Internal QA | Test with real HTML/image/video creatives |
| **Week 6** | Launch | Rollout + internal demo |
| **Post-Launch (Ongoing)** | Enhancements | Multi-clickTag detection, preview theming, report filters |

---

## **Stakeholders**

**Internal Stakeholders:**

- Ad Ops Team
- Programmatic Team
- Creative Team
- Account Managers

**External Stakeholders:**

- Clients (for native preview sharing)

**Product Owner:**

- *M.V. Kushal*

---

## **Dependencies**

- **JSZip Library** for HTML zip extraction
- **Modern Browser Support** (Chrome/Edge recommended)
- **GitHub Hosting / Pages** for tool access
- **Creative Assets** for ongoing test coverage

---

## **Constraints**

- **File Size Limits:** Large zips (>50MB) may lag during extraction.
- **Browser Performance:** Optimized for Chromium browsers.
- **External Resources:** CDN or cross-origin assets may fail to load in sandboxed previews.
- **Simulation Limitations:** Does not replicate real impression or tracking behavior of CM360/DSP.

---

## **TL;DR**

The **Internal Creative Validator v2.0** allows teams to upload up to **12 creatives** of any type (HTML5, image, video), validate them against **revenue impact rules**, and instantly check landing pages, click handlers, and dimensions. It also supports **PDF report export** and includes a **Native Preview Validator** for client demos.

This tool eliminates external tool limits, cuts QA time in half, and ensures every creative meets exchange readiness — driving faster, error-free campaign launches.
