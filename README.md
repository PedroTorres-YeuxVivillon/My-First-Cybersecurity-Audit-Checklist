# Basic Website Security Audit Checklist
*Created by: Pedro Torres*  
*Last Updated: [06/25/2025]*

## 📋 Introduction
This is my first attempt at creating a security checklist after studying cybersecurity basics. I'm focusing on common web vulnerabilities I've learned about recently. This checklist helps me systematically review basic website security.

## 🎯 How I Use This
- [✅] Go through each item one by one
- [✅] Take notes in the "My Findings" column
- [✅] Research anything I don't understand
- [✅] Learn from what I find!

## 🔍 The Checklist

### 1. HTTPS & Encryption
| Check | What to Look For | My Status | My Findings |
|-------|------------------|-----------|-------------|
| HTTPS in URL | Check if website uses `https://` instead of `http://` | [✅] | Site uses HTTPS by default; redirects from HTTP to HTTPS correctly.|
| Padlock Icon | Look for lock symbol in browser address bar | [✅] |Padlock visible; SSL certificate valid and issued by Let's Encrypt. |
| Mixed Content | Check browser console for "mixed content" warnings | [⚠️] | Found one insecure image (HTTP link); all other elements load securely.

### 2. Password Security
| Check | What to Look For | My Status | My Findings |
|-------|------------------|-----------|-------------|
| Password Strength | Test if weak passwords like "123456" are accepted | [❌] |Weak passwords accepted without any warnings; needs stronger password policy. |
| Common Passwords | Try passwords from top 10 common passwords list | [❌] |Accepted “password123” successfully, potential vulnerability. |

### 3. Input Validation
| Check | What to Look For | My Status | My Findings |
|-------|------------------|-----------|-------------|
| SQL Injection | Try entering `' OR '1'='1` in login fields | [❌] |Login bypassed with this input, vulnerable to SQL injection. |
| XSS Test | Try `<script>alert('test')</script>` in search boxes | [⚠️] |Script tag sanitized, but HTML encoding incomplete (alert didn’t trigger). Needs stricter input filtering. |

### 4. Information Disclosure
| Check | What to Look For | My Status | My Findings |
|-------|------------------|-----------|-------------|
| Error Messages | Look for technical details in error messages | [⚠️] |Some forms return raw SQL errors; could expose database structure. |
| Directory Listing | Check if `/uploads/` or `/images/` shows file lists | [✅] |Directory listing disabled, returns “403 Forbidden.” |

## 🛠️ Tools I'm Learning To Use
- **Browser Developer Tools** (F12) - for checking console errors
- **Nmap** - for scanning open ports (just learned the basics)
- **BuiltWith** - to see what technology the site uses

## 📝 Example Test I Did

**Website:** my-test-blog.com

**What I tried:**
- Checked for HTTPS: ✅ Yes, it has a padlock!
- Tested SQL injection: ❌ The login form accepted `' OR '1'='1` and let me in!
- Looked for error messages: ✅ Got a database error when I entered special characters

**What I learned:** This site needs input validation to prevent SQL injection attacks.



## ⚠️ Important Note
I only test websites I own or have explicit permission to test. I'm learning responsible security practices
This report was created based on Module I of the Google Cybersecurity Certificate from Coursera, along with my own notes. No Ai was used during the execution of this activity; After completion Grammar and syntax was reviewed with AI(DeepSeek).


---

*This checklist represents my current understanding as a beginner.*
