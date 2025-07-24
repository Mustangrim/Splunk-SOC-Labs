# Splunk Fields and Transforms Lab 02: Data Manipulation and Analysis

## Lab Overview

**Lab Focus:** Advanced search operators, field manipulation, and data transformation techniques for SOC operations  
**Difficulty:** Intermediate    
**Author:** Mykyta Palamarchuk  
**Role:** SOC Analyst | SIEM Operations & Threat Detection  
**Certification:** CompTIA Security+ (SY0-701)

### Environment Specifications
- **Platform:** Splunk Enterprise/Cloud web interface
- **Administrative Privileges:** Standard user access for search operations
- **Business Context:** Enterprise SOC environment at Buttercup Games
- **Technology Focus:** Boolean operators, field selection, transforming commands, statistical analysis

---

## Learning Objectives

Upon completion of this lab, participants will demonstrate:

1. **Boolean search proficiency** using OR, NOT operators for complex query construction
2. **Field manipulation skills** including selection, customization, and metadata extraction
3. **Data transformation mastery** using pipeline operators and statistical commands
4. **Aggregation techniques** with top, rare, and stats functions for threat analysis
5. **Search mode understanding** differentiating between Events and Statistics views
6. **Statistical analysis capabilities** for security metrics and performance evaluation

---

## Business Scenario

You are a systems and security operations analyst at Buttercup Games tasked with advanced log analysis and security monitoring. Your objective is to master Splunk's data manipulation capabilities including boolean logic, field transformations, and statistical analysis for comprehensive threat detection and incident investigation.

---

## Lab Exercises

### Exercise 1: Boolean Search Operations

#### Task 1.1: Complex Query Construction with Boolean Operators

**Objective:** Execute advanced searches using OR and NOT operators for database activity analysis.

**Procedure:**
1. Authenticate using credentials:
   - Username: `admin`
   - Password: `rangeforce`
2. Execute search: `sourcetype=csv (update OR insert) NOT email`
3. Analyze results for database modification activities

![Boolean Search Query Interface](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/boolean-search-query-interface.png)

![Boolean Search Results Display](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/boolean-search-results-display.png)

![Search Statistics Overview](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/search-statistics-overview.png)

**Analysis Questions:**
1. **Total events returned for all time:** 6244
2. **Events matched on 2020-04-28:** 211
3. **Average query duration (1 decimal place):** 18.4

---

### Exercise 2: Field Selection and Customization

#### Task 2.1: Field Selection Interface Navigation

**Objective:** Master field selection techniques for focused data analysis.

![Fields Selection Interface](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/fields-selection-interface.png)

#### Task 2.2: Purchase Activity Analysis with Custom Fields

**Objective:** Analyze purchase transactions using field filtering and selection.

**Procedure:**
1. Set time range: Since 2020-05-24
2. Execute search: `action=purchase bytes>1500`
3. Configure selected fields: bytes, clientIP, referer_domain

![Purchase Action Search Query](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/purchase-action-search-query.png)

![Field Selection Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/field-selection-results.png)

![Selected Fields Display](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/selected-fields-display.png)

**Analysis Questions:**
1. **Total events produced by search:** [Value from results]
2. **ClientIP of most recent event:** [Value from results]
3. **Referer_domain value sample:** [Value from results]

---

### Exercise 3: Data Transformation Commands

#### Task 3.1: Top Command for Domain Analysis

**Objective:** Identify most frequent domains using top transformation command.

**Procedure:**
1. Execute search: `sourcetype="access_combined_wcookie" | top referer_domain`
2. Analyze top referrer domains for traffic pattern identification

![Top Referer Domain Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/top-referer-domain-results.png)

**Analysis Results:**
- **Most common referer_domain:** http://www.buttercupgames.com

#### Task 3.2: Category Analysis for Purchase Actions

**Objective:** Analyze purchase patterns using filtered top commands.

**Procedure:**
1. Execute search: `sourcetype="access_combined_wcookie" action=purchase | top categoryId`
2. Identify second most popular category for purchase actions

![Top Category ID Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/top-category-id-results.png)

#### Task 3.3: Multi-Field Combination Analysis

**Objective:** Analyze field combinations using top command with multiple parameters.

**Procedure:**
1. Execute search: `sourcetype="access_combined_wcookie" | top limit=20 categoryId referer_domain`
2. Identify 11th highest count combination

![Top Multiple Fields Combination](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/top-multiple-fields-combination.png)

---

### Exercise 4: Search Modes and Interface Analysis

#### Task 4.1: Search Mode Interface Understanding

**Objective:** Understand difference between Events and Statistics search modes.

![Search Modes Tabs Interface](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/search-modes-tabs-interface.png)

![Search Mode Selection Interface](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/search-mode-selection-interface.png)

**Mode Characteristics:**
- **Verbose Mode:** Both Events and Statistics tabs populated
- **Smart Mode:** Single tab based on search type
- **Fast Mode:** Optimized for dashboards and reports

---

### Exercise 5: Rare Command Analysis

#### Task 5.1: Least Common Value Identification

**Objective:** Identify least common values using rare transformation command.

**Procedure:**
1. Execute search: `sourcetype="access_combined_wcookie" | rare clientIP`
2. Identify client IP with minimum event count

![Rare Command Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/rare-command-results.png)

---

### Exercise 6: Statistical Analysis Functions

#### Task 6.1: Event Count Analysis

**Objective:** Perform statistical counting for HTTP status analysis.

**Procedure:**
1. Execute search: `sourcetype="access_combined_wcookie" status=200 | stats count`
2. Calculate total events with HTTP 200 status

![Stats Count Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/stats-count-results.png)

#### Task 6.2: Average Calculation for Remove Actions

**Objective:** Calculate statistical averages for specific action types.

**Procedure:**
1. Execute search: `sourcetype="access_combined_wcookie" status=200 action=remove | stats avg(bytes) by action`
2. Calculate average bytes for remove actions

![Stats Average Function Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/stats-average-function-results.png)

---

## Technical Assessment

### Boolean Logic Mastery
- OR operator implementation for inclusive searches
- NOT operator usage for exclusion filtering
- Complex query construction with multiple operators

### Field Manipulation Skills
- Field selection interface navigation
- Custom field configuration
- Metadata extraction and analysis

### Data Transformation Proficiency
- Pipeline operator (|) implementation
- Top command usage for frequency analysis
- Rare command implementation for outlier detection
- Stats command application for statistical analysis

### Search Mode Understanding
- Events vs Statistics tab differentiation
- Verbose, Smart, and Fast mode characteristics
- Interface optimization for different use cases

---

## SOC Applications

### Operational Use Cases
- **Database Activity Monitoring:** Boolean searches for SQL injection detection
- **Traffic Analysis:** Field selection for network forensics
- **Threat Pattern Identification:** Statistical analysis for anomaly detection
- **Performance Monitoring:** Rare command usage for outlier identification

### Security Metrics
- Failed authentication frequency analysis
- Network traffic pattern identification
- Database modification tracking
- Performance baseline establishment

---

## Lab Completion

**Skills Validated:**
- Boolean search operator implementation
- Field selection and customization
- Data transformation command execution
- Statistical analysis function usage
- Search mode interface navigation

**Technical Competencies:**
- Advanced query construction
- Data aggregation techniques
- Statistical analysis capabilities
- Interface optimization skills

---

*Lab establishes advanced Splunk data manipulation skills essential for complex security analysis, threat hunting, and incident investigation in enterprise SOC environments.*
