# Risk Register

| **Risk ID** | **Risk Description** | **Possible Cause** | **Probability** | **Impact** | **Mitigation/Response Strategy** |
| ----------- | -------------------- | ------------------ | --------------- | ---------- | -------------------------------- |
| **R1** | Requirements of scheduling system are unclear or change mid project | Stakeholders not properly consulted initially. | Medium | High | Hold requirement workshops with all user roles to elicit requirements and document them formally. |
| **R2** | Sensitive personal and test result data is exposed or breached | Weak authentication/authorization system. Insufficient encryption of data. | Low | High | Conduct security testing/code review before release. Make sure to follow data protection regulations relevant to personal records. |
| **R3** | Project lags behind schedule | Overly optimistic initial estimates. Potential scope creep. | Medium | Medium | Track and monitor progress closely, prioritizing tasks that are falling behind schedule. |
| **R4** | Team lacks experience with the specific tech stack | Unfamiliarity with frameworks among developers | Medium | Medium | Early in the project conduct upskilling workshop/training. Add buffer time in tasks to allow for a learning curve. |
| **R5** | Double-booking or scheduling conflicts due to concurrent booking requests | Race conditions in the booking logic, without proper handling | Medium | High | Design the system to handle the conflicts reliably. E.g., implement database-level constraints and transaction locking on slot booking. |