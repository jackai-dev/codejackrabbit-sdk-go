# CodeJackRabbit Go API

<!-- omniwrap-api-reference eyJjb250cmFjdF9maW5nZXJwcmludCI6ImIwNjc4MWEyNmM0NDY5ZThmMTI4MzBhMDRkNDU1OTU3YmY2MjBkNDJiOWUxZGYxNTVlOTNlZTAwZjI5M2QxYzkiLCJvcGVyYXRpb25fY291bnQiOjI4LCJyZW5kZXJlciI6ImdvIiwidmVyc2lvbiI6IjEuNS4wIn0 -->

This generated index is tied to Semantic IR `1.14.0` and contract fingerprint `b06781a26c4469e8f12830a04d455957bf620d42b9e1df155e93ee00f293d1c9`. Every operation below is rendered from the same semantic contract and artifact-attested public member allocation as the SDK.

SDK maturity: **experimental**  
Artifact evidence: [`omniwrap-artifact.json`](omniwrap-artifact.json) binds this file by SHA-256 and is revalidated by the package gate.

## Client hooks and tracing

`option.WithHooks(option.Hooks{...})` registers four callbacks. Every attempt starts with `BeforeRequest` and ends with exactly one of `OnRetry` (another attempt follows), `AfterResponse` (the success the call returns) or `OnError` (the failure the call reports). Each receives the operation id, the HTTP method, the URL, the request headers, the attempt number (from 1), the time elapsed since the call started and, once the server answered, the HTTP status. No context carries a credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key header and API-key query parameter, and any configured credential value read `[redacted]`. Every hook receives an `option.HookContext` value holding copies: no hook can change the request.

`option.WithTracer(tracer)` opens one span per call through the tracer interface this SDK defines, named after the operation id, with `http.request.method`, `http.response.status_code` and `http.request.resend_count`. It needs no tracing library; README.md maps it onto the OpenTelemetry API.

## Shared types

- `AuditContextRequest`
- `AuditSnapshotsRequest`
- `ComplianceGateRequest`
- `DeveloperAuditRequest`
- `DeveloperEvidenceRequest`
- `FileChange`
- `FinOpsRequest`
- `ManagedDeveloperIdentity`
- `ManagedDeveloperIdentityRequest`
- `ReviewRequest`
- `WaitlistRequest`

## Resource `DeveloperIntelligence`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJEZXZlbG9wZXJJbnRlbGxpZ2VuY2UuQ29sbGVjdEF1ZGl0IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNvbGxlY3REZXZlbG9wZXJBdWRpdCIsInBhdGgiOiIvY2xpL21hbmFnZWQvZGV2ZWxvcGVyLWF1ZGl0IiwicmVzb3VyY2UiOiJEZXZlbG9wZXJJbnRlbGxpZ2VuY2UiLCJzZWN0aW9uX3NoYTI1NiI6ImRiNzg2ZWQ1ZGY1NTU0NDI2N2RkOWQ5OTQ3YjJiYjE1ZDlkOTJkMTMwZDk0YjAzMzRhZWI1NTU3ZWI1YmY2NGIiLCJzaWduYXR1cmVfc2hhMjU2IjoiZDBmOWIxMjU1N2UwZTEyYzFkYjVjMDdiY2Q5ZTE2NzZjYzFkZjNlYjYzODllZTgyNTA5YTZhOGIxMTM3ODM0YSJ9 -->
### `client.DeveloperIntelligence.CollectAudit`

Operation ID: `collectDeveloperAudit`  
Route: `POST` `/cli/managed/developer-audit`  

#### Signature

```go
func (service *DeveloperIntelligenceService) CollectAudit(ctx context.Context, params DeveloperIntelligenceCollectAuditParams, opts ...option.RequestOption) (*Response[DeveloperIntelligenceCollectAuditParamsResponse], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `DeveloperAuditRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Versioned report with source coverage, missing evidence and immutable snapshot reference. | application/json (object) |
| `default` | Explicit authentication, paid access, source authorization, capacity or collection blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "from": "2026-01-09",
    "repositoryId": "1",
    "to": "2026-01-18"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.DeveloperIntelligence.CollectAudit(ctx, /* body */ {"from": "2026-01-09", "repositoryId": "1", "to": "2026-01-18"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjb2xsZWN0RGV2ZWxvcGVyQXVkaXQifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJEZXZlbG9wZXJJbnRlbGxpZ2VuY2UuQ3VycmVudElkZW50aXR5IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImN1cnJlbnREZXZlbG9wZXJJZGVudGl0eSIsInBhdGgiOiIvY2xpL21hbmFnZWQvZGV2ZWxvcGVyLWlkZW50aXR5IiwicmVzb3VyY2UiOiJEZXZlbG9wZXJJbnRlbGxpZ2VuY2UiLCJzZWN0aW9uX3NoYTI1NiI6Ijk2YjgyYzJhMTg5ZDc4Nzk4NmE1MzQzZTBlY2RmOGY5ZjE4ZTBmMDA1MDE3MTVkOWQxN2I2MDgxZWFhY2FkZDMiLCJzaWduYXR1cmVfc2hhMjU2IjoiM2I4YmZhMzc3MWUyZTVmYjJlOGIzNWRlMGE0ZmJmOGRiOTM2MzJhNDNhOWJhZmEwODcwYmQxOGM0MmRjZmZlOCJ9 -->
### `client.DeveloperIntelligence.CurrentIdentity`

Operation ID: `currentDeveloperIdentity`  
Route: `POST` `/cli/managed/developer-identity`  

#### Signature

```go
func (service *DeveloperIntelligenceService) CurrentIdentity(ctx context.Context, params DeveloperIntelligenceCurrentIdentityParams, opts ...option.RequestOption) (*Response[*ManagedDeveloperIdentity], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ManagedDeveloperIdentityRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Current verified identity and authorized repositories. | application/json (ManagedDeveloperIdentity) |
| `default` | Explicit account, GitHub identity or source authorization blocker. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.DeveloperIntelligence.CurrentIdentity(ctx, /* body */ {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjdXJyZW50RGV2ZWxvcGVySWRlbnRpdHkifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJEZXZlbG9wZXJJbnRlbGxpZ2VuY2UuRGVjbGFyZVByb2plY3RDb250ZXh0IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImRlY2xhcmVEZXZlbG9wZXJQcm9qZWN0Q29udGV4dCIsInBhdGgiOiIvY2xpL21hbmFnZWQvYXVkaXQtY29udGV4dCIsInJlc291cmNlIjoiRGV2ZWxvcGVySW50ZWxsaWdlbmNlIiwic2VjdGlvbl9zaGEyNTYiOiJiNTAzODRjNDBjNTQwMmViMzIzMDQ5OGY2MmY0MGVkMDc5MzY5Y2MxNWJkMDU4MDJlMGZlYTBiM2MzYWQwY2MwIiwic2lnbmF0dXJlX3NoYTI1NiI6IjU0NmIwNGZhMWUyNGZmMGQxZWJiNzMxMTk4ZWQ3OTgyMTgyMDM3ZjM3M2I3ZTFlYTc1YzU5NDUyOTNjMTRjNmEifQ -->
### `client.DeveloperIntelligence.DeclareProjectContext`

Operation ID: `declareDeveloperProjectContext`  
Route: `POST` `/cli/managed/audit-context`  

#### Signature

```go
func (service *DeveloperIntelligenceService) DeclareProjectContext(ctx context.Context, params DeveloperIntelligenceDeclareProjectContextParams, opts ...option.RequestOption) (*Response[DeveloperIntelligenceDeclareProjectContextParamsResponse], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `AuditContextRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Immutable declaration or correction receipt. | application/json (object) |
| `default` | Explicit authorization, contributor identity, correction or storage capacity blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "declaration": {
      "contributorId": "1",
      "effectiveFrom": "2026-01-02",
      "effectiveTo": "2026-01-11",
      "snapshotId": "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "source": "example",
      "supersedes": "example",
      "type": "project_join",
      "value": "example"
    },
    "repositoryId": "1"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.DeveloperIntelligence.DeclareProjectContext(ctx, /* body */ {"declaration": {"contributorId": "1", "effectiveFrom": "2026-01-02", "effectiveTo": "2026-01-11", "snapshotId": "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa", "source": "example", "supersedes": "example", "type": "project_join", "value": "example"}, "repositoryId": "1"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJkZWNsYXJlRGV2ZWxvcGVyUHJvamVjdENvbnRleHQifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJEZXZlbG9wZXJJbnRlbGxpZ2VuY2UuTWFuYWdlZEF1ZGl0U25hcHNob3RzIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6Im1hbmFnZWRBdWRpdFNuYXBzaG90cyIsInBhdGgiOiIvY2xpL21hbmFnZWQvYXVkaXQtc25hcHNob3RzIiwicmVzb3VyY2UiOiJEZXZlbG9wZXJJbnRlbGxpZ2VuY2UiLCJzZWN0aW9uX3NoYTI1NiI6IjNjYzc4MTlkMjZmMDc0OTllNTBjZDY5OTA1ZjAwOWQ3NmU5MTU1ODQ4MDRlOTM2NmFhYmU1Y2U5MjliYjcxOWMiLCJzaWduYXR1cmVfc2hhMjU2IjoiNmVmZWRhMWU2NDJkMDM1YjJiMzc5ZWRlYmU0MmVmMjBiMTkwYTMzMDNiZjkzNGNiN2EzZTY1NTEzMzkyZDI4NCJ9 -->
### `client.DeveloperIntelligence.ManagedAuditSnapshots`

Operation ID: `managedAuditSnapshots`  
Route: `POST` `/cli/managed/audit-snapshots`  

#### Signature

```go
func (service *DeveloperIntelligenceService) ManagedAuditSnapshots(ctx context.Context, params DeveloperIntelligenceManagedAuditSnapshotsParams, opts ...option.RequestOption) (*Response[DeveloperIntelligenceManagedAuditSnapshotsParamsResponse], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `AuditSnapshotsRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Snapshot list or digest-verified immutable envelope. | application/json (object) |
| `default` | Explicit authorization, expiry, missing snapshot or integrity blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "action": "list",
    "repositoryId": "1"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.DeveloperIntelligence.ManagedAuditSnapshots(ctx, /* body */ {"action": "list", "repositoryId": "1"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJtYW5hZ2VkQXVkaXRTbmFwc2hvdHMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJEZXZlbG9wZXJJbnRlbGxpZ2VuY2UuUHJvdmlkZXJDb3N0RXZpZGVuY2UiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicHJvdmlkZXJDb3N0RXZpZGVuY2UiLCJwYXRoIjoiL2NsaS9tYW5hZ2VkL2Zpbm9wcyIsInJlc291cmNlIjoiRGV2ZWxvcGVySW50ZWxsaWdlbmNlIiwic2VjdGlvbl9zaGEyNTYiOiJhYmM4YzA0N2U3MjQ4NWJhMjgzMDA5OTQ1ZjMxYzAyYmE0NDdlNjFhYTkzMzNlOWMyZTY4NzE4OTIyNmQ2ZDIwIiwic2lnbmF0dXJlX3NoYTI1NiI6IjZkNmNlZmQ5ZTQ2NzlmMzY2ZDMxMWIwMGQ3MGI1Y2YzZTVkNmVmMjNkNjU3ZjJkYzU0NzE3NzRhZmExNWJjNDEifQ -->
### `client.DeveloperIntelligence.ProviderCostEvidence`

Operation ID: `providerCostEvidence`  
Route: `POST` `/cli/managed/finops`  

#### Signature

```go
func (service *DeveloperIntelligenceService) ProviderCostEvidence(ctx context.Context, params DeveloperIntelligenceProviderCostEvidenceParams, opts ...option.RequestOption) (*Response[DeveloperIntelligenceProviderCostEvidenceParamsResponse], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `FinOpsRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Server report or declaration receipt. Unknown costs remain null. | application/json (object) |
| `default` | Explicit permission, paid access, source or declaration validation blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "action": "report"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.DeveloperIntelligence.ProviderCostEvidence(ctx, /* body */ {"action": "report"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwcm92aWRlckNvc3RFdmlkZW5jZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJEZXZlbG9wZXJJbnRlbGxpZ2VuY2UuU3VibWl0RXZpZGVuY2UiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoic3VibWl0RGV2ZWxvcGVyRXZpZGVuY2UiLCJwYXRoIjoiL2NsaS9tYW5hZ2VkL2RldmVsb3Blci1ldmlkZW5jZSIsInJlc291cmNlIjoiRGV2ZWxvcGVySW50ZWxsaWdlbmNlIiwic2VjdGlvbl9zaGEyNTYiOiI0ZDZmZWVmOTFkNTE3OWMwOTExYTlkOWQzMTI5ZWU5ODE3ODM0NGNiMWQ5MjM1NjkzYTM2Mzk5NTJiOTgxMDU0Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImNlNjk2N2M2YzExNTQxN2FjN2I1NjAyYWY0YTg3ZTc5MDI2NjA4M2RiNTc3ZGRhN2MxN2I1NzI0M2YxZTlmMzEifQ -->
### `client.DeveloperIntelligence.SubmitEvidence`

Operation ID: `submitDeveloperEvidence`  
Route: `POST` `/cli/managed/developer-evidence`  

#### Signature

```go
func (service *DeveloperIntelligenceService) SubmitEvidence(ctx context.Context, params DeveloperIntelligenceSubmitEvidenceParams, opts ...option.RequestOption) (*Response[DeveloperIntelligenceSubmitEvidenceParamsResponse], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `DeveloperEvidenceRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Accepted and duplicate span counts. | application/json (object) |
| `default` | Explicit identity, repository, paid access or evidence validation blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "category": "coding",
    "input": {},
    "repositoryId": "1"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.DeveloperIntelligence.SubmitEvidence(ctx, /* body */ {"category": "coding", "input": {}, "repositoryId": "1"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdWJtaXREZXZlbG9wZXJFdmlkZW5jZSJ9 -->

## Resource `Health`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJIZWFsdGguR2V0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0SGVhbHRoIiwicGF0aCI6Ii9oZWFsdGgiLCJyZXNvdXJjZSI6IkhlYWx0aCIsInNlY3Rpb25fc2hhMjU2IjoiNGRmYjAwNTgxYTM3MTcyMDQ4ODA2NTFmYzg0NDJkNmMxODhmNmY0OGM3YTlhMGU4YWJiZDI3MTRjNGJkOWQ0YiIsInNpZ25hdHVyZV9zaGEyNTYiOiI1ODM5MzRjNzRkMDNhYTEzYjg5MDMyMDU1MmYxZjhmODc1MGE4YWU4YWEyMzc0MzdkY2Y2MWMzOGJkZDYzYmM2In0 -->
### `client.Health.Get`

Operation ID: `getHealth`  
Route: `GET` `/health`  

#### Signature

```go
func (service *HealthService) Get(ctx context.Context, params HealthGetParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Server health status | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.Health.Get(ctx)
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIZWFsdGgifQ -->

## Resource `V1`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5BbmFseXplQ29udHJhY3REcmlmdCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplQ29udHJhY3REcmlmdCIsInBhdGgiOiIvdjEvYW5hbHlzaXMvY29udHJhY3QtZHJpZnQiLCJyZXNvdXJjZSI6IlYxIiwic2VjdGlvbl9zaGEyNTYiOiIyYTc5MTA3NjNmYzMwNzFiMjdjYTAxYjI3YTliOTVjZTZkZjE5ZWIyYTliY2JiMTY0NjRkY2VmMDE1NGNkOTFjIiwic2lnbmF0dXJlX3NoYTI1NiI6IjE0NDhiYmQ4YTIxZTIyY2VjOTk4MmMxZGRiNjI2NTI5ODM2MjY1ZTVjMDFjNjYzMDllNmM1ODZlY2VhOGRiZGMifQ -->
### `client.V1.AnalyzeContractDrift`

Operation ID: `analyzeContractDrift`  
Route: `POST` `/v1/analysis/contract-drift`  

#### Signature

```go
func (service *V1Service) AnalyzeContractDrift(ctx context.Context, params V1AnalyzeContractDriftParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Contract drift report and SemVer recommendation | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.AnalyzeContractDrift(ctx, /* body */ {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplQ29udHJhY3REcmlmdCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5BbmFseXplUGVyZkZpbk9wcyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyIsInBhdGgiOiIvdjEvYW5hbHlzaXMvcGVyZi1maW5vcHMiLCJyZXNvdXJjZSI6IlYxIiwic2VjdGlvbl9zaGEyNTYiOiIwYzI4NTAxYTM2ZWNlMTA3OWJkYWY0NWVkODBmMzFiZmQ4MGRlYWI2MTkxMjA2NWYzMGE4NDYxOGUwY2M1NTk4Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImEwYTM2NDA5NWE4Yjk3NTg5NDExZTdkNjM1YmY5MDM5MTE4YTIyMTQ2NWEyZmEwNjg5ZGI3ZWVjMDQ3NzI4MjMifQ -->
### `client.V1.AnalyzePerfFinOps`

Operation ID: `analyzePerfFinOps`  
Route: `POST` `/v1/analysis/perf-finops`  

#### Signature

```go
func (service *V1Service) AnalyzePerfFinOps(ctx context.Context, params V1AnalyzePerfFinOpsParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Performance and FinOps audit report | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.AnalyzePerfFinOps(ctx, /* body */ {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5BbmFseXplIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImFuYWx5emVTdXBwbHlDaGFpbiIsInBhdGgiOiIvdjEvc3VwcGx5LWNoYWluL2FuYWx5emUiLCJyZXNvdXJjZSI6IlYxIiwic2VjdGlvbl9zaGEyNTYiOiJjOGQzNDFjMGY0ZDgyOTdhNWYwZjI0YWFjYzRhOGNkNTU5Njg3MTBjNzkxMmMwZWU3ZDc5MGVlYzUyMDUyOGY1Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImYzZjBiZTk2M2M3NGY0ZjdlNjA1OWJlYmE2ZjI3MWM1YTc5ZjE2Nzk2YjM1NDY3ZTQ1MWIyYjAzNjk0MjBhOGMifQ -->
### `client.V1.Analyze`

Operation ID: `analyzeSupplyChain`  
Route: `POST` `/v1/supply-chain/analyze`  

#### Signature

```go
func (service *V1Service) Analyze(ctx context.Context, params V1AnalyzeParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Supply-chain security audit | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.Analyze(ctx, /* body */ {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplU3VwcGx5Q2hhaW4ifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5CdWlsZEF1dG9maXhCdW5kbGUiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiYnVpbGRBdXRvZml4QnVuZGxlIiwicGF0aCI6Ii92MS9yZXZpZXdzL2F1dG9maXgiLCJyZXNvdXJjZSI6IlYxIiwic2VjdGlvbl9zaGEyNTYiOiI3ZTYxMTU4Y2Y3ZGRjZjhkMTRhMzUwZDhhNmNiNDgwNGUyOWU3MmMyOGQ1NGFjODk5ZGU5ZDQ1MDAxMDRhMDZmIiwic2lnbmF0dXJlX3NoYTI1NiI6ImU1NTE5MTdmZTNjZDViZjAwMmY5NWFiN2Y5NmJhY2Y1ZDgyMmRkYmU5ZThjZThmOTM1ODkwYTk0ZTc5YmJkMzgifQ -->
### `client.V1.BuildAutofixBundle`

Operation ID: `buildAutofixBundle`  
Route: `POST` `/v1/reviews/autofix`  

#### Signature

```go
func (service *V1Service) BuildAutofixBundle(ctx context.Context, params V1BuildAutofixBundleParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Remediation patch bundle | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.BuildAutofixBundle(ctx, /* body */ {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJidWlsZEF1dG9maXhCdW5kbGUifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5Db21wdXRlUmlza1JhZGFyIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNvbXB1dGVSaXNrUmFkYXIiLCJwYXRoIjoiL3YxL3Jldmlld3Mvcmlzay1yYWRhciIsInJlc291cmNlIjoiVjEiLCJzZWN0aW9uX3NoYTI1NiI6IjEyOTUxMzZmNDJhMWY3NzBiYmE4MThhMTljMzI5NmIwMWExMDRlOWRmNjNjY2RjNWUxMjBiZDUzYTc4ZmI4ZmQiLCJzaWduYXR1cmVfc2hhMjU2IjoiODdmYmRkZDg5NDA2YWQwODkyOTVjZjY4N2I1NWQ1MWFjOGU4MjJhODk3ZGUxYmI0YTBjNTRjMjQzNzdjZDJkZiJ9 -->
### `client.V1.ComputeRiskRadar`

Operation ID: `computeRiskRadar`  
Route: `POST` `/v1/reviews/risk-radar`  

#### Signature

```go
func (service *V1Service) ComputeRiskRadar(ctx context.Context, params V1ComputeRiskRadarParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | 6-axis Risk Radar telemetry | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.ComputeRiskRadar(ctx, /* body */ {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjb21wdXRlUmlza1JhZGFyIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5OZXdDb2RpbmciLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY3JlYXRlQ29kaW5nVGFzayIsInBhdGgiOiIvdjEvdGFza3MiLCJyZXNvdXJjZSI6IlYxIiwic2VjdGlvbl9zaGEyNTYiOiI0OGQ5OWU4N2JiYTlmM2QwYzI3NDhjMDQzNDcxMDBkZTBiZDBmYzVmZGRiYzcwYTYyYzU3ZjA5YmExMDY4MzdmIiwic2lnbmF0dXJlX3NoYTI1NiI6ImZiNDY4Y2Q0NjMzN2IxNTY1ZjQ5ZWYyZjg0YWEwNTI5MGNhYTgzNzM5ZDgwMTQzN2ZhY2ZkZTRlNDMwMGI4NDIifQ -->
### `client.V1.NewCoding`

Operation ID: `createCodingTask`  
Route: `POST` `/v1/tasks`  

#### Signature

```go
func (service *V1Service) NewCoding(ctx context.Context, params V1NewCodingParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Created coding task | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.NewCoding(ctx, /* body */ {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVDb2RpbmdUYXNrIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5OZXciLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY3JlYXRlUmV2aWV3IiwicGF0aCI6Ii92MS9yZXZpZXdzIiwicmVzb3VyY2UiOiJWMSIsInNlY3Rpb25fc2hhMjU2IjoiZTBjZmU0NWU0OWM1NjAxZTMwMTM3ZWVlOGNiOWVhNzIzZTNhNzk1ZTE1NjgxYjVhMDRiMTg3NTg4ZTY0ZDNmYiIsInNpZ25hdHVyZV9zaGEyNTYiOiIyNGFmODI1ZmU2YWU1ZmQ2YTEwNDg0YzY1ZTI1Njk1OTE5YzA2ZWQ0MjY0ZDA3OGJmMjA0ZmFkYWZhYjMyM2EzIn0 -->
### `client.V1.New`

Operation ID: `createReview`  
Route: `POST` `/v1/reviews`  

#### Signature

```go
func (service *V1Service) New(ctx context.Context, params V1NewParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Completed review result with findings, blast radius, and change stack | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.New(ctx, /* body */ {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVSZXZpZXcifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5FdmFsdWF0ZUdhdGUiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiZXZhbHVhdGVDb21wbGlhbmNlR2F0ZSIsInBhdGgiOiIvdjEvY29tcGxpYW5jZS9nYXRlIiwicmVzb3VyY2UiOiJWMSIsInNlY3Rpb25fc2hhMjU2IjoiMzBkMzhlM2M0ZTg1ZjMxMzRkZmYwM2Q0MjE5NDA1MDkwZmQ3MDA1OGJjZjI4ZTRhNjAyNTU0MGI0ODZlN2NkMCIsInNpZ25hdHVyZV9zaGEyNTYiOiI5ODNlZDE2M2I5Y2QxZGY2YjVkNmU3NDIxZTkwYzcyNGJlODUyOWI3YWNkZTk0ODZhZjQzN2U3NWY4Y2YxNzM0In0 -->
### `client.V1.EvaluateGate`

Operation ID: `evaluateComplianceGate`  
Route: `POST` `/v1/compliance/gate`  

#### Signature

```go
func (service *V1Service) EvaluateGate(ctx context.Context, params V1EvaluateGateParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ComplianceGateRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Compliance gate verdict and SHA-256 attestation | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.EvaluateGate(ctx, /* body */ {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJldmFsdWF0ZUNvbXBsaWFuY2VHYXRlIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5FeHBvcnRTYXJpZiIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJleHBvcnRTYXJpZiIsInBhdGgiOiIvdjEvY29tcGxpYW5jZS9zYXJpZiIsInJlc291cmNlIjoiVjEiLCJzZWN0aW9uX3NoYTI1NiI6IjY1YmJlMDA5NjZhYjU1ZWNmOGRlMzQ4NjhiZDYzMGRkNzllMWY3MjMxNWFlZGQyZGZkNWI2ZTZmZjllYzQyNWUiLCJzaWduYXR1cmVfc2hhMjU2IjoiMGE3NWUzNGEwNDU3N2RkZGFiMThlYjQ0YTdhOTBlZmEyY2ZlNGNiYTI5MzFiMTJhNTU5YzI3NDRiMjFhM2ZmZCJ9 -->
### `client.V1.ExportSarif`

Operation ID: `exportSarif`  
Route: `POST` `/v1/compliance/sarif`  

#### Signature

```go
func (service *V1Service) ExportSarif(ctx context.Context, params V1ExportSarifParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | SARIF 2.1.0 JSON document | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.ExportSarif(ctx, /* body */ {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJleHBvcnRTYXJpZiJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5GaW5hbGl6ZU1ldGVyaW5nUXVvdGEiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiZmluYWxpemVNZXRlcmluZ1F1b3RhIiwicGF0aCI6Ii92MS9zYWFzL21ldGVyaW5nL2ZpbmFsaXplIiwicmVzb3VyY2UiOiJWMSIsInNlY3Rpb25fc2hhMjU2IjoiNTU4MGEzY2UwMzZjZjcyOThlMjEwMjFmNzViZmFhYzFkYTI1YTQ3ZjExMDA3YWUxZWNlOTZmNWE3MjkyYzZmOCIsInNpZ25hdHVyZV9zaGEyNTYiOiI1NzU0YjUxYTViYTgxYjZmZTEyYTkyNjYyNDUxM2Y4YWRiZjY5ZjcxZTJkMTUzYTUwMTU3NjgxMGIwZDQzM2QwIn0 -->
### `client.V1.FinalizeMeteringQuota`

Operation ID: `finalizeMeteringQuota`  
Route: `POST` `/v1/saas/metering/finalize`  

#### Signature

```go
func (service *V1Service) FinalizeMeteringQuota(ctx context.Context, params V1FinalizeMeteringQuotaParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Finalized metering settlement | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.FinalizeMeteringQuota(ctx, /* body */ {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJmaW5hbGl6ZU1ldGVyaW5nUXVvdGEifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5HZW5lcmF0ZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJnZW5lcmF0ZVNib20iLCJwYXRoIjoiL3YxL3Nib20iLCJyZXNvdXJjZSI6IlYxIiwic2VjdGlvbl9zaGEyNTYiOiI5MWJkMzVhYjIyY2M5OGE1ZmFkZGZmMjUzZjZjYjE3NmJkOGQyZGRmNTlhNDg1Yjg2ZmNmMTQyNmI2ZjdkMGM2Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjEzZmY0NTAzOTY2MWM3NDg3MjUxNjU5NzM0NWYyY2YzMmYxZTllYjQyMzFkZTI4MzMxOTVjN2YzNzNmM2U5MGQifQ -->
### `client.V1.Generate`

Operation ID: `generateSbom`  
Route: `POST` `/v1/sbom`  

#### Signature

```go
func (service *V1Service) Generate(ctx context.Context, params V1GenerateParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | CycloneDX 1.5 SBOM JSON | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.Generate(ctx, /* body */ {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZW5lcmF0ZVNib20ifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5HZXRSb2kiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRBbmFseXRpY3NSb2kiLCJwYXRoIjoiL3YxL2FuYWx5dGljcy9yb2kiLCJyZXNvdXJjZSI6IlYxIiwic2VjdGlvbl9zaGEyNTYiOiI2OTRkNzk0ZDMwN2JhY2MxYWU2ODI4YTM5MjFhYTFjYTQzMWI0MTc3ZjdkOTc5M2M3ZjliZThiOGU1MmFmNTFlIiwic2lnbmF0dXJlX3NoYTI1NiI6IjBmNzMzZTRlMTI2NTc4NGMzMWYyYzUxMmY1MmVjNzczNzFhZWRmZTgzNWFjMDg4NmQzYTllMjFhMmE2ZTgzY2IifQ -->
### `client.V1.GetRoi`

Operation ID: `getAnalyticsRoi`  
Route: `GET` `/v1/analytics/roi`  

#### Signature

```go
func (service *V1Service) GetRoi(ctx context.Context, params V1GetRoiParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | ROI telemetry summary | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.GetRoi(ctx)
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBbmFseXRpY3NSb2kifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5HZXQiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRDYXBhYmlsaXRpZXMiLCJwYXRoIjoiL3YxL2NhcGFiaWxpdGllcyIsInJlc291cmNlIjoiVjEiLCJzZWN0aW9uX3NoYTI1NiI6IjdiNWM0NGRmYjI3NmYyNzJjZDFiYTEyMmU2YTIwZTZhYTM5NTFmNjM2ZTc3ZTJiOWM0ZjczYTUyNzIyNmU2NmQiLCJzaWduYXR1cmVfc2hhMjU2IjoiM2FhYzhjYmU0OWM2NjZmMzM4MDU1MDhjOTBkMWY0ZGY0MmYwMDNlYjI3MThiMTY5MWI3NWMzOGNlZGE5ZTBmZSJ9 -->
### `client.V1.Get`

Operation ID: `getCapabilities`  
Route: `GET` `/v1/capabilities`  

#### Signature

```go
func (service *V1Service) Get(ctx context.Context, params V1GetParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Capabilities catalog | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.Get(ctx)
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRDYXBhYmlsaXRpZXMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5HZXRCbHVlcHJpbnQiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRTYWFzQmx1ZXByaW50IiwicGF0aCI6Ii92MS9zYWFzL2JsdWVwcmludCIsInJlc291cmNlIjoiVjEiLCJzZWN0aW9uX3NoYTI1NiI6IjQ1ODgyMDQzNjkwMWI1NTk5MTUyZmMyNTZlZTAxZGQwZmU4YWFmNWZmMDhiNTdkNjY3OTA0NjU4MzU1Mzg0NDQiLCJzaWduYXR1cmVfc2hhMjU2IjoiY2FhYWQ5MGMyOTk2OWZiYjhiMTY3MjNlMTg1YTI1NGYyN2ZjMGY3ZDIwMmJhMmZlMzVhOWNmMGY3OGRlMWI2NiJ9 -->
### `client.V1.GetBlueprint`

Operation ID: `getSaasBlueprint`  
Route: `GET` `/v1/saas/blueprint`  

#### Signature

```go
func (service *V1Service) GetBlueprint(ctx context.Context, params V1GetBlueprintParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Autonomous SaaS blueprint | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.GetBlueprint(ctx)
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRTYWFzQmx1ZXByaW50In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5HZXRRdWV1ZSIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldFRyaWFnZVF1ZXVlIiwicGF0aCI6Ii92MS90cmlhZ2UiLCJyZXNvdXJjZSI6IlYxIiwic2VjdGlvbl9zaGEyNTYiOiI2ZTZlMTc2N2FlYzZiNzAxYzI5NThlMzExNjJjMjg1ODk1YzhiZGI2NTRkMjQxMzE2YWRhYzM4NzZmMzIwZGI3Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImI5MWIxZGYxMDIxMmRlODI1NjE5OWM3Nzc1NzU4MTg0Y2NiZTdiNDQ1ZTQyZmNmYzAzNjI4NDk0ZjYzMjEwZDYifQ -->
### `client.V1.GetQueue`

Operation ID: `getTriageQueue`  
Route: `GET` `/v1/triage`  

#### Signature

```go
func (service *V1Service) GetQueue(ctx context.Context, params V1GetQueueParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Triaged PR queue | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.GetQueue(ctx)
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRUcmlhZ2VRdWV1ZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5Jc3N1ZVN1cmZhY2VMZWFzZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJpc3N1ZVN1cmZhY2VMZWFzZSIsInBhdGgiOiIvdjEvc2Fhcy9zdXJmYWNlLWxlYXNlL2lzc3VlIiwicmVzb3VyY2UiOiJWMSIsInNlY3Rpb25fc2hhMjU2IjoiYjc1Mjc3MzViMDZkODA5ZTlkYzdkZTdhNDcwNzk5YTc3NDhlOTEyMjU2MWVmOTMxM2FiMzA5MzlkZGMyMTA0NSIsInNpZ25hdHVyZV9zaGEyNTYiOiJkNTJlMmY4YjZhYWE2YzAyOGZlMzM2YjFmNDdhZjRkY2JiNzQxMjg2NzMwMzQ5NTg2ZGNiZjljMjI4M2UwMGY5In0 -->
### `client.V1.IssueSurfaceLease`

Operation ID: `issueSurfaceLease`  
Route: `POST` `/v1/saas/surface-lease/issue`  

#### Signature

```go
func (service *V1Service) IssueSurfaceLease(ctx context.Context, params V1IssueSurfaceLeaseParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Issued surface lease token | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.IssueSurfaceLease(ctx, /* body */ {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJpc3N1ZVN1cmZhY2VMZWFzZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5MaXN0Q29kaW5nIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdENvZGluZ1Rhc2tzIiwicGF0aCI6Ii92MS90YXNrcyIsInJlc291cmNlIjoiVjEiLCJzZWN0aW9uX3NoYTI1NiI6IjYwMjMwOTEwMmNhZjI3YmZmZjE2ZTBmMTcwZjQ4Nzc3ZmFkMjIzY2JmODFkMDE5NTA2OWRmNzliZDg3ZjAxNDgiLCJzaWduYXR1cmVfc2hhMjU2IjoiMDE5ZWQ4ZWYyMzA5ZDRhNDE0ZmFhYjlkMTZmZGJkZGQwM2EwMDRmMzM5MjRjMzA3MThlZmU5OGQ5YmQ4ZGU5NyJ9 -->
### `client.V1.ListCoding`

Operation ID: `listCodingTasks`  
Route: `GET` `/v1/tasks`  

#### Signature

```go
func (service *V1Service) ListCoding(ctx context.Context, params V1ListCodingParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Task list | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.ListCoding(ctx)
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Q29kaW5nVGFza3MifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5MaXN0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdFdhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoiVjEiLCJzZWN0aW9uX3NoYTI1NiI6ImFkZGZkOTFjZjE3MTNlOTQxODYzYjk0OWQ2YTdiZmYzZmQ5MmU4NjcwZGViYTRjNjQyZmM5MDU5ZGYxYjQ0NjciLCJzaWduYXR1cmVfc2hhMjU2IjoiNjljZDM3NWVlOTZhYjY1ZjQ1M2Y5YjIzZTAxNDY2ZmY0YmZjOGI1NzQ4NTYwZTc5M2Q5MjU4MzE4MDIwNDRkNyJ9 -->
### `client.V1.List`

Operation ID: `listWaitlist`  
Route: `GET` `/v1/waitlist`  

#### Signature

```go
func (service *V1Service) List(ctx context.Context, params V1ListParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Waitlist entries | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.List(ctx)
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3QifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5QbGFuU3RhY2tlZFByU3BsaXQiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicGxhblN0YWNrZWRQclNwbGl0IiwicGF0aCI6Ii92MS9hbmFseXNpcy9zcGxpdC1wciIsInJlc291cmNlIjoiVjEiLCJzZWN0aW9uX3NoYTI1NiI6IjVlZGYxMTI5YjFkNzBjNDhmNWJmZTQxZTgxODY0ZmFiMDEyMjAwYjg5MTQ5ZTI3NzVlODVhNTk1M2YzZDI1NjciLCJzaWduYXR1cmVfc2hhMjU2IjoiN2Q3MGUxZjA2YzQ3MjdlYWRiZGNhY2EyZTY0ZWU4YjkwZWZhYjUxZmFmYjcwNTZjZDZhZWRhMDIxYTBmNDZkZSJ9 -->
### `client.V1.PlanStackedPrSplit`

Operation ID: `planStackedPrSplit`  
Route: `POST` `/v1/analysis/split-pr`  

#### Signature

```go
func (service *V1Service) PlanStackedPrSplit(ctx context.Context, params V1PlanStackedPrSplitParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Ordered stacked PR plan and git commands | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.PlanStackedPrSplit(ctx, /* body */ {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwbGFuU3RhY2tlZFByU3BsaXQifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5SZWdpc3RlciIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0IiwicGF0aCI6Ii92MS93YWl0bGlzdCIsInJlc291cmNlIjoiVjEiLCJzZWN0aW9uX3NoYTI1NiI6IjcxMDhjZTM0ZmJlZDUzZDQ4YWU3ZWU2MTdkYTU2YTgxNGQ1YzYwMjFkMjRkMGNhNGU0ZTQxYmUxMGNmYWFlNWQiLCJzaWduYXR1cmVfc2hhMjU2IjoiZmNmNTgzZjJlYWI2MWVlZWViYWYyNzM2MmEwMGVjZjg0MzEyNGM1OGVkZWI2YjI2OGI3YjRlMTcyMDkwZjNkMiJ9 -->
### `client.V1.Register`

Operation ID: `registerWaitlist`  
Route: `POST` `/v1/waitlist`  

#### Signature

```go
func (service *V1Service) Register(ctx context.Context, params V1RegisterParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `WaitlistRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Waitlist entry created | none |

#### Canonical required-input example

```json
{
  "body": {
    "email": "example-c65f@example.test"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.Register(ctx, /* body */ {"email": "example-c65f@example.test"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJWMS5SZXNlcnZlTWV0ZXJpbmdRdW90YSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJyZXNlcnZlTWV0ZXJpbmdRdW90YSIsInBhdGgiOiIvdjEvc2Fhcy9tZXRlcmluZy9yZXNlcnZlIiwicmVzb3VyY2UiOiJWMSIsInNlY3Rpb25fc2hhMjU2IjoiYTJmODUyODhjMDZhZDc4N2UxYjAzZTFiZWRkZThiNzZkNWVmMjBiNDViZTI0M2JmMTRkM2I1NDZlYzBhNjk3ZCIsInNpZ25hdHVyZV9zaGEyNTYiOiIzYzc1ZDA5NDUxMjg2MzYwMjliNzY3YmZmYjE4YTgzMTBkOGJhZWM3YWI3YzE2NGRkMGRjYjI4NTE3YmYzMGNjIn0 -->
### `client.V1.ReserveMeteringQuota`

Operation ID: `reserveMeteringQuota`  
Route: `POST` `/v1/saas/metering/reserve`  

#### Signature

```go
func (service *V1Service) ReserveMeteringQuota(ctx context.Context, params V1ReserveMeteringQuotaParams, opts ...option.RequestOption) (*Response[JSONValue], error)
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Metering reservation record | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```go
result, err := client.V1.ReserveMeteringQuota(ctx, /* body */ {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZXNlcnZlTWV0ZXJpbmdRdW90YSJ9 -->

