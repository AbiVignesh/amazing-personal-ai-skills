---
name: bank-statement-categorizer
description: Specialized skill for Indian personal finance bank statement analysis. Parse any bank statement (PDF or CSV format) and return a fully categorized transaction table with granular expense categorization, merchant identification, and inferred transaction purposes. Extract every single transaction row (no skipping or merging), clean descriptions, assign Category and Subcategory, flag inferred entries, and output both markdown table and CSV file. Use this skill whenever a user uploads or shares bank statement data in any format and wants organized expense tracking, spending analysis, or financial categorization. Works with all Indian banks and payment platforms (UPI, Wallets, etc.).
compatibility: Requires ability to parse PDF files and handle CSV data. Outputs CSV file artifact.
---

# Bank Statement Categorizer Skill

Analyze Indian personal finance bank statements with precision—extract every transaction, categorize systematically, and identify spending patterns.

## Overview

This skill transforms raw bank statement data into actionable financial intelligence by:

1. **Extracting** every single transaction row without skipping, merging, or summarizing
2. **Cleaning** descriptions (remove noise: UPI reference numbers, trace codes, etc.) while preserving merchant/payee identifiability
3. **Categorizing** each transaction with granular Category and Subcategory assignments
4. **Inferring** transaction purposes when descriptions are ambiguous, flagging inferences clearly
5. **Enriching** with Notes explaining reasoning (especially for inferred entries)
6. **Verifying** output completeness (row count matching source data)
7. **Delivering** results as both a clean markdown table AND a downloadable CSV file

The skill is optimized for Indian banking context: recognizes UPI transfers, local merchants (Swiggy, Zomato, Amazon Pay, Blinkit, Zepto, etc.), Indian rupees, and common Indian transaction patterns.

## Workflow

### Step 1: Receive & Parse Input

Accept bank statement data in one of these formats:
- **PDF**: Scanned/digital bank statements from any Indian bank (ICICI, HDFC, Axis, SBI, Kotak, RBL, etc.)
- **CSV**: Exported transaction data
- **Text**: Pasted statement data (less reliable, but parseable)

Ask clarifying questions if needed:
- **Bank name** (if not obvious from document)
- **Account type** (Savings, Current, Credit Card) — affects transaction interpretation
- **Date range** (should already be in data, but confirm)
- **Currency** (assume INR unless stated otherwise)

### Step 2: Parse All Transactions

Extract EVERY row from the statement:
- **Date**: Transaction date
- **Description**: Raw merchant/payee description
- **Debit**: Amount debited (outflow)
- **Credit**: Amount credited (inflow)
- **Balance**: Running balance (if provided in statement)

**Critical rule**: Do NOT skip any transaction. Do NOT merge similar transactions into summary rows. Each row in the source becomes one row in output.

### Step 3: Clean Descriptions

Process the Description field to remove noise while keeping merchant names clear:

**Remove:**
- UPI reference numbers (e.g., "UPI/123456789ABC")
- Transaction trace codes (e.g., "TXN REF 789456")
- Trailing codes or IDs
- Excessive whitespace or special characters
- Bank processing codes

**Keep:**
- Merchant name (e.g., "Amazon Pay", "Swiggy", "ICICI Bank", "XYZ Supermarket")
- Payee name (e.g., "Rent Payment to Landlord", "Salary from Employer")
- Location or branch info (e.g., "Café Coffee Day - Bandra", "Petrol Pump - Mumbai")
- Identifiable reference (e.g., "Insurance Premium - HDFC Life")

**Example**:
- Raw: `UPI/123456-AMAZON.COM|TXN REF ABC789-XYZ123`
- Cleaned: `Amazon.com`

### Step 4: Assign Category & Subcategory

For each transaction, assign both Category and Subcategory from the reference table below. Use the merchant name, amount, and context to determine the best fit.

**Special Rules:**
- **Blinkit/Zepto transactions**: Always categorize as `Food & Dining - Groceries - Blinkit` or `Food & Dining - Groceries - Zepto` (even if mixed items)
- **Credits**: Categorize the *source* (Salary, Refund, Transfer In, Interest, Cashback, etc.), not the use
- **Ambiguous entries**: Make your best inference and flag in Notes as `[Inferred]`
- **Multiple possible categories**: Choose the most likely based on amount, merchant, and context

### Step 5: Add Notes for Inferences

For any row where you made an assumption or inference:
- Explain your reasoning briefly
- Flag with `[Inferred]` prefix
- Example: `[Inferred] Likely grocery shopping based on Blinkit merchant`

For routine, obvious transactions (e.g., "Salary - ABC Company Ltd"), Notes can be empty or brief.

### Step 6: Verify Row Count

After completing the table:
- **Count source rows**: Total transaction rows in the original statement
- **Count output rows**: Total rows in your categorized table
- **Verify match**: Source row count = Output row count (should always be true if no rows were skipped)
- **Report**: Display verification statement: "✓ Row Count Verified: X transactions in source, X transactions in output table"

If counts don't match, review the source statement and output to find missing/duplicate rows before finalizing.

### Step 7: Output Formats

Deliver results in TWO formats:

#### Format 1: Markdown Table (for review in chat)
Clear, readable table with all columns:
```
| Date | Description | Debit (₹) | Credit (₹) | Balance (₹) | Category | Subcategory | Notes |
|---|---|---|---|---|---|---|---|
| 2024-01-01 | Salary - ABC Company Ltd | — | 75,000 | 100,000 | Income | Salary | |
| 2024-01-02 | Amazon.com | 2,500 | — | 97,500 | Shopping | Electronics | [Inferred] Mobile accessory |
```

#### Format 2: CSV File Artifact (for download/external use)
Same data, but as a downloadable CSV file. No pipe delimiters or markdown formatting—just clean CSV with headers.

## Category & Subcategory Reference

Expand subcategories as needed, but use these as the standard set:

| Category | Subcategories |
|---|---|
| **Food & Dining** | Groceries, Groceries - Blinkit, Groceries - Zepto, Restaurant, Swiggy/Zomato, Café/Coffee Shop, Bakery, Juice Bar, Specialty Food, Biryani, Idli-Dosa, Tiffin Services, Dairy Products/Milk, Dry Fruits, Diner |
| **Transport** | Fuel, Cab (Ola/Uber), Auto Rickshaw, Metro/Bus, Toll, Parking, Bike Service, Car Service, AC Service, Engine Oil, Air Filter, Travel Card Recharge, Long Distance Taxi |
| **Shopping** | Clothing, Shoes, Accessories, Electronics, Mobiles, Amazon/Flipkart, General Merchandise, Fashion Brands (Myntra, Zudio, Trends), Beauty Products, Home Decor, Jewelry, Furniture |
| **Utilities** | Electricity, Water, Gas, Internet/Broadband, Mobile Recharge, DTH/Cable, Landline, BPCL Fuel Bill |
| **Subscriptions** | OTT (Netflix/Hotstar), Software/SaaS (Zoom, Adobe, Apple Services, etc.), News Subscription, Cloud Storage, Gaming, Fintech (CRED Club) |
| **Health** | Pharmacy, Hospital, Lab Tests, Dental, Doctor Consultation, Health Insurance Premium, Fitness Tracker, Medicine Purchase |
| **Finance** | EMI, Loan Repayment, Credit Card Payment (CRED), Insurance Premium (Non-Health), Life Insurance (LIC), Bank Charges, Cash Withdrawal, Chit Payments |
| **Investments** | Mutual Fund, Mutual Fund SIP, Stocks/Brokerage (Zerodha), SIP, NPS (National Pension Scheme), Fixed Deposit, Gold Purchase, Crypto |
| **Transfers** | UPI Transfer, NEFT/IMPS, Bank Transfer, P2P Transfer, Money Transfer (to friends/family) |
| **Income** | Salary, Freelance/Contract Income, Refund, Cashback, Interest, Dividend, Bonus, Gift Received |
| **Travel** | Flight Booking (MakeMyTrip), Hotel (OYO), Train (IRCTC), Bus Booking (Redbus), Travel Packages (Klook), Taxi (Long Distance) |
| **Education** | Course Fee, Books, Tuition, Exam Fee (GMAT, IELTS, etc.), Coaching Classes, App Learning Subscriptions |
| **Entertainment** | Movies (Cinema/OTT rental), Events/Concerts, Gaming, Sports, Hobbies, Play Store |
| **Personal Care** | Salon/Haircut, Beauty Services, Gym Membership, Spa, Skincare, Grooming Products, Clothing Alterations |
| **Home & Living** | Paint & Building Materials (Asian Paints), Furniture, Home Decor, Real Estate Payments |
| **Miscellaneous** | Any unclassifiable transaction; provide explanation in Notes |

## Key Principles

### 1. Precision Over Aggregation
- Extract every row; never merge transactions
- Even if merchant appears 10 times, output 10 rows
- Maintains data integrity for analysis

### 2. Context-Aware Categorization
- Use merchant name as primary signal
- Use amount as secondary signal (e.g., ₹5,000+ for Electronics is more likely laptop than phone case)
- Use frequency/pattern if available (recurring = subscription; irregular = ad hoc purchase)
- Use location if available in description

### 3. Indian Merchant Pattern Recognition
**Insurance & Financial Products:**
- LIC, LICPGINEW, HDFC Life, Aditya Birla, Max Life → Life Insurance → Finance - Insurance Premium
- Health insurance (Aditya, Apollo, HDFC Health, etc.) → Health Insurance Premium
- CRED Club, Amazon Pay → Fintech credit card payment → Finance - Credit Card Payment
- Zerodha, 5paisa, Angel Broking → Stocks/Brokerage → Investments - Stocks

**Investment Products:**
- NPS (National Pension Scheme) → Investments - NPS
- Mutual Fund SIP, Paytm Money, Groww → Investments - Mutual Fund SIP
- Zerodha, Upstox → Investments - Stocks

**Auto & Vehicle Services:**
- Sanjay Auto, Bike Service, Engine Oil, Air Filter → Transport - Bike Service
- Shell, Indigo Fuel Pump, BPCL → Transport - Fuel
- AC Service → Transport - AC Service or Home - AC Service (context-dependent)

**Daily Essentials:**
- Blinkit, Zepto, Big Basket → Groceries
- Sobana, Milk delivery apps → Dairy Products/Milk
- Tiffin service, Dabbawala → Tiffin Services
- Zari Vault (payment app for vendor services) → Context-dependent

**Specialty & Niche:**
- Nandhana Palace, High on Chai → Specialty Food - Restaurant
- ZAD Nuts, Dry Fruits vendor → Dry Fruits
- Doveton Cafe, Starbucks, Madras Coffee → Coffee Shop
- Chudi Dhaar, Zudio, Myntra, Trends → Fashion Brands
- Premier Beauty, Salon services → Personal Care - Salon
- Klook, MakeMyTrip, Redbus, IRCTC → Travel
- Avenues GRT Jeweller, Oriana → Jewelry
- Asian Paints, BNR Estate → Home & Living
- Google Play, Apple Services → App Subscriptions

### 4. Transparent Inference
- Flag uncertain categorizations with `[Inferred]` in Notes
- Explain reasoning so user can correct if needed
- Example: `[Inferred] High amount at grocery store suggests big weekly shopping`

### 5. Indian Finance Specificity
- Recognize UPI transfers (not Finance category—use Transfers)
- Recognize Indian merchant names (Blinkit, Zepto, Swiggy, Zomato, Paytm, PhonePe, Airtel, Jio, etc.)
- Handle rupee amounts and Indian bank conventions
- Recognize common Indian deductions (TDS, Gratuity, EPF, Chit payments, etc.)
- Recognize insurance products specific to India (LIC, CRED Club, Zerodha, NPS)
- Recognize salary sources and payroll systems

### 6. Clean Output
- No extraneous information
- Consistent formatting (dates as DD-MM-YYYY or YYYY-MM-DD, amounts with commas for readability, etc.)
- Clear column headers
- Balance column included (if available in source; mark as "—" if not available)

## Example Output

### Input: Sample ICICI Bank Statement (5 transactions)
```
Date,Description,Debit,Credit,Balance
01-Jan-2024,Salary - Acme Corp,—,75000,100000
02-Jan-2024,AMAZON.COM UPI REF 123ABC,2500,—,97500
03-Jan-2024,BLINKIT TRANSFER,1200,—,96300
04-Jan-2024,FUEL PUMP SHELL,800,—,95500
05-Jan-2024,EMI CREDIT CARD,5000,—,90500
```

### Output: Categorized Table
| Date | Description | Debit (₹) | Credit (₹) | Balance (₹) | Category | Subcategory | Notes |
|---|---|---|---|---|---|---|---|
| 01-Jan-2024 | Salary - Acme Corp | — | 75,000 | 100,000 | Income | Salary | |
| 02-Jan-2024 | Amazon.com | 2,500 | — | 97,500 | Shopping | Electronics | [Inferred] E-commerce purchase |
| 03-Jan-2024 | Blinkit | 1,200 | — | 96,300 | Food & Dining | Groceries - Blinkit | |
| 04-Jan-2024 | Shell Petrol Pump | 800 | — | 95,500 | Transport | Fuel | |
| 05-Jan-2024 | Credit Card EMI Payment | 5,000 | — | 90,500 | Finance | EMI | |

✓ **Row Count Verified**: 5 transactions in source, 5 transactions in output table

### CSV Output File
```csv
Date,Description,Debit (₹),Credit (₹),Balance (₹),Category,Subcategory,Notes
01-Jan-2024,Salary - Acme Corp,—,75000,100000,Income,Salary,
02-Jan-2024,Amazon.com,2500,—,97500,Shopping,Electronics,[Inferred] E-commerce purchase
03-Jan-2024,Blinkit,1200,—,96300,Food & Dining,Groceries - Blinkit,
04-Jan-2024,Shell Petrol Pump,800,—,95500,Transport,Fuel,
05-Jan-2024,Credit Card EMI Payment,5000,—,90500,Finance,EMI,
```

## Special Handling Rules

### Blinkit & Zepto
- Always use `Food & Dining - Groceries - Blinkit` or `Food & Dining - Groceries - Zepto`
- Even if Blinkit shows mixed items (snacks, household, etc.), classify as Groceries with Blinkit subcategory
- Example: Blinkit ₹1,500 → `Food & Dining | Groceries - Blinkit`

### Credit Cards & Wallets
- Google Pay, Apple Pay, Paytm, PhonePe transfers: `Transfers | UPI Transfer` (if to person) or classify by use if identifying specific merchant
- Credit card payment (paying balance): `Finance | Credit Card Payment`
- Credit card purchase (appears as debit): Classify by what was purchased

### Ambiguous Small Amounts (₹100-500)
- ₹150 at Café Coffee Day → `Food & Dining | Café` (safe assumption)
- ₹200 at pharmacy → `Health | Pharmacy` (safe assumption)
- ₹300 payment to "S. Sharma" (no context) → `Transfers | P2P Transfer` + `[Inferred] Personal transfer based on description`

### Recurring Transactions
- If same merchant appears multiple times at same amount (e.g., Netflix ₹649 monthly): Categorize each occurrence separately, even if identical
- Don't merge into summary

### Missing or Incomplete Data
- If Balance column missing: Use "—" for all Balance entries
- If Date is unclear: Best guess and flag as `[Inferred] Date estimated`
- If Description is blank: Flag as `[Inferred] No description; assumed based on pattern`

## Checklist Before Finalizing Output

- [ ] All rows from source statement extracted (row count matches)
- [ ] Descriptions cleaned (no UPI refs, trace codes)
- [ ] Category assigned to every row
- [ ] Subcategory assigned to every row
- [ ] All inferred entries flagged with `[Inferred]` in Notes
- [ ] Credits are categorized by source (Salary, Refund, etc.), not by intended use
- [ ] Blinkit/Zepto entries use correct subcategory
- [ ] Markdown table created and readable
- [ ] CSV file created with proper headers and formatting
- [ ] Row count verification statement included
- [ ] Both outputs (Markdown + CSV) ready for delivery

## Output Delivery

### Tell the user:
1. **Row count verification**: "✓ Verified: X transactions extracted and categorized"
2. **Summary insights** (optional): "Top spending category: Food & Dining (₹5,200), followed by Transport (₹3,100)"
3. **Provide both**:
   - Markdown table in chat (for immediate review)
   - CSV file link (for download and external use)

### If Issues Found:
- "Found X ambiguous entries—flagged all with `[Inferred]`. Review Notes column for reasoning."
- "X transaction(s) lacked sufficient description—best classified as Miscellaneous. Check Notes for details."

## Important Notes

- **Privacy**: This skill handles sensitive financial data. Treat with utmost care; never share categorized data without user consent.
- **Accuracy Limitations**: Bank descriptions can be cryptic. Some categorizations are inferences; user should review and correct if needed.
- **Customization**: If user's spending patterns don't fit standard categories, offer to adjust. This reference list is a starting point, not a restriction.
- **Reusability**: Output CSV can be imported into Excel, Google Sheets, or other finance tools for further analysis.

