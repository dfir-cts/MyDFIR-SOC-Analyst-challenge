# Elastic Defend Setup and Telemetry Review: A Comprehensive Guide

This knowledge base article details the setup and usage of Elastic Defend (EDR), focusing on its installation, configuration, alert generation, and response actions.  This guide is based on a 30-day challenge focusing on Security Operations Center (SOC) analyst skills.  Elastic Defend (EDR) is Elastic's Endpoint Detection and Response solution.

## Overview

This document provides a step-by-step guide to installing and configuring Elastic Defend (Endpoint Detection and Response, or EDR), viewing its generated telemetry, and responding to alerts.  The guide specifically addresses using Elastic Defend with a free subscription and a 30-day trial, highlighting the differences in functionality.  Key features covered include data collection, NextGen antivirus integration, alert investigation, and response actions like host isolation (available with trial or paid subscriptions).


## Step-by-Step Installation and Configuration of Elastic Defend

**Prerequisites:**

* Access to an Elastic Stack environment.
* A Windows server (or other supported endpoint).
* A free Elastic subscription or a 30-day trial.


**Steps:**

1. **Access Integrations:** Click the hamburger menu icon (☰) in the top-left corner of your Elastic interface. Scroll down and select "Integrations."

2. **Add Elastic Defend:** Click on "Elastic Defend" and then "Add."

3. **Configure Integration:**
    * **Integration Name:**  Provide a descriptive name (e.g., "MyDFIR_EDR").
    * **Description:** Add a description (e.g., "Elastic EDR for 30-day DFIR challenge").
    * **Data Collection:** Select your desired data collection settings.
    * **NextGen Antivirus:** Configure NextGen antivirus integration if needed.
    * **EDR Mode:** Choose between "Essential EDR" and "Complete EDR."  "Complete EDR" provides full telemetry (available with a trial or paid subscription).
    * **Endpoint Type:** Select "Traditional endpoints" for desktops, laptops, and VMs, or "Cloud workloads" for Linux servers or Kubernetes environments.
    * **Host Selection:** Add the integration to your target host(s).  For example, select your Windows server policy if using a fleet management approach.

4. **Save and Deploy:** Click "Save and Continue" and then "Save and Deploy Changes."

5. **Verify Installation:** Navigate to Security -> Manage -> Endpoints. You should see your endpoint listed as running Elastic Defend.

## Viewing Elastic Defend Telemetry

After installation and configuration, Elastic Defend will begin collecting telemetry data.  To view this data:

1. **Open Kibana:** Access your Kibana instance.

2. **Open Discover:** Navigate to the "Discover" tab.

3. **Search for Events:** Search for relevant terms, such as "malware" to filter events.  Adjust the time range as needed (e.g., "Last 15 minutes").  Sort by timestamp (newest to oldest) for easier review.

4. **Analyze Events:** Review the generated alerts.  Key information includes event codes, file paths, file hashes, process trees, and other relevant details.  The example in the tutorial showed a malware prevention alert with details about the malicious file (`my-dfir-30.exe` in this case), its location, and its hash.

## Responding to Alerts

Elastic Defend allows for response actions to detected threats.  With a free subscription, host isolation is not available. However, with a trial or paid subscription, you can take actions like isolating the host.

1. **Navigate to Alerts:** Go to the "Security" section and view your alerts.

2. **View Alert Details:** Open the alert you wish to respond to.

3. **Edit Rule Settings:** Click on "Edit Rule Setting."

4. **Configure Response Action:** Under "Action," select "Elastic Defend" and choose your desired response (e.g., "Isolate host").

5. **Save Changes:** Save your changes to implement the response action.

## Best Practices

* **Regularly review alerts:**  Monitor Elastic Defend alerts proactively to identify and respond to threats in a timely manner.
* **Use a fleet management approach:** Manage your endpoints centrally for easier administration.
* **Configure appropriate response actions:** Tailor response actions to your environment and risk tolerance.
* **Keep your Elastic Defend agents updated:** Ensure your agents have the latest updates and signatures.

## Common Issues and Troubleshooting

* **Host Isolation Unavailable:** If host isolation is not working, verify that you have a trial or paid subscription.  Free subscriptions do not include this feature.
* **Alerts Not Appearing:** Check your data collection settings and ensure that the necessary data is being collected.  Verify that Kibana is correctly configured to receive and display the data.
* **Agent Communication Issues:** Ensure that your endpoints can communicate with your Elastic Stack. Check network connectivity and firewall rules.

## Related Resources

* **Elastic Defend Documentation:** Refer to the official Elastic documentation for detailed information on Elastic Defend features and configurations.
* **Elastic Security Community Forums:** Engage with the Elastic Security community for assistance and troubleshooting.


This guide provides a comprehensive overview of setting up and utilizing Elastic Defend.  Remember to consult the official Elastic documentation for the most up-to-date information and best practices.
