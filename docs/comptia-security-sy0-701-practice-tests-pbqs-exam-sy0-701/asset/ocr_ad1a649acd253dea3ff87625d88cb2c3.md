system is fixed. Which configuration should the authentication system be set to?

+   (A) Fail-open

+   (B) Fail-closed

+   (C) Fail-secure

+   (D) Fail-passive

**Explanation 269. Correct Answer: B. Fail-closed.** Fail-closed, also known as fail-secure, is a mode where if a system fails, it denies all requests by default, effectively “closing” access. In high-security environments, it’s often preferred to prevent any unauthorized access during system failures.

**Option A is incorrect.** Fail-open is the opposite of what the organization wants. In a fail-open scenario, if the system fails, it would allow all requests by default.

**Option C is incorrect.** While “fail-secure” is another term for “fail-closed”, the use of both terms in the options can confuse the test-taker. In this context, option B is the more appropriate choice.

**Option D is incorrect.** Fail-passive isn’t a standard term in the context of authentication failure modes. Fail-open and fail-closed (or fail-secure) are the primary recognized terms.

**Question 270.** A multinational company wants to allow its remote employees to securely access the corporate intranet over the Internet. The company’s primary concern is to ensure data confidentiality and integrity during transit. Which solution should the company implement?