# Release notes for eMagiz Infra v2

This update changes the Carwash (See https://docs.emagiz.com/bin/view/Main/eMagiz%20Academy/Fundamentals/fundamental-emagiz-cloud-inner-workings). Note that using this new version of the Carwash involves a DNS change, and thus relies on clients honoring TTLs of DNS records. This update also changes the IP Adresses used in the infrastructure. For more details, please contact Expert Services. Furthermore, TLSv1.0 is disabled in this update. Verify legacy software can handle atleast TLSv1.1 before updating. 

1) Changed ciphers and cipher suites
2) Disabled TLS V1.0 support and enable TLS V1.3 support.

Supported Ciphers in OpenSSL Format:  ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA256:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA256:DHE-RSA-AES128-SHA:DHE-RSA-AES256-SHA256:DHE-RSA-AES256-SHA:ECDHE-ECDSA-DES-CBC3-SHA:DHE-RSA-DES-CBC3-SHA:ECDHE-RSA-DES-CBC3-SHA:EDH-RSA-DES-CBC3-SHA:AES128-GCM-SHA256:AES256-GCM-SHA384:AES128-SHA256:AES256-SHA256:AES128-SHA:AES256-SHA:DES-CBC3-SHA:!DSS@SECLEVEL=1
Supported TLS Versions: TLSv1.1, TLSv1.2 and TLSv1.3