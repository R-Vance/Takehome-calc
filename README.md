# CA Household Paycheck & Tax Calculator

A single-file, client-side California paycheck and household tax calculator built for public employees. No server, no tracking, no ads — open `index.html` in any browser and it works.

---

## Features

### Paycheck breakdown
- Full per-paycheck itemization of every deduction and tax line
- Supports **weekly, bi-weekly, semi-monthly, and monthly** pay frequencies
- Health plan premiums entered **monthly** (auto-divided by pay frequency)
- All other deductions entered **per pay period**
- Overtime section with **auto-calculation** from hourly rate × hours, or manual annual entry

### Pre-tax deductions
- Medical, dental, vision (monthly)
- HSA, FSA, life/disability, commuter/parking, other Section 125 (per period)
- **Defined-benefit pension contribution** (CalPERS, STRS, PERS, or any DB plan) as a % of base salary
- **Employer Pick-Up / EPMC toggle (§414(h)(2)):** correctly separates contributions excluded from both federal and CA wages vs. standard employee contributions that are pre-tax federally but **taxable for CA** — the single most common source of CA tax calculation errors for public employees

### Retirement accounts
- **457(b)** — Traditional and Roth; correctly adds traditional 457(b) deferrals back to CA taxable income (CA does not conform to §457 deferrals)
- **401(k) / 401(a)** — Traditional and Roth with employer match
- Live annual total display with IRS contribution limit warnings ($23,500 for 2025)
- Projected retirement balance using compound growth (zero-return safe formula)
- 4% annual drawdown estimate

### Dependent & tax credits
- **Child Tax Credit** — $2,000/child under 17, with correct income phase-out (MAGI-based, not gross)
- **Credit for Other Dependents** — $500/each
- **Child & Dependent Care Credit** — full 14-tier IRS §21 rate table (20–35%)
- **CA Child & Dependent Care Credit** — full 9-tier R&TC §17052.6 table
- **CA Young Child Tax Credit (YCTC)** — $1,117/child under 6, with CA EITC income gate applied
- **CA Dependent Exemption Credit** — $433/dependent

### Taxes
- **2025 federal income tax brackets** and standard deductions
- **2024–25 CA FTB rate schedules** with correct personal exemption credits applied post-bracket (not subtracted from AGI)
- Social Security / OASDI (6.2%, wage base $176,100) — toggle to exempt
- Medicare (1.45% standard + 0.9% Additional Medicare Tax above $200k single / $250k MFJ) — correct MFJ threshold
- CA SDI (0.9%, wage base $153,164) — toggle to exempt

### Couple / household mode
- **Side-by-side Person A and Person B** — completely independent income, deductions, accounts, and dependents
- Each person has their own pay frequency, filing status, SS/SDI exemption, and deduction structure
- **True MFJ joint tax estimate:** combines both incomes on a single joint return and compares against individual withholding — flags under- or over-withholding so you can adjust W-4 Step 3 before filing
- Dependent credits combined correctly for the joint return
- **Social Security spousal benefit note** with WEP/GPO warnings where applicable
- Combined retirement account summary

### Single mode
Collapses to one person — no clutter.

### Print / PDF
Print button in the header. Results are print-styled — browser print or Save as PDF works cleanly.

---

## Tax accuracy notes

| Item | Implementation |
|---|---|
| Federal brackets | 2025 IRS tables |
| CA brackets | 2024–25 FTB schedules |
| CA standard deduction | $5,540 single / $11,080 MFJ / $11,080 HOH |
| CA personal exemption credit | $144 single / $288 MFJ / $433 HOH (applied post-bracket) |
| 457(b) CA treatment | Added back to CA taxable income (CA non-conformity) |
| Pension pickup (§414(h)(2)) | Toggle: excluded from fed+CA vs. excluded from federal only |
| CTC phase-out | MAGI-based (fedTaxable used as proxy), not gross |
| CDCC rate | Full 14-tier IRS table (20–35%) |
| CA CDCC rate | Full 9-tier FTB table (10–50%), 0% above $100k |
| YCTC | $1,117/child; income gate at ~CA EITC ceiling |
| Medicare surcharge | 0.9% above $200k single / $250k MFJ |
| SS wage base | $176,100 (2025) |
| SDI wage base | $153,164 (2025) |
| Retirement account FV | Zero-return safe formula |

---

## Usage

1. Download or clone the repository
2. Open `index.html` in any modern browser
3. No installation, no dependencies, no internet required after the Google Fonts load

```bash
git clone https://github.com/YOUR_USERNAME/ca-paycheck-calculator.git
cd ca-paycheck-calculator
open index.html   # macOS
# or just double-click index.html in your file manager
```

To host on GitHub Pages: push to a repository and enable **Settings → Pages → Deploy from branch → main / root**.

---

## Repository structure

```
/
├── index.html      # Complete self-contained calculator (HTML + CSS + JS)
└── README.md       # This file
```

All logic is in a single file for maximum portability. No build step, no npm, no frameworks.

---

## Disclaimer

This calculator is for **illustrative planning purposes only** and does not constitute tax, legal, or financial advice. Figures are estimates based on 2024–25 tax schedules and IRS/FTB rules as of the date of publication. Tax law changes frequently — verify current rates with the IRS (irs.gov) and California FTB (ftb.ca.gov). For official paycheck calculations, consult your employer's payroll department. For tax filing, consult a licensed CPA or tax professional.

---

## Contributing

Issues and pull requests welcome. If you spot a tax calculation error, please open an issue with:
- The specific field/formula you believe is wrong
- The correct value and source (IRS publication, FTB guidance, etc.)

---

*Built with plain HTML, CSS, and vanilla JavaScript. No tracking. No data leaves your browser.*
