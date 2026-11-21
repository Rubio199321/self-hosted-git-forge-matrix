# Self-Hosted Git Forge Matrix

> **Decision:** Choose how much collaboration and DevOps surface the forge must own, from SSH authorization through review-centric workflow to an integrated platform.

**For:** A developer team moving repositories, issues, code review, CI, and packages off a hosted forge.  

This is a non-commercial, source-traceable decision guide. It normalizes upstream declarations; it does not claim that repository reachability proves functionality, security, maintenance, or fitness.

**Start here:** [Download the forge workflow matrix](assets/forge-workflow-matrix.csv) — twelve projects, located upstream evidence, and explicit unknowns.

## Choose by workload


- Lightweight all-purpose forge: Gitea, Forgejo, Gogs, or GitBucket, after testing importers and actions/plugins.
- Integrated DevOps: GitLab CE or OneDev, accepting their greater operational ownership.
- Review-first workflow: Gerrit; SSH authorization without a web forge: Gitolite.
- Extensible JVM administration: SCM-Manager; classic project forge: Apache Allura or Pagure.
- Soft Serve is retained only as historical SSH-first context because upstream sunset it and ended security updates.

## Start with the collaboration unit

SSH authorization, patch-set review and pull-request platforms are not interchangeable. A forge UI does not by itself preserve CI, packages or review history.

## Collaboration model map


- **General lightweight forges** — Gitea, Forgejo, Gogs, and GitBucket cover repositories and issue/review workflows with different ecosystems and migration compatibility.
- **Integrated platforms** — GitLab CE and OneDev also own CI or packages; their databases, object storage, runners, and upgrades are one operating system.
- **Specialized Git collaboration** — Gerrit centers patch-set review; Gitolite centers SSH authorization; neither should be scored as a GitHub-clone UI.
- **Extensible or classic forges** — SCM-Manager, Apache Allura, and Pagure expose plugin or project-hosting models; verify current canonical docs and migration exporters.
- **Historical context** — Soft Serve demonstrates an SSH-first terminal forge, but upstream has sunset it and promises no further security updates.


## Forge workflow matrix

| Project | Role | Review and collaboration unit | CI or package ownership | Migration and state surface |
|---|---|---|---|---|
| Gitea | lightweight general forge | Expected workflow is: Fork -> Patch -> Push -> Pull Request | team collaboration, package registry and CI/CD which can reuse GitHub Actions. | We maintain a list of Gitea-related projects at gitea/awesome-gitea, where you can discover more third-party projects, including SDKs, plugins, themes, and more… |
| GitLab CE | integrated DevOps platform | If you wish to clone a copy of GitLab without proprietary code, you can use the read-only mirror of GitLab located at https://gitlab.com/gitlab-org/gitlab-foss/… | - Complete continuous integration (CI) and continuous deployment/delivery (CD) pipelines to build, test, and deploy your applications | - Manage Git repositories with fine grained access controls that keep your code secure |
| OneDev | integrated DevOps forge | Integrate with Renovate to update project dependencies via pull requests. Merge pull requests automatically when approved by required reviewers, or pass require… | CI/CD pipeline, to facilitate code review. Demo | Arrange gadgets in custom dashboard to get important information at a glance. Share dashboard with users or groups, or make it public for everyone. See It In Ac… |
| GitBucket | JVM forge | - Issues, Pull Requests and Wiki for repositories | Unknown in the frozen upstream README | Note 1: GitBuclet 4.47.0 and 4.48.0 contain large database migrations affecting core tables such as REPOSITORY and ACCOUNT. We strongly recommend backing up you… |
| Soft Serve | historical SSH-first forge | Unknown in the frozen upstream README | hooks. Defining global hooks is useful if you want to run CI/CD for example. | To continue innovating in this space and supporting our most important work, we’ve sunset Soft Serve. The code will continue to be open source and publicly avai… |
| Gitblit | traditional Git server | Unknown in the frozen upstream README | Unknown in the frozen upstream README | 1. Import the gitblit project into your Eclipse workspace. |
| SCM-Manager | extensible SCM platform | Unknown in the frozen upstream README | Unknown in the frozen upstream README | The separate build-plugins build imports the same catalog through its settings file. Node and Yarn versions are also centralized in the catalog and accessed wit… |
| Gogs | compact general forge | - Pull requests with merge commit, rebase and squash merges, inline reviews\ and stacks\. | - Actions\ and compute\. - Packages\ and hosting\. | - SHA-256 repositories, deploy keys and LFS (local or S3\). - Forks, mirrors and migration from other code hosts, with GitHub two-way sync\. |
| Forgejo | community general forge | pull requests, wikis, kanban boards and much more to coordinate with your team. | or use the package registry to publish it for docker, npm and many other package managers. | Unknown in the frozen upstream README |
| Gerrit Code Review | review-centric forge | Note that we do not accept Pull Requests via the GitHub mirror. | NOTE: release is a counter that starts with 1 and indicates the number of packages that have been released with the same version of the software. | The instruction how to configure GerritForge/BinTray repositories is here |
| Pagure | classic project forge | Unknown in the frozen upstream README | Unknown in the frozen upstream README | Unknown in the frozen upstream README |
| Apache Allura | project forge | Unknown in the frozen upstream README | Unknown in the frozen upstream README | Allura is an open source implementation of a software "forge", a web site that manages source code repositories, bug reports, discussions, mailing lists, wiki p… |

Values are short excerpts from the frozen upstream README, not feature-test scores. The CSV retains the located evidence for each cell. “Unknown” means the retrieved document did not establish that axis; it is not a claim that the feature is absent.

## Assemble the minimal stack


Inventory repositories, issues, pull/merge requests, LFS, wiki, releases, packages, CI secrets, deploy keys, webhooks, users, and audit history separately. Trial one repository with protected branches and CI. Keep the old forge read-only until hashes, permissions, issues, and clone URLs are reconciled.


## Adoption notes by project

### Gitea

- **Choose it for:** Small teams wanting a broad lightweight forge.
- **License at the frozen source:** [MIT](https://raw.githubusercontent.com/go-gitea/gitea/6f8ebc0b2fb0eb247273f7da4059c5e5999de691/LICENSE).
- **Adoption test:** Test source-forge importers, Actions runner isolation, LFS/packages, auth, and full repository-plus-database restore.
- **Source:** [go-gitea/gitea](https://github.com/go-gitea/gitea).

### GitLab CE

- **Choose it for:** Teams deliberately consolidating DevOps capabilities.
- **License at the frozen source:** [open-core: MIT CE plus proprietary/source-available ee code](https://raw.githubusercontent.com/gitlabhq/gitlabhq/d7b9a6176ab4e279465ba3ee09922cde2b74de47/LICENSE).
- **Adoption test:** Upstream describes open-core licensing: CE is MIT while ee files are proprietary/source-available. Scope runners, registry, object storage, and upgrades.
- **Source:** [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq) (official mirror; [canonical GitLab source](https://gitlab.com/gitlab-org/gitlab)).

### OneDev

- **Choose it for:** Teams preferring one integrated application.
- **License at the frozen source:** [MIT root grant; inspect separately supplied components before adoption](https://raw.githubusercontent.com/theonedev/onedev/852a011a10c0177b0dad690edea7c0285a9c7de2/license.txt).
- **Adoption test:** Validate runner isolation, build storage, package retention, identity, and migration exporters before consolidating.
- **Source:** [theonedev/onedev](https://github.com/theonedev/onedev).

### GitBucket

- **Choose it for:** Straightforward JVM deployments.
- **License at the frozen source:** [Apache-2.0](https://raw.githubusercontent.com/gitbucket/gitbucket/4b217c482812badc03b1471b199aaf1548db02ca/LICENSE).
- **Adoption test:** Upstream warns some releases require major database or H2 migration; back up and rehearse upgrades.
- **Source:** [gitbucket/gitbucket](https://github.com/gitbucket/gitbucket).

### Soft Serve

- **Choose it for:** Readers studying a compact terminal-first design.
- **License at the frozen source:** [MIT](https://raw.githubusercontent.com/charmbracelet/soft-serve/e87b6c01725c8f5fc3632dfc7e01c1d3f4573840/LICENSE).
- **Adoption test:** Upstream sunset the project, archived the repository, and states no further security updates; exclude from new production shortlists.
- **Source:** [charmbracelet/soft-serve](https://github.com/charmbracelet/soft-serve).

### Gitblit

- **Choose it for:** Compact established Git hosting.
- **License at the frozen source:** [Apache-2.0](https://raw.githubusercontent.com/gitblit-org/gitblit/569d430f299b51b203bce88bc4c8e866a8bd009b/LICENSE).
- **Adoption test:** Repository README uses README.markdown; verify current release cadence, identity integration, LFS, and migration scope.
- **Source:** [gitblit-org/gitblit](https://github.com/gitblit-org/gitblit).

### SCM-Manager

- **Choose it for:** Teams valuing a managed plugin ecosystem.
- **License at the frozen source:** [AGPL-3.0 at the frozen current revision; historical BSD terms do not describe this checkout](https://raw.githubusercontent.com/scm-manager/scm-manager/b14c0fb2f16eed8f6716e0377fe2007676b68fc1/LICENSE.txt).
- **Adoption test:** The frozen root LICENSE is AGPL-3.0, not the historical BSD grant. Check plugins, authentication, full backup and the license of the selected release.
- **Source:** [scm-manager/scm-manager](https://github.com/scm-manager/scm-manager).

### Gogs

- **Choose it for:** Very small installations wanting a long-established forge.
- **License at the frozen source:** [MIT](https://raw.githubusercontent.com/gogs/gogs/abd4df3745de4316a21e963c0cdba924ba45b2d1/LICENSE).
- **Adoption test:** API support is described as experimental upstream; test migration, hooks, LFS, security settings, and release cadence.
- **Source:** [gogs/gogs](https://github.com/gogs/gogs).

### Forgejo

- **Choose it for:** Teams wanting a community-governed Gitea-family forge.
- **License at the frozen source:** [GPL-3.0-or-later for v9 and later; pre-v9 releases were MIT](https://codeberg.org/forgejo/forgejo/raw/commit/71d3fb8767dc89a14b283b6d3e08c91a66d52525/LICENSE).
- **Adoption test:** Canonical source is Codeberg, not a GitHub convenience mirror; test migration compatibility and runner security for the chosen release.
- **Source:** [forgejo/forgejo](https://codeberg.org/forgejo/forgejo).

### Gerrit Code Review

- **Choose it for:** Teams whose primary unit is code review rather than pull requests.
- **License at the frozen source:** [Apache-2.0](https://gerrit.googlesource.com/gerrit/+/b7573770408b832f2f8ccd890da9541db24d2623/COPYING?format=TEXT).
- **Adoption test:** Canonical clone is gerrit-review.googlesource.com; plan account mapping, review-history migration, plugins, and index backup.
- **Source:** [gerrit-review.googlesource.com/gerrit](https://gerrit-review.googlesource.com/gerrit).

### Pagure

- **Choose it for:** Teams studying or operating the Pagure workflow.
- **License at the frozen source:** [GPL-2.0-or-later](https://forge.fedoraproject.org/apps/pagure/raw/commit/89293fe6500e5ca2f8df389f4bec1a9da71ab75b/LICENSE).
- **Adoption test:** pagure.io is a read-only sunset archive; use the Fedora Forge repository as canonical and re-check deployment documentation.
- **Source:** [forge.fedoraproject.org/apps/pagure](https://forge.fedoraproject.org/apps/pagure).

### Apache Allura

- **Choose it for:** Organizations needing a classic integrated project forge.
- **License at the frozen source:** [Apache-2.0](https://raw.githubusercontent.com/apache/allura/2ca94f7931ab38c33d0eecc51f8f74c0077c1540/LICENSE).
- **Adoption test:** Confirm supported SCM tools, dependencies, identity, migration/export, and current release path; broad scope increases operating burden.
- **Source:** [apache/allura](https://github.com/apache/allura).

## Reconcile one trial repository

1. Inventory issues, reviews, CI, LFS, packages, keys and identities separately.
2. Import one trial repository with protected branches and working CI.
3. Reconcile hashes, review history and permissions from both ends.
4. Keep the old forge read-only and restore the new forge from its full state.

## What this guide covers

Developer collaboration and forge migration, not coding-agent evaluation or deployment control planes.

## Located sources and update policy

[`sources.json`](sources.json) binds each cited declaration to a commit, document, exact line range and local snapshot hash. [`assets/projects.json`](assets/projects.json) holds the normalized roles and decision axes. Current HEAD reachability is recorded separately; it is not a maintenance or security assessment. Licensing is version- and directory-specific. Re-read the selected release before adoption.

Run the local evidence and package checks, then opt into public-source reachability:

```bash
python3 scripts/verify_sources.py
python3 scripts/verify_sources.py --online
```

These checks validate source binding, excerpts, hashes, language, the decision asset and nonempty public content. They do not certify feature behavior, migration success or restore success. No popularity score, paid placement or affiliate ranking is used. Restricted-license and historical examples are explicit contrasts, not silently recommended open-source defaults.
