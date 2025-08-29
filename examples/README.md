# LEWIS Examples

This directory contains practical examples and use cases for LEWIS (Linux Environment Working Intelligence System).

## 📁 Example Categories

### 🔍 Basic Usage Examples
- **[Basic Reconnaissance](./01-basic-recon/README.md)**: Simple domain and network reconnaissance
- **[Vulnerability Scanning](./02-vuln-scanning/README.md)**: Automated vulnerability assessment
- **[Report Generation](./03-reporting/README.md)**: Creating professional security reports

### 🤖 AI-Powered Examples
- **[Natural Language Queries](./04-ai-queries/README.md)**: Interacting with LEWIS using natural language
- **[Intelligent Analysis](./05-ai-analysis/README.md)**: AI-powered threat detection and analysis
- **[Smart Recommendations](./06-ai-recommendations/README.md)**: Context-aware security suggestions

### 🔬 Research Examples
- **[Academic Research](./07-research/README.md)**: Using LEWIS for cybersecurity research
- **[Dataset Creation](./08-datasets/README.md)**: Building research datasets
- **[Experimental Frameworks](./09-experiments/README.md)**: Setting up reproducible experiments

### 🏢 Enterprise Examples
- **[Compliance Scanning](./10-compliance/README.md)**: Automated compliance assessments
- **[Incident Response](./11-incident-response/README.md)**: Security incident handling
- **[Continuous Monitoring](./12-monitoring/README.md)**: Ongoing security monitoring

### 🔌 Integration Examples
- **[API Integration](./13-api-integration/README.md)**: Integrating LEWIS with other tools
- **[Custom Plugins](./14-plugins/README.md)**: Developing custom LEWIS plugins
- **[Workflow Automation](./15-automation/README.md)**: Automated security workflows

## 🚀 Quick Start Examples

### Command Line Interface
```bash
# Basic system information
lewis info

# Start a simple network scan
lewis scan network --target 192.168.1.0/24

# Ask LEWIS for security advice
lewis ask "How do I test for SQL injection vulnerabilities?"

# Generate a security report
lewis report create --template executive --project my-project
```

### Python API
```python
from lewis import LewisAPI

# Initialize LEWIS
lewis = LewisAPI()

# Start vulnerability scan
scan = lewis.scans.create(
    target="https://example.com",
    scan_type="web_application"
)

# Get AI-powered analysis
analysis = lewis.intelligence.analyze(scan.results)
print(f"Risk Level: {analysis.risk_level}")
```

### Web Interface
```javascript
// JavaScript example for web dashboard
const lewis = new LewisWebAPI('your-api-key');

// Start real-time monitoring
lewis.monitoring.start({
    targets: ['192.168.1.0/24'],
    alerts: true,
    dashboard: 'security-overview'
});
```

## 📋 Example Index

| Example | Difficulty | Time | Description |
|---------|------------|------|-------------|
| [Hello LEWIS](./01-basic-recon/hello-lewis.md) | Beginner | 5 min | Your first LEWIS command |
| [Web App Scan](./02-vuln-scanning/webapp-scan.md) | Intermediate | 30 min | Complete web application security assessment |
| [AI Threat Analysis](./05-ai-analysis/threat-analysis.md) | Advanced | 60 min | AI-powered threat detection and analysis |
| [Research Dataset](./08-datasets/research-dataset.md) | Advanced | 2 hours | Creating research datasets for academic work |
| [Enterprise Dashboard](./12-monitoring/enterprise-dashboard.md) | Expert | 4 hours | Setting up enterprise security monitoring |

## 🔧 Running Examples

### Prerequisites
```bash
# Install LEWIS
pip install lewis-security

# Clone examples repository
git clone https://github.com/yashab-cyber/lewis-research-paper.git
cd lewis-research-paper/examples

# Set up environment
export LEWIS_API_KEY="your-api-key"
export LEWIS_WORKSPACE="/path/to/workspace"
```

### Individual Examples
```bash
# Navigate to specific example
cd 02-vuln-scanning

# Follow the README instructions
cat README.md

# Run the example
python webapp-scan-example.py
```

### Interactive Tutorial
```bash
# Start interactive tutorial
lewis tutorial start

# Select example category
lewis tutorial select --category "basic-usage"

# Follow guided walkthrough
lewis tutorial next
```

## 🎯 Use Case Scenarios

### Scenario 1: Security Researcher
**Goal**: Analyze new vulnerability patterns in web applications

**Examples to follow**:
1. [Dataset Creation](./08-datasets/) - Collect vulnerability data
2. [AI Analysis](./05-ai-analysis/) - Pattern recognition and classification
3. [Research Framework](./09-experiments/) - Reproducible experiments

### Scenario 2: Penetration Tester
**Goal**: Comprehensive security assessment of client infrastructure

**Examples to follow**:
1. [Basic Reconnaissance](./01-basic-recon/) - Information gathering
2. [Vulnerability Scanning](./02-vuln-scanning/) - Automated testing
3. [Report Generation](./03-reporting/) - Professional deliverables

### Scenario 3: Security Analyst
**Goal**: Monitor and respond to security threats

**Examples to follow**:
1. [Continuous Monitoring](./12-monitoring/) - Real-time threat detection
2. [Incident Response](./11-incident-response/) - Automated response workflows
3. [AI Recommendations](./06-ai-recommendations/) - Intelligent decision support

## 📚 Learning Path

### Beginner Path (2-4 hours)
1. **Getting Started**: Hello LEWIS example
2. **Basic Scanning**: Simple network reconnaissance
3. **Report Creation**: Generate your first security report
4. **AI Interaction**: Ask LEWIS security questions

### Intermediate Path (1-2 days)
1. **Web Application Testing**: Complete web app security assessment
2. **API Integration**: Connect LEWIS with existing tools
3. **Custom Workflows**: Automate repetitive security tasks
4. **Data Analysis**: Analyze scan results with AI

### Advanced Path (1-2 weeks)
1. **Research Projects**: Academic cybersecurity research
2. **Custom Plugins**: Extend LEWIS functionality
3. **Enterprise Integration**: Large-scale deployment
4. **Machine Learning**: Train custom security models

## 🛠️ Development Examples

### Plugin Development
```python
# Example: Custom vulnerability scanner plugin
from lewis.plugins import ScannerPlugin

class CustomScanner(ScannerPlugin):
    def __init__(self):
        super().__init__(name="custom-scanner")
    
    def scan(self, target):
        # Custom scanning logic
        return {
            "vulnerabilities": [...],
            "confidence": 0.95
        }
```

### API Extension
```python
# Example: Custom API endpoint
from lewis.api import APIEndpoint

class CustomEndpoint(APIEndpoint):
    def post(self, request):
        # Handle custom functionality
        return {"status": "success"}
```

## 🧪 Testing Examples

Each example includes comprehensive tests:

```bash
# Run example tests
cd examples/02-vuln-scanning
python -m pytest tests/

# Run specific test
pytest tests/test_webapp_scan.py::test_sql_injection_detection
```

## 📊 Performance Benchmarks

Performance benchmarking examples:

```bash
# Benchmark scanning performance
python benchmarks/scan_performance.py

# Memory usage analysis
python benchmarks/memory_usage.py

# Scalability testing
python benchmarks/scalability_test.py
```

## 🔍 Troubleshooting Examples

Common issues and solutions:

- **[Connection Issues](./troubleshooting/connection-issues.md)**
- **[Performance Problems](./troubleshooting/performance.md)**
- **[Configuration Errors](./troubleshooting/configuration.md)**

## 🤝 Contributing Examples

We welcome community-contributed examples! See our [contribution guidelines](../CONTRIBUTING.md) for:

- Example format standards
- Documentation requirements
- Testing expectations
- Review process

### Example Contribution Template
```
examples/
├── XX-your-example/
│   ├── README.md           # Detailed explanation
│   ├── example.py          # Main example code
│   ├── requirements.txt    # Dependencies
│   ├── data/              # Sample data files
│   ├── tests/             # Test cases
│   └── screenshots/       # Visual results
```

## 📞 Support

Need help with examples?

- **GitHub Issues**: [Report issues](https://github.com/yashab-cyber/lewis-research-paper/issues)
- **Discord**: [Join community](https://discord.gg/lewis-community)
- **Email**: [contact@yashabalam.me](mailto:contact@yashabalam.me)

---

**Happy Learning!** 🎓

*These examples are designed to help you master LEWIS and advance your cybersecurity skills.*