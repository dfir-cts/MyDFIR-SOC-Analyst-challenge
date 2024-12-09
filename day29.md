# Elastic Defend Setup Tutorial

This knowledge base article details the setup and usage of Elastic Defend (EDR), focusing on its installation, configuration, alert generation, and response actions. This guide is based on a 30-day challenge focusing on Security Operations Center (SOC) analyst skills. Elastic Defend (EDR) is Elastic's Endpoint Detection and Response solution.

## Overview

This document provides a step-by-step guide to installing and configuring Elastic Defend (Endpoint Detection and Response, or EDR), viewing its generated telemetry, and responding to alerts. The guide specifically addresses using Elastic Defend with a free subscription and a 30-day trial, highlighting the differences in functionality. Key features covered include detailed data collection specifics, NextGen antivirus integration configuration options and troubleshooting, alert investigation techniques with example scenarios, and response actions like host isolation (available with trial or paid subscriptions), including a comparison of actions available with free vs. paid plans.


## Step-by-Step Installation and Configuration of Elastic Defend

**Prerequisites:**

* Access to an Elastic Stack environment (version 8.x or higher is recommended.  Elasticsearch, Kibana, and the Elastic Agent are required).  [Link to Elastic Stack setup documentation](https://www.elastic.co/guide/index.html)  Specific version compatibility information can be found within the Elastic Defend documentation linked below.
* A supported endpoint operating system: Windows Server 2019 and later, Windows 10 and later, macOS 10.15 and later, and various Linux distributions (refer to the compatibility matrix for the most up-to-date list). [Link to Elastic Defend compatibility documentation](https://www.elastic.co/guide/index.html)
* A free Elastic subscription or a 30-day trial.  [Link to obtain a trial license](https://www.elastic.co/trial)


**Steps:**

1. **Access Integrations:** Click the hamburger menu icon (☰) in the top-left corner of your Elastic interface. Scroll down and select "Integrations."  [Screenshot of Integrations menu]

2. **Add Elastic Defend:** Click on "Elastic Defend" and then "Add."  [Screenshot of "Add Elastic Defend" button and configuration screen]

3. **Configure Integration:**
    * **Integration Name:** Provide a descriptive name (e.g., "MyDFIR_EDR").
    * **Description:** Add a description (e.g., "Elastic EDR for 30-day DFIR challenge").
    * **Data Collection:** Select your desired data collection settings.  Available options include:
        * **Process Events:** Captures information about process creation, termination, and modifications.
        * **File Events:** Records file system activity, including file creation, deletion, modification, and access.
        * **Network Events:** Monitors network connections and traffic.
        * **Registry Events:** Tracks changes to the Windows Registry (Windows only).
        * **Authentication Events:** Logs authentication attempts and successes.
        * **Security Events:** Collects security-related events from the operating system.

        The implications of each option on performance and data volume are detailed in the official Elastic Defend documentation.  For high-security environments, selecting all options may be necessary, but it will increase data volume and resource consumption. For low-impact deployments, you can start with a subset of options, such as Process Events and File Events.  [Table comparing data collection options and their resource impact]

    * **NextGen Antivirus:** Configure NextGen antivirus integration if needed.  This integration enhances threat detection by correlating EDR data with antivirus alerts.  Supported antivirus solutions include [list supported vendors].  Configuration steps vary depending on the vendor; consult the vendor's documentation for specific instructions. [Link to relevant documentation if available]

    * **EDR Mode:** Choose between "Essential EDR" and "Complete EDR." "Complete EDR" provides full telemetry (available with a trial or paid subscription), including advanced features like host isolation and detailed behavioral analysis. "Essential EDR" provides a more limited set of features and data.  [Table comparing Essential EDR and Complete EDR features]

    * **Endpoint Type:** Select "Traditional endpoints" for desktops, laptops, and VMs, or "Cloud workloads" for Linux servers or Kubernetes environments.  Supported cloud platforms include [list supported platforms].  Configuration for each endpoint type is detailed in the Elastic Defend documentation.

    * **Host Selection:** Add the integration to your target host(s). For example, select your Windows server policy if using a fleet management approach.  Methods for host selection include manual addition, using a fleet management system (recommended for large deployments), or using group policies (for Windows environments). [Table comparing host selection methods]

4. **Save and Deploy:** Click "Save and Continue" and then "Save and Deploy Changes."  [Screenshots to illustrate the process]

5. **Verify Installation:** Navigate to Security -> Manage -> Endpoints. You should see your endpoint listed as running Elastic Defend, with a status of "active" and showing the last check-in time.  If the status is not "active," check the agent logs for error messages.  Common issues and troubleshooting steps are detailed in the "Common Issues and Troubleshooting" section. [Screenshot of the Endpoints view showing a successfully installed agent]


## Viewing Elastic Defend Telemetry

After installation and configuration, Elastic Defend will begin collecting telemetry data. To view this data:

1. **Open Kibana:** Access your Kibana instance.

2. **Open Discover:** Navigate to the "Discover" tab.

3. **Search for Events:** Use Kibana's query language (KQL) to search for relevant terms.  For example, `event.kind:process AND process.name:"*suspicious*"`, or `event.kind:file AND file.path:"/tmp/*"`. Adjust the time range as needed.  Sort by timestamp (newest to oldest) for easier review.  [Screenshots of example Kibana queries and visualizations]

4. **Analyze Events:** Review the generated alerts. Key information includes event codes (see the table below), file paths, file hashes, process trees, and other relevant details. The example in the tutorial showed a malware prevention alert with details about the malicious file (`my-dfir-30.exe` in this case), its location, and its hash.  [Table mapping event codes to their descriptions]  [Screenshots of example alert details, highlighting key data fields and their interpretations. Include explanations of process trees and their significance in threat analysis.]


## Responding to Alerts

Elastic Defend allows for response actions to detected threats. With a free subscription, host isolation is not available. However, with a trial or paid subscription, you can take actions like isolating the host.  [Table detailing response actions available for each subscription tier]

1. **Navigate to Alerts:** Go to the "Security" section and view your alerts.

2. **View Alert Details:** Open the alert you wish to respond to.

3. **Edit Rule Settings (for paid subscriptions):** Click on "Edit Rule Setting."  This allows you to create custom rules based on specific criteria (e.g., specific file hashes, process names, or network connections) and define corresponding response actions.  [Screenshot showing how to create a custom rule and configure response actions]

4. **Configure Response Action:** Under "Action," select "Elastic Defend" and choose your desired response (e.g., "Isolate host").  [Table explaining the implications of each response action and providing best practices for selecting appropriate actions]

5. **Save Changes:** Save your changes to implement the response action.


## Best Practices

* **Regularly review alerts:**  Monitor Elastic Defend alerts at least daily, prioritizing alerts based on severity and potential impact.  Use Kibana dashboards to visualize alert trends and identify potential patterns.

* **Use a fleet management approach:** Manage your endpoints centrally using a system like Elastic Agent or other fleet management tools for easier administration and consistent policy enforcement.  [Link to relevant documentation on fleet management]

* **Configure appropriate response actions:**  Tailor response actions to your environment and risk tolerance.  For example, you might choose to automatically isolate a host for critical alerts, while manually investigating less critical alerts.

* **Keep your Elastic Defend agents updated:** Ensure your agents have the latest updates and signatures by regularly checking for updates through the Elastic Stack management interface.  [Screenshot showing how to check for agent updates]


## Common Issues and Troubleshooting

* **Host Isolation Unavailable:** If host isolation is not working, verify that you have a trial or paid subscription. Free subscriptions do not include this feature.  Check the agent logs for any error messages related to host isolation.  Ensure that the necessary permissions are granted to the Elastic Defend agent.

* **Alerts Not Appearing:**  Check your data collection settings and ensure that the necessary data is being collected. Verify that Kibana is correctly configured to receive and display the data.  Check for data ingestion errors in Elasticsearch logs.  Ensure that the correct indices are configured in Kibana.

* **Agent Communication Issues:** Ensure that your endpoints can communicate with your Elastic Stack. Check network connectivity and firewall rules.  Verify that the Elastic Agent is running and communicating correctly.  Check for any network connectivity issues between the endpoints and the Elastic Stack.


## Related Resources

* **Elastic Defend Documentation:** [Link to official Elastic Defend documentation]
* **Elastic Security Community Forums:** [Link to Elastic Security community forums]


This guide provides a comprehensive overview of setting up and utilizing Elastic Defend. Remember to consult the official Elastic documentation for the most up-to-date information and best practices.
