---
title: "Postmortem for *.bazel.build SSL certificate expiry"
url: "/2026/01/16/ssl-cert-expiry.html"
date: "2026-01-16"
feed_url: "https://blog.bazel.build/feed.xml"
---
On 2025-12-26, at 07:35 UTC, the SSL certificates for many *.bazel.build domains expired. This resulted in widespread build breakages for many Bazel users, as several crucial domains serve essential functionality used by nearly all Bazel builds. It was reported by users on GitHub , Slack , and the bazel-discuss mailing list.
