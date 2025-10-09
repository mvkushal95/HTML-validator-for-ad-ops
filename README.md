# All-In-One Creative Validator PRD(Internal Tool):

---

## **Goals & Objectives**

### **Business Goal**

Accelerate campaign delivery by streamlining and automating creative QA across all asset types — HTML5, image, and video — while reducing dependency on external tools.

### **Product Objective**

Develop an enhanced, browser-based **Creative Validator** that:

- Allows **multi-asset uploads (up to 12 files)** across formats (HTML5, image, video)
- Performs **revenue-impact-based validations** (file size, dimensions, redirect checks)
- Provides a **centralized, single-session validation workflow** for Creative, Ad Ops, and Programmatic teams
- Supports **client-facing previews** through the **Native Preview Validator tab** for Account Managers


## **Hypothesis**

If we provide an all-format internal validator with automated rule checks (size, landing page, click handler, and dimensions) and native preview capability, then:

- Teams can QA 20–30 creatives in a single session without tool restrictions.
- The validator will eliminate manual size checks and reduce trafficking errors caused by non-compliant assets.
- Overall QA time per campaign will drop by **50% or more**, enabling faster and more accurate launches.

---

## **Proposed Solution**

We will built into a **multi-format Creative Validator** with integrated revenue-impact checks and native preview support.

### **Core Features**

### **1. Multi-File Upload (Up to 12 Assets)**

- Supports mixed asset uploads: `.zip`, `.jpg`, `.png`, `.mp4`, `.webm`
- Files processed simultaneously within a single validation session

### **2. Revenue Impact Rulebook**

- Automatic validation against file size thresholds:
    - **HTML & Image Files:** ≤ 5 MB → *Accepted by Exchange*
    - **Video Files:** ≤ 1 GB → *Accepted by Exchange*
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

- Validate large creative batches quickly (12 at once)
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

| Metric |
| --- |
| 100% creatives render correctly at intended ad sizes |
| 95%+ clickTags and landing pages extracted accurately |
| Average QA time per campaign reduced by ≥50% |
| 0 trafficking errors related to missing/broken clickTags |
| Adoption by all internal teams within 1 month of release |

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

The **Internal Creative Validator** allows teams to upload up to **12 creatives** of any type (HTML5, image, video), validate them against **revenue impact rules**, and instantly check landing pages, click handlers, and dimensions. It also supports **PDF report export** and includes a **Native Preview Validator** for client demos.

This tool eliminates external tool limits, cuts QA time in half, and ensures every creative meets exchange readiness — driving faster, error-free campaign launches.
