# Gibbon LMS Arbitrary File Write / RCE
## Vulnerability Information
**Arbitrary File Write in Gibbon LMS for RCE (CVE-2023-45878)**<br><br>
GibbonEdu Gibbon LMS version 25.0.1 and earlier allows Arbitrary File Write because rubrics_visualise_saveAjax.php does not require authentication. The endpoint accepts the img, path, and gibbonPersonID parameters. The img parameter is expected to be a base64 encoded image. If the path parameter is set, the defined path is used as the destination folder, concatenated with the absolute path of the installation directory. The content of the img parameter is base64 decoded and written to the defined file path. This allows creation of PHP files that permit Remote Code Execution (unauthenticated).

## References
- https://nvd.nist.gov/vuln/detail/CVE-2023-45878
- https://herolab.usd.de/security-advisories/usd-2023-0025/

## Description
This script provides a *pseudo*-interative shell. A single PHP is uploaded to the remote system and the local script provides a wrapper to interact with it directly. When a command is submitted, it returns the HTTP response from the PHP payload. In the event the payload file is removed from the remote system, the script will detect a 404 error page response, and perform a new upload and resubmit the last command.

## Usage
```python3 gibbonlms_cmd_shell.py url```

## Example
```python3 gibbonlms_cmd_shell.py http://example.com```

## Disclaimer
This script is provided for educational purposes. Please pwn responsibly.
