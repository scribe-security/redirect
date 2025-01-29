# redirect
Adjust arguments and redirect to ScribeHub

Accessing this page with human readable parameters will translate to base64 encoded parameters and redirect to the scribehub page.

The parameters handled are only the searchPhrase, that has to be formatted as:
- `key:value||key2:value||...`
- `key%3Avalue||key2%3Avalue||...`

Notes:

The original Superset query format has limitation (so a rule name with spaces and columns can do query injection or produce unpredictable results. This in not dangerous because superset does not allow distructive operations).

Experiment:
run `python -m http.server 8090`

And browse to:
http://localhost:8090/redirect.html?path=%2Fsbom?redirectTabName=Vulnerabilities&searchPhrase=product%3AScribot||product_version%3A40||show_file_components%3Afalse


