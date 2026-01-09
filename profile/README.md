# Secure Identity Federation for Cloud-Native Infrastructure

Modern infrastructure spans multiple clouds and platforms. Identity shouldn't be the hard part.

## The Problem

Your Kubernetes pod needs to access AWS S3, a Google Cloud database, and an Azure-authenticated API. Today, you have three bad options:

1. Store static credentials (insecure, manual rotation, credential sprawl)
2. Use cloud-specific workload identity (great until you need to cross cloud boundaries)
3. Build custom federation (brittle, doesn't scale, becomes a maintenance burden)

The same problem hits CI/CD pipelines, MCP servers, service meshes, and anywhere services need to cross platform boundaries.

## Our Solution

We're building open-source tools for OAuth 2.0 token exchange that work as a universal identity translator:

### Connection Broker

Exchange any identity for any other identity with centralized policy management. Kubernetes service account → AWS credentials. GitHub OIDC token → GCP access. Cloud IAM role → MCP server token.

Configure three things:

- **Sources**: Identities in your infrastructure (K8s, Spire, AWS, GCP, Azure, OIDC)
- **Targets**: Services they need to access (APIs, MCP servers, cloud resources)
- **Grants**: Who can access what, with which permissions

### Client-Side Proxy

Zero application changes. Set HTTP_PROXY environment variable. Your app makes requests normally. The proxy handles identity exchange automatically.

### MCP Server Proxy

Secure MCP servers with path-based access control. Wrap existing REST APIs as MCP resources without code changes.

### Key Benefits

- No stored credentials - Short-lived tokens, automatic rotation
- Standards-based - OAuth 2.0 token exchange (RFC 8693), OIDC
- Multi-cloud native - Bridge any identity to any platform
- Centralized policy - One place to manage access across your infrastructure
- Full audit trail - Know who accessed what, when, and how
- Zero code changes - Transparent proxies, standard protocols

### Use Cases

- **MCP Server Authentication**: Secure AI agent access with proper identity and authorization
- **Multi-Cloud Kubernetes**: Pods accessing AWS, GCP, and Azure without stored credentials
- **CI/CD Pipelines**: GitHub Actions deploying to multiple clouds securely
- **Service Mesh Federation**: Cross-cloud service authentication
- **Developer Access**: Just-in-time, scoped access to production resources
- **B2B Integration**: External partner identity mapping with fine-grained control

## Status

🚧 Early Development - We're building in public and seeking feedback.

Coming Soon:

- Core connection broker implementation
- Client-side proxy with HTTP_PROXY support
- MCP server proxy with access control
- Detailed tutorials and reference architectures

## Get Involved

We're a small team of senior security engineers (20+ years building enterprise software) tackling a problem we've faced repeatedly: secure identity across platform boundaries shouldn't be this hard.
Interested in:

- Early access and testing?
- Contributing to design or implementation?
- Sharing your multi-cloud identity challenges?

-->
