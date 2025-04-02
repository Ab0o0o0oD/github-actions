# Send Email via MS Graph

This GitHub Action allows you to send an email with an attachment using Microsoft Graph API.

## Inputs

| Name             | Description                          | Required |
|----------------|----------------------------------|----------|
| `receiver-email` | Recipient email address          | ✅       |
| `file-path`      | Path to the file to attach       | ✅       |
| `content-type`   | MIME type of the attachment     | ✅       |
| `email-subject`  | Email subject                   | ✅       |
| `email-content`  | Email body content              | ✅       |

## Usage

```yaml
jobs:
  send-email:
    runs-on: ubuntu-latest
    steps:
      - name: Send Email via MS Graph
        uses: ./
        with:
          receiver-email: "recipient@example.com"
          file-path: "path/to/attachment.pdf"
          content-type: "application/pdf"
          email-subject: "Subject of the email"
          email-content: "Hello, this is the email body."
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

## License

This project is licensed under the MIT License.

