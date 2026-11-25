# n8n Automation Projects

Portfolio site for my n8n projects. The first project is an **AI Recruitment Screening System**: an application form saves CVs to Google Drive, Gemini scores each CV against the job every hour, candidates get the right email, and an error workflow reports failures.

Live site: https://YOUR-USERNAME.github.io/YOUR-REPO/

## Workflows

| File | Trigger | What it does |
|---|---|---|
| `workflows/recruitment-1-intake.json` | Form | Validates the application, saves the CV to Drive, logs a row with Status `New` |
| `workflows/recruitment-2-ai-screening.json` | Every hour | Reads CVs (PDF text or Gemini OCR), scores them, emails invites or declines, flags borderline cases for HR |
| `workflows/recruitment-3-error-handler.json` | Error + schedules | Logs failures, sends alerts, a daily digest and a queue heartbeat |

## Screening rules

70 or more: interview. 40 to 69: HR decides. Below 40: polite decline.

## Services needed

n8n, Google Sheets, Google Drive, Gmail, Google Gemini API.

## Import steps

1. In n8n, create a folder and import each JSON file.
2. Create Google (Sheets, Drive, Gmail) and Gemini credentials in n8n, then open every node with a warning and pick them.
3. Replace every `YOUR_ID` and `you@example.com` with your own Sheet, Drive folder and email.
4. Set `Recruitment 3 - Error Handler` as the error workflow of workflows 1 and 2.
5. Activate the workflows and use the Production URL of the form.
