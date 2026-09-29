# 🎓 Certigo - Enterprise-Grade Bulk Certificate Generator

**Certigo** is a powerful, robust, and highly optimized C# Windows Forms desktop application designed to automate the mass production of customized certificates. Whether you are generating 10 or 10,000 certificates, Certigo handles it with dynamic templates, smart data parsing, and seamless Google Drive cloud synchronization.
 <!-- Replace with actual screenshot later -->

## ✨ Key Features

### 🚀 Core Generation Engine
*   **Mass PDF Generation:** Blazing fast local PDF rendering using `iText7`.
*   **Dynamic Templating (Per-Participant):** Swap front and back certificate backgrounds dynamically based on CSV data (e.g., Gold template for 1st Place, Standard template for participants).
*   **Smart Duplicate Handling:** Automatically resolves identical names by appending numbers (e.g., `John Doe.pdf`, `John Doe (2).pdf`), preventing accidental file overwrites.
*   **Dynamic File Naming:** Define output file names using smart tags like `[Name]_[CertNumber]`.
*   **Digital Signatures:** Integrated `SignatureService` to apply digital signatures to generated PDFs.

### 📊 Advanced Data Handling
*   **Enterprise CSV State Machine:** A custom-built, highly resilient CSV parser that is immune to Excel copy-paste formatting errors, regional delimiter conflicts (commas vs. semicolons), and multi-line paragraph text.
*   **Auto-Migration:** Automatically updates legacy CSV structures to the latest format without losing user data.
*   **Smart Data Cleansing:** Automatically formats and capitalizes participant names.

### ☁️ Cloud Integration & UX
*   **Google Drive Sync:** Automatically authenticate and upload generated certificates to a shareable Google Drive folder.
*   **Real-time Analytics:** Displays upload speed (MB/s or KB/s), estimated time of arrival (ETA), and byte-level progress.
*   **Graceful Cancellation:** A highly responsive `Stop` button utilizing `CancellationTokenSource` allows users to safely abort mass generation/upload processes midway.
*   **Taskbar Integration:** Windows Taskbar progress bar support (`Microsoft.WindowsAPICodePack`).
*   **Seamless Auto-Updates:** Built-in GitHub Releases checker. Notifies users of new versions and silently upgrades the application via `.msi` installers.

---

## 📥 Installation

1. Go to the [Releases page](../../releases) on this repository.
2. Download the latest `CertigoInstaller.msi` file.
3. Run the installer and follow the on-screen instructions.
4. Launch **Certigo** from your Windows Start Menu!

*(Certigo features an internal Auto-Update engine, so you will always be prompted when a new version is available!)*

---

## 🛠️ How to Use

### 1. Load Your Template
Click **Load Template** to select your base certificate design (JPG/PNG). The live preview canvas allows you to drag, resize, and align the `Name`, `Certificate Number`, and `Body` text directly on the image.

### 2. Prepare Your Data (CSV)
Click **Load/Edit CSV** to open the data source. Certigo uses a strict 5-column layout:
```csv
Name,CertNumber,Body,Template,BackPageTemplate
John Doe,CERT-001,Has completed the training,,
Jane Doe,CERT-002,Has completed the training,C:\Templates\Gold.jpg,C:\Templates\Gold_Back.jpg
```
*   **Template / BackPageTemplate (Optional):** Provide a local file path to dynamically override the default design for specific individuals.

> **💡 Pro Tip for Complex Body Text:** 
> Do not hardcode complex logic into the CSV manually. Use an **Excel Master File** with formulas like `=TEXTJOIN(...)` and `=IF(...)` to generate dynamic paragraphs, then simply Copy-Paste the final values into Certigo's CSV file!

### 3. Generate & Upload
*   Define your preferred **File Naming Format** (e.g., `[CertNumber] - [Name]`).
*   Check **Upload to Google Drive** if you want cloud synchronization.
*   Click **Generate**. Sit back and watch the progress bar!

---

## 📄 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
