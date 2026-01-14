# 📉 Project: Google Analytics Audience Segmentation

![Platform](https://img.shields.io/badge/Platform-Google%20Analytics-orange)
![Skill](https://img.shields.io/badge/Skill-Audience%20Segmentation-blue)
![Type](https://img.shields.io/badge/Type-Practical%20Implementation-green)

## 📋 Project Description
This project focuses on the practical application of audience segmentation within the Google Analytics ecosystem. Moving beyond aggregate data, this workflow demonstrates how to isolate specific user subsets to uncover actionable behavioral insights.

The project was executed in a simulated virtual workspace with pre-installed analytical tools, ensuring a hands-on approach to data manipulation.

## 🛠️ Execution Roadmap: Tasks & Methodology

The following tasks were completed to master the segmentation engine:

### **Task 1: Define Segments**
* **Objective:** Established the foundational understanding of what a segment is within the analytics context.
* **Action:** Reviewed real-world examples of segments (Demographic vs. Behavioral) and mapped out strategies for how these segments can be leveraged for business optimization and ROI analysis.
* **Outcome:** Classification of different segment types relevant to business KPIs.

### **Task 2: Use System Segments**
* **Objective:** Leverage pre-built capabilities of Google Analytics.
* **Action:** Explored and applied "System Segments" (default segments provided by Google) to filter traffic data without manual configuration.
* **Outcome:** Ability to instantly analyze standard cohorts like "Mobile Traffic," "Organic Search," and "Returning Users."

### **Task 3: Create and Use Custom Segments**
* **Objective:** Go beyond default limitations.
* **Action:** Constructed "Custom Segments" tailored to specific business logic.
* **Outcome:** Demonstrated how to apply these custom filters to standard reports to isolate niche audience behaviors.

### **Task 4: Create Conditions for Custom Segments**
* **Objective:** Implement logic-based filtering.
* **Action:** Defined specific conditions (e.g., *Users who viewed > 3 pages AND are from London*).
* **Outcome:** Mastery of conditional logic (AND/OR operators) in audience filtering.

### **Task 5: Create Sequences for Custom Segments**
* **Objective:** Analyze user journey and behavior flow.
* **Action:** Built sequential segments to track users who followed a specific path (e.g., *Step 1: Viewed Product -> Step 2: Added to Cart*).
* **Outcome:** Understanding of sequential behavior, which is crucial for funnel analysis and conversion rate optimization (CRO).

### **Task 6: Import Custom Segments**
* **Objective:** Leverage community knowledge.
* **Action:** Learned the workflow to import advanced segment configurations from the **Google Solutions Gallery**.
* **Outcome:** Ability to integrate industry-standard segment templates into the workspace.

### **Task 7: Manage Segments**
* **Objective:** Governance and sharing.
* **Action:** performed administrative tasks including editing, copying, deleting, and sharing custom segments across teams.
* **Outcome:** Full lifecycle management of analytics assets.

---

## 💡 Data Science Context
*Why is this relevant to the repository?*
The "Sequences" (Task 5) and "Conditions" (Task 4) created here serve as the **logic layer** for the Machine Learning models in this repo. For instance, the sequential rules defined in GA can be validated using the **Markov Chain Attribution Model** found in Module 03.




# 📈 Analysis Log & Visual Walkthrough

This document serves as the **analytical appendix** to the main project. It documents the step-by-step application of segmentation techniques on the *Google Merchandise Store* dataset, highlighting key visual insights and data interpretations.

---

## Task 1: Defining the Strategy
*Before diving into the tools, we established the segmentation hierarchy.*

### Analytical Approach
We classified potential segments into three categories based on business value:
1.  **Macro-Segments:** Mobile vs. Desktop (Device Category).
2.  **Micro-Segments:** Users from California who viewed > 3 pages (Geo + Behavior).
3.  **Outcome-Segments:** Users who added to cart but didn't purchase (Cart Abandoners).

> **Key Insight:** Defining the "Who" before the "How" prevents analysis paralysis.

### Google Analytics Segmentation Theory

This document outlines the core architectural concepts of Audience Segmentation as defined in the Google Analytics framework.

### 1. The Three Levels of Segmentation
Data in Google Analytics is structured in a hierarchy. Understanding the scope (Level) is critical for accurate analysis.

| Scope Level | Definition | Context |
| :--- | :--- | :--- |
| **User** | People visiting your site. | Top level. Covers all visits by a single person over time. |
| **Session** | User behavior during a single session. | Middle level. Covers interactions within one specific visit. |
| **Hit** | Site interactions during a session. | Lowest level. Single actions like a page view or a click. |

---

### 2. Capabilities & Limitations
Segments are powerful, non-destructive filters that allow for retrospective analysis.

###  Key Features
* **Non-Destructive:** Segments **do not alter** the underlying data (unlike filters).
* **Retroactive:** Can be applied to **historic data** (past dates).
* **Universal:** Applied to almost any report in Google Analytics.
* **Comparative:** You can compare multiple segments (up to 4) in a single report.
* **Collaborative:** Segments can be shared with other users.

### Technical Limitations
* **Max Comparison:** Only up to **4 segments** can be applied to a report simultaneously.
* **Time Frame:** User-based segments are limited to a **90-day** date range.

---

### 3. Common Segmentation Examples
Segments allow us to isolate specific subsets of traffic based on behavior, geography, or acquisition.

* **Geography:** Users from a specific country, region, or state.
* **Conversion:** Users who complete a purchase.
* **Cart Abandonment:** Users who add a product to the cart but do **not** make a purchase.
* **Content Consumption:** Sessions that include a view of a specific type of page.
* **Acquisition:** Sessions from a specific type of traffic source (e.g., Organic vs. Paid).

---

### 4. Case Study: User Scope vs. Session Scope
*How scope selection affects data accuracy (The $200 Logic).*

**Scenario:** We want to segment users who spent **$200 or more**.

* **User A:** Spends **$25** in Session 1 and **$180** in Session 2. (Total: $205).
* **User B:** Spends **$200** in just one session.

**The Result:**
1.  **If using a USER Segment:** Includes **both** User A and User B (Because A's *total* lifetime value > $200).
2.  **If using a SESSION Segment:** Includes **only** User B (Because only User B hit the target within a single visit).







---

## 🔵 Task 2: System Segments Application
*Using Google's pre-built models to analyze standard cohorts.*

![System Segments Visualization](PLACEHOLDER_FOR_SCREENSHOT_TASK2.png)
*(Insert a screenshot showing a comparison, e.g., "All Users" vs. "Mobile Traffic")*

### 🧐 Observation
By applying the **"Mobile Traffic"** system segment against **"All Users"**:
* **Metric Observed:** Bounce Rate / Conversion Rate.
* **Finding:** Mobile users showed a higher bounce rate compared to the site average, suggesting potential UX optimization needs on the mobile interface.

---

## 🟣 Task 3: Custom Segment Construction
*Creating a niche segment to isolate high-engagement users.*

![Custom Segment Builder](PLACEHOLDER_FOR_SCREENSHOT_TASK3.png)
*(Insert screenshot of the Segment Builder interface)*

### 🛠️ Configuration Details
* **Segment Name:** *Engaged Desktop Users*
* **Criteria:** `Device Category = Desktop` AND `Session Duration > 3 minutes`.

### 📉 Impact on Data
Isolating this group revealed that while they make up a smaller percentage of traffic, they account for a disproportionately high share of revenue.

---

## 🟠 Task 4: Conditional Logic (Boolean Filtering)
*Applying complex AND/OR logic to refine targeting.*

![Conditions Tab](PLACEHOLDER_FOR_SCREENSHOT_TASK4.png)
*(Insert screenshot of the 'Conditions' tab in Segment Builder)*

### 🧠 Logic Structure
We utilized the **Conditions** tab to filter users who meet specific multi-dimensional criteria:
* `Pageviews > 3`
* **AND**
* `Location = London`

> **Data Science Note:** This corresponds to Boolean masking in Python (e.g., `df[(df['views'] > 3) & (df['city'] == 'London')]`).

---

## 🔴 Task 5: Sequential Segmentation (Funnel Analysis)
*Tracking user journeys across time.*

![Sequence Segment](PLACEHOLDER_FOR_SCREENSHOT_TASK5.png)
*(Insert screenshot of the 'Sequences' setup showing Step 1 -> Step 2)*

### 🔄 The Journey
We defined a sequence to identify **Cart Abandoners**:
1.  **Step 1:** Viewed Product Page.
2.  **Step 2:** Added to Cart.
3.  **Step 3:** (Exclude) Transaction.

### 💡 Strategic Insight
This segment represents the "Low Hanging Fruit" for retargeting campaigns. These users have high intent but encountered friction at checkout.

---

## 🟤 Task 6 & 7: Import & Management
*Governance and scalability of analytics assets.*

![Segment List Management](PLACEHOLDER_FOR_SCREENSHOT_TASK7.png)
*(Insert screenshot of the segment list showing Shared/Imported segments)*

### 📂 Asset Management
* **Importing:** Leveraged the *Google Solutions Gallery* to adopt industry-standard e-commerce segments.
* **Governance:** Cleaned up duplicate segments and shared the finalized "High-Value" definitions with the team to ensure data consistency across reports.

---

### 🏁 Final Conclusion
Through this project, we transitioned from aggregate data viewing to granular audience analysis. The use of **Sequential Segments** provided the most actionable insight for immediate ROI improvement (Retargeting).
