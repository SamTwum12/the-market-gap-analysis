# Market Gap Analysis: Open Food Facts

## A. The Executive Summary
This market analysis of the Open Food Facts dataset (500,000 products) reveals a significant "Blue Ocean" opportunity in the Sweets category, which is the most underserved space for health-conscious consumers. The data identifies a specific Opportunity Zone for products containing ≥13g of protein and less than 5g of sugar per 100g — thresholds derived from the 75th/25th percentile of existing high-protein / low-sugar Sweets products. Only 4.0% of the 47,875 products in this category currently sit in the High-Protein / Low-Sugar quadrant, the lowest penetration of any major category. Furthermore, the "Candidate's Choice" NutriScore Gap Analysis confirms that Sweets carries the worst average NutriScore of all categories (5.00 — effectively all E-grade), meaning a NutriScore A/B product in this aisle would have an immediate and decisive on-shelf advantage, particularly in EU markets where front-of-pack scoring influences purchasing decisions. The top protein-source ingredients identified across all Blue Ocean products are Milk, Soy, and Whey, providing clear formulation precedent. Consequently, the recommended strategy is to launch a high-protein, low-sugar sweet snack that competes on both superior macronutrients and a clean NutriScore label.
## B. Project Links
* **Notebook:** The full analysis code, PDF, and HTML reports can be found in the [Google Colab](https://colab.research.google.com/drive/1JNyB5uQTvgXfOr8pP0UaUA3NEi2Q5pfo?usp=sharing).
* **Dashboard:** [Interactive Streamlit Dashboard](https://sugartrap-analysis-icgmjhqjqyimkaqxrhkrie.streamlit.app/)
* **Presentation:** [Link to Slides (PDF/PPT)](https://drive.google.com/file/d/1p7QEoHxJN_CFfurw8OvIrIEPSJR9rpTD/view?usp=sharing)

## C. Technical Explanation

### Data Cleaning Strategy
The cleaning process followed three main steps to produce a reliable dataset for analysis.
Step 1 – Dropping Missing Values: Rows were removed where product_name, sugars_100g, or proteins_100g were null, since these fields are essential for the scatter plot analysis. This brought the dataset down to ~400,000 rows.

Step 2 – Removing Biologically Impossible Values: Any nutrient value outside the range [0, 100] per 100g of food was filtered out, since no single nutrient can physically exceed the total weight of the food. This was applied across seven nutrient columns (sugars, proteins, fat, fiber, saturated fat, salt, carbohydrates). An additional energy sanity check capped energy-kcal_100g at 900 kcal, the theoretical maximum for pure fat. Combined, these filters removed roughly 15,000+ rows.

Step 3 – Trimming Extreme Outliers: Values above the 99th percentile for both sugar and protein were removed to reduce the influence of extreme edge cases (like near-pure sugar products) on clustering and visualization, without discarding biologically valid data.
Final result: A clean dataset of ~384,000–391,000 rows (slight variation depending on pipeline order), ready for exploratory analysis. 

### Candidate's Choice: NutriScore Gap Analysis
Candidate's Choice: NutriScore Gap Analysis

I added this section as my personal differentiator because I wanted to go beyond just cleaning and visualizing data , I wanted to answer a real business question with it.

Why I chose this angle?
 NutriScore is becoming increasingly influential on EU food packaging, and I thought it was interesting to ask  which categories are dominated by poor grades (D/E)? Because those are exactly where a reformulated, healthier product would stand out most on shelf. That felt like a genuinely useful insight, not just an analysis for its own sake.

What I actually did?

I started by building a category mapping function that reads the raw categories_tags field and assigns each product a clean, readable label like Beverages, Snacks, or Meats. Anything that didn't match a keyword got grouped as "Other."

Then I converted the NutriScore letters to numbers (A=1 through E=5) so I could calculate an average score per category and rank them. This told me which categories were nutritionally weakest overall.

Finally, I visualized the full grade distribution per category as a stacked horizontal bar chart, color-coded green to red. I chose this chart type specifically because it shows not just the average but the spread, you can see at a glance whether a category is consistently bad or just has a skewed tail.

What I was trying to show:?
 I wanted my project to go beyond description and make a strategic point — if you're a food manufacturer, here's where your healthier product has the biggest gap to exploit. That was the thinking behind adding it, and it's the part of the project I'm most proud of.


## 🛑 CRITICAL: Pre-Submission Checklist

**Before you submit your form, you MUST complete this checklist.**

> ⚠️ **WARNING:** If you miss any of these items, your submission will be flagged as "Incomplete" and you will **NOT** be invited to an interview. 
>
> **We do not accept "permission error" excuses. Test your links in Incognito Mode.**

### 1. Repository & Code Checks
- [x] **My GitHub Repo is Public.** (Open the link in a Private/Incognito window to verify).
- [x] **I have uploaded the `.ipynb` notebook file.**
- [x] **I have ALSO uploaded an HTML or PDF export** of the notebook.
- [x] **I have NOT uploaded the massive raw dataset.** (Use `.gitignore` or just don't commit the CSV).
- [x] **My code uses Relative Paths.** 

### 2. Deliverable Checks
- [x] **My Dashboard link is publicly accessible.** (No login required).
- [x] **My Presentation link is publicly accessible.** (Permissions set to "Anyone with the link can view").
- [x] **I have updated this `README.md` file** with my Executive Summary and technical notes.

### 3. Completeness
- [x] I have completed **User Stories 1-4**.
- [x] I have completed the **"Candidate's Choice"** challenge and explained it in the README.

**✅ Only when you have checked every box above, proceed to the submission form.**

---
