# Silent Breach: Unmasking Insider Threats in Ethiopia’s Digital Identity and Critical Infrastructure Systems

## Project Overview:

Insider threats pose a significant risk to Ethiopia’s rapidly expanding digital ecosystem, including critical systems like the Fayda Digital ID program, banking platforms, telecom subscriber databases, government ministries, aviation, and energy sectors. These threats often originate from trusted insiders—employees or contractors—who misuse their access to steal sensitive data, sabotage operations, or manipulate records.

**Silent Breach** is an advanced insider threat detection system designed to proactively identify and mitigate these risks by deploying realistic decoy assets (e.g., fake files, dummy database entries) across organizational networks. By monitoring interactions with these decoys, the system generates real-time alerts, builds behavioral profiles, and provides actionable insights to security teams, enabling early detection and response before significant damage occurs.

This project is tailored for Ethiopia’s critical infrastructure, offering a lightweight agent for monitored systems and a centralized web-based dashboard for alert aggregation, investigation, and reporting. It addresses unique regional challenges, drawing lessons from incidents like Kenya’s Huduma Namba breach, and aligns with Ethiopia’s National Cybersecurity Strategy.

---

## Features:

- **Decoy Asset Deployment:** Automatically generates and manages realistic but fake files, database entries, and system objects that contain no sensitive data.  
- **Real-Time Access Monitoring:** Tracks unauthorized or suspicious interactions with decoys, capturing metadata such as user ID, timestamp, device details, and access method.  
- **Behavioral Profiling:** Analyzes user activity to detect anomalies, such as after-hours access or repetitive decoy targeting.  
- **Centralized Dashboard:** Provides a web-based interface for real-time visualization of alerts, activity logs, and risk assessments across multiple systems.  
- **Secure Alerting:** Sends encrypted, tamper-proof alerts to security teams for immediate investigation.  
- **Automated Reporting:** Generates detailed incident reports with forensic evidence for audits and investigations.  
- **Ethiopian Context Customization:** Includes decoy scenarios tailored for critical sectors like Digital ID, banking, telecom, education, aviation, and energy.

## Deliverables:

1. **Insider Threat Detection Agent:** A lightweight Python-based tool to deploy decoys and monitor access on target systems (Linux/Windows).  
2. **Centralized Web Dashboard:** A React-based interface for real-time alert aggregation, behavioral analysis, and report generation.  
3. **Sample Decoy Scenarios:** Predefined decoy assets for Ethiopian sectors, including Digital ID, banking, and SCADA systems.  
4. **Comprehensive Documentation:** Includes installation guides, system architecture, usage instructions, and test scenarios.  
5. **Demo Scripts:** Automated test cases simulating insider threat behaviors to demonstrate detection capabilities.  
6. **Fayda Mock UI and Demo Site:** A demo site and mock UI mimicking the Fayda Digital ID interface, created since fayda.et is restricted, to simulate insider threat scenarios.  
7. **Small E-Banking App Setup:** A small e-banking application to replicate the infrastructure of the Commercial Bank of Ethiopia (CBE) for testing Fayda ID-related insider threats.  
8. **Insider Data Access Simulation:** Tools to simulate unauthorized data access, privilege escalation, data tampering, and mass data export threats.  
9. **Unusual Behavior Detection Module:** A module featuring log analysis, anomaly detection, real-time alerting, and session recording for identifying suspicious insider activities.  
10. **Decoy Trap System:** A system for creating decoy assets that must not be accessed by users; if accessed, it triggers a breach alert with data masking (e.g., masking sensitive data with placeholders like "251****8894").

## Technical Architecture:

- **Agent:** A Python-based service running on monitored hosts, responsible for deploying decoys and sending encrypted event data.  
- **Backend Server:** A Flask-based RESTful API that receives and processes alerts, storing them in a PostgreSQL database with TLS encryption.  
- **Frontend Dashboard:** A React web application for visualizing alerts, user activity profiles, and generating reports.  
- **Communication:** TLS-encrypted HTTPS for secure data transmission between agents and the backend.  
- **Optional Tools:** A CLI-based configuration tool for managing decoy assets and system settings.

## Installation & Usage:

1. **Agent Installation:** Deploy the Python-based agent on Linux/Windows hosts using provided installation scripts.  
2. **Backend Setup:** Install the Flask backend and PostgreSQL database on a secure server. Configure TLS certificates for encrypted communication.  
3. **Dashboard Access:** Access the React-based dashboard via a web browser after setting up the backend.  
4. **Decoy Configuration:** Use the CLI tool or dashboard to deploy sector-specific decoy assets.  
*Detailed instructions are provided in the accompanying documentation.*

---

## Ethiopian Critical Infrastructure Insider Threat Scenarios:
The following scenarios illustrate how **Silent Breach** detects insider threats across Ethiopia’s critical sectors:

### Main Scenario: National Digital ID Insider Threat:
**Background:** Ethiopia’s Fayda Digital ID program stores sensitive biometric and demographic data for millions of citizens, critical for government services, banking, and social programs.  
**Insider Threat:** A system administrator creates a hidden backdoor account to access citizen data after hours, exporting encrypted data chunks to a personal cloud account while altering audit logs.  
**Detection by Silent Breach:**  
- Fake citizen records with realistic but dummy details are seeded into the database.  
- Any access to these records triggers a silent alert to INSA, capturing timestamp, user ID, and IP address.  
- Behavioral profiling detects unusual login times and specific data queries, flagging the administrator for investigation.

### Scenario 1: Commercial Bank of Ethiopia Core Banking Insider:
**Background:** The CBE’s core banking system processes millions of daily transactions.  
**Insider Threat:** An IT staff member plants malicious SQL queries to skim micro-amounts (e.g., 0.10 ETB) from multiple accounts, deleting log entries to hide their tracks.  
**Detection:**  
- Fake “high-balance” accounts are created as decoys.  
- Any transaction involving these accounts triggers an alert.  
- The system detects a pattern of fractional withdrawals, flagging the insider’s activity.

### Scenario 2: Ethio Telecom Subscriber Database:
**Background:** Ethio Telecom’s centralized database contains KYC data for all SIM card owners.  
**Insider Threat:** A customer service employee sells verified SIM card details to fraudsters for SIM swap attacks.  
**Detection:**  
- Dummy subscriber entries with valid-looking phone numbers are seeded.  
- Queries to these accounts from a non-standard workstation trigger alerts, including workstation ID and employee details.

### Scenario 3: Ministry of Education National Exam Database:
**Background:** The Ministry of Education hosts Grade 12 national exam results.  
**Insider Threat:** An IT staff member alters exam results for bribes.  
**Detection:**  
- Decoy student IDs with impossible grades (e.g., 100% in all subjects) are inserted.  
- Any modification attempt triggers an instant alert, logging user credentials for investigation.

### Scenario 4: Ethiopian Airlines Flight Operations System:
**Background:** Ethiopian Airlines manages flight crew schedules, passenger manifests, and maintenance logs.  
**Insider Threat:** A rogue operations officer modifies maintenance logs to conceal skipped inspections.  
**Detection:**  
- Decoy aircraft entries with outdated maintenance status are inserted.  
- Any modification triggers alerts and forensic logging for immediate response.

### Scenario 5: Ethiopian Electric Power Grid SCADA System:
**Background:** Ethiopia’s power grid relies on SCADA systems for electricity distribution.  
**Insider Threat:** A technician alters SCADA commands to cause localized blackouts.  
**Detection:**  
- Fake “control switches” and power nodes are added to the SCADA interface.  
- Any command sent to these nodes triggers immediate security intervention.

## Insider vs. Outsider Threat Context:

### Global Trends:
- **Insider Threats:** Account for ~30-35% of cybersecurity incidents globally (Verizon 2023, IBM X-Force 2023, Ponemon Institute 2023).  
- **Outsider Threats:** Represent ~65-70% of incidents, including hackers, malware, and phishing.  
- **Why Insiders Are Critical:** Insiders cause higher damage per incident due to privileged access and system knowledge, with attacks often persisting longer before detection.

### Sector-Specific Insights:
- In finance, government, and energy sectors, insider threats can account for up to 40% of incidents due to high access levels (FS-ISAC 2022).  
- In Ethiopia, the rapid digitization of infrastructure (e.g., Digital ID, mobile banking) increases insider threat risks due to limited monitoring maturity.

### Regional Context: Kenya’s Huduma Namba Breach:
In 2021, Kenya’s Huduma Namba digital ID platform suffered a major breach, exposing personal data of millions. While primarily attributed to external attackers, insider complicity or negligence was suspected, amplifying the damage. This incident underscores the need for robust insider threat detection in Ethiopia’s similar digital transformation efforts.

## Why Silent Breach Is Critical for Ethiopia:
- **National Importance:** Ethiopia’s digital transformation, including the Fayda Digital ID, relies on public trust and system integrity.  
- **Unique Challenges:** Current cybersecurity measures focus on external threats, leaving gaps in insider detection.  
- **Regional Relevance:** Lessons from Kenya’s Huduma Namba breach highlight the urgency of addressing insider risks.  
- **Scalable Solution:** Silent Breach is lightweight, customizable, and designed for Ethiopia’s critical infrastructure, aligning with INSA’s cybersecurity goals.

## Future Enhancements:
- Integration with INSA’s SIEM tools for seamless threat correlation.  
- Machine learning for advanced anomaly detection in behavioral profiles.  
- Multi-factor authentication and tamper-proof logging for agent security.  
- Mobile app for real-time alerts to incident response teams.  
- Expansion to other African nations facing similar insider threat challenges.

## Contributors:
- Abrham Mucheye  
- Hundaol Begna Telbaso  
- Fisseha Akele  
- Abemelek Tadesse  
- Yafet Tesfaye Yeilma  

## License
MIT License

## References:
- OWASP Insider Threat Guidelines  
- Ethiopian National Cybersecurity Strategy  
- INSA Cybersecurity Reports (publicly available)  
- Verizon 2023 Data Breach Investigations Report  
- IBM X-Force Threat Intelligence Index 2023  
- Ponemon Institute Cost of Insider Threats Report 2023  
- FS-ISAC 2022 Financial Sector Threat Report  
- Kenya Huduma Namba Breach Reports (2021)

