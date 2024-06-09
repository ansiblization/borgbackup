# Ansible role for installing scheduled borgbackup jobs

The borgbackup jobs to be scheduled have to be defined as a list named `borgbackup_jobs`:

```yml
borgbackup_jobs: [{borgbackup_vars}, ...]
borgbackup_vars:
    name: "{{ borgbackup_job.name }}"
    paths: "{{ borgbackup_job.paths }}"
    repository: "{{ borgbackup_job.repository }}"
    exclude: "{{ borgbackup_job.exclude | default([]) }}"
    archive_format: "{{ borgbackup_job.archive_format | default('{now}') }}"
    encryption: "{{ borgbackup_job.encryption | default('none') }}"
    passphrase: "{{ borgbackup_job.passphrase | default(None) }}"
    compression: "{{ borgbackup_job.compression | default('zstd') }}"
    schedule: "{{ borgbackup_job.schedule | default(None) }}"
    conflicts: "{{ borgbackup_job.conflicts | default([]) }}"
    state: "{{ borgbackup_job.state | default('present') }}"
    keep_daily: "{{ borgbackup_job.keep_daily | default(7) }}"
    keep_weekly: "{{ borgbackup_job.keep_weekly | default(4) }}"
    keep_monthly: "{{ borgbackup_job.keep_monthly | default(6) }}"
```
