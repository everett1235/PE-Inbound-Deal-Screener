# PE Inbound Deal Screener

An automated, AI-driven inbound deal flow screening pipeline designed specifically for Private Equity (PE) firms and venture capital funds. This workflow monitors a designated inbound folder for incoming pitch decks, extracts the raw text data, passes it to an enterprise-grade AI model acting as a PE Associate, and delivers structured investment insights directly to your inbox.

Built as an automated blueprint deployable on **Make.com**.

---

## 🚀 Features

- **Automated Inbound Monitoring:** Watches a specific Google Drive folder (`01_Inbound_Pitch_Decks`) for newly modified or uploaded Google Docs pitch decks[cite: 1].
- **Deep Text Extraction:** Dynamically fetches document structures and extracts granular text metadata safely[cite: 1].
- **AI Investment Associate:** Leverages **Gemini 3.5 Flash** with rigid system instructions to parse text with extreme precision, avoiding data hallucinations[cite: 1].
- **Structured Metric Extraction:** Delivers unified reporting on key parameters:
  - Company Name & Industry Sector[cite: 1]
  - Target Raise Amount[cite: 1]
  - Key Team/Founders[cite: 1]
  - Investment Thesis Highlights & Red Flags[cite: 1]
- **File Lifecycle Management:** Appends a `Processed - ` prefix to analyzed docs to maintain pristine folder hygiene[cite: 1].
- **Instant Alerts:** Pushes fully styled HTML digests directly to investment team emails immediately upon analysis completion[cite: 1].
- **Enterprise-Grade Error Handling:** Features built-in automatic retries and break protocols to safeguard against API limits or transient system dropouts[cite: 1].

---

## 🛠️ System Architecture & Workflow Flow

The Make.com scenario executes sequentially across 5 core nodes:


```

[Google Drive: Watch] ➔ [Google Docs: Get Text] ➔ [Gemini AI: Analyze] ➔ [Google Drive: Rename] ➔ [Gmail: Alert]

```

1. **Watch Files in a Folder (ID 5):** Checks for Google Docs inside the `PE Deal Flow Pipeline/01_Inbound_Pitch_Decks` directory[cite: 1].
2. **Get a Document (ID 9):** Extracts the target document contents dynamically based on the mapped ID from Step 1[cite: 1].
3. **Create a Completion (ID 3):** Routes content into the Gemini 3.5 Flash engine configured with expert PE heuristics[cite: 1].
   - *Error Handler (ID 15):* Automatically triggers a 3-try retry sequence spaced 5 minutes apart if an inference fault occurs[cite: 1].
4. **Update a File (ID 14):** Appends `Processed - ` to the original filename so it isn't evaluated multiple times[cite: 1].
5. **Send an Email (ID 10):** Dispatches the cleanly structured markdown/text summary as raw HTML to the fund's deal-flow inbox[cite: 1].

---

## 📋 AI Prompt & Guardrails

The processing engine runs under a strict behavioral persona constraint:

> **System Instruction:** 
> *"You are an expert Private Equity Investment Associate specializing in inbound deal flow screening and processing pitch decks. Your goal is to analyze the text content of an incoming pitch deck and extract structured investment data with extreme precision. Maintain a sharp, analytical, and highly professional tone. Do not hallucinate data; if a piece of information is missing from the document text, explicitly state 'Not Provided'."*[cite: 1]

---

## ⚙️ Setup & Deployment

### Prerequisites
* A verified **Make.com** account (hosted on `us2.make.com` or your native zone)[cite: 1].
* Google Workspace connection with access to Google Drive and Gmail[cite: 1].
* An active API Connection configured for Gemini AI[cite: 1].

### Installation Steps
1. Create a folder hierarchy in your Google Drive named: `PE Deal Flow Pipeline/01_Inbound_Pitch_Decks`[cite: 1].
2. Create a new scenario in Make.com.
3. Click the three dots menu at the bottom toolbar, select **Import Blueprint**, and upload the raw JSON file provided in this repository[cite: 1].
4. Re-authorize the following standard connections when prompted:
   - Google Drive connection[cite: 1]
   - Google Docs connection[cite: 1]
   - Gemini AI connection[cite: 1]
   - Gmail connection[cite: 1]
5. Update the recipient email address in the final **Gmail** module (ID 10) to point to your internal team distribution alias[cite: 1].
6. Switch the scheduling toggle to **ON**.

---

## 📄 License
This workflow architecture is open-source software licensed under the MIT License.

```
