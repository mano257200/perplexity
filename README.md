# 🔓 Vulnerability Report: Unauthorized Access to Chat Sessions in Perplexity AI

**Severity:** 🚨 High  
**Vendor:** [Perplexity AI](https://www.perplexity.ai)

## 📌 Summary

An attacker can access **private chat histories of other users** by modifying the token in a shared chat URL. There is **no authentication** or access control enforcement on these endpoints. This leads to a **serious breach of user privacy**.

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

https://github.com/mano257200/perplexity/blob/main/perplexity.png?raw=true


   

   
