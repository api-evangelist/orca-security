---
title: "WordPress “Comment2Shell” XSS-to-RCE Chain Lets Unauthenticated Attackers Compromise Servers via Malicious Comments"
url: "https://orca.security/resources/research/cve-2026-93485-wordpress-comment2shell-rce/"
date: "2026-09-22"
author: "The Orca Research Pod"
feed_url: "https://orca.security/resources/blog/feed/"
---
Executive Summary A high-severity vulnerability (CVE-2026-93485, CVSS 7.1) was disclosed affecting WordPress Core, allowing attackers to achieve full remote code execution via a stored cross-site scripting flaw in the comment rendering pipeline. Due to the potential for complete server compromise, immediate patching is required. About CVE-2026-93485 The issue originates from the wpautop() function in wp-includes/formatting.php, […]
