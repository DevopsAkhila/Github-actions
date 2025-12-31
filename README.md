Exercise 3: Reusable Workflow for Vercel Deployment
Agenda:

Create a reusable workflow for deploying a static site to Vercel.
Call it from a caller workflow with inputs (e.g., project ID).
Handle failures with notifications (e.g., Slack webhook via secret).
Objectives: Modularize actions, pass parameters, integrate external services.

Expected Steps:

Create a simple static site (HTML/JS).
In Vercel dashboard, create a project linked to your repo (get Project ID from settings).
Add secret VERCEL_TOKEN (from Vercel integrations) and SLACK_WEBHOOK (dummy: "https://hooks.slack.com/...").
Implement reusable workflow in .github/workflows/reusable-deploy.yml (outputs success/fail).
Caller workflow in .github/workflows/deploy-site.yml: Triggers on PR, calls reusable with input.
Push/PR; check Vercel deploys and Slack sim (logs echo webhook call).
Experiment: Pass invalid input, observe error propagation.
