# Investigate Web Attack 

## Overview

In this lab, I investigated a web-attack alert in LetsDefend and followed the evidence from the initial alert through the related web logs. The goal was not just to identify a suspicious request, but to understand what the attacker was trying to do, whether the activity was successful, and what should happen next from a defensive point of view.

The investigation focused on the request details that matter most in a web incident: source IP address, targeted URL, HTTP method, response code, user agent, timestamps, and the payload itself. I reviewed these fields together rather than relying on one indicator alone, since a single unusual request does not always mean a system has been compromised.

## Objective

The objectives of the investigation were to:

- Validate whether the alert represented malicious activity.
- Identify the attack pattern used in the request.
- Determine the affected web resource and the likely attacker intent.
- Check whether the server response suggested a successful attack.
- Gather useful indicators and recommend containment or hardening actions.

## Investigation Process

I started by reviewing the alert information and establishing a timeline of the suspicious activity. I then inspected the HTTP request and looked for common web-attack characteristics, such as encoded payloads, unusual parameters, traversal sequences, script injection attempts, or database-related keywords.

Next, I pivoted through the available logs to see whether the same IP address made additional requests, targeted other endpoints, or changed techniques after receiving a response from the server. This helped separate a one-off probe from a more deliberate attack attempt.

I also considered the HTTP status codes in context. A `200` response can indicate success, but it can also mean the application returned a normal page while rejecting the malicious input. Likewise, `4xx` and `5xx` responses are useful clues, but they do not prove the request was harmless. The request payload, application behavior, and related log entries all need to support the conclusion.

## Key Findings

- The alert was investigated by correlating the web request with surrounding log activity.
- The suspicious request contained characteristics consistent with a web-based attack attempt.
- The targeted endpoint and request parameters were reviewed to determine the intended impact.
- Related requests from the same source were checked for reconnaissance, repeated exploitation attempts, or lateral targeting of other pages.
- The server response was analyzed to assess whether the attack was likely blocked, unsuccessful, or needed further validation.

## Indicators Reviewed

During the investigation, I examined the following artifacts:

- Source IP address and any related requests
- Target host, URI, and query parameters
- HTTP request method and response status code
- User-Agent, referrer, and request headers
- Timestamp sequence and request frequency
- Encoded or obfuscated payload content
- Web server and application log entries

## Recommended Response Actions

Based on the investigation workflow, the following actions would be appropriate when this type of activity is confirmed in a real environment:

1. Block or rate-limit the malicious source IP at the WAF, reverse proxy, or firewall when justified by the evidence.
2. Preserve the relevant web, application, and security logs for further analysis.
3. Review the affected endpoint for input-validation and output-encoding gaps.
4. Search for the same payload pattern across other web assets.
5. Verify that the attempted action did not result in unauthorized access, data exposure, file changes, or application errors.
6. Add detections for the observed pattern and monitor for repeat attempts.

## What I Learned

T
