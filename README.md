# ADK Short Bot

A Python-based agent that helps shorten messages using Google's Agent Development Kit (ADK) and Vertex AI.

## Prerequisites

- Python 3.12+
- Poetry (Python package manager)
- Google Cloud account with Vertex AI API enabled
- Google Cloud CLI (`gcloud`) installed and authenticated
  - Follow the [official installation guide](https://cloud.google.com/sdk/docs/install) to install gcloud
  - After installation, run `gcloud init` and `gcloud auth login`

## Installation

1. Clone the repository:
```bash
git clone https://github.com/bhancockio/deploy-adk-agent-engine.git
cd adk-short-bot
```

2. Install Poetry if you haven't already:
```bash
curl -sSL https://install.python-poetry.org | python3 -
```

3. Install project dependencies:
```bash
poetry install
```

4. Activate the virtual environment:
```bash
source $(poetry env info --path)/bin/activate
```

## Configuration

1. Create a `.env` file in the project root with the following variables:
```bash
GOOGLE_GENAI_USE_VERTEXAI=TRUE
GOOGLE_CLOUD_PROJECT=your-project-id
GOOGLE_CLOUD_LOCATION=your-location  # e.g., us-central1
GOOGLE_CLOUD_STAGING_BUCKET=gs://your-bucket-name
```

2. Set up Google Cloud authentication:
```bash
gcloud auth login
gcloud config set project your-project-id
```

3. Enable required APIs:
```bash
gcloud services enable aiplatform.googleapis.com
```

## Usage

### Local Testing

1. Create a new session:
```bash
poetry run deploy-local --create_session
```

2. List all sessions:
```bash
poetry run deploy-local --list_sessions
```

3. Get details of a specific session:
```bash
poetry run deploy-local --get_session --session_id=your-session-id
```

4. Send a message to shorten:
```bash
poetry run deploy-local --send --session_id=your-session-id --message="Shorten this message: Hello, how are you doing today?"
```

### Remote Deployment

1. Deploy the agent:
```bash
poetry run deploy-remote --create
```

2. Create a session:
```bash
poetry run deploy-remote --create_session --resource_id=your-resource-id
```

3. List sessions:
```bash
poetry run deploy-remote --list_sessions --resource_id=your-resource-id
```

4. Send a message:
```bash
poetry run deploy-remote --send --resource_id=your-resource-id --session_id=your-session-id --message="Hello, how are you doing today? So far, I've made breakfast today, walkted dogs, and went to work."
```

5. Clean up (delete deployment):
```bash
poetry run deploy-remote --delete --resource_id=your-resource-id
```

## Project Structure

```
adk-short-bot/
├── adk_short_bot/          # Main package directory
│   ├── __init__.py
│   ├── agent.py           # Agent implementation
│   └── prompt.py          # Prompt templates
├── deployment/            # Deployment scripts
│   ├── local.py          # Local testing script
│   └── remote.py         # Remote deployment script
├── .env                  # Environment variables
├── poetry.lock          # Poetry lock file
└── pyproject.toml       # Project configuration
```

## Development

To add new features or modify existing ones:

1. Make your changes in the relevant files
2. Test locally using the local deployment script
3. Deploy to remote using the remote deployment script
4. Update documentation as needed

## Troubleshooting

1. If you encounter authentication issues:
   - Ensure you're logged in with `gcloud auth login`
   - Verify your project ID and location in `.env`
   - Check that the Vertex AI API is enabled

2. If deployment fails:
   - Check the staging bucket exists and is accessible
   - Verify all required environment variables are set
   - Ensure you have the necessary permissions in your Google Cloud project

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

[Your chosen license]
