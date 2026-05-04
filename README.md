# Phishing-email-analysis


## Overview
This project documents my analysis of real-world phishing emails.  
The goal is to identify Indicators of Compromise (IOCs) and understand  
the social engineering tactics attackers use.

## Skills demonstrated
- Email header analysis
- IOC identification
- Social engineering awareness
- Threat documentation

---

## Sample 1 — Fake PayPal Alert

**Subject:** Your account has been limited — action required  
**Sender (displayed):** service@paypal.com  
**Sender (actual):** noreply@paypa1-secure.ru  

### What I found
| Indicator | Finding |
|---|---|
| Sender domain | Spoofed — "paypa1" with a number 1 instead of letter l |
| Urgency language | "Your account will be suspended in 24 hours" |
| Suspicious link | hxxp://paypal-secure-login.ru/verify (defanged) |
| Grammar issues | "Please to verify your informations immediately" |
| Attachment | None |

### Verdict
Phishing. Spoofed sender domain + urgency tactics + non-PayPal URL.

---

## Sample 2 — Fake IT Help Desk

**Subject:** URGENT: Reset your password now  
**Sender (displayed):** IT Support  
**Sender (actual):** itsupport@company-helpdesk.xyz  

### What I found
| Indicator | Finding |
|---|---|
| Sender domain | Not a real company domain — generic .xyz |
| Urgency language | "URGENT" in subject + "within 1 hour" in body |
| Suspicious link | hxxp://resetpassword-now.xyz/login |
| Request type | Asking for current password via email — red flag |
| Impersonation | Pretending to be internal IT team |

### Verdict
Spear phishing attempt. Targets employees by impersonating IT support.

---

## Sample 3 — Fake Microsoft 365 Login

**Subject:** Your Microsoft account sign-in was blocked  
**Sender (displayed):** Microsoft Account Team  
**Sender (actual):** no-reply@micros0ft-alerts.com  

### What I found
| Indicator | Finding |
|---|---|
| Sender domain | "micros0ft" — zero instead of letter o |
| Link destination | hxxps://microsoft-login-verify.net (not microsoft.com) |
| Visual spoofing | Email design mimics official Microsoft branding |
| Goal | Steal Microsoft 365 credentials |

### Verdict
Credential harvesting phishing. Classic brand impersonation attack.

---
## Sample 4 — Fake Casino Rewards Promotion

**Subject:** 🎰 Congratulations! You've been selected for an exclusive reward  
**Sender (displayed):** Casino Rewards VIP Team  
**Sender (actual):** vip-rewards@casinorewards-claim.net  

### What I found
| Indicator | Finding |
|---|---|
| Sender domain | Not official — "casinorewards-claim.net" vs real "casinorewards.com" |
| Urgency language | "Claim your reward within 48 hours or it expires" |
| Suspicious link | hxxp://casinorewards-vip-claim.net/collect?id=928471 |
| Too-good offer | "You've won $500 in free credits — no deposit needed" |
| Personal info request | Asks for full name, address, and credit card to "verify identity" |
| Attachment | None — all credential theft via link |
| Impersonation | Copies Casino Rewards branding and colour scheme |

### Social engineering tactics used
| Tactic | Example in this email |
|---|---|
| Greed trigger | Promise of free $500 credits |
| Urgency | 48-hour expiry countdown |
| Authority | Fake "VIP Team" sender name |
| Familiarity | Mimics a brand the target already trusts |

### What a real Casino Rewards email looks like
- Sent from @casinorewards.com only
- Never asks for credit card to claim free credits
- Links go to casinorewards.com — not third-party domains
- No unsolicited "you've been selected" prize emails

### Verdict
Phishing — credential and financial data harvesting. Attacker uses  
brand trust combined with greed and urgency to trick loyalty program  
members into handing over personal and payment information.

---

## IOC Summary Table

| Sample | Tactic | Domain Spoof | Urgency | Data Targeted |
|---|---|---|---|---|
| PayPal | Account suspension | paypa1-secure.ru | 24 hrs | Login credentials |
| IT Help Desk | Internal impersonation | company-helpdesk.xyz | 1 hr | Password |
| Microsoft 365 | Brand impersonation | micros0ft-alerts.com | None | M365 credentials |
| Casino Rewards | Prize/greed lure | casinorewards-claim.net | 48 hrs | Payment + personal info |

## Key Takeaways
- Always check the actual sender domain, not the display name
- Urgency and fear are the most common social engineering triggers
- Legitimate companies never ask for passwords via email
- Defang URLs before sharing them (replace http with hxxp)
- Typosquatting domains are a major red flag (paypa1, micros0ft)

## Tools & References
- [MXToolbox Email Header Analyzer](https://mxtoolbox.com/EmailHeaders.aspx)
- [VirusTotal URL Scanner](https://www.virustotal.com)
- [PhishTool](https://www.phishtool.com)
- ISC2 CC Domain 1 — Security Principles
- Cisco CyberOps — Threat Analysis module
