# Splunk Visualizations Lab 05: Dashboard Creation and Data Visualization

## Lab Overview

**Lab Focus:** Comprehensive dashboard creation, data visualization, and field extraction for SOC monitoring and threat analysis  
**Difficulty:** Advanced    
**Author:** Mykyta Palamarchuk  
**Role:** SOC Analyst | SIEM Operations & Threat Detection  
**Certification:** CompTIA Security+ (SY0-701)

### Environment Specifications
- **Platform:** Splunk Enterprise/Cloud web interface
- **Administrative Privileges:** Dashboard creation and visualization permissions
- **Business Context:** Enterprise SOC environment at Buttercup Games
- **Technology Focus:** Dashboard design, visualization creation, field extraction, threat pattern analysis

---

## Learning Objectives

Upon completion of this lab, participants will demonstrate:

1. **Dashboard architecture proficiency** creating comprehensive SOC monitoring dashboards from scratch
2. **Multi-visualization mastery** implementing pie charts, single value panels, and bar charts for threat analysis
3. **Advanced field extraction skills** using REX functions and field extraction wizards for data manipulation
4. **Threat visualization expertise** transforming security events into actionable visual intelligence
5. **SOC dashboard optimization** designing effective monitoring interfaces for continuous threat detection
6. **Interactive analysis capabilities** correlating multiple data sources through integrated dashboard panels

---

## Business Scenario

You are a systems and security operations analyst at Buttercup Games tasked with building a comprehensive SOC dashboard for your security team. Recent security incidents including SSH brute force attacks and website application errors require continuous monitoring and visualization. Your objective is to create an integrated dashboard that provides real-time threat intelligence, pattern recognition, and proactive security monitoring capabilities.

---

## Lab Exercises

### Exercise 1: SOC Dashboard Foundation

#### Task 1.1: Dashboard Infrastructure Creation

**Objective:** Establish foundational SOC dashboard infrastructure for comprehensive security monitoring.

**Dashboard Requirements:**
- Centralized security event visualization
- Multi-panel layout for diverse threat indicators
- Real-time monitoring capabilities for incident response

**Procedure:**
1. Authenticate using credentials:
   - Username: `admin`
   - Password: `rangeforce`
2. Navigate to **Search & Reporting** app
3. Access **Dashboards** tab from upper menu bar
4. Select **Create New Dashboard** button

![Dashboard Creation Interface](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/dashboard-creation-interface.png)

**Dashboard Configuration:**
- **Title:** SOC Dashboard
- **ID:** soc_dashboard (auto-generated)
- **Permission:** Private (SOC analyst specific)

**Strategic Value:** Centralized dashboard provides unified view of security posture, enabling rapid threat identification and coordinated incident response across multiple attack vectors.

---

### Exercise 2: SSH Brute Force Attack Visualization

#### Task 2.1: Authentication Failure Pattern Detection

**Objective:** Identify and analyze SSH brute force attack patterns using search analysis.

**Threat Context:** Malicious actors conducting brute force attacks against Angels & Scooters server infrastructure require immediate detection and response through visual analysis of authentication failure patterns.

**Search Implementation:**
1. Navigate to **Search** tab
2. Execute search: `sourcetype="auth" failed`
3. Analyze failed SSH login attempt patterns

![SSH Failed Login Search](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/ssh-failed-login-search.png)

#### Task 2.2: IP Address Extraction and Analysis

**Objective:** Extract attacking IP addresses using REX function for threat actor identification.

**Advanced Query Construction:**
1. Implement IP extraction: `sourcetype="auth" failed | rex "(?<ip>\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})"`
2. Apply frequency analysis: `| top ip`

![IP Extraction Rex Function](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/ip-extraction-rex-function.png)

![Top IP Results Display](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/top-ip-results-display.png)

**Threat Intelligence Analysis:**
- **Most aggressive brute force IP:** 10.55.55.55
- **Attack Pattern:** Multiple IP addresses indicate coordinated attack campaign
- **Response Priority:** Immediate blacklisting of primary attack source

#### Task 2.3: Pie Chart Visualization Creation

**Objective:** Transform SSH attack data into visual threat intelligence using pie chart representation.

**Visualization Process:**
1. From search results, access visualization options
2. Select **Save As** → **Dashboard Panel**

![Visualization Selection Interface](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/visualization-selection-interface.png)

![Column Chart Circle Selection](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/column-chart-circle-selection.png)

**Panel Configuration:**
- **Dashboard:** Existing (SOC Dashboard)
- **Panel Title:** Failed SSH logins
- **Panel Content:** Pie Chart

![Dashboard Panel Configuration](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/dashboard-panel-configuration.png)

![Pie Chart Dashboard Setup](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/pie-chart-dashboard-setup.png)

![Dashboard Save Confirmation](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/dashboard-save-confirmation.png)

**Operational Impact:** Visual representation enables rapid threat actor identification and attack volume assessment for immediate incident response coordination.

---

### Exercise 3: Website Error Monitoring Implementation

#### Task 3.1: PHP Error Detection and Analysis

**Objective:** Implement comprehensive website error monitoring for Angels & Scooters application security.

**Error Analysis Requirements:**
- Real-time PHP warning detection
- 24-hour monitoring window implementation
- Suspicious file access pattern identification

**Search Implementation:**
1. Execute search: `source="/var/log/angelsscooters/error.log"`
2. Configure time range: Last 24 hours (real-time)

![Error Log Search Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/error-log-search-results.png)

**Security Investigation Results:**
- **Suspicious file access attempt:** /root/secret.txt
- **Attack Pattern:** Unauthorized access to sensitive system files
- **Threat Assessment:** Potential privilege escalation or data exfiltration attempt

#### Task 3.2: Single Value Panel Implementation

**Objective:** Create single value monitoring panel for immediate error count visibility.

**Panel Development Process:**
1. Access search results for access log: `source="/var/log/angelsscooters/access.log"`

![Access Log Search Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/access-log-search-results.png)

2. Navigate to **Visualization** tab
3. Configure **Pivot** interface for statistical analysis

![Pivot Interface Configuration](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/pivot-interface-configuration.png)

![Single Value Panel Setup](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/single-value-panel-setup.png)

**Panel Configuration:**
- **Time Range:** Last 24 hours
- **Dashboard:** SOC Dashboard
- **Panel Title:** Recent errors
- **Panel Content:** Single value
- **Model Title:** recent errors

![Dashboard Panel Config Form](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/dashboard-panel-config-form.png)

![Single Value Dashboard Setup](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/single-value-dashboard-setup.png)

![Dashboard Save Complete](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/dashboard-save-complete.png)

**Monitoring Value:** Single value panel provides instant visibility into current error status, enabling rapid response to application security incidents.

---

### Exercise 4: User Agent Analysis and Bar Chart Creation

#### Task 4.1: Advanced Field Extraction Implementation

**Objective:** Extract user agent fields using Splunk's field extraction wizard for comprehensive traffic analysis.

**Field Extraction Requirements:**
- User agent pattern identification from access logs
- Regular expression-based field creation
- Automated field extraction wizard utilization

**Extraction Process:**
1. Execute search: `source="/var/log/angelsscooters/access.log"`

![Access Log Field Extraction](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/access-log-field-extraction.png)

2. Access **Extract New Fields** wizard from Interesting Fields panel

![Extract New Fields Wizard](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/extract-new-fields-wizard.png)

![Field Extraction Wizard Interface](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/field-extraction-wizard-interface.png)

#### Task 4.2: Field Extraction Wizard Configuration

**Objective:** Configure automated field extraction using regular expression methodology.

**Wizard Configuration Steps:**
1. Select extraction method: **Regular Expression**

![Regular Expression Method Selection](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/regular-expression-method-selection.png)

2. Highlight user agent portion of event data

![User Agent Field Highlighting](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/user-agent-field-highlighting.png)

3. Configure field parameters:
   - **Field Name:** user_agent

![Field Name Configuration](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/field-name-configuration.png)

![Field Extraction Completion](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/field-extraction-completion.png)

![Field Validation Interface](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/field-validation-interface.png)

![Field Extraction Wizard Finish](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/field-extraction-wizard-finish.png)

#### Task 4.3: User Agent Frequency Analysis

**Objective:** Analyze user agent distribution patterns for traffic analysis and potential bot detection.

**Analysis Implementation:**
1. Execute comprehensive user agent analysis: `source="/var/log/angelsscooters/access.log" | top user_agent`

![Top User Agents Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/top-user-agents-results.png)

**Traffic Analysis Results:**
- **Most popular user agent:** [Extract from search results]
- **Pattern Recognition:** Identification of legitimate browsers vs automated tools
- **Security Assessment:** Detection of potential scraping or attack tools

#### Task 4.4: Bar Chart Dashboard Integration

**Objective:** Create comprehensive bar chart visualization for user agent distribution analysis.

**Visualization Configuration:**
1. Access **Visualization** tab for chart type selection
2. Convert default pie chart to bar chart format
3. Configure dashboard integration

**Panel Configuration:**
- **Dashboard:** SOC Dashboard
- **Panel Title:** Top user agents
- **Panel Content:** Bar Chart

**Analytical Value:** Bar chart provides comparative analysis of user agent frequencies, enabling identification of suspicious automated traffic and potential security threats.

---

## Technical Assessment

### Dashboard Architecture Mastery
- Comprehensive SOC dashboard creation from foundational requirements
- Multi-panel layout design for diverse security monitoring needs
- Integration of various visualization types for complete threat visibility

### Visualization Proficiency
- Pie chart implementation for threat actor distribution analysis
- Single value panel creation for immediate status monitoring
- Bar chart development for comparative traffic analysis

### Advanced Field Manipulation
- REX function implementation for IP address extraction
- Field extraction wizard utilization for complex data parsing
- Regular expression methodology for automated field creation

### Threat Analysis Integration
- SSH brute force attack pattern visualization
- Website error monitoring and suspicious file access detection
- User agent analysis for traffic pattern recognition and bot detection

---

## SOC Applications

### Operational Use Cases
- **Continuous Threat Monitoring:** Real-time dashboard provides comprehensive security posture visibility
- **Incident Response Coordination:** Visual threat intelligence enables rapid response team coordination
- **Pattern Recognition:** Multi-visualization approach identifies attack trends and threat actor behaviors
- **Performance Monitoring:** Application error tracking ensures service availability and security

### Security Metrics Enhancement
- **Attack Source Identification:** IP-based threat actor mapping and blacklisting priorities
- **Application Security Monitoring:** Real-time error detection and suspicious file access alerting
- **Traffic Analysis:** User agent distribution monitoring for automated threat detection
- **Dashboard Efficiency:** Centralized monitoring reduces investigation time and improves response effectiveness

---

## Lab Completion

**Skills Validated:**
- Comprehensive SOC dashboard architecture and creation
- Multiple visualization type implementation and optimization
- Advanced field extraction using REX functions and extraction wizards
- Threat pattern analysis and visual intelligence development
- Security monitoring dashboard integration and management

**Technical Competencies:**
- Enterprise dashboard design for security operations
- Data visualization mastery for threat analysis
- Field manipulation and extraction automation
- Multi-source data correlation and presentation
- SOC workflow optimization through visual intelligence

---

## Course Completion Certificate

**Congratulations!** 🎉

You have successfully completed the **Splunk SOC Labs Course** and demonstrated mastery across all five comprehensive laboratory exercises:

✅ **Lab 01:** Foundation Navigation and Search Fundamentals  
✅ **Lab 02:** Data Manipulation and Analysis  
✅ **Lab 03:** Advanced Search and Time-based Analysis  
✅ **Lab 05:** Dashboard Creation and Data Visualization  

**Professional Skills Achieved:**
- **SIEM Platform Mastery:** Complete Splunk proficiency for enterprise security operations
- **Threat Detection Expertise:** Advanced search techniques for security event identification
- **Data Analysis Proficiency:** Field manipulation, filtering, and statistical analysis capabilities
- **Visualization Excellence:** Dashboard creation and visual threat intelligence development
- **SOC Operations Readiness:** Real-world security monitoring and incident response skills

**Career Impact:**
This comprehensive skill set positions you for advanced SOC analyst roles, SIEM administration responsibilities, and cybersecurity leadership positions in enterprise environments. Your expertise in Splunk-based security operations provides immediate value to organizations requiring sophisticated threat detection and incident response capabilities.

---

*This final lab completes your journey through comprehensive Splunk security operations training, establishing expert-level capabilities in SIEM-based threat detection, analysis, and visualization for professional cybersecurity operations.*
