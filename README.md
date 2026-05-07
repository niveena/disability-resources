# Disability Resources Dashboard
### UVA & Charlottesville Community

An interactive, single-page web app for navigating disability resources at the University of Virginia and in the broader Charlottesville community. Built as a course project for **EDIS 2020** at the University of Virginia.

**Live site:** [niveena.github.io/disability-resources](https://niveena.github.io/disability-resources)

---

## What it does

- **Two resource tabs** -- UVA resources (free, enrolled students only) and Charlottesville community resources (open to all)
- **Hover to preview** -- hover any card to see access requirements, cost, and hours without clicking
- **Click for full details** -- opens a modal with contact info, directions link, and eligibility breakdown
- **Live filters** -- filter by category, cost, diagnosis requirement, or whether a resource is open right now
- **Disability law section** -- plain-language summaries of ADA, Section 504, IDEA, ADAAA, and Virginia-specific laws
- **Google Maps links** -- every physical location links directly to directions
- **Mobile responsive** -- works on phones and tablets

---

## Resources included

### UVA (enrolled students, all free)
| Resource | Category |
|----------|----------|
| SDAC -- Student Disability Access Center | Academic Accommodations |
| CAPS -- Counseling & Psychological Services | Mental Health |
| TimelyCare | Mental Health (24/7 virtual) |
| UVA Library Access Services | Assistive Technology |
| UVA Captioning & Transcription Project | Captioning |

### Charlottesville Community (open to all)
| Resource | Category |
|----------|----------|
| Region Ten Community Services Board | Mental Health & Developmental |
| The Arc of the Piedmont | Developmental Disabilities |
| JABA -- Jefferson Area Board for Aging | Aging & Disability Support |
| Virginia DARS -- Vocational Rehabilitation | Vocational Rehab |
| PVCC Disability Services | Academic Accommodations |
| Charlottesville Dept. of Social Services | Government & Benefits |

---

## How to add or edit resources

All resource data lives in `index.html` inside two JavaScript arrays near the top of the `<script>` block

**To add a UVA resource**, find the `RESOURCES` array and paste in a new object following this shape:

```js
{
  id: 6,                          // unique number, don't reuse
  name: "Resource Name",
  description: "One or two sentences describing what this resource does.",
  category: "Display Label",      // shown on the card tag
  categoryKey: "academic",        // "academic" | "mental" | "assistive" | "captioning" | "community"
  icon: "📋",                     // emoji shown on the card
  callToConfirm: false,           // set true if any details need verification
  unverifiedNote: "",             // explanation shown in modal if callToConfirm is true
  accessRequirements: {
    diagnosisRequired: false,
    insuranceRequired: false,
    enrolledRequired: true,
    cost: "free"                  // "free" | "sliding scale" | "paid" | "varies"
  },
  hours: {
    display: "Mon-Fri, 8:00 AM - 5:00 PM",
    days: [1,2,3,4,5],            // 0=Sun, 1=Mon ... 6=Sat
    openHour: 8,
    closeHour: 17,
    alwaysOpen: false,
    unknown: false
  },
  location: {
    type: "on-grounds",           // "on-grounds" | "off-grounds" | "virtual"
    address: "Building Name, UVA"
  },
  contact: {
    phone: "434-000-0000",        // or null
    email: "email@virginia.edu",  // or null
    website: "https://example.com"
  },
  lastUpdated: "2025-01-01"
}
```

**To add a community resource**, paste the same structure into the `COMMUNITY_RESOURCES` array. Use these `categoryKey` values: `"mental"`, `"developmental"`, `"rehabilitation"`, `"support"`, `"academic"`, `"community"`.

**To update an existing resource**, find its entry by `id` or `name` and edit the relevant fields. Set `lastUpdated` to today's date.

---
## Data accuracy

- **UVA resources** -- verified against official UVA websites (spring 2025). Check back each semester as hours and contacts can change.
- **Community resources** -- gathered from public organizational websites. Several entries are marked "Call to confirm" where specific details (hours, eligibility) could not be independently verified. Always call ahead before visiting.

---

## Course context

This dashboard was created for **EDIS 2020: Introduction to Disability Studies** at the University of Virginia as an interactive educational resource exploring access, accommodation, and disability rights in a university and community setting. 

## Limitations
This dashboard is a best-effort resource guide compiled individually from public websites, phone directories, and direct outreach. It is not exhaustive and is not affiliated with or endorsed by the University of Virginia or any of the organizations listed. Resource details can change at any time, and some entries (marked "Call to confirm") could not be fully verified at the time of publication. Always confirm details directly with the organization before visiting or relying on this information.
This site is actively growing. If you know of a resource that should be listed, find an error, or have updated information, please open a GitHub issue or reach out directly.




---

*Data current as of Spring 2026. If you find an error or a resource that should be added, please open an issue or submit a pull request.*