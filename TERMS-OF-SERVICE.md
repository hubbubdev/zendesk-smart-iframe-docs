{% raw %}
# Terms of Service

## Data Disclosure

### Data Accessed

Smart iFrame accesses the following Zendesk data through the Zendesk App Framework (ZAF) SDK:

- **Ticket fields:** ID, subject, status, priority, brand, form, and custom fields
- **Requester (end-user) fields:** User ID, email, external ID, phone number, and social identity fields (Twitter/X, Facebook, Google)
- **Assignee fields:** User ID, email, and group ID
- **Current user (agent) fields:** User ID and email
- **Account fields:** Subdomain

### How Data Is Used

All accessed data is used **exclusively for client-side URL template variable substitution**. When an admin configures a URL template (e.g., `https://example.com/lookup?email={{ticket.requester.email}}`), the app replaces the template variables with live Zendesk values to construct the iframe URL. This processing happens entirely within the browser — no data is sent to any external server for processing.

### Data Storage

Smart iFrame **does not store, export, or transmit any Zendesk data** to Hubbub Studios or any third party. All data remains within the Zendesk environment and the agent's browser session.

### Analytics

Anonymous, non-personally-identifiable usage analytics are collected via PostHog for product improvement purposes. These events contain **no Zendesk data, no ticket content, and no personally identifiable information**. Analytics track only app lifecycle events (e.g., app loaded, iframe rendered).

## Use

Smart iFrame is provided free of charge as a utility. You may use it as-is for any purpose within your Zendesk workspace.

## No Warranty / Liability

This software is provided "as is", without warranty of any kind, express or implied. Hubbub Studios accepts no liability for any damages, data loss, or interruption of service arising from the use or inability to use this app. Use at your own risk.
{% endraw %}
