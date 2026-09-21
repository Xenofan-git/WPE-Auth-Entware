# WPE-Auth-Entware

Minimal WPE WebKit authentication runtime for Entware/Linux.

## Purpose

This repository isolates the browser-engine part of an authentication flow from the main application.

The first target is a small headless WPE WebKit runtime that can load an OAuth page and execute JavaScript inside the page. This is important for OAuth flows where credentials are returned in a URL fragment and therefore are not sent to the HTTP server.

## Target platform

- ARM64 / aarch64
- Entware/Linux
- Keenetic-class embedded systems
- WPE WebKit 2.54+
- WPEPlatform 2.0

The current CI milestone first validates the WPE WebKit build on GitHub Actions. The final deployment target is an Entware-compatible ARM64 build.

## Design goals

- Keep the runtime as small as practical.
- Use native C and WPE WebKit.
- Keep browser-engine code independent from the main application.
- Support JavaScript access to the final browser URL.
- Avoid exposing real credentials in build logs.
- Leave interactive CAPTCHA/login as a later milestone.
- Produce reproducible CI artifacts.

## Repository layout

```text
src/
  main.c

CMakeLists.txt

.github/
  workflows/
    build.yml
```

## Current milestone

The immediate goal is:

1. Build WPE WebKit successfully.
2. Build the minimal authentication probe against it.
3. Produce a CI artifact.
4. Validate the binary on the actual ARM64/Entware target.
5. Only then integrate the runtime into the main application.

## Security

Real access tokens must never be committed to this repository or printed into CI logs.

This project is an authentication runtime component. It does not contain user credentials, private keys, or hard-coded authorization tokens.

## Status

Development / build validation.
