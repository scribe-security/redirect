# redirect
Adjust arguments and redirect to ScribeHub

Accessing this page with human readable parameters will translate to base64 encoded parameters and redirect to the scribehub page.

The parameters handled are only the searchPhrase, that has to be formatted as:
- `key:value;;key2:value;;...`
- `key%3Avalue;;key2%3Avalue;;...`

Example:
https://scribe-security.github.io/redirect/redirect.html?path=%2Fsbom?redirectTabName=Vulnerabilities&searchFilters=product:Star-Generator;;product_version:0.3.31;;show_file_components:false

Notes:

The original Superset query format has limitation (so a rule name with spaces and columns can do query injection or produce unpredictable results. This in not dangerous because superset does not allow distructive operations).

To experiment:

run `python -m http.server 8090`

And browse to:
http://localhost:8090/redirect.html?path=%2Fsbom?redirectTabName=Vulnerabilities&searchFilters=product%3AScribot;;product_version%3A40;;show_file_components%3Afalse


Generated:
https://app.scribesecurity.com/sbom?redirectTabName=Vulnerabilities&searchFilters=JTdCJTIycHJvZHVjdCUyMiUzQSU1QiUyMlNjcmlib3QlMjIlNUQlMkMlMjJwcm9kdWN0X3ZlcnNpb24lMjIlM0ElNUIlMjI0MCUyMiU1RCUyQyUyMnNob3dfZmlsZV9jb21wb25lbnRzJTIyJTNBJTVCJTIyZmFsc2UlMjIlNUQlN0Q

From browser:

https://app.scribesecurity.com/sbom?redirectTabName=Vulnerabilities&searchFilters=JTdCJTIycHJvZHVjdCUyMiUzQSU1QiUyMlNjcmlib3QlMjIlNUQlMkMlMjJwcm9kdWN0X3ZlcnNpb24lMjIlM0ElNUIlMjI0MCUyMiU1RCU3RA

https://app.scribesecurity.com/sbom?redirectTabName=Vulnerabilities&searchFilters=JTdCJTIycHJvZHVjdCUyMiUzQSU1QiUyMmNvZGVfdG9fY2xvdWQlMjIlNUQlMkMlMjJwcm9kdWN0X3ZlcnNpb24lMjIlM0ElNUIlMjIwLjguMSUyMiU1RCUyQyUyMnNob3dfZmlsZV9jb21wb25lbnRzJTIyJTNBJTVCJTIyZmFsc2UlMjIlNUQlN0Q

For testing on Staging:
Staging:
http://localhost:8090/redirect-to-staging.html?path=%2Fsbom?redirectTabName=Vulnerabilities&searchFilters=vuln_id:CVE-2021-44906;;show_file_components%3Afalse

http://scribe-security.github.io/redirect/redirect-to-staging.html?path=%2Fsbom?redirectTabName=Vulnerabilities&searchFilters=vuln_id:CVE-2021-44906;;show_file_components%3Afalse

Filter by attestation file ID:

http://scribe-security.github.io/redirect/redirect.html?path=%2Fpolicy%2Fevidence&searchFilters=evidence_id:379264

Filter by initiative and product version:
http://scribe-security.github.io/redirect/redirect.html?path=%2Fpolicy%2Fevaluation&searchFilters=initiative:SSDF;;product:Scribot;;product_version:40