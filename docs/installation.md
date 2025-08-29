# LEWIS Installation Guide

This guide provides detailed instructions for installing and setting up LEWIS (Linux Environment Working Intelligence System) for research and development purposes.

## 📋 Prerequisites

### System Requirements
- **Operating System**: Linux-based (Ubuntu 20.04+, Kali Linux, Termux)
- **Python**: 3.8 or higher
- **Memory**: Minimum 4GB RAM (8GB recommended for research work)
- **Storage**: At least 2GB free space
- **Network**: Internet connection for downloading dependencies

### Required Tools
- Git
- Python pip
- Docker (optional but recommended)
- Virtual environment manager (venv or conda)

## 🛠️ Installation Methods

### Method 1: Development Installation (Recommended for Researchers)

```bash
# 1. Clone the repository
git clone https://github.com/yashab-cyber/lewis-research-paper.git
cd lewis-research-paper

# 2. Create a virtual environment
python3 -m venv lewis-env
source lewis-env/bin/activate  # On Windows: lewis-env\Scripts\activate

# 3. Install dependencies (when available)
pip install -r requirements.txt

# 4. Install LEWIS in development mode
pip install -e .

# 5. Verify installation
lewis --version
```

### Method 2: Docker Installation

```bash
# 1. Pull the LEWIS Docker image (when available)
docker pull yashabcyber/lewis:latest

# 2. Run LEWIS in a container
docker run -it --name lewis-container yashabcyber/lewis:latest

# 3. For development with volume mounting
docker run -it -v $(pwd):/workspace yashabcyber/lewis:dev
```

### Method 3: Conda Installation

```bash
# 1. Create conda environment
conda create -n lewis python=3.9
conda activate lewis

# 2. Clone and install
git clone https://github.com/yashab-cyber/lewis-research-paper.git
cd lewis-research-paper
conda install --file conda-requirements.txt
pip install -e .
```

## 🔧 Environment-Specific Setup

### Kali Linux Setup
```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Install system dependencies
sudo apt install -y python3-pip python3-venv git

# Install security tools integration
sudo apt install -y nmap nikto sqlmap metasploit-framework

# Clone and setup LEWIS
git clone https://github.com/yashab-cyber/lewis-research-paper.git
cd lewis-research-paper
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### Termux (Android) Setup
```bash
# Update packages
pkg update && pkg upgrade

# Install dependencies
pkg install python git

# Setup storage access
termux-setup-storage

# Clone and install
git clone https://github.com/yashab-cyber/lewis-research-paper.git
cd lewis-research-paper
pip install -r requirements.txt
```

### Ubuntu Server Setup
```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Install Python and dependencies
sudo apt install -y python3 python3-pip python3-venv git

# Install additional tools for enterprise features
sudo apt install -y docker.io postgresql nginx

# Setup LEWIS
git clone https://github.com/yashab-cyber/lewis-research-paper.git
cd lewis-research-paper
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## ⚙️ Configuration

### Initial Configuration
```bash
# Initialize LEWIS configuration
lewis init

# Configure basic settings
lewis config set --api-key YOUR_API_KEY
lewis config set --workspace /path/to/workspace
lewis config set --log-level INFO
```

### Advanced Configuration
```bash
# Configure machine learning models
lewis ml configure --model-path /path/to/models
lewis ml download --model threat-detection

# Setup security tools integration
lewis tools configure --nmap-path /usr/bin/nmap
lewis tools configure --metasploit-path /usr/share/metasploit-framework

# Configure reporting
lewis reporting configure --output-format pdf,html
lewis reporting configure --template-path /path/to/templates
```

## 🧪 Verification

### Basic Functionality Test
```bash
# Test LEWIS core functionality
lewis test --basic

# Test AI components
lewis test --ai-models

# Test security tools integration
lewis test --security-tools

# Generate test report
lewis test --comprehensive --output test-report.html
```

### Research Environment Validation
```bash
# Validate research dataset access
lewis research validate-datasets

# Test experimental frameworks
lewis research test-framework

# Verify citation and documentation tools
lewis docs verify
```

## 🐳 Docker Development Environment

### Build Development Image
```dockerfile
# Dockerfile for LEWIS development
FROM python:3.9-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .
RUN pip install -e .

EXPOSE 8000
CMD ["lewis", "serve"]
```

### Docker Compose for Research
```yaml
version: '3.8'
services:
  lewis:
    build: .
    ports:
      - "8000:8000"
    volumes:
      - ./data:/app/data
      - ./models:/app/models
    environment:
      - LEWIS_ENV=research
      - LOG_LEVEL=DEBUG
```

## 🔍 Troubleshooting

### Common Issues

**Issue**: ImportError for required modules
```bash
# Solution: Reinstall dependencies
pip install --force-reinstall -r requirements.txt
```

**Issue**: Permission denied errors
```bash
# Solution: Fix permissions
sudo chown -R $USER:$USER ~/.lewis
chmod 755 ~/.lewis
```

**Issue**: Memory errors during model loading
```bash
# Solution: Increase virtual memory
sudo sysctl vm.max_map_count=262144
```

### Debugging Mode
```bash
# Run LEWIS in debug mode
lewis --debug --verbose

# Check system compatibility
lewis doctor

# View detailed logs
lewis logs --tail 100
```

## 📊 Performance Optimization

### System Optimization
```bash
# Optimize for research workloads
echo 'vm.swappiness=10' | sudo tee -a /etc/sysctl.conf
echo 'vm.vfs_cache_pressure=50' | sudo tee -a /etc/sysctl.conf

# Setup GPU acceleration (if available)
lewis gpu setup --cuda-version 11.8
```

### Memory Management
```bash
# Configure memory limits
lewis config set --memory-limit 6GB
lewis config set --cache-size 1GB
lewis config set --batch-size 32
```

## 🔐 Security Considerations

### Secure Installation
```bash
# Create dedicated user for LEWIS
sudo useradd -m -s /bin/bash lewis-user
sudo usermod -aG docker lewis-user

# Set proper permissions
sudo chown -R lewis-user:lewis-user /opt/lewis
chmod 750 /opt/lewis
```

### Network Security
```bash
# Configure firewall rules
sudo ufw allow 8000/tcp
sudo ufw enable

# Setup SSL certificates
lewis ssl generate --domain localhost
```

## 📚 Next Steps

After successful installation:

1. **Read the [User Guide](user-guide.md)** for detailed usage instructions
2. **Explore [Examples](../examples/)** to understand capabilities
3. **Review [API Reference](api-reference.md)** for integration
4. **Join our [Community](../CONTRIBUTING.md)** for support and collaboration

## 🆘 Support

If you encounter issues during installation:

- **Check our [Troubleshooting Wiki](https://github.com/yashab-cyber/lewis-research-paper/wiki/Troubleshooting)**
- **Open an [Issue](https://github.com/yashab-cyber/lewis-research-paper/issues)**
- **Join our [Discord Community](https://discord.gg/lewis-community)**
- **Email**: [contact@yashabalam.me](mailto:contact@yashabalam.me)

---

**Note**: LEWIS is currently in the research phase. Some features mentioned in this guide are planned for future releases. Check the [project status](../README.md#status) for current availability.