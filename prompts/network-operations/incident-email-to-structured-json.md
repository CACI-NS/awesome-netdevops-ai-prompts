# Incident email to structured JSON
Contributed by [@spoofnet](https://github.com/spoofnet)

## Overview
Processes HTML or Plain-text Incident Alert emails from the likes of Azure Monitor, PRTG NMS (Network Management System) and Servicenow and provides a structured JSON output for use in other Automation or CI/CD pipelines. Aims to convert human-readable Incident emails in differing formats into structured data for programmatic processing.

## AI Prompt
```text
For the following Incident email, follow the instructions given in after each Prompt: to calculate each Value: by processing the Prompt: against the JSON input specified above. Respond with a raw JSON dict object:
Key: incident-reference
Value Type: String
Prompt: Incident Reference of this Servicenow Incident, in format 'INC9999999', where '9' is any number

Key: incident-severity
Value Type: Integer
Prompt: Incident Severity of this Servicenow Incident, typically expressed as 'Severity: 9 - Word' where 9 is any number and Word is a descriptive importance signifier like Low, Medium or High

Key: incident-priority
Value Type: Integer
Prompt: Incident Priority of this Servicenow Incident, typically expressed as 'Priority: 9 - Word' where 9 is any number and Word is a descriptive importance signifier like Low, Medium or High

Key: incident-summary
Value Type: String
Prompt: One-line Incident Summary of this Servicenow Incident, focusing on the affected Network Device, Interface, Circuit or VPN Tunnel from the entire email, in human-readable English, aimed at a NOC (Network Operations Centre) as the audience

Key: incident-detail
Value Type: String
Prompt: Incident Summary of this Servicenow Incident, in human-readable English, aimed at a NOC (Network Operations Centre) as the audience. If the email content looks like an SNMP Trap, interpret it accordingly and provide a bulleted English-language response. If the email content looks like an Azure Monitor alert, interpret it accordingly and provide a bulleted English-language response. If the email content looks like a PRTG NMS alert, interpret it accordingly and provide a bulleted English-language response.

For duplicated information, assume the first match as correct.
Respond only with the raw JSON object, do not add any Markdown or code fencing (codefencing) to the response.
Be accurate and critical; if in doubt, respond with the correct Key name and 'Unknown' as the value for a String or 0 as the value for an Integer:

{{email_body}}
```

## Example AI Response
```json
{
    "incident-reference": "INC1234567",
    "incident-severity": 3,
    "incident-priority": 2,
    "incident-summary": "Data Disk IOPS Consumed Percentage >= 90%",
    "incident-detail": "- Condition: Data Disk IOPS Consumed Percentage >= 90%\\n- Assigned to: Team ABC"
}
```

## Usage Notes
* Works best in OpenAI Chat GPT-4o mini
* Replace any moustache variables such as `{{data_here}}` with the relevant text or data for your specific scenario