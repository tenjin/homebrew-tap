# Security

## Reporting a vulnerability

Please do not open a public issue for a security problem. Email [support@tenjin.com](mailto:support@tenjin.com) with "Security: homebrew-tap" in the subject, and include:

- what the problem is, and what an attacker could do with it;
- the package and version, and the steps to reproduce it;
- your name or handle, if you would like to be credited.

We will acknowledge your report, keep you informed while we work on a fix, and credit you if you wish.

## Scope

This repository holds package definitions only. A problem here is one in what a package does: it downloads from somewhere other than its tool's releases, its checksum does not match the release, or an install step does more than it should.

A vulnerability in a tool itself belongs to that tool. Follow its own security policy, for example the [Tenjin CLI's](https://github.com/tenjin/tenjin-cli/blob/main/SECURITY.md).
