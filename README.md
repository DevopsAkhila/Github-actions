Exercise 2: Conditional Deployment with Secrets and Approvals
Agenda:

Set up a multi-environment deployment (dev/staging/prod) with branch-based conditions.
Use GitHub secrets for sensitive data (e.g., API keys).
Implement manual approval gates for production using environment protections.
Objectives: Secure deployments, enforce reviews, handle job conditions dynamically.

Expected Steps:

Add a dummy deploy script that echoes secrets (don't expose real ones).
In repo Settings > Secrets and variables > Actions, add secrets: API_KEY (value: "dummy-key"), DB_URL (value: "dummy-db").
Write workflow:
Trigger on push to main or develop.
Build job always.
Deploy jobs: Conditional on branch (develop → dev, main → staging/prod).
Prod deploy requires approval (set up in Settings > Environments > "production" with required approvers).

Push to develop (deploys to dev), then main (triggers approval for prod). Approve in Actions tab.
Experiment: Use if conditions wrong, observe skips; test secret exposure (it should mask in logs).
