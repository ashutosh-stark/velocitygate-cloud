# velocitygate-cloud

A waitlist landing page for VelocityGate Cloud — the zero-latency AI firewall.

## Email Submission Setup

Submitted emails are saved to `waitlist/emails.txt` in this repository via a GitHub Actions workflow triggered by a `repository_dispatch` event. No external backend is required.

### Steps to enable email collection

1. **Create a fine-grained Personal Access Token (PAT)**
   - Go to **GitHub → Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**.
   - Set **Repository access** to only `velocitygate-cloud`.
   - Under **Permissions → Repository permissions**, set **Contents** to **Read and write**.
   - Copy the generated token.

2. **Replace the placeholder token in `index.html`**
   ```js
   const GITHUB_TOKEN = 'YOUR_GITHUB_PAT_HERE'; // replace this value
   ```
   Paste your PAT in place of `YOUR_GITHUB_PAT_HERE`.

3. **Deploy the site** (e.g. GitHub Pages from the `main` branch).

When a visitor submits their email, the page calls the GitHub API to trigger the `save-email` workflow, which appends the email address to `waitlist/emails.txt` and commits the change automatically.
