# To-Do Task Automation

A complete Python automation tool that extracts task data and automatically generates scheduled, repeating tasks in Microsoft To Do. 

This project utilizes the **Microsoft Graph API** to seamlessly create distinct task lists, assign specific due dates, and apply custom recurrence rules (daily, weekly, etc.)

## Project Structure
This repository has a Script (`todo_sync.py`)**: The core automation script that reads the parsed JSON file and pushes the tasks to Microsoft To Do via the Graph API.

## Features
* **Automated List Creation:** Automatically checks for existing To Do lists (Areas) and creates them if they do not exist.
* **Custom Recurrence:** Supports "daily", "weekly", "monthly", "yearly", or one-time tasks.
* **Timezone Support:** Properly formats due dates using the Microsoft Graph API standards.
* **Secure Authentication:** Uses the Microsoft Authentication Library (MSAL) and environment variables to keep credentials safe.

## Setup Instructions

### 1. Microsoft Azure Setup
To use the Microsoft Graph API, you need to register a free app in Azure:
1. Go to the Azure Portal and search for **App registrations**.
2. Click **New registration**, name your app, and select "Personal Microsoft accounts only".
3. Under Redirect URI, choose **Public client/native (mobile & desktop)** and enter `http://localhost`.
4. Copy the **Application (client) ID**.
5. Go to **API permissions** -> **Add a permission** -> **Microsoft Graph** -> **Delegated permissions** and add `Tasks.ReadWrite`.

### 2. Local Installation
Clone this repository and install the required Python libraries:
```bash
git clone <your-repository-url>
cd <your-repository-folder>
pip install -r requirements.txt

### 3. Environment Configuration
Create a .env file in the root directory. Add your copied Client ID:
CLIENT_ID=your_client_id_here
(Note: Ensure your .gitignore includes the .env file so your credentials are never uploaded to GitHub).

## Important Data Security Warning
**Never commit your personal tasks, app ideas, or private data to GitHub.** 
This repository is configured to ignore the `tasks.json` file. If you build your own data extraction scripts (e.g., pulling data from any Tasks App), ensure those script folders and raw data files are added to your `.gitignore` before committing.



Usage Guide
Step 1: Extract and Format Data
If you are converting external data, run your Pandas script to generate a tasks.json file in the root directory. The JSON format must look like this:

JSON:
[
    {
        "area": "Development",
        "title": "Review Python Data Structures",
        "due_date": "2026-07-16",
        "recurrence_type": "daily" 
    }
]

Step 2: Run the Automation
Run the main script from your terminal:

Bash
python todo_sync.py

A browser window will open asking you to log into your Microsoft account to authorize the script. Once authorized, the script will automatically create your lists and tasks in Microsoft To Do.


## Disclaimer

This is an independent, individual project and is not affiliated with, endorsed by, or approved by Microsoft. 

Users are strictly advised to conduct their own security research and thoroughly review the code before execution to ensure it meets their safety and privacy requirements. Please test the script on your end to verify it behaves as expected without causing unintended issues. 

Use this tool entirely at your own risk. The creator assumes no liability or responsibility for any data loss, account issues, system disruptions, or other damages that may arise from the use of this Software.