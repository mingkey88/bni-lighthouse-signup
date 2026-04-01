# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-page visitor registration form for **BNI Lighthouse Chapter** (Singapore business networking group). The entire app lives in one self-contained HTML file (`BNILightHouse_PhysicalMeeting_SignUp_Form.html`) with inline CSS and JavaScript — no build tools, no dependencies, no package manager.

## Architecture

- **Single HTML file** — all styles (`<style>`) and logic (`<script>`) are inline. No external CSS/JS files.
- **Fonts**: Google Fonts — Playfair Display (headings) + DM Sans (body).
- **Design system**: CSS custom properties in `:root` define the BNI brand palette (`--bni-red`, `--bni-gold`, etc.) and UI tokens.
- **Form submission**: Currently uses a simulated submit (`setTimeout` → success overlay). There is no real backend integration yet — `handleSubmit()` just shows a success state after 800ms.
- **Meeting date dropdown**: Hardcoded `<option>` values with a `"date - type"` format (e.g., `"10 April 2026 - physical"`). The `updateMeetingType()` function parses the value suffix to toggle between physical/zoom badge styles.

## Key Considerations

- Meeting dates and pricing (S$65 physical / free Zoom) are hardcoded in the HTML and must be updated manually each quarter.
- The form collects: full name, email, contact number, meeting date, inviter name, trade, and company role — all required fields.
- No form validation beyond HTML5 `required` attributes.
- The physical meeting venue is **Suntec Convention Centre, Room 304, Level 3**.
- Social links point to `@bnilighthouse` on Instagram and LinkedIn.
