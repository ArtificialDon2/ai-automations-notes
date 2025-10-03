# N8N basics

## JSON
- A finished workflow in n8n can be **exported as a JSON file**.  
- Think of JSON as a **portable copy** or **blueprint** of your workflow — it stores all the nodes, connections, and settings in text form.  
- You don’t need JSON for everyday use. It’s mainly for:  
  - **Backing up** your workflows  
  - **Sharing** them with others  
  - **Moving** them to another n8n setup  
- When imported, JSON instantly **recreates the same workflow** in n8n.  

---

## Webhooks
- A **webhook** is like a **doorbell** for your workflow.  
- It gives your workflow a **public URL**. When something "rings" that URL (like a form submission or another app sending data), the workflow starts.  
- Webhooks are useful when:  
  - The platform you want to connect to isn’t natively supported in n8n  
  - You need your workflow to react instantly to outside events  

---

## OAuth, Client ID & Client Secret
- To connect apps like Gmail, n8n uses **OAuth2**.  
- Think of it as n8n showing Google an **ID card** and a **password** before being allowed in.  
  - **Client ID** → the *public name tag* of your app (tells Google "this is n8n").  
  - **Client Secret** → the *private password* that proves the app really is n8n.
- In n8n Cloud, the Client ID/Secret are already preconfigured, so you just click Sign in with Google.

---

## DebugHelper
 - Lets you **see the exact data** flowing through at that point.  
- Modes:  
  - **Throw Error** → Stops the workflow so you can inspect the data.  
  - **Log Output** → Shows the data but lets the workflow continue.  
  - **Nothing** → Ignores the data (useful if you leave it in production).  
- Debug is useful when:  
  - You’re not sure if earlier nodes are outputting the data you expect  
  - An HTTP Request or Function node keeps failing and you need to check inputs