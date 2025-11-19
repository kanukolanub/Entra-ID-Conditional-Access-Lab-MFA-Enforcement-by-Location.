# Entra-ID-Conditional-Access-Lab-MFA-Enforcement-by-Location.
# 🛡️ Entra ID Conditional Access Lab: MFA Enforcement by Location

## 💡 Project Goal

The primary objective of this lab was to implement and validate a **Zero Trust** principle: Enforce Multi-Factor Authentication (MFA) for users accessing sensitive cloud applications **only** when they are connecting from an **Untrusted Network** (Outside the corporate perimeter).

This project showcases hands-on proficiency in designing and troubleshooting identity security policies.

## 🛠️ Key Skills Demonstrated

| IAM Domain | Specific Technique | Business Value |
| :--- | :--- | :--- |
| **Conditional Access** | Policy creation using **Include/Exclude** logic for **Named Locations**. | Secures access based on user context (Location). |
| **Session Management** | Implementing **Sign-in Frequency** controls. | Mitigates session hijacking risk and prevents MFA token reuse. |
| **Troubleshooting** | Diagnosing "MFA Not Triggering" issues using **Sign-in Logs**. | Ability to audit policy application and identify root causes of security bypasses. |
| **Zero Trust** | Enforcing "Never Trust, Always Verify" by requiring MFA upon change of location/session. | Reduces organizational risk and strengthens compliance posture. |

## ⚙️ Tools and Setup

* **Identity Provider:** Microsoft Entra ID (formerly Azure AD)
* **Policy Control:** Conditional Access Blade
* **Auditing:** Entra Sign-in Logs (Monitoring & Health)
* **Target Application:** Microsoft Office 365
* **Testing Environments:** Home Wi-Fi (Defined Trusted Location) and Mobile Hotspot (Untrusted Location)

## 📝 Lab Scenarios & Key Findings

The lab was conducted in two main phases to isolate the impact of session controls.

### Phase 1: Default Settings (No Sign-in Frequency Control)

| Test Condition | Expected Result | Actual Result | Root Cause Found in Logs |
| :--- | :--- | :--- | :--- |
| **Trusted Network** (Home Wi-Fi) | No MFA Trigger | No MFA Trigger | **Correct Policy Application:** Policy successfully excluded the Trusted Location. |
| **Untrusted Network** (Hotspot) | **MFA SHOULD Trigger** | No MFA Trigger | **Session Bypass:** System re-used the existing valid **MFA Claim/Token** from a previous session, satisfying the grant requirement. |

### Phase 2: Implementing Session Controls

The policy was modified to include the **Session Control: Sign-in Frequency set to "Every time"**. This forces re-authentication and re-evaluation of the MFA requirement, overriding the token validity.

| Test Condition | Expected Result | Actual Result | Policy Validation |
| :--- | :--- | :--- | :--- |
| **Trusted Network** (Home Wi-Fi) | MFA Trigger | MFA Trigger | Proved the **Sign-in Frequency** control was active (it forces the check, regardless of location). |
| **Untrusted Network** (Hotspot) | MFA Trigger | **MFA Trigger** | **Success:** The combination of an **Untrusted Location** and the **Session Control** successfully enforced the required MFA prompt. |

## 🚀 Conclusion

The successful implementation demonstrates that effective Conditional Access relies not only on defining **conditions** and **grants** but also on layering in granular **session controls** to prevent security bypasses via credential token reuse. The Sign-in Logs were instrumental in diagnosing the initial session-related failure.

---

[Your Email Address]

Project Link: [https://github.com/YourUsername/YourRepoName]
