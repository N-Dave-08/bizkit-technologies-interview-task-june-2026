# NOTES

## 1. Explain one fix

The original code only checked if the new booking's start date was inside an existing booking (`start_b <= start_a <= end_b`). This missed cases where the new booking started earlier but still overlapped the existing booking. I changed the check to `start_a <= end_b and start_b <= end_a`, which catches all overlapping date ranges while still allowing bookings that don't overlap.

## 2. Show the failure

Original code incorrectly allowed:

- Existing booking: **2026-01-10 → 2026-01-15**
- New booking: **2026-01-08 → 2026-01-18**

After the fix, this booking is correctly rejected because the date ranges overlap.

## 3. AI use

I used ChatGPT to discuss the existing code, validate my understanding of the business rules, and review potential fixes. My prompts typically consisted of three parts: the task or instruction, the relevant code or project context, and any constraints (such as preserving the existing structure or following the stated business rules). I treated the responses as suggestions rather than final answers, verifying each proposed change by reading the code, testing the affected scenarios, and confirming the behavior matched the application's requirements before keeping the change.
