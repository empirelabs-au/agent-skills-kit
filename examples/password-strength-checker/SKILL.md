---
name: password-strength-checker
description: Use when you need to evaluate the strength of a password or passphrase, give actionable improvement advice, or explain password policy best practice.
domain: security
status: active
---

# Password Strength Checker

Evaluate a password or passphrase against a pragmatic strength model and give
actionable, concrete improvement advice. Works from a single string supplied
by the user or from a list of strings.

## Steps

1. Receive the password as input. If the user supplies it in plain text,
   treat it as sensitive: never echo it back in full, never write it to a
   file, never include it in logs.

2. Evaluate the password against these factors:

   - Length: count the characters. Under 12 is weak regardless of other
     factors; 12-15 is acceptable; 16+ is strong.
   - Composition: note presence of uppercase, lowercase, digits, symbols,
     and whitespace.
   - Commonality: check against the top 1,000 most common passwords list if
     available (e.g. "password", "123456", "qwerty", "letmein"). A match is
     an instant fail.
   - Sequentiality: flag runs like "abcdef", "123456", "qwerty", or repeated
     characters like "aaaaaa".
   - Personal relevance: flag the string if it contains a name, a year of
     birth, a pet name, or other personally identifiable tokens the user
     volunteers.

3. Produce a verdict: `weak`, `acceptable`, or `strong`, with one line of
   reasoning per factor.

4. Give improvement advice, ordered by impact:

   - Use 3+ random words joined by spaces or symbols (a passphrase), or a
     password manager generated string.
   - Never reuse the password across sites.
   - Enable two-factor authentication wherever available.

5. Output format, in order:

   ```
   Verdict: <weak|acceptable|strong>
   Why: <one line per factor>
   Improve: <top 2 recommendations>
   ```

## Pitfalls

- PITFALL: echoing the full password back in the output. The user may have
  pasted a real credential. Redact all but the first two and last two
  characters when you need to reference it.
- PITFALL: treating length alone as sufficient. A 20-character string of
  "aaaaaaaaaaaaaaaaaaaa" is weak. Composition and commonality checks matter.
- PITFALL: trusting the user's claim that a string is "random". Randomness is
  not visible from the string alone; say so and recommend a manager instead
  of claiming the string is random.
- PITFALL: recommending forced periodic rotation. Current guidance from
  NIST and similar bodies is to rotate on compromise, not on a calendar.
  Recommend unique, long, and manager-stored over rotating.

## Verification

The output contains exactly one verdict line from the allowed set, at least
one "Why" line, and at least two "Improve" items. No input beyond the first
and last two characters appears anywhere in the output.

## Related

- Security hygiene: enable 2FA, use a password manager, check breach lists.
- For organizational policy, see your own security team's guidance before
  externalizing recommendations.
