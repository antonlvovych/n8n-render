# n8n-render

This guide provides detailed instructions for deploying n8n on Render using Docker and PostgreSQL. Follow the steps below to set up and configure n8n.

## Installation Instructions

### 1. Deploy the Service
- Open your [Render Blueprints](https://dashboard.render.com/blueprints).
- Use this repository as a **Blueprint** to create a new web service.
- Render will automatically build and deploy your n8n instance using the `render.yaml` configuration.

### 2. Post-Deployment Configuration
After the service is deployed, configure the following environment variables in the Render dashboard:

- **`N8N_EDITOR_BASE_URL`**  
  Set this to the full URL of your deployed n8n instance (e.g., `https://your-n8n-domain.onrender.com`).

- **`WEBHOOK_URL`**  
  Set this to the same domain as above (e.g., `https://your-n8n-domain.onrender.com`).

- **`GENERIC_TIMEZONE`**  
  Set the default timezone for workflows. Leave it blank or specify a timezone (e.g., `UTC`, `America/New_York`).

#### Steps to Add Environment Variables:
1. Navigate to your service in the Render dashboard.
2. Go to the **Environment Variables** section.
3. Add the variables as described above.

### 3. Restart the Service
After adding the environment variables, restart your web service in the Render dashboard to apply the changes.

### Important Note
Both `N8N_EDITOR_BASE_URL` and `WEBHOOK_URL` are critical for the correct functioning of the n8n editor and webhooks.  
If you change their values, you **must restart the web service** for the changes to take effect.

## Additional Notes

- **Persistent Storage**  
  Ensure the `mountPath` for the disk remains `/home/node/.n8n` to prevent data loss or configuration issues.

- **Testing Webhooks**  
  To ensure webhooks work correctly, the `WEBHOOK_URL` should always match the publicly accessible domain.

## Updating Configuration
If you need to make changes to the configuration (e.g., change the region for the web service or the database), follow these steps:

1. Fork this repository to your own GitHub account.
2. Modify the `render.yaml` file with the required changes.
3. Push the changes to your forked repository.
4. Redeploy the service using the updated repository as the new **Blueprint**.
