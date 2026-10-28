<h1>Week 3 Helpdesk Exercise</h1>
<a href = "https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwir2eP5pNyXAxVRd2wGHVeTNwcQFnoECBAQAQ&url=https%3A%2F%2Fsysdesks.com%2F&usg=AOvVaw3JZRWmcdfUv9AB3_rGtlEy&opi=89978449">Source</a>

<h2>Ticket 1</h2>
<img src="https://github.com/Jabawari/Week3_help/blob/ddf5301b8647f270b188a202f70a7ccbe267c3fd/Screenshot%202026-10-26%20142227.png" alt="App Screenshot" width="500">
<p><strong>Problem Description:</strong> An unwanted application consistently reinstalled itself after standard deletion attempts. Inspection revealed a persistence mechanism configured within Windows Task Scheduler, where an automated trigger executed a background command with the flag /reinstall/silent. </p>
<img src="https://github.com/Jabawari/Week3_help/blob/ddf5301b8647f270b188a202f70a7ccbe267c3fd/Screenshot%202026-10-26%20142906.png" alt="App Screenshot" width="500">
<img src="https://github.com/Jabawari/Week3_help/blob/ddf5301b8647f270b188a202f70a7ccbe267c3fd/Screenshot%202026-10-26%20143053.png" alt="App Screenshot" width="500">
<p><strong>Solution and Action Steps:</strong> To permanently remove the application and prevent automated reinstallation, the scheduled task executing the silent reinstall argument was deleted from the Task Scheduler library. Following the removal of the task trigger, the primary application files and registry entries were uninstalled via Settings > Apps > Installed apps. A system reboot confirmed that the background task no longer triggered and the application did not reappear.</p>
<p><strong>Alternative Solutions and Prevention:</strong> To prevent recurring reinstallations in the future, administrator privileges should be restricted for non-essential accounts so persistence mechanisms cannot be registered without explicit approval. Alternatively, running an antimalware scan (such as Windows Defender or Malwarebytes) can automatically detect and remove persistence entries, or system policies can be configured via Group Policy (gpedit.msc) to restrict unauthorized tasks from executing silent installer flags.</p>

<h2>Ticket 2</h2>
<img src="https://github.com/Jabawari/Week3_help/blob/ddf5301b8647f270b188a202f70a7ccbe267c3fd/Screenshot%202026-10-26%20143820.png" alt="App Screenshot" width="500">
<p><strong>Problem Description:</strong> The user, Maya, reported an issue where her email was not syncing properly. As a result, she was unable to receive any new incoming messages from her coworkers, even after they confirmed that the emails had already been sent.</p>
<img src="https://github.com/Jabawari/Week3_help/blob/ddf5301b8647f270b188a202f70a7ccbe267c3fd/Screenshot%202026-10-26%20144606.png" alt="App Screenshot" width="500">
<p><strong>Solution and Steps Taken:</strong> Upon investigation, the root cause was identified as the Sync Host_*** service (or OneSyncSvc) being stopped. To resolve the issue, the Windows Services management console (services.msc) was opened, and the Sync Host service properties were inspected. The service status was changed from stopped to running by manually starting it, and its startup type was updated to Automatic to ensure the service remains enabled and running even after system restarts.</p>
<p><strong>Alternative Solutions and Prevention:</strong> To avoid similar syncing issues in the future, users can check account settings within their email client (e.g., Windows Mail/Outlook) to ensure sync options for email and calendar are toggled on and set to download new content as items arrive. Additionally, administrators can prevent users or optimization scripts from inadvertently disabling critical background synchronization services by implementing Group Policy rules or running routine maintenance checks.</p>

<h2>Ticket 3</h2>
<img src="https://github.com/Jabawari/Week3_help/blob/ddf5301b8647f270b188a202f70a7ccbe267c3fd/Screenshot%202026-10-26%20150545.png" alt="App Screenshot" width="500">
<p><strong>Problem Description:</strong> An employee reported an issue where their computer's system clock was display-configured two hours behind the correct local time after returning from a business trip. This time discrepancy was caused by the system remaining locked to the time zone of the travel destination, which prevented scheduled calendar alerts, local timestamps, and time-sensitive applications from synchronizing accurately.</p>
<img src="https://github.com/Jabawari/Week3_help/blob/ddf5301b8647f270b188a202f70a7ccbe267c3fd/Screenshot%202026-10-26%20151504.png" alt="App Screenshot" width="500">
<p><strong>Solution and Steps Taken:</strong> To resolve the issue, the Windows configuration settings were opened by navigating to Settings > Time & Language > Date & Time. Under the Date & Time options, the Time zone dropdown menu was selected and manually updated to reflect the employee's correct local time zone. Once updated, the system clock immediately refreshed to display the accurate local time.</p>
<p><strong>Alternative Solutions and Prevention:</strong> To avoid similar manual adjustments in the future, users can toggle on the "Set time zone automatically" option within the Date & Time settings menu, allowing Windows to dynamically update the time zone via location services whenever they travel.</p>

<h2>Ticket 4</h2>
<img src="https://github.com/Jabawari/Week3_help/blob/ddf5301b8647f270b188a202f70a7ccbe267c3fd/Screenshot%202026-10-27%20145847.png" alt="App Screenshot" width="500">
<p><strong>Problem Description:</strong> An employee reported that a company-borrowed laptop was stolen while offsite. Because the stolen laptop could potentially be used by an unauthorized party to access sensitive company data and network resources, immediate incident response was required to revoke the device's access and mitigate data exposure risks.</p>
<img src="https://github.com/Jabawari/Week3_help/blob/ddf5301b8647f270b188a202f70a7ccbe267c3fd/Screenshot%202026-10-27%20150108.png" alt="App Screenshot" width="500">
<p><strong>Solution and Steps Taken:</strong> To neutralize the security threat, the stolen laptop was immediately located within Active Directory Administrative Center (or Active Directory Users and Computers) and its computer object account was set to Disabled. This action immediately prevents the device from authenticating against the corporate domain or accessing internal network assets. Additionally, the employee's user account status was verified to ensure it remained active and functional, allowing them to continue working securely from a replacement device without experiencing unnecessary account lockouts.</p>
<p><strong>Alternative Solutions and Prevention:</strong> To further secure the stolen device and strengthen future asset protection, IT can initiate a remote wipe or device retirement action through a Mobile Device Management (MDM) solution such as Microsoft Intune, as disabling Active Directory alone does not automatically wipe cached local data or prevent offline logins. Additionally, ensuring all company laptops have mandatory BitLocker drive encryption enabled, multi-factor authentication (MFA) enforced, and a forced password reset applied to the impacted user's credentials will safeguard corporate data even if a physical device is compromised or stolen.</p>

<h2>Ticket 5</h2>
<img src="https://github.com/Jabawari/Week3_help/blob/ddf5301b8647f270b188a202f70a7ccbe267c3fd/Screenshot%202026-10-27%20154005.png" alt="App Screenshot" width="500">
<p><strong>Problem Description:</strong> Harun’s account details in Active Directory were outdated following an internal role transition, as he was still listed under the Customer Success department despite having been transferred to the Finance department. This misconfiguration resulted in incorrect department attribution and missing access permissions required for his new position.</p>
<img src="https://github.com/Jabawari/Week3_help/blob/ddf5301b8647f270b188a202f70a7ccbe267c3fd/Screenshot%202026-10-27%20154350.png" alt="App Screenshot" width="500">
<p><strong>Solution and Steps Taken:</strong> To update Harun's profile, Active Directory Users and Computers (ADUC) was opened and his user account object was located. Under the Organization tab, his Department field was updated from "Customer Success" to "Finance". Next, under the Member Of tab, his group memberships were modified to remove old departmental groups and add him to the appropriate distribution and security lists: Finance DL and Finance Staff. These changes were applied to ensure his administrative record reflects his current department and grants him proper network access and email distribution.</p>

<h2>Key Learnings This Week:</h2>
<ul>
  <li>Technical Skill Development & Troubleshooting</li>
  <ul>
    <li>Advanced System Utilities: Expanded core diagnostic skills by utilizing Task Scheduler and Windows Services (services.msc) alongside Task Manager and Event Viewer to identify background processes, automated triggers, and root causes during system troubleshooting.</li>
    <li>Proficiency Goal: Recognized the importance of mastering deeper administrative utilities to improve issue resolution speed and become a more effective Helpdesk Support Technician.</li>
  </ul>
  <li>Professional Development & Soft Skills</li>
  <ul>
    <li>User Empathy & Perspective: Developed a greater understanding of user experience, recognizing that issues which appear simple from an IT perspective (such as single-click settings adjustments) can significantly impact end-user productivity.</li>
    <li>Service Excellence: Approaching every ticket with patience and empathy to ensure clean communication and positive user interactions regardless of issue complexity.</li>
  </ul>
</ul>
