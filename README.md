# Billable Task & Call Tracker

A lightweight, single-file HTML tool designed to streamline the process of calculating billable hours from task lists and phone calls. 

This tool is optimized for **European number formats** (using commas for decimals) and allows for rapid generation of ticket summaries for billing systems.

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![Tech](https://img.shields.io/badge/stack-HTML%20%2F%20JS%20%2F%20XLSX-orange.svg)

## 🚀 Key Features

* **Excel Import:** Drag-and-drop support for `.xlsx` and `.xls` files.
* **Smart Grouping:** Automatically organizes tasks into accordion dropdowns based on group names.
* **Call Converter:** Converts raw minutes (Base 60) into billable decimal hours (Base 100).
    * *Example: 15 minutes → 0,25*
* **Dual Descriptions:** Supports an internal `TaskName` for you (the user) and a formal `OutputString` for the client/invoice.
* **Manual Edit Mode:** The summary text box is fully editable. If you make a manual change, the app pauses auto-updates to preserve your text.
    * Includes a **"Revert to Auto"** button to discard changes and re-sync with checkboxes.
* **Rounding Logic:**
    * **Actual Total:** The exact mathematical sum of all selected tasks.
    * **Billable Total:** Rounded up to the nearest 0.25 increment.

## 📋 Data Preparation (Excel)

To use the tool, your Excel file must follow this structure. The headers are case-insensitive.

| Column Header | Description | Required | Example |
| :--- | :--- | :--- | :--- |
| **TaskName** | The name displayed in the list (for your reference). | **Yes** | `Password Reset` |
| **TaskValue** | The time value (supports `.` or `,`). | **Yes** | `0,25` |
| **TaskGroup** | Groups tasks into a dropdown folder. | No | `Security` |
| **OutputString** | The formal text used in the final summary copy. | No | `Executed standard password reset procedure` |

> **Note:** If `OutputString` is blank, the tool will fallback to using `TaskName` in the final summary.

## 🛠️ How to Use

1.  **Open the App:** simply double-click `index.html` in your browser. No server or installation required.
2.  **Load Data:** Drag your Excel file into the drop zone.
3.  **Ticket Reference:** Enter the Ticket Number (e.g., `INC-1029`).
4.  **Select Tasks:**
    * Use the **Search Bar** to find tasks (filters both task names and group names).
    * Click checkboxes to add items to the total.
5.  **Add Calls (Optional):**
    * Switch to the **Call Converter** tab.
    * Enter minutes and the person's name.
    * Click **Add Call** to push it to the calculation.
6.  **Copy Summary:**
    * Review the text in the bottom box.
    * (Optional) Manually edit the text if needed.
    * Click **COPY STRING** to paste it into your ticketing system.

## ⚙️ Technical Details

* **Privacy:** This tool runs 100% client-side. No data is ever uploaded to a server.
* **Dependencies:** Uses [SheetJS (xlsx)](https://sheetjs.com/) via CDN to parse Excel files.
* **Localization:** Hardcoded to output decimals with commas (`,`) for European system compatibility.

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
