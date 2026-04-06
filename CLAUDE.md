# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-page visitor registration form for **BNI Lighthouse Chapter** (Singapore business networking group). The entire app lives in one self-contained HTML file (`index.html`) with inline CSS and JavaScript — no build tools, no dependencies, no package manager.

## Architecture

- **Single HTML file** — all styles (`<style>`) and logic (`<script>`) are inline. No external CSS/JS files.
- **Fonts**: Google Fonts — Playfair Display (headings) + DM Sans (body).
- **Design system**: CSS custom properties in `:root` define the BNI brand palette (`--bni-red`, `--bni-gold`, etc.) and UI tokens.
- **Form submission**: `handleSubmit()` sends a `fetch()` POST (JSON via `text/plain`, `no-cors`) to a Google Apps Script web app, which appends rows to a Google Sheet ("BNI Lighthouse Visitor Registrations") on a personal Google account. Fields sent: `fullName`, `email`, `contactNumber`, `meetingDate`, `meetingType`, `invitedBy`, `trade`, `companyRole`.
- **EDM poster**: `edm-poster.jpg` in the root directory. Source images are stored in `EDM_Weekly/` and updated weekly.
- **Meeting date dropdown**: Hardcoded `<option>` values with a `"date - type"` format (e.g., `"10 April 2026 - physical"`). The `updateMeetingType()` function parses the value suffix to toggle between physical/zoom badge styles.

## Key Considerations

- Meeting dates and pricing (S$65 physical / free Zoom) are hardcoded in the HTML and must be updated manually each quarter.
- The form collects: full name, email, contact number, meeting date, inviter name, trade, and company role — all required fields.
- No form validation beyond HTML5 `required` attributes.
- The physical meeting venue is **Suntec Convention Centre, Room 304, Level 3**.
- Social links point to `@bnilighthouse` on Instagram and LinkedIn.
- The Google Apps Script URL is hardcoded in `handleSubmit()`. If the script is redeployed with a new URL, update it in `index.html`.
- The BNI Google account cannot be used for the Sheet integration — a personal Google account is used instead. The sheet can be shared with the BNI account for viewing.
