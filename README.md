# Agent System Project

A production-ready AI agent system built with Google Cloud's Vertex AI Agent Engine. This project demonstrates deploying and managing AI agents at scale using Google Cloud infrastructure.

## 🚀 Features

- Fully managed AI agent deployment
- Scalable cloud infrastructure
- Session management and persistence
- Secure authentication via Google Cloud IAM
- Professional monitoring and logging
- REST API endpoints for agent interaction

## 📋 Prerequisites

- Python 3.9+
- Poetry for dependency management
- Google Cloud CLI
- Google Cloud project with Agent Engine API enabled
- Proper IAM permissions

## 🛠️ Installation

```bash
# Clone the repository
git clone [your-repo-url]
cd agent-system

# Install dependencies
poetry install

# Configure Google Cloud
gcloud auth login
gcloud config set project agent-101-457716
```

## 🔧 Configuration

Set up your environment variables:

```bash
GOOGLE_CLOUD_PROJECT=agent-101-457716
GOOGLE_CLOUD_LOCATION=us-central1
GOOGLE_CLOUD_STAGING_BUCKET=agent-101-staging
```

## 📦 Deployment

Deploy your agent to Agent Engine:

```bash
poetry run python deployment/remote.py --create
```

## 🔌 Usage

### Create a Session
```bash
poetry run python deployment/remote.py --create_session --resource_id=687792901685510144
```

### Send Messages
```bash
poetry run python deployment/remote.py --send \
    --resource_id=687792901685510144 \
    --session_id=YOUR_SESSION_ID \
    --message="Your message here"
```

## 🏗️ Project Structure

```
agent-system/
├── deployment/
│   ├── remote.py      # Deployment management
│   └── utils.py       # Utility functions
├── agent/
│   ├── core.py        # Core agent logic
│   └── tools.py       # Agent tools
├── tests/             # Test suite
├── poetry.lock        # Lock file
└── pyproject.toml     # Project configuration
```

## 📊 Monitoring

Monitor your agent through Google Cloud Console:
- Cloud Monitoring for metrics
- Cloud Logging for logs
- Cloud Trace for performance analysis

## 🔑 Security

- Authentication via Google Cloud IAM
- Encrypted communication
- Secure session management
- Rate limiting and quota management

## 📝 License

[Your chosen license]

## 🤝 Contributing

[Your contribution guidelines]
