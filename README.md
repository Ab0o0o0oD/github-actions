# Send Email via Microsoft Graph API

This GitHub Action sends an email via the Microsoft Graph API with an attachment.

## Inputs

| Name                 | Description                     | Required |
|----------------------|---------------------------------|----------|
| `recipient_email`    | Recipient email address        | ✅       |
| `attachment_path`    | Path to the file to attach     | ✅       |
| `attachment_mime_type` | MIME type of the attachment | ✅       |
| `subject`           | Email subject                  | ✅       |
| `body_content`      | Email body content             | ✅       |

## Usage

```yaml
jobs:
  send-email:
    runs-on: ubuntu-latest
    steps:
      - name: Send Email via MS Graph
        uses: your-repo/send-email-action@v1
        with:
          recipient_email: "example@example.com"
          attachment_path: "./report.pdf"
          attachment_mime_type: "application/pdf"
          subject: "Monthly Report"
          body_content: "Please find the attached report."
```

## Secrets

This action requires the following secrets:

| Secret Name           | Description |
|---------------------|-------------|
| `EMAIL_SERVICE_URL`  | The API URL for sending emails via Microsoft Graph |
| `AZURE_TENANT_ID`    | Azure Tenant ID |
| `AZURE_CLIENT_ID`    | Azure Client ID |
| `AZURE_CLIENT_SECRET` | Azure Client Secret |

## How It Works

1. Converts the file attachment to a base64-encoded string.
2. Constructs a JSON payload for Microsoft Graph API.
3. Retrieves an OAuth2 token using client credentials.
4. Sends an HTTP request to Microsoft Graph to send the email with the attachment.

## Notes

- Ensure that the provided Azure credentials have the necessary permissions to send emails via Microsoft Graph API.
- The MIME type of the attachment should match the actual file type.
- The email is sent using the `application/json` content type.


