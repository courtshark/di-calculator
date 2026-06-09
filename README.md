# Equity Gap Calculator

A browser-based tool that measures **Disproportionate Impact (DI)** across student subgroups using the official CCCCO **PPG-1 (Percentage Point Gap)** methodology.

**Live site →** [https://di-calculator.com/](https://di-calculator.com/)

---

## What it does

The calculator shows which student groups are succeeding at lower rates than their peers — and by exactly how much. It flags Disproportionate Impact when a group's success rate falls below the college-wide comparison rate by more than the statistical margin of error (Threshold E).

Results are color-coded:
- 🔴 **Disproportionate Impact** — gap exceeds the margin of error
- 🟡 **Watch** — gap is notable but within the margin of error
- ✅ **No DI** — group is performing at or above the comparison rate

---

## How to use it

### Option 1 — Manual entry
Enter subgroup names, success counts, and enrollment totals directly into the input tables. Data is saved automatically in your browser.

### Option 2 — Import from a CSV or Excel file
Click **Import Data** and upload a student-level export. The tool auto-detects columns for year, race/ethnicity, gender, age, discipline, education goal, and course. After import, use the filter bar to focus on a specific course.

**Supported columns in your upload:**
| Column | Examples |
|---|---|
| Term / Year | `Term`, `AcademicYear` |
| Race/Ethnicity | `Race`, `Ethnicity` |
| Gender | `Gender` |
| Age | `Age`, `AgeGroup` |
| Successes | `SuccessCount`, `Passed` |
| Total enrolled | `EnrollmentCount`, `Total` |
| Course | `Course`, `Section`, `CRN` |
| Discipline | `Discipline`, `Subject`, `Dept` |
| Education Goal | `EducationGoal`, `IntendedGoal` |

---

## Analysis tabs

| Tab | What it analyzes |
|---|---|
| Race/Ethnicity | AM Ind/Ntv Alsk, Asian, Black, Hispanic/Latinx, White, etc. |
| Gender | Men, Women, Non-binary/Other |
| Age | Under 18, 18–24, 25–39, 40+ |
| Discipline | Subject area / department |
| Ed. Goal | Transfer, AA/AS, career, personal enrichment, etc. |

Switch tabs to view DI analysis for each dimension. When data is imported, tabs populate automatically.

---

## Exporting results

Click **Export Excel** to download a `.xlsx` file with four sheets:

| Sheet | Contents |
|---|---|
| DI Analysis | PPG-1 value and DI status per group per year |
| Success Rates | Calculated success rate (%) per group per year |
| Students Succeeded | Raw success counts |
| Total Enrolled | Raw enrollment counts |

---

## Sharing results

Click **Share** to copy a URL that encodes the full dataset. Anyone with the link sees the exact same view — same data, same filters, same tab.

---

## Methodology

This tool implements the **CCCCO PPG-1** method as defined in the *Student Equity and Achievement Program* guidelines:

```
PPG-1 = sgRate − compRate
```

Where:
- `sgRate` = subgroup success rate
- `compRate` = success rate of all *other* students (proportionality index)
- **DI is flagged when** `PPG-1 ≤ −E` (Threshold E = margin of error based on subgroup size)

The tool requires a minimum of **n = 10** students per subgroup to report results, per CCCCO guidance.

---

## Project files

| File | Purpose |
|---|---|
| `index.html` | Page structure and all UI markup |
| `script.js` | All logic — data grid, calculations, import, export, share |
| `style.css` | Styling |
| `xlsx.full.min.js` | SheetJS library for Excel import/export (bundled locally) |

No build step. No framework. Open `index.html` in any browser or deploy as a static site.

---

## Running locally

```bash
npx serve -p 4200 .
# then open http://localhost:4200
```

---

## Deployment

Hosted on Vercel and connected to this repository. Every push to the `main`
branch deploys automatically to production; pushes to other branches create
preview deployments.

- **Production:** [di-calculator.com](https://di-calculator.com)

---

Built by Courtney Youngberg
