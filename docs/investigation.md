# Investigation Notes

## Questions I will answer

1. What is suspicious and why?
2. What evidence supports it?
3. How far did it go (scope)?
4. What is the most likely story (hypothesis)?
5. What should a SOC do next (containment + remediation)?

## Timeline

Performed baseline user activity (login, reboot, application use) to observe normal authentication events in the Windows Security log.

Multiple failed logon attempts (Event ID 4625) for user employee01 were observed within a short time window, followed by a successful logon (Event ID 4624).

## Evidence collected

normal activity :

Event ID 4624 : successful login by employee01 observed at : 04:25:41

Event ID 4625 : failed login attempt by employee01 at : 04:25:35 reason : Unknown username or Password .

suspicious activity :

Event ID 4625: Multiple failed logon attempts for user employee01 within a short time window.

Event ID 4624: Successful logon for user employee01 immediately following failed attempts.



Screenshots supporting the investigation are available in the /screenshots directory.



## Findings

The sequence of repeated failed authentication attempts followed by a successful login deviates from established baseline behaviour and is consistent with password guessing or brute-force activity.

No evidence of additional affected accounts or systems was observed within the scope of this host.

## Recommendations

Investigate the source of the failed attempts, enforce account lockout policies, and require a password reset for the affected account.

