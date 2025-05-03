# 🔓 Vulnerability Report: Unauthorized Access to Chat Sessions in Perplexity AI

**Severity:** 🚨 High  
**Vendor:** [Perplexity AI](https://www.perplexity.ai)

## 📌 Summary

Perplexity AI includes chat tokens directly in the URL when users share chat sessions. These tokens are not protected by authentication or expiration controls. As a result, anyone who captures the URL (and its token) can access the full chat history — even outside the original session.\

---

## ⚠️ Vulnerability Details

- The chat token is embedded in the URL as a GET parameter.
- URLs are accessible to anyone who has the link — with no authentication.
- The token can be captured or leaked via:
- Network sniffing tools like Wireshark on unsecured networks
- Browser history
- Referrer headers when links are clicked from other sites
- Shared clipboard misuse
- Proxy logs, DNS logs, etc.

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

- Full unauthorized access to another user's private chat data.
- Potential exposure of personal or sensitive information.
- Non-expiring, predictable links increase exploitability.
- **Possible violation of data privacy laws**, such as:
- General Data Protection Regulation (GDPR)
- California Consumer Privacy Act (CCPA)

---

## ⚠️ Severity

**HIGH**  
This vulnerability allows data leakage across accounts and users with no validation. The simplicity of exploitation increases its impact.

---

## 🧪 Proof of Concept (PoC)

- Performed successfully in **incognito mode**.
- No login required to retrieve another user's chat via token.
- Confirmed repeatable with multiple valid tokens.

![PoC Screenshot](https://github.com/mano257200/perplexity/blob/main/POC-Perplexity.png?raw=true)


   

   
