# Smart iFrame (Zendesk App)

Easily embed a 3rd party application or website into your Zendesk agent workspace just by specifying the URL.

Get it now in the Zendesk App Marketplace: https://www.zendesk.com/marketplace/apps/support/1020069/smart-iframe/

You can leverage data about the Zendesk ticket, assigned user, current user, and requester to formulate dynamic URLs using `{{double brace}}` template variables.

## Template Variables

Use `{{double braces}}` around any supported variable to embed live Zendesk data into the URL at runtime.

**Example:** Setting up the app with URL `https://mysite.com/profile/{{ticket.requester.id}}` will result in an embedded iFrame to URL `https://mysite.com/profile/1234` where `1234` is the Zendesk user ID of the ticket requester.

### Ticket

| Variable | Description |
|---|---|
| `{{ticket.id}}` | ID of the active ticket |
| `{{ticket.subject}}` | Subject line of the ticket |
| `{{ticket.status}}` | Status of the ticket |
| `{{ticket.priority}}` | Priority of the ticket |
| `{{ticket.brand.id}}` | ID of the brand associated with the ticket |
| `{{ticket.form.id}}` | ID of the ticket form used |
| `{{ticket.customField:custom_field_<field_id>}}` | Value of a custom field — replace `<field_id>` with the numeric custom field ID |

### Requester (End-User)

| Variable | Description |
|---|---|
| `{{ticket.requester.id}}` | ID of the ticket requester |
| `{{ticket.requester.email}}` | Email address of the requester |
| `{{ticket.requester.externalId}}` | Externally-mapped ID of the requester |
| `{{ticket.requester.$phone}}` | Phone number of the requester, e.g. `+15556667777` |
| `{{ticket.requester.$phone-us}}` | Phone number in US format, digits only, e.g. `5556667777` |
| `{{ticket.requester.$twitter}}` | Twitter/X handle of the requester |
| `{{ticket.requester.$facebook}}` | Facebook identity of the requester |
| `{{ticket.requester.$google}}` | Google identity of the requester |

### Assignee (Agent)

| Variable | Description |
|---|---|
| `{{ticket.assignee.user.id}}` | ID of the assigned agent |
| `{{ticket.assignee.user.email}}` | Email of the assigned agent |
| `{{ticket.assignee.group.id}}` | ID of the assigned group |

### Current User (Agent Viewing the Ticket)

| Variable | Description |
|---|---|
| `{{currentUser.id}}` | ID of the current agent |
| `{{currentUser.email}}` | Email of the current agent |

### Legacy Variables

The original 8 template strings are still fully supported and work unchanged. They are automatically mapped to their dot-notation equivalents internally.

| Legacy | Equivalent |
|---|---|
| `{ticket_id}` | `{{ticket.id}}` |
| `{current_user_id}` | `{{currentUser.id}}` |
| `{current_user_email}` | `{{currentUser.email}}` |
| `{requester_id}` | `{{ticket.requester.id}}` |
| `{requester_email}` | `{{ticket.requester.email}}` |
| `{requester_external_id}` | `{{ticket.requester.externalId}}` |
| `{assignee_id}` | `{{ticket.assignee.user.id}}` |
| `{assignee_email}` | `{{ticket.assignee.user.email}}` |

![screenshot-1](https://github.com/user-attachments/assets/58117894-59c4-4c47-b75a-2749b9fcb751)
![screenshot-2](https://github.com/user-attachments/assets/7d13a447-dced-442a-aeef-6a80c03b35b8)


## Release Log

**v3.0.0**
- Extended attributes: Most Zendesk attributes are now supported as template variables, such as custom fields (e.g. `{{ticket.customField:custom_field_1234}}`) and requester external ID (`{{ticket.requester.externalId}}`)

---

### iFrame Not Working?

Not all websites can be rendered within an iFrame. If you see this:

![screenshot-3](https://github.com/user-attachments/assets/9c530d40-8e86-491e-aa09-084d9c4ee1c2)

The application may be blocking this behavior. This is a decision made by the respective website owner / administrator.

Opening the browser developer tools console should present some additional information, such as:

```
Refused to display 'https://thewebsiteyouwanttoiframe.com/' in a frame because it set 'X-Frame-Options' to 'sameorigin'.
```

If you are attempting to configure Smart iFrame with a 3rd party vendor application, you can reach out to their support department and discuss further.

If you or your company owns the website you are trying to iFrame, you may need to speak with your system administrator about disabling restrictive controls that are set via the HTTP header `X-Frame-Options`

If `X-Frame-Options` is set to `DENY` or `SAMEORIGIN` (and it doesn't match the criteria), the browser will block the framing.
