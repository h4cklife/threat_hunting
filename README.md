# Phishing & Threat Hunting Classes

## Whois Class

Whois class usage example

$ python3

```python
from libs.whois import Whois
w = Whois(domain="example.com")
output = w.get_whois_response()
dict_data = w.parse_whois_response_to_dict(output)

print(dict_data)
{'Domain Name': 'EXAMPLE.COM', 'Registry Domain ID': '2336799_DOMAIN_COM-VRSN', 'Registrar WHOIS Server': 'whois.iana.org', 'Registrar': 'RESERVED-Internet Assigned Numbers Authority', 'Registrar IANA ID': '376', 'Registrar Abuse Contact Email': '', 'Name Server': 'B.IANA-SERVERS.NET', 'DNSSEC': 'signedDelegation', 'DNSSEC DS Data': '370 13 2 BE74359954660069D5C63D200C39F5603827D7DD02B56F120EE9F3A86764247C', 'domain': 'EXAMPLE.COM', 'organisation': 'Internet Assigned Numbers Authority', 'created': '1992-01-01', 'source': 'IANA'}

w.dict_to_json_str(data=dict_data)
'{"Domain Name": "EXAMPLE.COM", "Registry Domain ID": "2336799_DOMAIN_COM-VRSN", "Registrar WHOIS Server": "whois.iana.org", "Registrar": "RESERVED-Internet Assigned Numbers Authority", "Registrar IANA ID": "376", "Registrar Abuse Contact Email": "", "Name Server": "B.IANA-SERVERS.NET", "DNSSEC": "signedDelegation", "DNSSEC DS Data": "370 13 2 BE74359954660069D5C63D200C39F5603827D7DD02B56F120EE9F3A86764247C", "domain": "EXAMPLE.COM", "organisation": "Internet Assigned Numbers Authority", "created": "1992-01-01", "source": "IANA"}'

```


## SSLChecker Class

SSLChecker class usage example

$ python3

```python
from libs.sslchecker import SSLChecker
sslc = SSLChecker(domain='example.com')

sslc.get_ssl_full_details_as_dict()
{'subject': [[['countryName', 'US']], [['stateOrProvinceName', 'California']], [['localityName', 'Los Angeles']], [['organizationName', 'Internet Corporation for Assigned Names and Numbers']], [['commonName', '*.example.com']]], 'issuer': [[['countryName', 'US']], [['organizationName', 'DigiCert Inc']], [['commonName', 'DigiCert Global G3 TLS ECC SHA384 2020 CA1']]], 'version': 3, 'serialNumber': '0AD893BAFA68B0B7FB7A404F06ECAF9A', 'notBefore': 'Jan 15 00:00:00 2025 GMT', 'notAfter': 'Jan 15 23:59:59 2026 GMT', 'subjectAltName': [['DNS', '*.example.com'], ['DNS', 'example.com']], 'OCSP': ['http://ocsp.digicert.com'], 'caIssuers': ['http://cacerts.digicert.com/DigiCertGlobalG3TLSECCSHA3842020CA1-2.crt'], 'crlDistributionPoints': ['http://crl3.digicert.com/DigiCertGlobalG3TLSECCSHA3842020CA1-2.crl', 'http://crl4.digicert.com/DigiCertGlobalG3TLSECCSHA3842020CA1-2.crl']}

sslc.get_ssl_important_details_as_dict()
{'notBefore': '2025-01-15T00:00:00 UTC', 'notAfter': '2026-01-15T23:59:59 UTC', 'caIssuers': ['http://cacerts.digicert.com/DigiCertGlobalG3TLSECCSHA3842020CA1-2.crt'], 'serialNumber': '0AD893BAFA68B0B7FB7A404F06ECAF9A', 'countryName': 'US', 'stateOrProvinceName': 'California', 'localityName': 'Los Angeles', 'organizationName': 'Internet Corporation for Assigned Names and Numbers', 'issuer': {'countryName': 'US', 'organizationName': 'DigiCert Inc', 'commonName': 'DigiCert Global G3 TLS ECC SHA384 2020 CA1'}}

sslc.verify_ssl_certificate()
True

sslc.verify_ssl_active()
True

```