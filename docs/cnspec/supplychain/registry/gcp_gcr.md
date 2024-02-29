---
title: Google Container Registry
sidebar_label: Google Container Registry
sidebar_position: 4
displayed_sidebar: cnspec
description: This page provides an overview of how to use Mondoo to scan Google Container Registry for vulnerabilities in your containers.
image: /img/featured_img/mondoo-gcp.jpg
---

The [Container Registry](https://cloud.google.com/container-registry/docs) allows you to store container images within Google Cloud. To learn about the Google Cloud container registry, read the Container Registry [Get Started Guide](https://cloud.google.com/container-registry/docs).

<!-- prettier-ignore -->
import Partial from "./_providers-note.mdx";

<Partial />{" "}

## Prerequisite

Install the [gcloud](https://cloud.google.com/sdk/install) command and [log in](https://cloud.google.com/sdk/gcloud/reference/auth/login) using `gcloud auth login`.

Set your project:

```bash
$ gcloud config set project <projectID>

Updated property [core/project].
```

List all available container repositories:

```bash
$ gcloud container images list

NAME
gcr.io/<projectID>/<repoName>
```

List the repositories' tags:

```bash
$ gcloud container images list-tags gcr.io/<projectID>/<repoName>

DIGEST        TAGS    TIMESTAMP
e5dd9abc37df  latest  2020-03-20T20:20:23
a98d9dcf3a34  16.04   2020-02-21T23:22:30
0925d0867157  18.04   2020-02-21T23:20:44
61844ceb1dd5  19.04   2020-01-16T02:20:47
```

To authenticate with the registry, [log in with gcloud](https://cloud.google.com/container-registry/docs/advanced-authentication#standalone-helper)

```bash
gcloud auth configure-docker
```

## Scan

To scan an individual repository, enter:

```bash
cnspec scan container registry gcr.io/<projectID>/<repoName>

  →  loaded configuration from /Users/suki/.config/mondoo/mondoo.yml
Start the vulnerability scan:
  →  resolve asset connections
  →  verify platform access to a98d9dcf3a34
  →  gather platform details
  →  detected ubuntu 16.04
  →  gather platform packages for vulnerability scan
  →  found 96 packages
  ✔  completed analysis for a98d9dcf3a34
  →  verify platform access to 0925d0867157
  →  gather platform details
  →  detected ubuntu 18.04
  →  gather platform packages for vulnerability scan
  →  found 89 packages
  ✔  completed analysis for 0925d0867157
  →  verify platform access to 61844ceb1dd5
  →  gather platform details
  →  detected ubuntu 19.04
  →  gather platform packages for vulnerability scan
  →  found 89 packages
  ✔  completed analysis for 61844ceb1dd5
  →  verify platform access to e5dd9abc37df
  →  gather platform details
  →  detected ubuntu 18.04
  →  gather platform packages for vulnerability scan
  →  found 89 packages
  ✔  completed analysis for e5dd9abc37df
Advisory Reports Overview
  ■  SCORE  NAME          SCORE
  ■  0.0    a98d9dcf3a34  ══════════
  ■  0.0    0925d0867157  ══════════
  ■  4.6    61844ceb1dd5  ══════════
  ■  0.0    e5dd9abc37df  ══════════
```

Google Cloud also ships with non-standard extensions to search images on your project level. To use those extensions, use the `gcp gcr` provider:

```bash
cnspec scan gcp gcr <projectID>
```

---
