# Moegeo Geofeed Community Repository

由 MoeDove LLC 维护的社区驱动型 Geofeed 聚合仓库。

本仓库旨在为网络运营商提供一个集中展示和聚合 [RFC 8805](https://datatracker.ietf.org/doc/html/rfc8805) 格式 Geofeed 文件的平台。通过聚合各家的 Geofeed，第三方定位服务商可以更便捷地获取和更新 IP 地理位置信息。

## 🚀 如何提交您的 Geofeed？(How to submit)

我们**不**在仓库中直接存储您的 IP 数据，而是让您提交您自己托管的 `geofeed.csv` 的 URL。

1. **Fork 本仓库**。
2. 复制 `feeds/example.yml` 并以您的 ASN 命名（例如：`AS12345.yml`），放入 `feeds/` 目录。
3. 在 YAML 文件中填入您的网络信息和 Geofeed URL。
4. **提交 Pull Request (PR)**。

我们的 GitHub Actions 将自动验证您提供的文件格式及 URL 的可达性和有效性。

### 🛡️ 归属权验证 (Ownership Validation)
如果您在提交 PR 时的 Commit 进行了 [GPG 签名验证](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification)，并且该 Commit 邮箱与您 ASN 在 RIR (WHOIS/RDAP) 中注册的邮箱一致，系统将自动通过归属权验证，加快合并速度。否则，管理员将进行人工审核。

## 💡 为什么使用 URL 提交？
- 客户只需在自己的基础设施上维护原始的 Geofeed 文件，随时更新无需反复提交 PR。
- 我们的聚合脚本每天会自动拉取最新的数据。

更多详情，请查看 [CONTRIBUTING.md](./CONTRIBUTING.md)。
