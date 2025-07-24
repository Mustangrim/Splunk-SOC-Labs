# Splunk Basics Lab 01: Foundation Navigation and Search Fundamentals

## Lab Overview

**Lab Focus:** Essential Splunk interface navigation and fundamental search techniques for SOC operations  
**Difficulty:** Foundation    
**Author:** Mykyta Palamarchuk  
**Role:** SOC Analyst | SIEM Operations & Threat Detection  
**Certification:** CompTIA Security+ (SY0-701)

### Environment Specifications
- **Platform:** Splunk Enterprise/Cloud web interface
- **Administrative Privileges:** Standard user access for search operations
- **Business Context:** Enterprise SOC environment at Buttercup Games
- **Technology Focus:** Splunk navigation, search fundamentals, and log analysis

---

## Learning Objectives

Upon completion of this lab, participants will demonstrate:

1. **Splunk interface proficiency** including navigation between apps and core components
2. **Search fundamentals mastery** using term-based queries and advanced search syntax
3. **Results analysis capabilities** interpreting timelines, fields, and event data
4. **SOC investigation techniques** applying search methods to security incident analysis
5. **Log source understanding** identifying key metadata fields for forensic analysis
6. **Query refinement skills** using multiple terms and quoted phrases for precision searching

---

## Business Scenario

You are a systems and security operations analyst at Buttercup Games. The company operates a Splunk SIEM environment that ingests web transactions, database activity, and system security logs. Your objective is to master Splunk's navigation and search capabilities for daily SOC operations, including investigating failed authentication attempts and analyzing security events.

---

## Lab Exercises

### Exercise 1: System Access and Interface Navigation

#### Task 1.1: Authentication and App Selection

**Objective:** Access Splunk web interface and navigate to search environment.

**Procedure:**
1. Navigate to Splunk web interface
2. Authenticate using credentials:
   - Username: `admin`
   - Password: `rangeforce`
3. Acknowledge message boxes
4. Select **Search & Reporting** from left navigation panel

![Search & Reporting App Selection](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/search-reporting-app-selection.png)

#### Task 1.2: Interface Component Identification

**Objective:** Identify critical search interface components.

**Components:**
- **Search Bar:** Central query input
- **Time Selector:** Temporal scope control (right side)
- **App Components:** Top navigation elements

![Search Page Interface Overview](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/search-page-interface-overview.png)

---

### Exercise 2: Basic Search Operations

#### Task 2.1: Term-Based Search Execution

**Objective:** Execute basic search to identify failed authentication events.

**Procedure:**
1. Set time picker to **All time**
2. Enter search term: `failed`
3. Execute search

![Basic Failed Search Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/basic-failed-search-results.png)

![Detailed Search Results View](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/detailed-search-results-view.png)

#### Task 2.2: Search Interface Analysis

**Objective:** Analyze search execution interface.

![Search Interface Demonstration](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/search-interface-demonstration.png)

#### Task 2.3: Results Component Analysis

**Objective:** Analyze three-component results interface.

**Components:**
1. **Timeline:** Event frequency distribution
2. **Fields Panel:** Metadata extraction (left sidebar)
3. **Events List:** Detailed event data

![Search Results Components Overview](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/search-results-components-overview.png)

![Events List Detailed View](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/events-list-detailed-view.png)

**Critical Fields:**
- **host:** Source system identifier
- **source:** Data origin path/protocol
- **sourcetype:** Data format classification

#### Task 2.4: Event Analysis and Data Extraction

**Objective:** Extract forensic data from search results.

![Event Timeline Analysis](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/event-timeline-analysis.png)

**Analysis Questions:**
1. **Most recent event date (MM/DD/YY):** 5/27/20
2. **Most recent failed login username:** ubuntu
3. **Most recent event source:** /var/log/splunk/default/linux_s_30DAY.log

---

### Exercise 3: Advanced Search Techniques

#### Task 3.1: Multi-Term Search Construction

**Objective:** Refine search using multiple terms.

**Procedure:**
1. Modify existing search to include: `failed root`
2. Execute refined search
3. Analyze results for root account authentication failures

#### Task 3.2: Quoted String Search

**Objective:** Execute precise phrase matching.

**Procedure:**
1. Clear search bar
2. Enter: `"failed password for root"`
3. Execute search

![Quoted Phrase Search Results](https://raw.githubusercontent.com/Mustangrim/Splunk-SOC-Labs/main/assets/screenshots/quoted-phrase-search-results.png)

**Results:** 7,282 events containing exact phrase

**Analysis:** High volume indicates potential brute force attack against privileged account.

---

## Technical Assessment

### Interface Navigation
- App selection and navigation efficiency
- Component identification accuracy
- Time range configuration

### Search Query Construction
- Basic term search execution
- Multi-term query construction
- Quoted phrase syntax implementation

### Results Analysis
- Metadata field identification
- Event data extraction
- Timeline interpretation

---

## SOC Applications

### Operational Use Cases
- **Incident Triage:** Rapid security event identification
- **Threat Hunting:** Proactive compromise indicator searches
- **Compliance Monitoring:** Authentication failure reporting
- **Forensic Analysis:** Event sequence examination

### Performance Metrics
- Reduced Mean Time to Detection (MTTD)
- Improved incident response efficiency
- Enhanced compliance reporting capability

---

## Lab Completion

**Skills Validated:**
- Splunk interface navigation
- Basic and advanced search construction
- Security event identification
- Results interpretation
- Metadata analysis

**Technical Competencies:**
- SIEM platform proficiency
- Log analysis methodology
- Investigation techniques
- Query optimization

---

*Lab establishes foundation for advanced Splunk security operations including threat detection, incident response, and security monitoring in enterprise environments.*
