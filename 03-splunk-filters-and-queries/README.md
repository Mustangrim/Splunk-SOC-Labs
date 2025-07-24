# Splunk Filters and Queries Lab 03: Advanced Search and Time-based Analysis

## Lab Overview

**Lab Focus:** Advanced time-based filtering, field-based queries, and structured data analysis for SOC operations  
**Difficulty:** Intermediate    
**Author:** Mykyta Palamarchuk  
**Role:** SOC Analyst | SIEM Operations & Threat Detection  
**Certification:** CompTIA Security+ (SY0-701)

### Environment Specifications
- **Platform:** Splunk Enterprise/Cloud web interface
- **Administrative Privileges:** Standard user access for search operations
- **Business Context:** Enterprise SOC environment at Buttercup Games
- **Technology Focus:** Time filtering, field-based searches, structured data analysis

---

## Learning Objectives

Upon completion of this lab, participants will demonstrate:

1. **Timeline filtering proficiency** using interactive timeline selection and date range controls
2. **Precision time analysis** with date and time range specifications for incident investigation
3. **Field-based query mastery** leveraging structured data fields for targeted searches
4. **Advanced field discovery** using All Fields interface for comprehensive data exploration
5. **Temporal correlation skills** analyzing security events across specific time periods
6. **Structured data manipulation** optimizing queries using field metadata and relationships

---

## Business Scenario

You are a systems and security operations analyst at Buttercup Games conducting advanced log analysis and temporal security investigations. Your objective is to master Splunk's time-based filtering and field-based query capabilities for precise incident investigation, threat timeline analysis, and structured data examination.

---

## Lab Exercises

### Exercise 1: Timeline-based Event Filtering

#### Task 1.1: Interactive Timeline Navigation

**Objective:** Master timeline interface for temporal event analysis.

**Timeline Interaction Techniques:**
- Mouse hover for event count visualization
- Click selection for single-day filtering
- Drag selection for multi-day analysis windows

![Timeline Hover Visualization](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/timeline-hover-visualization.png)

![Timeline Selection Interface](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/timeline-selection-interface.png)

#### Task 1.2: Failed Authentication Timeline Analysis

**Objective:** Analyze failed authentication patterns using timeline filtering.

**Procedure:**
1. Set time picker to **All time**
2. Execute search: `"failed password for root"`
3. Use timeline to analyze 4-day period starting May 6, 2020
4. Identify IP address from last event of May 2, 2020

![Failed Password Timeline Analysis](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/failed-password-timeline-analysis.png)

![May 2 Last Event IP](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/may-2-last-event-ip.png)

**Analysis Results:**
1. **Events "failed password for root" (4 days from May 6, 2020):** 1005
2. **IP address from last event May 2, 2020:** 12.130.60.5

---

### Exercise 2: Date Range Filtering

#### Task 2.1: Date Range Picker Configuration

**Objective:** Configure precise date range filters for security investigations.

![Date Range Picker Interface](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/date-range-picker-interface.png)

#### Task 2.2: User-specific Authentication Analysis

**Objective:** Analyze failed authentication attempts for specific user accounts.

**Procedure:**
1. Execute search: `failed tomcat`
2. Configure date range: Before May 15, 2020
3. Count failed login attempts

![Failed Tomcat Search Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/failed-tomcat-search-results.png)

#### Task 2.3: SSH Session Analysis

**Objective:** Analyze SSH session establishment patterns.

**Procedure:**
1. Execute search: `"sshd session opened"`
2. Configure date range: May 17, 2020 to May 23, 2020
3. Count session establishment events

![SSHD Session Search Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/sshd-session-search-results.png)

---

### Exercise 3: Precise Date and Time Range Analysis

#### Task 3.1: Date and Time Range Picker

**Objective:** Execute precise temporal filtering using date and time specifications.

![Date Time Range Picker](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/date-time-range-picker.png)

#### Task 3.2: Bot Activity Analysis

**Objective:** Analyze automated bot activity patterns using precise time filtering.

**Procedure:**
1. Execute search: `googlebot`
2. Configure time range: May 1, 2020 17:00 to May 4, 2020 08:00
3. Analyze bot version and activity patterns

![Googlebot Search Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/googlebot-search-results.png)

![Googlebot Version Analysis](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/googlebot-version-analysis.png)

**Analysis Results:**
1. **Googlebot events (May 1 17:00 to May 4 08:00):** 363
2. **Googlebot version:** 2.1

#### Task 3.3: Application Resource Loading Analysis

**Objective:** Analyze specific application resource loading patterns.

**Procedure:**
1. Execute search: `category.screen`
2. Configure time range: April 29, 2020 14:00 to 14:30
3. Count resource loading events

![Category Screen Search Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/category-screen-search-results.png)

**Analysis Results:**
- **Category.screen loads (April 29, 14:00-14:30):** 26

---

### Exercise 4: Field-based Query Operations

#### Task 4.1: Sourcetype-based Data Analysis

**Objective:** Execute field-based queries using structured data fields.

**Procedure:**
1. Execute search: `sourcetype=access_combined_wcookie`
2. Analyze structured web access data

![Sourcetype Access Combined Search](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/sourcetype-access-combined-search.png)

**Common Splunk Fields:**
- **timestamp:** Event date/time
- **host:** Event origin system
- **source:** Splunk input location
- **sourcetype:** Metadata parsing configuration
- **index:** Event storage location

#### Task 4.2: Field-based Event Counting

**Objective:** Execute precise field-based queries for event quantification.

![Sourcetype Event Count Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/sourcetype-event-count-results.png)

#### Task 4.3: Action-based Transaction Analysis

**Objective:** Analyze specific transaction types using action field filtering.

**Procedure:**
1. Execute search: `sourcetype=access_combined_wcookie action=purchase`
2. Count purchase transaction events

![Action Purchase Search Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/action-purchase-search-results.png)

#### Task 4.4: Referrer Domain Analysis

**Objective:** Analyze traffic sources using referrer domain field filtering.

**Procedure:**
1. Execute search: `sourcetype=access_combined_wcookie action=purchase referer_domain="http://www.google.com"`
2. Set time range: Since May 18, 2020
3. Count Google-referred purchase events

![Referer Domain Google Search](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/referer-domain-google-search.png)

---

### Exercise 5: Advanced Field Discovery and Analysis

#### Task 5.1: All Fields Interface Navigation

**Objective:** Master comprehensive field discovery using All Fields interface.

![All Fields Dialog Interface](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/all-fields-dialog-interface.png)

![Expanded Field Values View](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/expanded-field-values-view.png)

#### Task 5.2: Cart Action Field Analysis

**Objective:** Analyze shopping cart actions using comprehensive field examination.

**Procedure:**
1. Set time picker to **All time**
2. Execute search: `sourcetype=access_combined_wcookie action=addtocart`
3. Open All Fields dialog for comprehensive field analysis

![All Fields Interface Analysis](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/all-fields-interface-analysis.png)

#### Task 5.3: File Field Value Analysis

**Objective:** Examine file field diversity and distribution.

![File Field Values Count](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/file-field-values-count.png)

**Analysis Results:**
- **File field value count:** 11

#### Task 5.4: Product ID Coverage Analysis

**Objective:** Analyze product identification field coverage across events.

![Product ID Coverage Percentage](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/product-id-coverage-percentage.png)

**Analysis Results:**
- **ProductId event coverage percentage:** 95.68

#### Task 5.5: User Agent Analysis

**Objective:** Identify most common user agent patterns.

![User Agent Common Value](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/user-agent-common-value.png)

**Analysis Results:**
- **Most common useragent value:** Mozilla/5.0

#### Task 5.6: URI Path Analysis

**Objective:** Analyze specific URI path access patterns.

![URI Path Search Analysis](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/uri-path-search-analysis.png)

**Analysis Results:**
- **Events containing uri_path /search.do:** 16

---

## Technical Assessment

### Timeline Filtering Mastery
- Interactive timeline navigation and selection
- Date range picker configuration and implementation
- Precise date and time range specification

### Field-based Query Proficiency
- Sourcetype-based data filtering
- Action field analysis for transaction monitoring
- Referrer domain investigation for traffic analysis

### Advanced Field Analysis
- All Fields interface navigation and utilization
- Field value distribution analysis
- Coverage percentage interpretation and application

### Temporal Correlation Skills
- Multi-day event pattern analysis
- Precise time window investigation
- Cross-temporal event correlation

---

## SOC Applications

### Operational Use Cases
- **Incident Timeline Reconstruction:** Precise temporal event correlation
- **Authentication Failure Analysis:** User-specific and time-bound investigation
- **Bot Activity Monitoring:** Automated traffic pattern identification
- **Application Performance Analysis:** Resource loading and transaction monitoring

### Security Metrics
- Failed authentication frequency by user and timeframe
- Bot activity patterns and version identification
- Transaction volume analysis by referrer source
- Application resource utilization patterns

---

## Lab Completion

**Skills Validated:**
- Timeline-based event filtering and analysis
- Date and time range precision configuration
- Field-based query construction and execution
- Advanced field discovery and examination
- Temporal event correlation and investigation

**Technical Competencies:**
- Advanced temporal filtering techniques
- Structured data field manipulation
- Comprehensive field analysis capabilities
- Security event timeline reconstruction

---

*Lab establishes advanced Splunk filtering and query skills essential for precise incident investigation, temporal security analysis, and structured data examination in enterprise SOC environments.*
