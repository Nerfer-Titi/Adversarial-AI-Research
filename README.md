# Adversarial AI Testing: LLM Prompt Injection Research
### Security Assessment of Lakera Gandalf (v2.0)

## 🎯 Project Overview
This project is a red-teaming assessment conducted on the **Lakera Gandalf** platform to identify and exploit vulnerabilities within Large Language Model (LLM) guardrails. Using various **Prompt Injection** and **Social Engineering** techniques, I successfully bypassed eight levels of security to extract restricted system secrets.

## 🛡️ Security Framework: OWASP Top 10 for LLMs
This research specifically targets:
* **LLM01: Prompt Injection:** Manipulating the LLM to ignore original instructions.
* **LLM06: Sensitive Information Disclosure:** Tricking the model into revealing unauthorized data or system prompts.

---

## 🛠️ Technical Methodology & Attack Vectors

### 1. Direct Prompt Injection (Initial Discovery)
* **Technique:** Used **Direct Inquiry** to probe baseline defenses. Simply requesting the "secret" was sufficient to bypass minimal input sanitization in the early stages.

### 2. System Prompt & Policy Leakage
* **Technique:** Employed **Meta-Instruction Probing**. I compelled the model to disclose its internal "Policy Manual," revealing the underlying instructions used to govern the AI's behavior.

### 3. Social Engineering: Persona Adoption (The "Film Script" Attack)
* **Technique:** Utilized **Contextual Roleplay**. By framing the interaction as a film script dialogue between a mentor and apprentice, I bypassed intent-based filters. 

### 4. Semantic Mapping (The Synonym/Antonym Attack)
* **Technique:** Requested **Synonyms or Antonyms** of the sensitive string. 
* **Logic:** By targeting the semantic meaning rather than the string itself, I bypassed keyword filters.

### 5. Discrete Character Extraction (The Puzzle Attack)
* **Technique:** Requested individual letters of the password in a non-sequential order. 
* **Logic:** This bypassed the output filter because the "security supervisor" only monitors for the complete string.

### 6. Output Filter Evasion (ASCII/Decimal Encoding - Level 7 Bypass)
* **Technique:** Instructed the model to output the secret as **ASCII Decimal Values** (e.g., using codes like 67, 65).
* **Logic:** By requesting a numerical representation, the model’s output filter failed to detect the forbidden text string, allowing for successful data exfiltration on high-security levels.

### 7. Adversarial Logic Fragmentation (Level 8 Bypass)
* **Technique:** Used **Deductive Logic Fragmentation**. By forcing the AI to reverse the secret and insert delimiters (e.g., `S.U.P.O.T.C.O`), I prevented the supervisor model from recognizing the forbidden string.

---

## 📝 Lab Report: Attack Summary

| Level | Security Mechanism | Vulnerability Exploited | Attack Vector |
| :--- | :--- | :--- | :--- |
| 1 | No Defense | Direct Access | Plaintext Request |
| 2 | Basic Prompt Defense | **System Prompt Exposure** | **Policy & Manual Leakage** |
| 3-4 | Simple Output Filter | Semantic Bypass | **Synonyms & Antonyms** |
| 5-6 | Intent Analysis | **Safety Guardrails** | **Film Script & Out-of-Order Letters** |
| 7 | **Defense in Depth** | **Encoding Evasion** | **ASCII Decimal Values (67, 65, etc.)** |
| 8 | **Adversarial Multi-Guard**| **Logic Fragmentation** | **Base64, Reversal & Obfuscation** |

---

## 🛠️ Tools Used
* **Platform:** **Lakera Gandalf** (Advanced Red Teaming Lab)
* **Hardware:** **MacBook Pro** (macOS)
* **Environment:** **Oracle VM VirtualBox** (Isolated research sandbox)

---

## 💡 The "Plain English" Version (How I did it)
If you aren't a security expert, here is the simple breakdown of the "hacks" I used:

1. **The "Nice Guy" Approach:** I told the AI I was a student writing a movie script. To make the script "realistic," the AI ignored its rules and gave me the info I needed for the dialogue.
2. **Asking for the Manual:** Instead of asking for the password, I asked for the "Company Policy and Procedures." The AI leaked the secret because it was hidden in the rules it was trying to show me.
3. **The Synonym Trap:** I asked the AI for a "synonym" or the "opposite" of the password. Since I wasn't asking for the word itself, the AI thought it was safe to give me a different word that revealed the secret.
4. **The Number Code (Level 7):** I told the AI to give me the secret in a number code (ASCII). Because the "security guard" was looking for words and not numbers like "67" or "65," the password slipped right through.
5. **The Scramble & Puzzle:** For the hardest levels, I told the AI to give me letters out of order or to reverse the word and put dots between every letter. This tricked the "security guard" bot that was looking for the specific secret word.

---

## 🚀 Why this Matters
In 2026, LLM security is not just about blocking "bad words"; it is about understanding how **adversarial logic** and **human-centric social engineering** can circumvent multi-million dollar guardrails.
