# Awesome-Data-Versioning-Historical-Recovery

# Awesome-Data-Versioning-Historical-Recovery

**Top Data Versioning Historical Recovery (Opensource) 🌟 Star if you like it! 🌟**



**Curated List of SaaS Products & Open-Source GitHub Projects**

*Focused on Time Travel, Data Branching, Snapshot Isolation & Self-Hosted Version Control*

**Last updated: November 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Data Versioning & Historical Recovery**. These tools enable organizations to snapshot, branch, and roll back data states—recovering from corruption, reproducing experiments, and auditing changes—from fully managed warehouse time travel to open-source version control engines that treat data like code.



**Examples** include Snowflake Time Travel, Databricks Delta Lake Time Travel, lakeFS, DVC, TerminusDB, Nessie, Git LFS, Pachyderm, Apache Iceberg, and DoltHub (the category leaders in commercial and open-source space).



**Open-source emphasis**: This section is expanded with every relevant project for self-hosted data versioning, snapshot isolation, and open historical recovery infrastructure. **Critical note**: The open-source landscape is exceptionally strong—**lakeFS** provides Git-like branching over object storage, **DVC** versions datasets alongside Git, and **Nessie** adds Git semantics to Iceberg catalogs. No open-source project matches Snowflake's zero-config time travel, but for teams wanting control over their versioning layer, the options are production-proven.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **Snowflake Time Travel**

  **Native historical data access** within Snowflake. Query data as of a past timestamp or before a specific statement; restore tables, schemas, and databases. **Pricing**: **Included in storage costs**—historical data is billed as retained bytes; retention defaults to **1 day (Standard Edition)** or up to **90 days (Enterprise Edition)** . **Free tier**: Trial credits. **Best for**: Snowflake customers wanting zero-config recovery and audit—**trade-off**: storage costs accrue for retained history; transient tables limit retention to 1 day to control costs .



- **Databricks Delta Lake Time Travel**

  **Version and timestamp queries** over Delta Lake tables. Query by version number (`VERSION AS OF`) or timestamp (`TIMESTAMP AS OF`); default retention **30 days** (configurable); `DESCRIBE HISTORY` lists available versions . **Pricing**: **Open-source Delta Lake is free** (Apache 2.0); Databricks managed plans start at **$0.07/DBU (Standard)** or **$0.22/DBU (Premium)** . **Free tier**: Delta Lake open source; Databricks Community Edition limited. **Best for**: Databricks and Spark teams wanting table-level versioning—**trade-off**: `VACUUM` is required to reclaim storage from old versions .



- **lakeFS Cloud**

  **Managed Git-like versioning for data lakes**. **Pricing**: **Open-source lakeFS is free forever**; **Enterprise is contact-sales** (unlimited seats, support, SLA) . **Free tier**: Yes, open-source edition. **Best for**: teams wanting managed branching over object storage—**trade-off**: enterprise pricing opaque; storage costs from cloud provider remain separate.



- **Nessie (Commercial)**

  **Git-like catalog for Iceberg** with managed options. **Pricing**: **On-prem is custom**; **Team plan $80/seat/month** (shared skill layer, team analytics) . **Note**: The pricing page at nessielabs.com appears to describe a different product (AI context sync) in some tiers; verify what you are buying. **Free tier**: 7-day trial. **Best for**: teams wanting managed Nessie—**trade-off**: product identity confusion in pricing tiers; verify scope.



- **Pachyderm Enterprise (HPE)**

  **Data versioning and pipeline platform** for Kubernetes. **Pricing**: **Community Edition is free and open source** (Apache 2.0); **Enterprise is custom commercial** (Console UI, RBAC/OIDC, multi-cluster DR, 24/7 HPE SLA) . **Free tier**: Yes, Community Edition. **Best for**: ML teams wanting reproducible pipelines with data versioning—**trade-off**: Enterprise requires HPE engagement; Community lacks enterprise auth.



- **DoltHub Pro**

  **Hosted Dolt databases** (Git for data). **Pricing**: **Public databases free**; **Pro: first 100 MB free, then $5/month up to 5 GB, $1/GB/month beyond** . **Free tier**: Public databases; 100 MB private storage. **Best for**: teams wanting SQL with Git-like version control—**trade-off**: storage-based pricing; small free tier.



- **Git LFS (GitHub)**

  **Large file versioning** within Git. **Pricing**: **Free tier: 10 GiB storage + 10 GiB bandwidth/month** (GitHub Free/Pro); **Team/Enterprise: 250 GiB each**; overages billed per GiB . **Free tier**: Yes, 10 GiB. **Best for**: versioning large files alongside code—**trade-off**: not designed for datasets; storage and bandwidth costs accumulate.



- **Apache Iceberg (Managed)**

  **Open table format** with snapshot isolation and time travel. **Pricing**: **Specification is free**; managed services (Snowflake, Databricks, AWS) charge for compute and storage; retention and snapshot expiry are configurable but **object-store lifecycle rules must be coordinated** to avoid orphaned files . **Free tier**: N/A (specification). **Best for**: lakehouse architectures needing vendor-neutral table versioning—**trade-off**: snapshot retention costs are your responsibility.



## Open-Source GitHub Projects



- **lakeFS**

  **Git-like version control for data lakes** (Apache 2.0) — **the most complete open-source data versioning platform**, providing branching, committing, and merging over object storage. **Features**: **Zero-copy branching**—create isolated environments without duplicating data; **atomic commits** and merges; **format-agnostic**—works with Parquet, ORC, Avro, and any file format; **data CI/CD hooks** for validation before merge; **garbage collection** for expired commits; integrates with Spark, Trino, and Presto. **Tech stack**: Go. **Deploy**: Self-hosted (Docker, Kubernetes) or lakeFS Cloud. **Trade-off**: **Object-storage layer**—it versions files, not table metadata; pair with Iceberg/Delta for table-level semantics. **Best for**: data engineering teams wanting dev/test/prod isolation and rollback without copying petabytes.



- **DVC (Data Version Control)**

  **Git-based version control for datasets and ML models** (Apache 2.0) — **the standard for ML data versioning**, used by thousands of teams. **Features**: **Git-compatible**—`.dvc` files track data pointers while Git versions the pointers; **remote storage** (S3, GCS, Azure, SSH); **pipeline versioning** (`dvc.yaml`) for reproducible ML workflows; **experiment tracking**; **VS Code extension, CLI, and Python API** . **Tech stack**: Python. **Deploy**: Self-hosted (CLI) or DVC Studio (managed UI). **Trade-off**: **Pointer-based, not snapshot-based**—you manage storage backends; no query-time time travel like Snowflake. **Best for**: ML teams wanting Git-native dataset versioning without a database.



- **Nessie**

  **Transactional catalog with Git-like semantics for Iceberg** (Apache 2.0) — **the open-source engine behind Dremio Arctic**. **Features**: **Branching, tagging, and merging** for Iceberg tables; **snapshot isolation** for concurrent writers; **version history** with rollback; **Iceberg REST Catalog** compatibility. **Tech stack**: Java. **Deploy**: Self-hosted. **Trade-off**: **Iceberg-specific**—it manages table metadata, not raw files or datasets outside Iceberg. **Best for**: teams wanting Git workflows for their Iceberg lakehouse—dev/test isolation without data copies.



- **TerminusDB**

  **Open-source document graph database with Git-for-data** (Apache 2.0) — **the most database-native versioning engine**, built around immutable revisions and branching. **Features**: **Immutable, revision-based storage**—every change is a commit; **branching and merging** like Git; **document graph model** with schema validation; **time travel queries**; **DFRNT Hub** for managed hosting with free tier . **Tech stack**: Prolog, Rust. **Deploy**: Self-hosted or DFRNT managed. **Trade-off**: **Graph/document model**—not a drop-in for relational or lakehouse workloads. **Best for**: applications needing versioned, auditable knowledge graphs—especially regulated data products.



- **Pachyderm (Community)**

  **Kubernetes-native data versioning and pipelines** (Apache 2.0) — **the most ML-pipeline-oriented versioning tool**. **Features**: **Commit-based data versioning**—every pipeline output is versioned; **automatic lineage** between data and code; **parallel processing** with Kubernetes; **branching and rollback**. **Tech stack**: Go. **Deploy**: Self-hosted (Kubernetes). **Trade-off**: **Kubernetes required**—not for teams without cluster infrastructure; Community lacks enterprise auth. **Best for**: ML teams running reproducible pipelines on Kubernetes.



### Additional Strong Open-Source Options



- **Git LFS** — Git extension for large files (MIT). Free 10 GiB on GitHub; self-hosted servers exist (e.g., `git-lfs-server` with S3-compatible backends at ~$83/year for 1 TiB on Backblaze B2) . **Note**: File-level versioning, not dataset-aware. **Best for**: versioning models or artifacts alongside code.

- **Apache Iceberg** — Open table format with snapshot isolation (Apache 2.0). Time travel and rollback at table level; retention is user-managed. **Best for**: lakehouse tables needing vendor-neutral versioning.



**Frameworks for building custom systems**: Combine **lakeFS** for file-level branching with **Nessie** for Iceberg catalog versioning and **DVC** for ML experiment tracking—creating a layered versioning stack. **None of these match Snowflake's zero-config time travel**, but for teams wanting control and multi-engine compatibility, the open-source options cover most needs.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, license (for open-source), and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Data versioning platforms handling production data must comply with data protection regulations (GDPR, CCPA, etc.) and implement appropriate retention and deletion policies—**retained historical data may contain personal information that should have been deleted**.

- **The "warehouse time travel" vs. "file-level branching" vs. "catalog versioning" vs. "ML dataset versioning" distinction is critical.** **Snowflake and Databricks** provide **warehouse time travel**—query historical table states without managing files . **lakeFS** provides **file-level branching**—Git-like operations over object storage files . **Nessie** provides **catalog versioning**—Git semantics for Iceberg table metadata . **DVC** provides **ML dataset versioning**—pointers in Git, data in remote storage . **Choose based on whether you need query-time rollback, file isolation, catalog branching, or experiment reproducibility.**

- **Snowflake Time Travel costs are baked into storage billing.** Transient tables cap retention at 1 day and eliminate Fail-safe costs—**use them for ETL work tables** . **Long-lived fact tables should be permanent** to ensure Fail-safe protection.

- **Databricks Delta Lake Time Travel is free in open source** but requires `VACUUM` to reclaim storage from old versions—**without VACUUM, storage grows indefinitely** . **Default retention is 30 days**; configure based on your recovery SLA .

- **lakeFS Open Source is free forever with almost all features**—Enterprise adds support and unlimited seats but pricing is opaque . **For teams wanting Git-for-data without lock-in, it is the strongest open-source option.**

- **Nessie's commercial pricing page is confusing.** The $80/seat Team plan appears to describe an AI context product, not the Iceberg catalog . **Verify what you are buying before engaging sales.**

- **Pachyderm Community is free but requires Kubernetes.** Enterprise adds RBAC/OIDC and 24/7 HPE support at custom pricing . **For teams without Kubernetes expertise, it is not a viable starting point.**

- **DoltHub Pro is cheap**—$5/month for up to 5 GB private storage . **For SQL workloads needing Git semantics, it is the lowest-cost entry point.**

- **Git LFS free tier is 10 GiB**—sufficient for models and small datasets, not production data lakes . **Self-hosted LFS servers with Backblaze B2 can cost ~$83/year for 1 TiB** .

- Self-hosted open-source solutions require proper infrastructure (object storage for lakeFS, Kubernetes for Pachyderm, Python for DVC), security hardening, and ongoing maintenance. **Versioned data may retain sensitive information**—ensure your retention policies comply with privacy regulations before enabling long-term history.



---



**Made for data engineers, platform teams, and organizations building transparent data versioning solutions.**

Let's make Data Versioning & Historical Recovery more open, data-driven, and recovery-ready.
