---
title: Critical Unauthenticated RCE in Kopia Backup via SSH ProxyCommand Injection
url: https://orca.security/resources/blog/kopia-backup-rce-vulnerability/
date: '2026-05-26'
author: The Orca Security Team
feed_url: https://orcasecurity.io/feed
---
A critical vulnerability (CVE-2026-45695, CVSS 9.8) was disclosed affecting Kopia, the open-source backup and restore tool, allowing attackers to achieve unauthenticated remote code execution via SSH command-line argument injection. Due to the potential for full system compromise without any authentication, immediate patching is required. Technical Overview The issue originates from Kopia’s HTTP server API endpoint […] The post Critical Unauthenticated RCE in Kopia Backup via SSH ProxyCommand Injection appeared first on Orca Security .
