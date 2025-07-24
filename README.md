# 🎓 Academic Stack Planner (n8n Workflow)

An automated academic planning tool designed to generate personalized, semester-specific roadmaps for tech students. Powered by **n8n** and **Google Gemini**, this workflow emails a complete plan and schedules every task directly into your Google Calendar.

## 🤔 Why This Project?

Students often struggle to structure their learning, especially when tackling a new tech stack. This tool solves that problem by providing a clear, actionable, and time-bound 6-month roadmap. It bridges the gap between ambition and execution by automating the entire planning process, from generation to scheduling.

---

## ✨ Key Features

-   **🤖 AI-Powered Planning**: Leverages Google Gemini to create a detailed 6-month academic roadmap for any chosen tech stack (AI/ML, Full Stack, Cybersecurity, etc.).
-   **📧 Automated Email Delivery**: Instantly sends the personalized roadmap in a clean, readable HTML format directly to the student's inbox.
-   **🗓️ Smart Calendar Integration**: Automatically parses the roadmap and adds each task as a distinct event in Google Calendar, spread evenly over the semester.
-   **🔧 Fully Customizable**: Built on n8n's visual workflow editor, making it easy to adapt the prompt, schedule, or integrations.

---

## 🛠️ Tech Stack

-   **Workflow Automation**: **n8n** (Cloud or Self-Hosted)
-   **AI Content Generation**: **Google Gemini API**
-   **Email Automation**: **Gmail API**
-   **Scheduling**: **Google Calendar API**

---

## ⚙️ How It Works

1.  **📝 Student Input**: The workflow is triggered when a student fills out a form with their name, year, desired tech stack, and current skill level.
2.  **🧠 AI Generation**: Gemini AI receives the input and generates a comprehensive semester roadmap, formatted in clean HTML.
3.  **📨 Email Dispatch**: A code node extracts the student's email and the HTML roadmap. Gmail then sends the personalized plan.
4.  **📅 Calendar Scheduling**: Another code node processes the roadmap, splitting it into individual tasks. Each task is then created as an event in Google Calendar, scheduled sequentially across the semester.

---

## 🚀 Getting Started

### Prerequisites

-   An active **n8n** instance (either [n8n Cloud](https://n8n.io/cloud/) or a [self-hosted](https://docs.n8n.io/hosting/installation/) version).
-   A **Google Account** to create API credentials for Gemini, Gmail, and Google Calendar.

### 1. Import the Workflow

1.  Clone this repository or download the `academic_stack_planner_email_updated.json` file.
2.  In your n8n dashboard, navigate to **Workflows** and click the **Import from File** button.
3.  Upload the `.json` file. The workflow will appear in your editor.

### 2. Configure Credentials

You must connect your Google accounts to n8n. Create credentials by navigating to the **Credentials** tab in your n8n sidebar.

| Service | Credential Type | Required Scopes | Setup Guide |
| :--- | :--- | :--- | :--- |
| **Gmail** | `Gmail OAuth2` | `https://www.googleapis.com/auth/gmail.send` | [Google Cloud Console](https://console.cloud.google.com/) |
| **Google Calendar** | `Google Calendar OAuth2`| `https://www.googleapis.com/auth/calendar` | [Google Cloud Console](https://console.cloud.google.com/) |
| **Gemini AI** | `Google Gemini` | N/A | [Google AI Studio](https://aistudio.google.com/app/apikey) |

Assign your created credentials to the **Google Gemini**, **Gmail**, and **Google Calendar** nodes in the workflow.

---

## 💡 Sample Input

The workflow can be triggered by a webhook or manual run. It expects a JSON object with the following structure:

```json
{
  "name": "Gaurav",
  "discipline": "B.Tech / B.S",
  "year": "3",
  "stack": "AI/ML",
  "level": "Intermediate",
  "skills": "Python, ML basics",
  "email": "gauravrpjoshi1205@gmail.com"
}
