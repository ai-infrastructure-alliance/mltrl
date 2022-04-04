# MLTRL Ethics Checklist

We include an example ethics playbook for use in MLTRL. There are three sections to use as described in the MLTRL journal paper:
1. Pre-dev, per project
2. Post-dev, per project
3. Guiding questions, for teams and the org

This example comes from a 200-person enterprise machine learning startup with clients in healthcare, retail, and automotive industries in US and Europe. Each item was drafted by the company's Ethics Council, revised following feedback from all teams, and approved by the executive team and board.

---

**Purpose:**
We seek to create an objective process that allows us to analyze AI use cases in order to create trusted products and solutions for the ongoing benefit of humanity. These guidelines and questions help us navigate various ethical considerations/gray areas, allowing us to decide, at an appropriate point in the product and sales cycle, or whether to pursue (or not pursue) projects and answer critical questions about how to execute projects responsibly.


## Pre-Development Ethics Evaluation/Checklist

*Purpose: The project owner (and working group) will complete this template of questions for any new project. These questions help navigate the ethical considerations / gray areas, and they should result in buy-in (or not) to pursue said project.*

### Data ownership and rights

1. How do we use or reuse data that is given to us by clients?
2. How do we store data? What about PII?
3. What information do we need to give clients about where data is housed, transferred to, etc.?

### Data collection and storage

1. How do we verify security throughout data collection, transferal,  processing, and storage?
2. How do we ensure that the clients' usage aligns with PII protection and policy?
3. If relevant, precisely how are we de-identifying / anonymizing data?

### Legal

1. How do we ensure that we are legally compliant, specifically pertaining to PII protection and other client proprietary data security?
2. How do we ensure that individuals (especially protected classes) aren’t being harmed or affected by unfair biases?

### Privacy etc.

1. How do we seek informed, affirmative consent from individuals?
2. How do we provide users with clear and accessible opt-out options?
3. How do we notify individuals about access to their personal data?
4. How do we notify individuals about potential changes to policy?
5. How do we inform individuals of how their data is being used and/or shared?

### Second-order effects, and third-party users

1. What information do we need to give end-users about how data is collected, stored, transferred, etc?
2. How do we guarantee intended use of tech and data?
3. How do we maintain the intended use of tech and data down the road?

### Miscellaneous

1. How can we accurately and precisely communicate the results of our algorithms?
2. How do we ensure we won't mislead (all stakeholders)?
3. What are potential ways users can be harmed? How do we mitigate and monitor these risks?

(For *personally identifiable information (PII)*, we adopt the definition provided by the U.S. General Services Administration and the definition of *personally identifiable data (PID)* provided by GDPR compliance.)



## Post-Development Ethics Evaluation/Checklist

*One paragraph of explanation is expected for each question.*

1. Have we ensured that our technologies are legally compliant?
2. Have we listed how this technology can be attacked or abused?
3. Have we tested our training data to ensure it is fair and representative?
4. Have we studied and understood possible sources of bias in our data?
5. Does our team reflect diversity of opinions, backgrounds, and kinds of thought?
6. What kind of user consent do we need to collect and to store the data?
7. Do we have a mechanism for gathering consent from users?
8. Have we explained clearly what users are consenting to?
9. Do we have a mechanism for redress if people are harmed by the results?
10. Can we shut down this software in production?
11. Have we tested for fairness with respect to different user groups?
12. Have we tested for disparate error rates among different user groups?
13. Do we test and monitor for model drift to ensure our software remains fair over time?
14. Do we have a plan to protect and secure user data?
15. How do we communicate issues / policy changes / updates to users?



## High-level questions

*These questions and responses have been drafted by the company's Ethics Council, revised following feedback from all teams, and approved by the executive team and board.*

1. What is our stance on gathering and storing personally identifiable information (PII)?
    - We adhere to all relevant local, state, federal, international, etc. laws and regulations in the jurisdictions where we operate.
    - We strive to preserve individuals’ power by giving notice and seeking consent.
    - When interacting with users (through an Augustus app, website, etc.) we offer explicit opt-in / opt-out for data sharing; opt-out is the default selection, and we do not bias selections one way or another (e.g. unlike Facebook privacy settings).
    - Gathering vs storing vs using data:
        - We’ll gather and securely store data. We do not hand personally identifiable information over to business clients or third parties. (Exception to data collection and storage policy below.)

2. What is our stance on tracking individuals?
    - We may monitor individuals in specific locations but only track across locations, businesses, etc. as outlined below.
    - Tracking by biometrics?
        - We may gather and securely store data, but we do not hand personally identifiable information over to business clients and third parties.
    - Wi-fi tracking?
        - We only track individuals with full, informed consent.

3. Are we comfortable collecting non-PII data and handing it over to clients without knowing what it will be used for or who it will be sent to?
    - If we are utilizing the client hardware and software to gather this data, then they own the data, unless otherwise contractually specified.
    - If we are utilizing our own hardware and software to gather this data, then we use the data and allow our clients to have access to this data through secure and limited means.
    - We explicitly state in contractual agreements that gathered and generated datasets shall not be used to derive PII, by the client or by downstream users.

4. Do we have mechanisms in place to ensure that data is only used for the intended purpose?
    - We explicitly state in contractual agreements that gathered and generated datasets shall not be used to derive PII, by the client or by downstream users.
    - Deployed systems will include data monitoring mechanisms for this purpose, when appropriate/possible.

5. What use cases will we avoid pursuing?
    - That enable, promote, or advance illegal activity
    - That cause physical harm
    - That encourage harmful and abusive biases

6. What governments or regimes are we unwilling to work with?
    - Those that violate internationally recognized standards regarding human rights.
    - Those on the [UN Sanctions List](https://www.un.org/securitycouncil/content/un-sc-consolidated-list)
