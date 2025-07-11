Here’s the **enhanced and organized version** of your **Onboarding Access Request Guide**, now including:

1. An explanation of **AD group integration with Okta/SSO**, including special cases like **Imperva/Incapsula**.
2. Clear **subsections for ServiceNow**: Request Creation and Status Checking.
3. **Per-app access instructions** (e.g., Incapsula / Akamai API Security), including troubleshooting steps, examples, and sample screenshots.

---

# 🛠️ Employee Onboarding – Access Request Guide

**Version:** 1.4
**Last Updated:** 19 June 2025
**Owner:** IT Department / People Ops

---

## 📌 Purpose

This document helps new joiners understand how to request and verify access to required systems, tools, and physical spaces. It includes:

* Email & VPN setup
* App access via OKTA SSO & AD groups
* DL verification
* Badge request
* App-specific instructions (e.g., Incapsula, Akamai API Security)
* ServiceNow ticket process

---

## 🔐 AD Group Integration with OKTA SSO

Most applications in our environment are protected by **Single Sign-On (SSO)** using **OKTA**.
Access control is handled by **Active Directory (AD) groups**.

### ✅ How It Works:

* Each application is **mapped to an AD group**
* If your **domain ID** is added to that AD group, OKTA grants you access to the app via the OKTA dashboard
* You do **not** need separate credentials for the app

📝 **However**, for some applications like **Imperva (Incapsula WAF)** or **Snowflake**, additional configuration is required inside the application (post-login), such as assigning **roles, policies, or app-level permissions**.

---

## 🗃️ Application → AD Group Mapping

| **App Name**                                | **AD Group**             | **SP Contact / Notes**                                                                  | **Sample Ticket (REQ#)** |
| ------------------------------------------- | ------------------------ | --------------------------------------------------------------------------------------- | ------------------------ |
| **Jira**                                    | `AD-JIRA-USERS`          | Request access from Jira owner                                                          | `REQ1234567`             |
| **Confluence**                              | `AD-CONFLUENCE-USERS`    | Same as Jira                                                                            | `REQ1234568`             |
| **Akamai API Security** *(formerly Noname)* | `AD-AKAMAI-API-SECURITY` | Access via Okta tile. Confirm app roles inside Akamai console                           | `REQ1234569`             |
| **Incapsula WAF (Imperva)**                 | `AD-WAF-OPS-ADMIN`       | Requires additional config in **Imperva console** or access will fail with login prompt | `REQ1234570`             |
| **SentinelOne Console**                     | `AD-SEC-ENDPOINT-OPS`    | Security team assigns roles after group approval                                        | `REQ1234571`             |
| **Workday** *(HR Portal)*                   | `AD-WORKDAY-USERS`       | Auto-assigned during onboarding                                                         | `REQ1234572`             |

---

## 📥 ServiceNow – Access Request Process

### 🔹 1. How to Create a Request

1. Open [ServiceNow Portal](https://servicenow.company.com)
2. You will be redirected to **OKTA** → login using your corporate credentials
3. Navigate:
   🛠️ **Access Management** → **Request Group Membership**
4. In the **Search bar**, type the required **AD Group name** (see table above)
5. Provide:

   * Justification for access
   * Manager’s name/email
   * **SP (Service Provider)** contact if needed
6. Submit your request

📝 *SP (Service Provider)* refers to the **app owner or admin team** who needs to approve the request, e.g., `john.doe@company.com` for WAF.

---

### 🔍 2. How to Check Ticket Status

1. In [ServiceNow](https://servicenow.company.com), go to **My Requests**
2. Locate your ticket or filter by ticket ID (`REQ1234567`)
3. Track ticket status:

| **Status**             | **Meaning**                                                                                                 |
| ---------------------- | ----------------------------------------------------------------------------------------------------------- |
| **Pending Approval**   | Waiting for one or more approvers (e.g., Manager, SP)                                                       |
| **In Progress**        | IT or App team is handling the request                                                                      |
| **Closed / Completed** | Task marked done – ⚠️ For some apps like Imperva, further in-app config is needed before actual access works |

---

## 🔐 Dedicated App Instructions & Troubleshooting

### 🔸 Incapsula WAF (Imperva)

#### 🔹 How to Access

1. Login to [Okta](https://okta.company.com)
2. Find and click on **Incapsula WAF / Imperva** tile
3. If provisioned correctly:

   * You’ll be signed in automatically via OKTA SSO
   * Dashboard loads with your permissions

#### 🛠️ Troubleshooting

| **Issue**                                                                  | **Cause**                                                             | **Solution**                                                                     |
| -------------------------------------------------------------------------- | --------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Redirected to **Imperva login screen** asking for manual username/password | You’re in the AD group, but NOT yet configured inside Imperva console | Contact `alice.lee@company.com` to complete your Imperva role config             |
| "Access Denied" error after SSO                                            | Missing app roles or incorrect group                                  | Confirm you’re in the right AD group (`AD-WAF-OPS-ADMIN`) and app config is done |

#### 🖼️ Example Screenshot

**Incorrect Config (Prompted for Login):**
![Imperva Login Prompt](https://via.placeholder.com/600x300?text=Imperva+Login+Screen+%28Manual+Login%29)

**Correct Config (SSO Passed):**
![Imperva OKTA SSO](https://via.placeholder.com/600x300?text=Imperva+SSO+Dashboard)

---

### 🔸 Akamai API Security *(formerly Noname Security)*

#### 🔹 How to Access

1. Login to [Okta](https://okta.company.com)
2. Click the **Akamai API Security** tile
3. If access is correctly configured:

   * You’ll land on the Akamai dashboard
   * Your API dashboards, logs, or alerts should load

#### 🛠️ Troubleshooting

| **Issue**                          | **Cause**                                | **Solution**                                            |
| ---------------------------------- | ---------------------------------------- | ------------------------------------------------------- |
| “Access Denied” or Blank Dashboard | Missing user role inside Akamai platform | Contact `secops@company.com` to assign correct role     |
| App not showing on OKTA            | Not in `AD-AKAMAI-API-SECURITY` group    | Submit ServiceNow request with SP: `secops@company.com` |

---

### 🔸 SentinelOne Console

#### 🔹 How to Access

1. Login to [Okta](https://okta.company.com)
2. Click **SentinelOne** tile
3. Dashboard should load directly

#### 🛠️ Troubleshooting

* Contact `security-ops@company.com` if roles are not assigned or console access fails.

---

## 🖼️ Example Screenshots

### 1. OKTA Portal – App Tiles

![OKTA Dashboard](https://via.placeholder.com/600x300?text=OKTA+Dashboard+with+Incapsula+%2F+Akamai)

---

### 2. ServiceNow – Request Form

![ServiceNow Group Request](https://via.placeholder.com/600x300?text=ServiceNow+Group+Membership+Form)

---

### 3. Imperva Login Failure (SSO Not Configured)

![Manual Login Prompt](https://via.placeholder.com/600x300?text=Imperva+asking+for+Username)

---

## 📚 Reference Links

* 🔗 [OKTA Login](https://okta.company.com)
* 🔗 [ServiceNow Portal (via OKTA)](https://servicenow.company.com)
* 🔗 [DL & AD Group Sheet](https://intranet.company.com/dl-mapping)
* 🔗 [PPM Time Tracker](https://ppm.company.com)

---

## 📞 Contacts

| **Area**                | **Contact**                                |
| ----------------------- | ------------------------------------------ |
| IT Helpdesk             | `helpdesk@company.com`                     |
| HR & Badge              | `hr@company.com`, `facilities@company.com` |
| Security (SP/Approvals) | `security-ops@company.com`                 |
| App Specific SPs        | See app table above                        |

---

