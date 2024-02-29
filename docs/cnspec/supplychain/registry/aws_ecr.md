---
title: Discover and Scan Elastic Container Registry (ECR) Images
sidebar_label: Elastic Container Registry (ECR)
sidebar_position: 2
displayed_sidebar: cnspec
description: This page provides an overview of how to use Mondoo to scan Elastic Container Registry for vulnerabilities in your containers.
image: /img/featured_img/mondoo-aws.jpg
---

The [Amazon Elastic Container Registry](https://aws.amazon.com/ecr/) allows you to store container images within AWS. To learn about the AWS container registry, read the [Getting Started Guide](https://aws.amazon.com/ecr/getting-started/) in the AWS documentation.

When it scans an AWS account, cnspec can automatically discover and scan all ECR images in the account.

<!-- prettier-ignore -->
import Partial from "./_providers-note.mdx";

<Partial />{" "}

## Prerequisites

Ensure you have your AWS credentials configured properly:

```bash
$ cat ~/.aws/credentials

[default]
aws_access_key_id = AKIAIOSFODNN7EXAMPLE
aws_secret_access_key = wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY

[mondoo]
aws_access_key_id = AKIAIOSFODNN7EXAMPLE
aws_secret_access_key = wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
```

If you want to use a specific profile, set `AWS_PROFILE`

```bash
export AWS_PROFILE=mondoo
```

You can also set the region:

```bash
export AWS_REGION=us-east-1
```

## Scan

After we completed the login, cnspec can scan the registry:

```bash
$ cnspec scan aws --discover ecr
→ loaded configuration from /Users/letha/.config/mondoo/mondoo.yml using source default
→ using service account credentials
→ discover related assets for 1 asset(s)
→ synchronize assets

 luna-mars@sha256:ad2e043042a33820554not396437ca2adcfee710e1022real058c7f2274a3d22 ━━━━━━━━━━━━━━ 100% score: B


Asset: luna-mars@sha256:ad2e043042a33820554not396437ca2adcfee710e1022real058c7f2274a3d22
----------------------------------------------------------------------------------------

Data queries:
os.hostname: "localhost.localdomain"
asset.title: "Ubuntu 22.04.3 LTS, Docker Image"
groups.where.list: []
asset.platform: "ubuntu"
users.where.list: [
  0: {
    name: "mwezi"
    gid: 65534
    uid: 65534
    home: "/mwezi-home"
    sshkeys: []
    shell: "/usr/sbin/mwezi"
    sid: ""
    authorizedkeys.list: []
... 3 more lines ...
command.stdout.trim: ""
python.packages: []
title: "Ubuntu 22.04.3 LTS, Docker Image"
arch: "arm64"
asset: {
  kind: "container-image"
  title: "Ubuntu 22.04.3 LTS, Docker Image"
  arch: "arm64"
  platform: "ubuntu"
  runtime: "docker-image"
  name: "luna-mars@sha256:ad2e043042a33820554c396437ca2adcfee710e1022ad058c7f2274a3d22d8d4"
}
... 1 more lines ...
machine.chassis: {
  manufacturer: ""
  serial: ""
  version: ""
  assetTag: ""
}
product: ""
machine.baseboard: {
  version: ""
  manufacturer: ""
  serial: ""
  assetTag: ""
  product: ""
}
manufacturer: ""
mount.list: []
asset.eol.date: 2027-03-31 17:00:00 -0700 PDT
command.stdout.trim: ""
machine.baseboard.product: ""
machine.bios: {
  version: ""
  releaseDate: ""
  vendor: ""
}
packages.list: [
  0: {
    version: "3.118ubuntu5"
    name: "adduser"
    origin: ""
  }
  1: {
    version: "2.4.11"
    name: "apt"
    origin: ""
... 497 more lines ...
services.where.list: []
command.stdout.trim.+: "M"
asset.arch: "arm64"
machine.system: {
  sku: ""
  serial: ""
  family: ""
  version: ""
  product: ""
  uuid: ""
  manufacturer: ""
}
mondoo.version: "9.14.0"
packages.list: [
  0: package name="adduser" version="3.118ubuntu5"
  1: package name="apt" version="2.4.11"
  2: package name="base-files" version="12ubuntu4.4"
  3: package name="base-passwd" version="3.5.52build1"
  4: package name="bash" version="5.1-6ubuntu1"
  5: package name="bsdutils" version="1:2.37.2-4ubuntu3"
  6: package name="coreutils" version="8.32-4.1ubuntu1"
  7: package name="dash" version="0.5.11+git20210903+057cd650a4ed-3build1"
  8: package name="debconf" version="1.5.79ubuntu1"
... 93 more lines ...
asset.version: "22.04"
if: "Unknown"
"ubuntu"
""
kernel.modules: []
machine.baseboard.manufacturer: ""
version: "22.04"
asset: {
  build: ""
  version: "22.04"
  platform: "ubuntu"
}
platform: "ubuntu"

Checks:
✕ Fail:  C  50  Ensure filesystem integrity is regularly checked
✓ Pass:  A 100  Ensure permissions on all logfiles are configured
✓ Pass:  A 100  Ensure Avahi server is stopped and not enabled
✓ Pass:  A 100  Ensure NFS and RPC are stopped and not enabled
✓ Pass:  A 100  Ensure DNS server is stopped and not enabled
✕ Fail:  B  60  Ensure audit log storage size is configured
✓ Pass:  A 100  Ensure system accounts are non-login
✓ Pass:  A 100  Ensure rsync service is stopped and not enabled
✓ Pass:  A 100  Ensure shadow group is empty
✕ Fail:  C  50  Ensure auditd is installed
✓ Pass:  A 100  Ensure SNMP server is stopped and not enabled
✓ Pass:  A 100  Ensure telnet server is stopped and not enabled
✓ Pass:  A 100  Ensure Samba is stopped and not enabled
✕ Fail:  C  50  Ensure unsuccessful unauthorized file access attempts are collected
✕ Fail:  B  60  Ensure audit logs are not automatically deleted
✕ Fail:  C  50  Ensure rsyslog Service is enabled
✓ Pass:  A 100  Ensure X Window System is not installed
✓ Pass:  A 100  Ensure root group is empty
✕ Fail:  C  50  Ensure rsyslog default file permissions configured
✕ Fail:  D  25  Ensure TCP SYN Cookies is enabled
. Skipped:      Ensure secure permissions on /etc/gshadow- are set
✓ Pass:  A 100  Ensure HTTP Proxy server is stopped and not enabled
✕ Fail:  D  25  Ensure secure ICMP redirects are not accepted
✓ Pass:  A 100  Ensure HTTP servers are stopped and not enabled
. Skipped:      Ensure secure permissions on /etc/group- are set
✓ Pass:  A 100  Ensure no known platform advisories exist
✓ Pass:  A 100  Ensure no duplicate UIDs exist
✕ Fail:  D  25  Ensure bogus ICMP responses are ignored
✕ Fail:  C  40  Ensure Advanced Intrusion Detection Environment (AIDE) is installed
✕ Fail:  D  25  Ensure ICMP redirects are not accepted
✓ Pass:  A 100  Ensure LDAP server is stopped and not enabled
. Skipped:      Ensure secure permissions on /etc/passwd- are set
✓ Pass:  A 100  Ensure sudo logging is enabled
✓ Pass:  A 100  Ensure rsh server is stopped and not enabled
✕ Fail:  D  10  Ensure address space layout randomization (ASLR) is enabled
✓ Pass:  A 100  Ensure secure permissions on /etc/gshadow are set
✓ Pass:  A 100  Ensure IMAP and POP3 server is stopped and not enabled
! Error:        Ensure successful file system mounts are collected
✓ Pass:  A 100  Ensure tftp server is stopped and not enabled
✕ Fail:  B  60  Ensure events that modify user/group information are collected
. Skipped:      Ensure journald is configured to compress large log files
✓ Pass:  A 100  Ensure default group for the root account is GID 0
✕ Fail:  B  60  Ensure session initiation information is collected
✓ Pass:  A 100  Ensure login and logout events are collected
✓ Pass:  A 100  Ensure events that modify date and time information are collected
✕ Fail:  B  60  Ensure system is disabled when audit logs are full
✓ Pass:  A 100  Ensure file deletion events by users are collected
✓ Pass:  A 100  Ensure access to the su command is restricted
✓ Pass:  A 100  Ensure DHCP server is stopped and not enabled
✓ Pass:         Platform is not end-of-life
✓ Pass:         Ensure the platform is not near or currently end-of-life
✕ Fail:  D  25  Ensure packet redirect sending is disabled
✓ Pass:  A 100  Ensure events that modify the system\'s network environment are collected
✓ Pass:  A 100  Ensure secure permissions on /etc/shadow are set
✓ Pass:  A 100  Ensure secure permissions on /etc/passwd are set
✓ Pass:  A 100  Ensure mail transfer agent is configured for local-only mode
✓ Pass:  A 100  Ensure prelink is disabled
✓ Pass:  A 100  Ensure talk server is stopped and not enabled
✕ Fail:  C  40  Ensure broadcast ICMP requests are ignored
✓ Pass:  A 100  Ensure system administrator actions (sudolog) are collected
. Skipped:      Ensure journald is configured to write logfiles to persistent disk
. Skipped:      Ensure secure permissions on /etc/shadow- are set
✕ Fail:  D  25  Ensure IP forwarding is disabled
✕ Fail:  C  50  Ensure auditing for processes that start prior to auditd is enabled
✕ Fail:  C  50  Ensure rsyslog is installed
. Skipped:      Ensure journald is configured to send logs to rsyslog
✓ Pass:  A 100  Ensure CUPS is stopped and not enabled
✓ Pass:  A 100  Ensure FTP server is stopped and not enabled
✓ Pass:  A 100  Ensure each user is a member of a group
✓ Pass:  A 100  Ensure the audit configuration is immutable
✕ Fail:  D  25  Ensure IPv6 router advertisements are not accepted
✕ Fail:  C  50  Ensure changes to system administration scope (sudoers) is collected
✕ Fail:  C  50  Ensure discretionary access control permission modification events are collected
✓ Pass:  A 100  Ensure no duplicate GIDs exist
✕ Fail:  C  50  Ensure auditd service is enabled
✓ Pass:  A 100  Ensure no duplicate group names exist
! Error:        Ensure events that modify the system\'s Mandatory Access Controls are collected
✕ Fail:  D  25  Ensure core dumps are restricted
✕ Fail:  C  50  Ensure kernel module loading and unloading is collected
✓ Pass:  A 100  Ensure no duplicate user names exist
✓ Pass:  A 100  Ensure secure permissions on /etc/group are set
✕ Fail:  C  40  Ensure suspicious packets are logged
✕ Fail:  D  25  Ensure source routed packets are not accepted
✓ Pass:  A 100  Ensure NIS server is stopped and not enabled
✓ Pass:  A 100  Ensure UID_MIN is set to 1000
✕ Fail:  D  25  Ensure Reverse Path Filtering is enabled
✓ Pass:  A 100  Ensure all GIDs in /etc/passwd exist in /etc/group

Vulnerabilities:
  ■  SCORE  PACKAGE         INSTALLED          FIXED             AVAILABLE
  ■  0      libpam-modules  1.4.0-11ubuntu2.3  1.5.2-6ubuntu1.1

Overall CVSS score: 0.0


Scanned 1 asset

Ubuntu 22.04.3 LTS
    B luna-mars@sha256:ad2e043042a33820554c396437ca2adcfee710e1022ad058c7f2274a3d22d8d4

See more scan results and asset relationships on the Mondoo Console: https://edge.console.mondoo.com/space/fleet/2b8va6KZDNOVql0f5fLlakhZUfl?spaceId=distracted-hawking-771479
```

---
