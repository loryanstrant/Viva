---
title: Hybrid Workforce Experience Power BI report
description: Learn how to use the Microsoft Viva Insights Power BI template to know about your organization's hybrid workforce experience
author: lilyolason
ms.author: v-lilyolason
ms.topic: article
ms.localizationpriority: medium 
ms.collection: viva-insights-advanced 
ms.service: viva 
ms.subservice: viva-insights 
search.appverid: 
- MET150 
manager: anirudhbajaj
audience: Admin
---

# Hybrid workforce experience report 

As leaders figure out their organization’s new working models, the Hybrid workforce experience Power BI report helps organizations understand how hybrid work affects employees in various work modes differently. The report identifies opportunities to improve the experience of employees working in the following ways:

* Mostly onsite
* Mostly remote
* Onsite some days of the week and remote on others (hybrid)

The report has six sections, which each address different facets of the employee experience that hybrid working models may impact. Key metrics provide a deep-dive into each topic, along with a **Why it matters** interpretation and **recommended actions**.

![Screenshot that shows the Hybrid workforce experience Power BI report, Report summary.](/viva/insights/advanced/images/hwfe-ga-pbi-summary.png)

To populate the report in Power BI, you’ll need to set up and successfully run the predefined **Hybrid workforce experience** query  in Viva Insights.

## Demonstration

The following demonstration uses sample data that’s only representative of this report and might not be exactly what you see in a live report specific to your organization's unique data.

<iframe title="Hybrid workforce experience - Summary" width="600" height="373.5" src="https://msit.powerbi.com/view?r=eyJrIjoiMTI3OTdkZDQtYTllYy00MDUwLTk4NzEtYTljM2I1YjIyZjEyIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9" frameborder="0" allowFullScreen="true"></iframe>

## Prerequisites

Before you can run the queries and populate the report in Power BI, you’ll need to:

* Be assigned the role of **Insights Analyst** in Viva Insights.
* Have the June 2022 (or newer) version of Power BI Desktop installed. If you have an earlier version of Power BI installed, uninstall it before installing the new version. Then go to [Get Power BI Desktop](https://powerbi.microsoft.com/en-us/getting-started-with-power-bi/).
* Have the following attributes uploaded as part of your organizational data:
  * **OnsiteDays**, an attribute identifying the number of days someone works onsite. This could be based on behavioral data such as badge data or Wi-Fi data, or other sources such as a tag in the HR system identifying the number of days an employee intends to work onsite. You might get this data in one of two ways—through a weekly update of onsite days or by using a monthly update of onsite days to calculate the weekly number:
    * If an employee’s number of onsite days is available on a weekly basis (that is, values are between 0 and 5), make sure to include a row with an **EffectiveDate** and **OnsiteDays** value per person per week in your organizational data. You can choose the frequency with which you like to update this data—weekly or monthly.
    * If you’re using an employee’s number of onsite days per month, you can upload the monthly number of onsite days in Viva Insights on a monthly basis.

  * **SupervisorIndicator**, an attribute indicating whether someone is a manager.
  * **HireDate**, an attribute indicating the person’s hire date is required to be able to load the **New hire onboarding insights**. Without this attribute, however, the rest of the report will still load.

For more details on organizational data preparation and upload, download our [step-by-step guide](https://go.microsoft.com/fwlink/?linkid=2205161).

You can add new attributes to your organizational data at any time. For more details on how to add new data for existing employees, review the documentation on [subsequent uploads](../../admin/upload-org-data-subsequent.md).

## Report setup

### Run query

>[!Note]
> For this release of Viva Insights, this report is currently only available in English and will only work with data generated from the English version of Viva Insights.

1. In the analyst experience in Viva Insights, select **Analysis**.

2. Under **Power BI templates**, navigate to **Hybrid workforce experience** and select **Start analysis**. For more information about the Hybrid workforce experience template before running your analysis, select **Learn more**.

3. Under **Query setup**:
    1. Type a **Query name**.
    1. Select a **Time period**. **Time period** defaults to **Last 3 months**.
    1. Optional: You can set the query to automatically update by checking the **Auto-refresh** box. When you select the **Auto-refresh** option, your query automatically runs and computes a new result every time Viva Insights gets updated collaboration data for licensed people.

    >[!NOTE]
    >If the organizational data used in an auto-refreshing query changes (for example, an attribute name is altered or an attribute is removed), you might see an error when you run the query.

    4. Optional: Type a **Description**.

         Selecting **More settings** brings you to a pane, but there’s nothing you need to change there.

        In this pane:
    
        * Power BI queries are set to **Group by Week**. You can't edit this field.
        * The **Metric rules** field defaults to **Meeting exclusions rule (preferred rule)**. This field isn’t customizable in this release; for more information, refer to [Metric rules](../metric-rules.md).
![Hybrid workforce experience query setup](/viva/insights/advanced/images/hwfe-ga-pbi-setup.png)

1. Under **Predefined template metrics**, leave prepopulated metrics as they appear.  

    >[!NOTE]
    > Metrics in Power BI templates can't be edited in this release of Viva Insights. To expand the full list of metrics included in the Power BI template, select the arrow in the box beneath **Metrics, filters, and organizational attributes**.

    ![Hybrid workforce experience query predefined metrics](/viva/insights/advanced/images/hwfe-ga-pbi-predefined-metrics.png)

1. You can filter the employees in scope for the report under **Select which employees you want to include in the query**. Don’t remove the predefined “Is Active” filter. For more details about filter and metric options, see [Create a custom Person query](../person-query.md).
![Is active filter](/viva/insights/advanced/images/pbi-templates-isactive-filter.png)

1. Under **Select which employee attributes you want to include in the query**, select the **HireDate** attribute if available. Then, add other organizational attributes. You can add up to seven organizational attributes, including **HireDate**. After the query runs, you can use these attributes to group and filter the reports.

    >[!IMPORTANT]
    >Some employee attributes are required to set up this Power BI template, which are preselected for you in the query. *Do not remove any preselected attributes.*
    >
    >If you see attributes marked in red and the query’s **Run** button disabled, it means that these required attributes are missing from your organizational data. Contact your admin to upload them.

1. Select **Run** on the upper right side of the screen, which can take a few minutes to complete.

1. When your query results are ready, go to the **Query results** page and select the **Power BI** icon to download the Power BI template and copy the query identifier. You'll need the query identifier later.

1. Select **Run** on the upper right side of the screen, which can take a few minutes to complete.

### Link report to query

9. Open the downloaded Hybrid workforce experience template.

10. If prompted to select a program, select **Power BI**.

11. When prompted by Power BI:
    1. Paste in the query identifier.
    1. Set the **Minimum group size** for data aggregation within this report's visualizations in accordance with your company's policy for viewing Viva Insights data.
    1. Select **Load** to import the query results into Power BI.

12. If prompted by Power BI, sign in using your organizational account. Power BI will load and prepare the data, which can take some time to complete for large files.

>[!Important]
> You need to sign in to Power BI with the same account you use to access Viva Insights.

## Report settings

After the **Hybrid workforce experience report** is set up and populated with Viva Insights data in Power BI, map values as prompted, which are listed below:

|Attribute value| Prompt|
|---------------|-------|
|Mostly onsite  | Select the number of average % of onsite work days that best describe the work mode of employees that work mostly onsite (that is, from the company’s main worksite). |
|Hybrid | Select the average number of onsite work days that best describe the work mode of employees that work onsite some days during the week and remote on others.|
|Mostly remote| Select the  average number of onsite work days that best describe the work mode of employees that work mostly remote (that is, from home or some other location outside the company’s main worksite).|
|Individual contributors| Select the attribute values that identify employees as individual contributors who do not manage people within your organization.|
|Managers| Select the attribute values that identify managers who manage people within your organization, such as **Mgr** and **Mgr+**.|

![Hybrid workforce experience Power BI report, Report settings](/viva/insights/advanced/images/hwfe-ga-PBI-questions.png)

After this initial prompt, you can then select **Settings** at top right of any page to view and change the following parameters:

* **Select the time period for the report** – Select the time period for which you want to view data in the report.  
* **Select an attribute to group data by** – Select the primary group-by attribute shown in all the reports. You can change this attribute at any time and all report pages will show group values by the new attribute.
* **Select optional report filter** – Select the organizational attribute and values you want to filter the employees in the report.
* **Exclusions** – Use the check boxes to:
    * Exclude employees who are likely non-knowledge workers (that is, those spending less than five hours per week on average in meetings, emails, and/or Teams calls and chats).
    * Exclude weeks that are likely holiday or paid-time-off weeks, or weeks that individuals are on other types of leave.

    ![Screenshot that shows Hybrid workforce experience Power BI report, Customize work mode.](/viva/insights/advanced/images/hwfe-ga-pbi-settings.png)

## About this report

This section:

* Provides metrics specific to this report.
* Lists the six main report pages. For each report page, this section provides the business question the page seeks to answer and describes the type of insights and data the page contains.
* Describes the report’s **Track changes** page.

### Pages

#### Employee work mode

**Does the distribution of employees by work mode meet expectations and is there a potential disconnect between management and individual contributors?**

This page shows the percent of employees by work mode (that is, Mostly onsite, Hybrid, Mostly remote, or Unclassified*) according to the latest week of data, split out by group. This page also highlights a potential disconnect between the share of managers and individual contributors working Mostly onsite, Hybrid, or Mostly remote. In case the **OnsiteDays** data is updated periodically, the **Explore the trends** button allows you to review the trend of percent of employees tagged as “Mostly onsite,” “Hybrid,” “Mostly remote,” and “Unclassified.”

*If an employee is categorized as “Unclassified,” it means that there was no numerical **OnsiteDays** value found in the organizational data. The “Unclassified” employee category is not displayed in the remainder of this report.

#### Collaboration habits

**How does hybrid work impact meeting engagement and collaboration patterns throughout the week?**

This page shows the average weekly time employees in different work modes spend collaborating in meetings, emails, Teams calls, or Teams chats on different days of the week. The numbers allow you to analyze whether employees in different work modes have equitable access to collaboration opportunities and tools. This page also shows, by work mode, the average share of meeting time during which employees multitask by sending emails or Teams chats.

#### Connectivity and belonging

**How does hybrid work impact the employees’ connectivity and sense of belonging?**

This page shows the average internal employee network size, split by work mode, including a three-month time trend. This page also shows the average weekly hours employees spent collaborating in small groups (with fewer than eight people), broken out by work mode.

#### Work-life balance and flex work

**How does hybrid work impact flexible schedules and the employees’ ability to unplug?**

This page shows, by work mode, the percent of employees collaborating outside of their working hours as set in Outlook for more than five hours per week. The chart on the right takes into account both the number of distinct daily hours employees participate in meetings, emails, and Teams chats or calls, as well as the average weekly hours employees spend collaborating outside of their set working hours. By combining both metrics, the page shows the following working patterns:

* Long non-standard hours: employees with more than nine distinct active hours a day and spending more than five hours a week in collaboration outside of set working hours.
* Long hours: employees with more than nine active hours a day but fewer than five hours a week in collaboration outside of set working hours.
* Flexible hours: employees with nine or fewer active hours a day, but who spend more than five hours a week outside of typical or set working hours.
* Low-collaboration & standard hours: employees with nine or fewer active hours a day and fewer than five hours per week spent in collaboration outside of set working hours. These employees are either successfully keeping their hours in check or depend less on collaboration to get their jobs done.

#### New hire onboarding

**How fast are new hires integrating into the organization’s network and are they getting the manager support they need?**

This page shows the average weekly time new hires get with their manager, broken out by work mode. New hires are defined as employees with tenure of less than one year. The toggle key allows you to review all time spent in meetings or calls where both the employee and their manager are present. This information can help a manager:

* Provide support and mentoring.
* Focus on the time spent in 1:1s with the employee, which presents a great opportunity for new-hire coaching and providing direction.

The chart on the right shows the average internal new-hire network size in an employee’s first couple of months, broken out by work mode. This chart indicates the pace at which new hires in different work modes are building their networks and integrating in the organization.

#### Manager connection

**How does the employee and manager work mode impact the employees’ access to manager coaching?**

This page shows, by work mode, the average 1:1 time employees get with their manager. The chart on the right explores whether a manager’s work mode affects the 1:1 time employees get with their manager. If the correlation is **Large**, Mostly onsite managers might have an unconscious tendency to give preferential treatment to those employees in the immediate vicinity.
  
#### Track changes

**How are behaviors evolving for employees in different work modes?**

This page shows the trends for key leading indicator metrics that were introduced throughout the report, including metrics about collaboration habits, employee networks, work-life balance, new hire onboarding, and the manager connection.

### Other features

The report also includes the following features:

* **Break out by group** panes, which allow you to do further drill-throughs on the report pages and group data by different organizational attributes.
* **Take action** panes, which list opportunity areas and recommended actions for each section in the report.
* **Settings**, where you can:
    * Select the time period and organizational attribute by which to view the reports.
    * Select which employees to include in the reports.
    * Use exclusion options.
* **Glossary** that describes the metrics used in the different reports.

## Power BI tips, FAQs, and troubleshooting

For details about how to share the report and other Power BI tips, troubleshoot any issues, or review the FAQ, see [Power BI tips, FAQ, and troubleshooting](./power-bi-faq-troubleshoot.md).

## Related topic

[Access query results and modify existing queries](/viva/insights/advanced/analyst/query-results.md)
