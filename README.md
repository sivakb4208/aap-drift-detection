EDA (every 60 seconds)
        ↓
drift_detect.yml runs on VM1
        ↓
    ┌───────────────────────────┐
    │                           │
No Drift                   Drift Found
    │                           │
    ↓                           ↓
Job SUCCESS              Job FAILS
"✅ Compliant"           Drift report written
                         to /tmp/drift_report.txt
                                ↓
                         remediate.yml runs
                         Re-applies:
                         - sysctl settings
                         - SSH hardening
                         - Services started/stopped
                         - Timestamp written to
                           /etc/aap_last_remediation
                                ↓
                         verify.yml runs
                         Re-checks everything
                                ↓
                    ┌───────────────────┐
                    │                   │
               PASSED ✅           FAILED ❌
               "Node compliant"    Alert raised
