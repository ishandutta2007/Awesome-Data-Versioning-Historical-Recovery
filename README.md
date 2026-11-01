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

- [Sector Overview & Market Dynamics](#sector-overview--market-dynamics)
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)



## Sector Overview & Market Dynamics

The global data versioning and dataset recovery sector is estimated at **$527M to $2.3B+** (as part of a broader **$15B–$31B+** data backup, recovery, and time-travel resilience market), driven by strict regulatory auditing, ML model reproducibility, and ransomware point-in-time recovery. The market exhibits **moderate fragmentation with high concentration around core lakehouse/cloud data warehouse platforms**: hyper-scalers and giants (Snowflake, Databricks, Microsoft/GitHub) dominate standard analytics workloads with winner-take-most dynamics, while specialized open-table and Git-for-data providers (lakeFS/Treeverse, DoltHub, DVC) cater to niche multi-cloud and Kubernetes-native versioning workflows.



## SaaS/Hosted Platforms

| Product | Company Valuation / Revenue Scale | Starting Pricing | Free Tier Limits | Key Highlights & Trade-offs |
| :--- | :--- | :--- | :--- | :--- |
| **Git LFS (GitHub)** | Parent (Microsoft): ~$3.1T market cap; GitHub standalone ARR: **$2.0B+** | **$0.07/GiB/month** for storage + **$0.0875/GiB** for bandwidth out (metered beyond included allowance) | **Free Forever**: 10 GiB storage & 10 GiB monthly bandwidth included for GitHub Free/Pro accounts (250 GiB each for Enterprise) | Integrated directly into GitHub repositories; best for versioning large binary assets with code, but bandwidth/storage costs add up for massive datasets. |
| **Databricks Delta Lake Time Travel** | **$134B valuation**; ARR: **$5.4B+** | Managed clusters start at **$0.07/DBU** (Standard) or **$0.22/DBU** (Premium) | **14-day free trial** with up to **$400 credits**; plus **Databricks Free Edition** (free forever with serverless compute daily quotas, 1 workspace/metastore) | Native table-level versioning & rollback (`VERSION AS OF`); open-core Delta Lake is Apache-2.0; requires regular `VACUUM` to clean old Parquet files. |
| **Snowflake Time Travel** | **~$50B–$60B market cap**; Annual Revenue: **$3.63B+** (FY2025) | On-demand Standard edition starts at **$2.00/credit** compute + **$23/TB/month** storage | **30-day free trial** with **$400 usage credits** (no permanent free storage/compute tier) | Native historical time travel queries and database cloning up to 1 day (Standard) or 90 days (Enterprise); zero configuration, but historical retained bytes add storage costs. |
| **Pachyderm Enterprise (HPE)** | Parent (HPE): **~$32B market cap**; Annual Revenue: **$34.3B** | Enterprise licensing is quote-based upon contact (historically starting on custom annual contracts per cluster/worker core) | **Free Forever**: Community Edition is 100% free & open-source on Kubernetes (unlimited pipelines, lacks enterprise RBAC/SSO) | Data-driven pipelines on Kubernetes with automated data provenance and lineage; requires Kubernetes infrastructure expertise. |
| **Nessie (Dremio Cloud Catalog)** | Dremio Valuation: **$2.0B**; Total funding: $410M | Standard Pay-As-You-Go starts at **$0.20/DCU-hour** (e.g., 2XSmall engine at $3.20/hour) | **Free Forever**: Dremio Cloud Standard includes free catalog usage, capped at up to 10 users, 200 tables, and 1,000 views (plus 14-day Enterprise trial) | Catalog-level Git semantics (branch, tag, merge) for Apache Iceberg; enables isolated multi-table transactional commits without data duplication. |
| **Apache Iceberg (AWS Managed / S3 Tables & Athena)** | Amazon / AWS: ~$2.0T market cap; AWS ARR: **$100B+** | Serverless pay-as-you-go: S3 Tables at **$0.023/GB/month**; Athena queries at **$5.00/TB scanned** (min 10 MB per query) | **12-month AWS Free Tier**: 5 GB S3 Standard storage, 20,000 GET requests, 2,000 PUT requests/month (Athena SQL queries have no free tier) | Open specification; zero license fee; vendor-neutral snapshot isolation; storage lifecycle rules and snapshot expiration must be managed to avoid orphan files. |
| **lakeFS Cloud** | Total funding: **$43M** (Series B in 2025; Dell / Norwest backed) | lakeFS Team Edition starts at **$499/month** (lakeFS Cloud Enterprise via quote) | **30-day free trial** for lakeFS Cloud / Team; lakeFS Community Edition is **free forever** self-hosted (capped at 1 user) | Git-like branching, merging, and commits over AWS S3, Azure Blob, or GCS object storage; versions unstructured and structured data alike without byte duplication. |
| **DoltHub Pro** | Total funding: **$21M–$23M** (Series B) | DoltHub Pro starts at **$5/month** (covers up to 5 GB; $1/GB/month beyond); Hosted Dolt instances start at **$50/month** | **Free Forever**: First 100 MB of private storage is free; public databases are 100% free with unlimited size; CLI open source is completely free | "Git for data" with full MySQL/PostgreSQL compatibility; supports branch, merge, diff, and cell-level conflict resolution directly in SQL. |



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
