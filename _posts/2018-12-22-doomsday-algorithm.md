---
layout: post
title: The Doomsday Algorithm
---

I record my way of performing Conway's Doomsday Algorithm here in order to potentially review it. The Doomsday Algorithm allows you to find out the day of week of any date.

Remember this sequence of numbers: 2 0 5 3.

Define the modulo operation like this `a mod n = b`. Take the closest number *lower* number than `a` divisble by `n` and call it `x`, then `b=abs(x-a)`. For example `21 mod 5 = 1`, because `x` is 20. But `-21 mod 5 = 4`, because `x` is -25.

Remember the doomsdays:
- 3.1. (4.1. when it's a leap year)
- 28.2. (29.2. when it's a leap year)
- 14.3. (= Pi day)
- 4.4.
- **9.5.**
- 6.6.
- **11.7.**
- 8.8.
- **5.9.**
- 10.10.
- **7.11.**
- 12.12.

First three months are irregular, otherwise when it's an even month, the day is the same as the month. Odd months are easy to remember using this mnemotechnique "I work 9 to 5 in a 7/11".

A leap year in the Gregorian calendar is a year which is divisible by 4, but is not divisible by 100, or is divisible by 400.

```py
year % 4 and not year % 100 or year % 400
```

Take a date (yyyy-MM-dd) as an example: 2025-02-01

Take the year 2025.

Divide the first two digits (20) by 4. Take the remainder. The remainder is 0. Take the number from the sequence 2 0 5 3 with the index 0. That is 2. Visualize it (2) on your index finger.

Divide the last two digits (25) by 12. Visualize the result (2) on your middle finger. Visualize the reminder (1) on your ring finger.

Divide the number on your ring finger by 4. The result (0) will hang on your pinkie.

Sum all of these numbers (2, 2, 1, 0) together. You get a 5. That means all the doomsdays of 2025 are Fridays (0 = Sunday, 1 = Monday, …, 5 = Friday).

Take the date 02-01. What is the Doomsday for February? 02-28. Take the day of the month of your date and subtract the Doomsday's day (1 - 28 = -27). Add the Doomsday for the year (5) to the result. -27 + 5 = -22. Take -22 mod 7, you get 6. 2025-02-01 is a Saturday.