# EdTech Platform Data Analysis Dashboard

An end-to-end Business Intelligence project that transforms raw, un-curated educational dataset profiles from major e-learning sites into actionable corporate strategies for a rising EdTech startup. The framework utilizes **Power BI**, **Power Query**, **M Language Scripting**, and **Advanced DAX** modeling to evaluate content monetization strategies, instructor performances, and user engagement metrics.

---

## 📊 Executive Project Architecture

The core objective of this deployment is to engineer an enterprise-ready dashboard that maps educational content traits directly to market performance metrics (such as viewership and popularity). The final output provides executives with macro-level market metrics while supporting deep categorical filtering.

### Key Analytical Pillars
* **Course Formats vs. Category Demand:** Mapping cross-industry distribution profiles of Specializations, Professional Certificates, Projects, and standalone Courses.
* **Viewership Dynamic Hierarchies:** Deep structural drill-downs evaluating language popularity across granular sub-categories.
* **Skill Demand Profiling:** Visual indexing of trending technological skills globally using custom layout visualizations.
* **Subtitled Content Monetization:** Isolating structural correlations between subtitle localization variety and total audience engagement.
* **Unified Duration Standards:** Normalizing varying course duration logs (minutes, hours, months, flexible schedules) to map structural curves between course length and audience retention.

---
VISIT -- https://app.powerbi.com/reportEmbed?reportId=e5d7a1fd-783a-49b8-bd77-a55d8c2b07e3&autoAuth=true&ctid=d3de91d7-5bb6-4ce1-a775-489e8e7143a8
## 🛠️ Data Pipeline & Transformation Specs (ETL)

The raw dataset spans **45 structural columns** comprising highly heterogeneous metadata. The following programmatic steps were completed inside the **Power Query Editor** to convert the unpolished schema into a clean data store:

```powerquery
/* Example conceptual pipeline snippet for custom feature parsing */
let
    Source = Table.SelectColumns(RawData, {"CourseID", "Category", "SubCategory", "Instructors", "Rating", "Duration"}),
    RemoveNulls = Table.SelectRows(Source, each ([Category] <> null)),
    ExtractRating = Table.TransformColumns(RemoveNulls, {{"Rating", each Text.BeforeDelimiter(_, " Stars"), type text}}),
    CastToDecimal = Table.TransformColumnTypes(ExtractRating, {{"Rating", type number}})
in
    CastToDecimal
