# Troubleshooting Library

## 1. HTTP Request Node Offline
**What happened:** Kept getting “offline” even though Ollama was running.  
**Why:** n8n was inside Docker. When we used localhost, it was pointing inside the container, not our machine. 
**Fix:** Use `host.docker.internal` instead of `localhost` in the URL:
 - Example: `http://host.docker.internal:11434/v1/models`

---

## 2. Port Already in Use (Ollama Error)
**What happened:** Ollama refused to start because port 11434 was busy.
**Why:** An old Ollama process was still running in the background.
**Fix:**
 - `ollama list     # shows installed models`
 `ollama run <model-name>   # starts the model you want`
 - Check with `netstat -ano | findstr 11434` (if we're not sure what's hogging the port)
 - Find the process in Task Manager and kill it.
 - Restart Ollama with `Ollama serve`.

---

## 3. Undefined Property / `trim` Error
**What happened:** The Gmail node expected text, but Ollama returned nothing.  
**Why:** We hadn’t given Ollama a proper prompt, so no output existed. 
**Fix:** We told n8n:
 | “If Ollama gives you a reply, use it. But if it’s empty, just say No response generated.”
 The actual fix looked like this:
{{$node["HTTP Request"].json["results"]?.[0]?.["output"] || "No response generated"}}
It means:
 - Look inside the HTTP Request node.
 - Try to grab the first result’s output.
 - If it’s not there → just show “No response generated” instead of breaking.

---

---

## 4. Bad request (Gmail Send Message)
**What happened:** Gmail threw a "Bad Request" error.
**Why:** Improperly formatted "To" field.
**Fix:**
 - Make sure the form field name matches (e.g. `email`).
 - Reference it like:
    `{{$json["email"]}}`
 - Double-check capitalization and spelling.

---

## 5. 