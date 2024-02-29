---
title: About Policies
id: cnspec-policies
sidebar_label: About Policies
displayed_sidebar: cnspec
sidebar_position: 1
description: Retrieve, store, customize, and create cnquery policies
image: /img/featured_img/mondoo-feature.jpg
---

Policies are the specifications that cnspec uses when it scans a system. Think of a policy as a checklist that cnspec relies on to ensure that a system is secure. In Mondoo and cnspec, these collections of security requirements are expressed as highly readable code.

## Policy as code​

Security policies and compliance frameworks typically are documents. Text describes each guideline and its rationale, and sometimes the consequences of not complying.

But documents don't check your environments. The work to verify that your infrastructure follows security standards is often manual, time intensive, and error prone. For example, if you need to manually demonstrate compliance for an audit, it can take weeks just to provide a snapshot of a single moment in time.

_Policy as code_ lets you automate compliance using security benchmarks and best practices. The code serves two purposes: It documents the security guidelines and it tests your systems to ensure they follow those guidelines.

## cnspec policies and policy bundles

Each cnspec policy is codified as a collection of checks that test for certain configuration settings. For example, the _Mondoo Linux Security - Users and Groups_ policy includes these checks:

- There are no users in the root group.
- No duplicate user names exist.
- All system accounts are non-login.

_Policy bundles_ are YAML files that contain at least one policy. They group related policies. For example, the _Mondoo Linux Security_ policy bundle contains a _Configure SSH Server_ policy that is specific to Linux, a _Logging_ policy that is specific to Linux, and other policies that define secure Linux practices.

Find policy bundles in Mondoo's [cnspec-policies](https://github.com/mondoohq/cnspec-policies) GitHub repo.

## How cnspec uses policies

When cnspec scans a target for compliance with security and other best practices, it refers to policies to learn what checks to make against the target.

For example, when you run this command, cnspec automatically detects the local platform and scans using the applicable policy or policies:

```bash
cnspec scan local
```

For example, if the local system is Windows, cnspec finds all policy bundles that apply to Windows. It runs all the checks in the policies in the Windows policy bundles.

This scan command specifies the policy bundle to use:

```bash
cnspec scan local --policy-bundle luna.mql.yaml
```

Instead of detecting the local system and finding appropriate policy bundles, cnspec refers to `luna.mql.yaml`, a custom policy bundle, to find the checks to run against the local system.

## Learn more

- To learn how to modify existing policies or write your own, read the [Policy Authoring Guide](/cnspec/cnspec-policies/write/).

- To learn about applying policies across your infrastructure and storing your own policies, read [Manage Policies](/cnspec/cnspec-policies/cnspec-manage-policies)

---
