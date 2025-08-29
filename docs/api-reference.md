# LEWIS API Reference

Complete API reference for LEWIS (Linux Environment Working Intelligence System) for developers and researchers.

## 📖 Overview

The LEWIS API provides programmatic access to all LEWIS functionality including:
- AI-powered security analysis
- Automated vulnerability assessment
- Intelligence gathering and threat detection
- Research data management
- Report generation and visualization

## 🚀 Getting Started

### Authentication

```python
from lewis import LewisAPI

# Initialize with API key
lewis = LewisAPI(api_key="your-api-key-here")

# Alternative: Use environment variable
# export LEWIS_API_KEY="your-api-key-here"
lewis = LewisAPI()
```

### Basic Usage

```python
# Check API status
status = lewis.system.status()
print(f"LEWIS Status: {status.health}")

# Get API information
info = lewis.system.info()
print(f"Version: {info.version}")
print(f"Features: {info.features}")
```

## 🔍 Core API Modules

### System API

#### `lewis.system`

**Methods:**
- `status()` - Get system health status
- `info()` - Get system information
- `config()` - Get/set configuration
- `logs(level="INFO", limit=100)` - Retrieve logs

```python
# System status
status = lewis.system.status()

# System configuration
config = lewis.system.config()
lewis.system.config({"scan_timeout": 3600})

# System logs
logs = lewis.system.logs(level="ERROR", limit=50)
```

### Workspace API

#### `lewis.workspaces`

**Methods:**
- `create(name, path, template=None)` - Create workspace
- `list()` - List all workspaces
- `get(name)` - Get workspace details
- `delete(name)` - Delete workspace
- `switch(name)` - Switch active workspace

```python
# Create workspace
workspace = lewis.workspaces.create(
    name="pentest-2024",
    path="/home/user/lewis/pentest-2024",
    template="penetration-testing"
)

# List workspaces
workspaces = lewis.workspaces.list()

# Switch workspace
lewis.workspaces.switch("pentest-2024")
```

### Project API

#### `lewis.projects`

**Methods:**
- `create(name, workspace, project_type)` - Create project
- `list(workspace=None)` - List projects
- `get(project_id)` - Get project details
- `update(project_id, **kwargs)` - Update project
- `delete(project_id)` - Delete project

```python
# Create project
project = lewis.projects.create(
    name="webapp-assessment",
    workspace="pentest-2024",
    project_type="web_application"
)

# Update project
lewis.projects.update(
    project.id,
    description="E-commerce web application security assessment",
    priority="high"
)
```

### Intelligence API

#### `lewis.intelligence`

**Methods:**
- `query(question, context=None)` - Natural language query
- `analyze(data, analysis_type)` - Analyze data with AI
- `recommend(context)` - Get AI recommendations
- `explain(finding_id)` - Explain findings

```python
# Natural language query
response = lewis.intelligence.query(
    "What are the most critical vulnerabilities in web applications?",
    context="web_security"
)

# Analyze scan results
analysis = lewis.intelligence.analyze(
    data=scan_results,
    analysis_type="vulnerability_assessment"
)

# Get recommendations
recommendations = lewis.intelligence.recommend({
    "target_type": "web_application",
    "technologies": ["php", "mysql"]
})
```

### Scanning API

#### `lewis.scans`

**Methods:**
- `create(target, scan_type, options={})` - Start scan
- `list(project_id=None)` - List scans
- `get(scan_id)` - Get scan details
- `get_results(scan_id)` - Get scan results
- `stop(scan_id)` - Stop running scan
- `delete(scan_id)` - Delete scan

```python
# Start web application scan
scan = lewis.scans.create(
    target="https://example.com",
    scan_type="web_application",
    options={
        "depth": 3,
        "authentication": {
            "type": "form",
            "username": "testuser",
            "password": "testpass"
        }
    }
)

# Get scan results
results = lewis.scans.get_results(scan.id)

# List all scans
all_scans = lewis.scans.list()
```

#### Scan Types

| Scan Type | Description | Parameters |
|-----------|-------------|------------|
| `network` | Network vulnerability scan | `targets`, `ports`, `timing` |
| `web_application` | Web app security scan | `target`, `depth`, `auth` |
| `infrastructure` | Infrastructure assessment | `range`, `services` |
| `wireless` | Wireless network scan | `interface`, `duration` |
| `mobile` | Mobile app analysis | `apk_path`, `platform` |

### Reconnaissance API

#### `lewis.recon`

**Methods:**
- `domain(target, options={})` - Domain reconnaissance
- `network(range, options={})` - Network discovery
- `osint(target, sources=[])` - OSINT gathering
- `subdomain_enum(domain)` - Subdomain enumeration
- `port_scan(target, ports=None)` - Port scanning

```python
# Domain reconnaissance
domain_info = lewis.recon.domain(
    target="example.com",
    options={"deep": True, "dns_records": True}
)

# Network discovery
network_info = lewis.recon.network(
    range="192.168.1.0/24",
    options={"timing": "fast", "os_detection": True}
)

# OSINT gathering
osint_data = lewis.recon.osint(
    target="example.com",
    sources=["whois", "dns", "search_engines"]
)
```

### Vulnerability Assessment API

#### `lewis.vulnerabilities`

**Methods:**
- `scan(targets, options={})` - Vulnerability scan
- `list(project_id=None, severity=None)` - List vulnerabilities
- `get(vuln_id)` - Get vulnerability details
- `verify(vuln_id)` - Verify vulnerability
- `mark_false_positive(vuln_id)` - Mark as false positive

```python
# Vulnerability scan
vuln_scan = lewis.vulnerabilities.scan(
    targets=["https://example.com"],
    options={"comprehensive": True}
)

# List high-severity vulnerabilities
high_vulns = lewis.vulnerabilities.list(
    project_id=project.id,
    severity="high"
)

# Get vulnerability details
vuln_details = lewis.vulnerabilities.get(vuln_id="vuln-001")
```

### Exploitation API

#### `lewis.exploits`

**Methods:**
- `search(query, filters={})` - Search exploits
- `get(exploit_id)` - Get exploit details
- `execute(exploit_id, target, options={})` - Execute exploit
- `get_sessions()` - Get active sessions

```python
# Search exploits
exploits = lewis.exploits.search(
    query="wordpress",
    filters={"severity": "critical", "verified": True}
)

# Execute exploit (with proper authorization)
session = lewis.exploits.execute(
    exploit_id="wp-admin-bypass-2024",
    target="https://vulnerable-site.com",
    options={"payload": "reverse_shell"}
)
```

### Machine Learning API

#### `lewis.ml`

**Methods:**
- `models()` - List available models
- `predict(model_name, data)` - Make predictions
- `train(model_name, dataset)` - Train custom model
- `evaluate(model_name, test_data)` - Evaluate model

```python
# List available models
models = lewis.ml.models()

# Threat detection prediction
prediction = lewis.ml.predict(
    model_name="threat_detector",
    data=network_traffic_sample
)

# Train custom model
training_result = lewis.ml.train(
    model_name="custom_malware_detector",
    dataset="/path/to/training_data.csv"
)
```

### Reporting API

#### `lewis.reports`

**Methods:**
- `create(template, data, options={})` - Generate report
- `list(project_id=None)` - List reports
- `get(report_id)` - Get report
- `export(report_id, format)` - Export report

```python
# Generate executive report
report = lewis.reports.create(
    template="executive_summary",
    data={
        "project_id": project.id,
        "findings": vulnerabilities,
        "timeframe": "2024-Q1"
    },
    options={"include_graphs": True}
)

# Export report as PDF
lewis.reports.export(report.id, format="pdf")
```

### Research API

#### `lewis.research`

**Methods:**
- `datasets()` - List research datasets
- `create_dataset(name, data_type)` - Create dataset
- `add_data(dataset_id, data)` - Add data to dataset
- `analyze_dataset(dataset_id, method)` - Analyze dataset
- `export_dataset(dataset_id, format)` - Export dataset

```python
# Create research dataset
dataset = lewis.research.create_dataset(
    name="web_vulnerabilities_2024",
    data_type="vulnerability_data"
)

# Add vulnerability data
lewis.research.add_data(
    dataset_id=dataset.id,
    data=vulnerability_findings
)

# Analyze dataset
analysis = lewis.research.analyze_dataset(
    dataset_id=dataset.id,
    method="statistical_analysis"
)
```

## 📊 Data Models

### Scan Result Model

```python
class ScanResult:
    id: str
    scan_id: str
    target: str
    timestamp: datetime
    findings: List[Finding]
    metadata: Dict
    status: str  # "completed", "running", "failed"
```

### Vulnerability Model

```python
class Vulnerability:
    id: str
    title: str
    description: str
    severity: str  # "critical", "high", "medium", "low"
    cvss_score: float
    cve_id: Optional[str]
    affected_component: str
    proof_of_concept: Optional[str]
    remediation: str
    references: List[str]
```

### Intelligence Response Model

```python
class IntelligenceResponse:
    query: str
    response: str
    confidence: float
    sources: List[str]
    recommendations: List[str]
    context: Dict
```

## 🔧 Configuration

### API Configuration

```python
# Configure API client
lewis.configure({
    "timeout": 300,
    "max_retries": 3,
    "verify_ssl": True,
    "base_url": "https://api.lewis.local"
})
```

### Scan Configuration

```python
# Configure scan settings
scan_config = {
    "network_scan": {
        "timing": "normal",  # "fast", "normal", "slow"
        "max_threads": 10,
        "timeout": 300
    },
    "web_scan": {
        "max_depth": 5,
        "max_pages": 1000,
        "user_agent": "LEWIS-Scanner/1.0"
    }
}

lewis.configure(scan_config)
```

## 🚨 Error Handling

### Exception Types

```python
from lewis.exceptions import (
    LewisAPIError,
    AuthenticationError,
    RateLimitError,
    ScanTimeoutError,
    InvalidTargetError
)

try:
    scan = lewis.scans.create(target="invalid-target")
except InvalidTargetError as e:
    print(f"Invalid target: {e}")
except RateLimitError as e:
    print(f"Rate limit exceeded: {e.retry_after} seconds")
except LewisAPIError as e:
    print(f"API error: {e.message}")
```

### Response Handling

```python
# Check response status
response = lewis.scans.create(target="https://example.com")
if response.success:
    print(f"Scan started: {response.data.id}")
else:
    print(f"Error: {response.error}")
```

## 📈 Rate Limits and Pagination

### Rate Limits

```python
# Check rate limit status
rate_limit = lewis.system.rate_limit_status()
print(f"Remaining requests: {rate_limit.remaining}")
print(f"Reset time: {rate_limit.reset_time}")
```

### Pagination

```python
# Paginate through results
page = 1
while True:
    scans = lewis.scans.list(page=page, per_page=50)
    if not scans.data:
        break
    
    for scan in scans.data:
        print(f"Scan: {scan.id}")
    
    page += 1
```

## 🔐 Security and Authentication

### API Key Management

```python
# Rotate API key
new_key = lewis.auth.rotate_key()
print(f"New API key: {new_key}")

# Validate API key
is_valid = lewis.auth.validate_key("api-key-to-check")
```

### Secure Communication

```python
# Configure SSL/TLS
lewis.configure({
    "ssl_verify": True,
    "ssl_cert": "/path/to/cert.pem",
    "ssl_key": "/path/to/key.pem"
})
```

## 📚 SDK Examples

### Comprehensive Security Assessment

```python
import lewis
from datetime import datetime

# Initialize LEWIS
api = lewis.LewisAPI()

# Create workspace and project
workspace = api.workspaces.create("security-assessment-2024")
project = api.projects.create("web-app-test", workspace.id, "web_application")

# Reconnaissance phase
recon_data = api.recon.domain("target.com", {"deep": True})
subdomains = api.recon.subdomain_enum("target.com")

# Vulnerability scanning
for subdomain in subdomains:
    scan = api.scans.create(
        target=f"https://{subdomain}",
        scan_type="web_application"
    )
    
    # Wait for scan completion
    while api.scans.get(scan.id).status == "running":
        time.sleep(30)
    
    results = api.scans.get_results(scan.id)

# AI analysis
vulnerabilities = api.vulnerabilities.list(project.id)
analysis = api.intelligence.analyze(vulnerabilities, "risk_assessment")

# Generate report
report = api.reports.create(
    template="comprehensive_security_report",
    data={"project_id": project.id}
)
```

### Research Data Pipeline

```python
# Create research dataset
dataset = api.research.create_dataset("malware_samples_2024", "malware")

# Collect data from multiple sources
for source in data_sources:
    malware_samples = collect_samples(source)
    api.research.add_data(dataset.id, malware_samples)

# AI-powered analysis
analysis_result = api.ml.predict("malware_classifier", dataset.id)

# Export results for publication
api.research.export_dataset(dataset.id, "csv")
```

## 📞 Support and Resources

### Getting Help

- **Documentation**: [https://docs.lewis.security](https://docs.lewis.security)
- **API Status**: [https://status.lewis.security](https://status.lewis.security)
- **Support**: [contact@yashabalam.me](mailto:contact@yashabalam.me)

### Community

- **GitHub**: [https://github.com/yashab-cyber/lewis-research-paper](https://github.com/yashab-cyber/lewis-research-paper)
- **Discord**: [https://discord.gg/lewis-community](https://discord.gg/lewis-community)
- **Stack Overflow**: Tag your questions with `lewis-security`

---

**Note**: This API reference covers the planned features of LEWIS. Some functionality may be in development. Check the [project status](../README.md) for current availability.