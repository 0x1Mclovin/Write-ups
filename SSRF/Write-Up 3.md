#SSRF 

SSRF with blacklist-based input filter: [link](https://portswigger.net/web-security/ssrf/lab-ssrf-with-blacklist-filter)

Some applications block input containing hostnames like `127.0.0.1` and `localhost`, or sensitive URLs like `/admin`. In this situation, you can often circumvent the filter using the following techniques:

- Use an alternative IP representation of `127.0.0.1`, such as `2130706433`, `017700000001`, or `127.1`.
- Register your own domain name that resolves to `127.0.0.1`. You can use `spoofed.burpcollaborator.net` for this purpose.
- Obfuscate blocked strings using URL encoding or case variation.
- Provide a URL that you control, which redirects to the target URL. Try using different redirect codes, as well as different protocols for the target URL. For example, switching from an `http:` to `https:` URL during the redirect has been shown to bypass some anti-SSRF filters

in this challenge we have tow filter that capt my payload the first one for the IP when i enter `127.0.0.1` it block me from access to resources and the second filter is when i enter admin as a directory `/admin` 
the bypass for the first problem is used `127.1` and the bypass for second problem is using double encoding 

**payload:**
`stockApi=http://127.1/%2561%2564%256D%2569%256E/delete?username=carlos`

