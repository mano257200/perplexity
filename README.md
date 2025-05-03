# 🔓Vulnerability Report: Chat Token Exposure & Unauthorized Access in Perplexity AI

**Severity:** 🚨 High  
**Vendor:** [Perplexity AI](https://www.perplexity.ai)

## 📌 Summary

Perplexity AI includes chat tokens directly in the URL when users share chat sessions. These tokens are not protected by authentication or expiration controls. As a result, anyone who captures the URL (and its token) can access the full chat history — even outside the original session.\

---

## 🛠️ Technical Details

### 1. Token Exposure via GET Parameter

- Token is exposed directly in the browser URL (GET request).
- Stored in:
  - Browser history
  - Referrer headers
  - Server logs
  - Network logs
  - Analytics and tracking tools

### 2. No Authentication or Access Control

- Anyone with a valid token can view the chat — **no login or identity check** required.
- Tokens remain permanently valid unless manually deleted.
- No access logging or notification for the original user.

### 3. Leakage Vectors

Tokens can be leaked or intercepted via:
- 🔍 Browser history
- 🔗 HTTP `Referer` headers
- 🌐 Unsecured network traffic (e.g., using Wireshark)
- 📋 Clipboard sharing
- 📁 Proxy or server logs (e.g., NGINX, Cloudflare)
- 🧭 Auto-filled URLs and cached tabs

### 4. No Security Features Present

- ❌ No expiration on shared links
- ❌ No revocation mechanism
- ❌ No rate limiting or brute-force protection
- ❌ No visibility controls or warning to user

---

## 🔗 Affected Endpoint

https://www.perplexity.ai/search/<token>

Example token: hi-RxWG5knCTUurDLABy27PMg


---

##  Steps to Reproduce

1. Log in to your Perplexity AI account (or proceed as a guest).
2. Obtain or observe another user's chat token (e.g., via shared link or recon).
3. Paste a modified URL such as:
   https://www.perplexity.ai/search/hi-RxWG5knCTUurDLABy27PMg
4. Open the link **in incognito mode** (even without being logged in).
5. Observe that the **chat history of another user** is accessible without authentication.

---

## 💥 Impact

- **Unauthorized access** to sensitive chatbot content, including:
  - Legal, medical, or financial questions
  - Personally identifiable information (PII)
  - Corporate or proprietary information
- **Severe privacy breach**, especially if shared unknowingly
- **Regulatory compliance risks**, including:
  - **GDPR** (Article 5, 32 – confidentiality & data minimization)
  - **CCPA** (user data protection and unauthorized access)
---

## ⚠️ Severity

**HIGH**  
This vulnerability allows data leakage across accounts and users with no validation. The simplicity of exploitation increases its impact.

---

## 🧪 Proof of Concept (PoC)

- Performed successfully in **incognito mode**.
- No login required to retrieve another user's chat via token.
- Confirmed repeatable with multiple valid tokens.
- The link is accessed by someone else (via referrer leak, history, logs, etc.).
- The full conversation is visible — **no authentication required**.

![PoC Screenshot](https://github.com/mano257200/perplexity/blob/main/POC-Perplexity.png?raw=true)


   

   
