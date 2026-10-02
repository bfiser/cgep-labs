policies/ac3_no_public.rego
    control_id: AC-3
    severity: critical
    remediation: "Set uniform_bucket_level_access = true, public_access_prevention = enforced. For firewalls, narrow source_ranges or remove the rule."
    cloud_target: gcp

policies/cm6_required_tags.rego
    control_id: CM-6
    severity: medium
    remediation: "Add the four required labels (project, environment, managed_by, compliance_scope) to the resource."
    cloud_target: gcp

policies/sc28_encryption.rego
    control_id: SC-28
    severity: high
    remediation: "Add an encryption { default_kms_key_name = ... } block referencing a google_kms_crypto_key you control."
    cloud_target: gcp

policies/ac3_no_public_aws.rego
   control_id: AC-3
   severity: critical
   remediation: "Every aws_s3_bucket must have an aws_s3_bucket_public_access_block referencing it, with all four flags true."
   cloud_target: aws

policies/cm6_required_tags_aws.rego
   control_id: CM-6
   severity: medium
   remediation: "Add the missing tags or use provider default_tags."
   cloud_target: aws

policies/sc28_encryption_aws.rego
   control_id: SC-28
   severity: high
   remediation: "Add aws_s3_bucket_server_side_encryption_configuration for the bucket."
   cloud_target: aws