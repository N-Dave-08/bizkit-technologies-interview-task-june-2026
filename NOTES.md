# NOTES

## 1. Explain one fix

The original code only checked if the new booking's start date was inside an existing booking (`start_b <= start_a <= end_b`). This missed cases where the new booking started earlier but still overlapped the existing booking. I changed the check to `start_a <= end_b and start_b <= end_a`, which catches all overlapping date ranges while still allowing bookings that don't overlap.

## 2. Show the failure

Original code incorrectly allowed:

- Existing booking: **2026-01-10 → 2026-01-15**
- New booking: **2026-01-08 → 2026-01-18**

After the fix, this booking is correctly rejected because the date ranges overlap.

## 3. AI use

I used ChatGPT as a discussion tool while working through the assessment. I usually gave it the task, the relevant code, and any constraints I wanted to follow, then asked questions about the logic or possible fixes. I didn't apply the suggestions blindly—I tested each one myself and only kept the changes that matched the requirements and worked correctly.
