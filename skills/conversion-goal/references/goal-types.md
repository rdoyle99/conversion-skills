# Goal types and how to detect them

| Goal | Detect with | Notes |
|---|---|---|
| Account created | redirect to `/welcome` or a server `user.created` | best default for self-serve products |
| Demo booked | the booking tool's confirmation URL or webhook | embeds can open slowly; count the confirmation, not the tap |
| Checkout paid | payment webhook | often too rare; use checkout opened as the goal and paid as a check |
| Waitlist joined | form post success | fine before launch |
| Install | the install command's first event | for developer tools |
