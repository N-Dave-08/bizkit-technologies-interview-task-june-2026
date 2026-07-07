# NOTES

## 1. Explain one fix

The original code only checked if the new booking's start date was inside an existing booking (`start_b <= start_a <= end_b`). This missed cases where the new booking started earlier but still overlapped the existing booking. I changed the check to `start_a <= end_b and start_b <= end_a`, which catches all overlapping date ranges while still allowing bookings that don't overlap.

## 2. Show the failure

Original code incorrectly allowed:

- Existing booking: **2026-01-10 → 2026-01-15**
- New booking: **2026-01-08 → 2026-01-18**

After the fix, this booking is correctly rejected because the date ranges overlap.

## 3. AI use

I used ChatGPT to help me think through the booking overlap logic. My prompts usually included the task, the relevant code for context, and any constraints I wanted to keep. I didn't copy the solution directly—I tested it with different booking dates to make sure it worked correctly and followed the application's rules.
