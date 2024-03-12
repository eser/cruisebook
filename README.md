# CruiseBook

CruiseBook is an innovative documentation system, which is designed for software development teams to record the challenges they face, decisions they make, and experiences they gain throughout their projects. Inspired by the "captain’s log" concept from Star Trek, CruiseBook allows team members to systematically document the knowledge and insights gained while working on a project. This not only facilitates the management of the current project but also creates a valuable knowledge base for future projects.

### Why do you need CruiseBook?

- **Creates a Great Prompt/Data Source for LLM-supported AI Workings with Codebases:**  
  This enables the AI to become more familiar with your codebase, offering insights and suggestions closely aligned with your project's context and history.

- **Flexible Categorization:**  
  CruiseBook entries can encompass a wide range of information, from general principles to specific module updates and business analysis outcomes.

- **Easy Access:**
  Documentation created in Markdown format allows for quick and easy access to information.

- **Knowledge Sharing:**
  Accelerates the onboarding process for new team members and encourages knowledge sharing among current members.

- **Evaluation Over Time:**
  Offers the opportunity to evaluate the development of the project and decision-making processes over time.

Certainly, here's how the description of CruiseBook, including its features and how to get started, would be articulated in English with the added highlight about its utility for AI and LLM:

### How to Create a CruiseBook:

1. **Create a CruiseBook Folder:** Create a `cruisebook/` folder within your project directory. This folder will house all your CruiseBook entries.
2. **Use the Template:** Base your entries on the suggested template above. Each entry should have a unique ID and clearly indicate which aspects of the project it pertains to.
3. **Write in Markdown Format:** Write your entries in Markdown format. This enhances readability and gives you more control over the content.
4. **Add Tags and Categories:** Use tags and categories to easily classify and find your entries.
5. **Maintain a Changelog:** Record changes made to your entries. This is valuable for understanding how the project evolved and how decisions were made.
6. **Encourage Team Members:** Encourage all team members to add to CruiseBook, documenting the challenges they encounter, solutions they devise, and insights they gain.

### Sample CruiseBook Entries

#### 1. Choosing Biome over Prettier and ESLint --fix for Code Formatting and Linting

```markdown
---
title: Choosing Biome over Prettier and ESLint --fix for Code Formatting and Linting

id: CB-G-20240312001
project: SuperApp
scope: This repository, All projects
type: Decision Record

tags: biome, prettier, eslint, code formatting, linting
authors: Jane Doe, John Smith
---

After an extensive review and comparison between Prettier, ESLint --fix, and Biome for our code formatting and linting needs within the SuperApp codebase, we have decided to proceed with Biome. Our decision was influenced by several factors:

    - **Consistency and Flexibility**: Biome offers a more adaptable configuration setup compared to Prettier and ESLint, allowing us to fine-tune our coding standards and styles more precisely.
    
    - **Integration and Performance**: In our testing, Biome showed better integration capabilities with our existing development tools and workflows. It also performed more efficiently in handling large codebases without significant impact on build times.
    
    - **Enhanced Code Quality**: Biome's advanced analysis features not only cover formatting issues but also detect potential code quality and performance issues, which are not as comprehensively covered by Prettier and ESLint.

    This decision aims to enhance the readability and maintainability of our codebase, ensuring that all team members can contribute to a consistently styled and high-quality codebase.

**Related Documents/References**:
    - Comparison Study Document: [Link to internal doc]
    - Biome Configuration Guide: [Link to internal guide]
```

#### 2. Query Failures Due to UTC Timezone Assumptions

```markdown
---
title: Query Failures Due to UTC Timezone Assumptions

id: CB-G-20240312002
project: GlobalTimeApp
scope: Entire Project
type: Incident Report

tags: utc, timezone, datetime offset, post-mortem, incident
authors: John Doe
---

During a routine feature deployment on our GlobalTimeApp project, we encountered significant issues with one of our core data retrieval queries. This problem led to inaccurate data being displayed to users in different timezones, directly impacting user experience on a global scale. The root cause was identified as the system's exclusive reliance on UTC for datetime storage, without considering the local datetime offset.

**Incident Summary**:

    - **Incident Discovery**: The issue was first noticed when users from Australia reported receiving data meant for users in the United States, resulting in a mix-up of information across time zones.
    
    - **Impact Analysis**: A preliminary investigation revealed that the query responsible for fetching user-specific data did not account for the user's timezone, leading to data inconsistency and confusion among our global user base.
    
    - **Root Cause**: The core issue was traced back to our database's datetime storage practices. By storing all datetime values in UTC without the accompanying datetime offset, the system lost context about the original time zone of the data.
    
    - **Resolution and Recovery**: The immediate fix involved updating the affected query to factor in the user's timezone, converting UTC times to the local times based on the user's settings. However, this was a temporary solution pending a more robust fix.

**Lessons Learned**:

The primary lesson from this incident is the critical importance of storing not just the UTC datetime values but also the datetime offset with each entry. This approach ensures that the system retains full context about the data's original timezone, enabling more accurate data retrieval and manipulation according to the user's local timezone. Additionally, this incident highlighted the need for comprehensive testing across different time zones, especially for features that impact global users.

**Action Items**:

1. **Database Schema Update**: Update all datetime storage to include datetime offset information alongside the existing UTC datetime values.
2. **Query Optimization**: Revise all data retrieval queries to utilize the datetime offset for timezone-aware data processing.
3. **Testing Protocol Enhancement**: Implement a testing protocol that includes scenarios across multiple timezones to prevent similar issues.

**Related Documents/References**:
    - Timezone Handling Best Practices: [Link to internal doc]
    - Database Schema Update Guide: [Link to internal guide]
```

### CruiseBook Specification

Each CruiseBook entry should follow a standardized format to ensure consistency and ease of navigation. The format is as follows:

```markdown
---
title: [Title of the Entry]

id: [Unique Identifier]
project: [Project Name]
scope: [Scope of the Entry]
type: [Type of the Entry]

tags: [tag1], [tag2], [tag3]
authors: [Author Name]
---

[Detailed Description of the Entry]

**CruiseBook Content**

**Action Items**:
(optional for some entry types)

1. [Action1]
2. [Action2]

**Related Documents/References**:
    - [Document/Link1]
    - [Document/Link2]

**[Additional Sections as Needed]**
```
