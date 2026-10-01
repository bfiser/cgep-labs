policies/ac3_no_public.rego
    control_id: AC-3
    severity: critical
    remediation: "Set uniform_bucket_level_access = true, public_access_prevention = enforced. For firewalls, narrow source_ranges or remove the rule."

policies/cm6_required_tags.rego
    control_id: CM-6
    severity: medium
    remediation: "Add the four required labels (project, environment, managed_by, compliance_scope) to the resource."

policies/sc28_encryption.rego
    control_id: SC-28
    severity: high
    remediation: "Add an encryption { default_kms_key_name = ... } block referencing a google_kms_crypto_key you control."


