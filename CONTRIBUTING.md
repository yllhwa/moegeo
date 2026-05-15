# 贡献指南 / Contributing Guidelines

感谢您向 Moegeo 提供 Geofeed 数据！请遵循以下指南以确保您的提交能够被快速处理。

## 提交格式

请在 `feeds/` 目录下创建一个 YAML 文件，文件名为您的自治系统号（例如：`AS12345.yml`）。文件内容如下：

```yaml
name: "您的组织或公司名称"
asn: "AS12345"
contact: "noc@example.com"
geofeed_urls:
  - "https://example.com/geofeed.csv"
  - "https://example.com/geofeed-v6.csv"
```

### 必填字段说明：
- `name`: 您的网络或组织全称。
- `asn`: 您的自治系统号，必须以大写 `AS` 开头。
- `contact`: 您的技术联系人邮箱。
- `geofeed_urls`: 一个包含 Geofeed URL 的列表。至少包含一个 URL。

## Geofeed URL 规范
您提供的 URL 必须：
1. 是 HTTP 或 HTTPS 协议。
2. 可公开访问且返回 `200 OK` 状态。
3. 内容严格符合 [RFC 8805](https://datatracker.ietf.org/doc/html/rfc8805) 的 CSV 格式。
   示例格式：
   ```csv
   192.0.2.0/24,US,US-WA,Seattle,
   2001:db8::/32,CN,CN-BJ,Beijing,
   ```

## 自动化检查与归属权验证

当您发起 Pull Request 时，GitHub Actions 会自动运行检查：
- 您的 YAML 文件格式是否正确。
- 您提供的 URL 是否可以访问。
- URL 下载的 CSV 是否包含合法 IP 前缀。

**✅ 加速合并：GPG 签名验证**
为了防止恶意冒充，我们使用自动化归属权验证。如果满足以下两个条件，您的 PR 将被标记为“归属权已验证”，管理员可以快速合并：
1. 您的 Commit 已通过 GitHub 的 GPG 签名验证。
2. 您的签名邮箱与 RIR（RIPE/ARIN/APNIC 等）数据库中该 ASN 的 WHOIS/RDAP 记录邮箱一致。

如果未满足以上条件，您的 PR 将进入人工审核流程，管理员可能会通过您填写的邮箱与您联系确认。
