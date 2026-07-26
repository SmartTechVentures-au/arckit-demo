# Live Sequence

1. **Orient the session - branch demo/stage1**

   `/arckit:start`

   Review the harness status, connected tools and decision tree.

2. **Create the organisation-wide governance space - branch demo/stage2**

   ```text
   /arckit:init 000-global
   ```

   This is the organisation-wide governance space for **The University of Funk**, an Australian university rationalising its Learning & Teaching technology ecosystem.

   Inputs are located in `demo-inputs/`.

3. **Define organisation-wide principles  - branch demo/stage3**

   ```text
   /arckit:principles
   ```

   Run within `000-global`, covering:

   * LMS boundaries
   * Integration approach
   * Platform governance
   * Student experience consistency

4. **Create the Learning & Teaching engagement - branch demo/stage4**

   ```text
   /arckit:init 001-lt-ecosystem
   ```

   The Learning & Teaching Baseline Strategy engagement, covering WP1–WP9 as defined in:

   `demo-inputs/consultant-brief.md`

   > **Pause on the:** “principles inherited from 000-global” line.

5. **Generate the stakeholder analysis**

   ```text
   /arckit:stakeholders
   ```

   Use:

   `demo-inputs/stakeholders.md`

6. **Generate the requirements - branch demo/stage5**

   ```text
   /arckit:requirements
   ```

   Use:

   `demo-inputs/requirements-register.md`

7. **Assess key risks - branch demo/stage6**

   ```text
   /arckit:risk
   ```

   Focus on:

   * Integration fragility
   * Licence waste
   * Shadow IT

8. **Create the architecture decision record - branch demo/stage7**

   ```text
   /arckit:adr Echo360 vs Microsoft Stream for lecture capture
   ```

9. **Conduct the Australian Privacy Impact Assessment - branch demo/stage8**

   ```text
   /arckit:au-pia
   ```

   Use:

   `demo-inputs/privacy-context.md`

   Cover:

   * The 13 Australian Privacy Principles
   * Sensitive data held in Sonia
   * APP 8 and offshore disclosure

10. **Assess Essential Eight posture  - branch demo/stage9**

    ```text
    /arckit:au-e8-posture
    ```

    Use the Microsoft self-assessment in:

    `demo-inputs/privacy-context.md` — §3

11. **Build the engagement outputs - branch demo/stage10**

    First, generate the build plan:

    ```text
    /arckit:build 001 --plan
    ```

    Then run the full build:

    ```text
    /arckit:build 001
    ```

    **Onto the finale.**

12. **Demonstrate end-to-end traceability - branch demo/stage11**

    ```text
    /arckit:traceability
    ```

    This shows:

    ```text
    Requirement → System → Decision → Risk → APP Finding → Roadmap
    ```

## Stretch Activity

Run the Notifiable Data Breaches playbook:

```text
/arckit:au-ndb-playbook
```

Use the Sonia tabletop scenario in:

`demo-inputs/privacy-context.md` — §4

## Recovery if a Run Stalls

Enter:

```text
Continue from where you stopped. Do not stop until complete.
```

Then run:

```text
/arckit:health
```
