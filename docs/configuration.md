# Configuration Guide

## Setting Up Telegram API

1. Create a new bot with BotFather on Telegram:
   a. Open Telegram and search for BotFather
   b. Send `/newbot` command
   c. Follow instructions to name your bot and get the API token

2. Configure the Telegram Trigger node:
   a. Paste your API token
   b. Set up webhook URL if using webhook mode

## Setting Up Google Gemini API

1. Go to Google Cloud Console (console.cloud.google.com)
2. Create a new project or select an existing one
3. Enable the PaLM API for your project
4. Create API credentials:
   a. Go to APIs & Services > Credentials
   b. Create a new API key
   c. Restrict the key to the PaLM API for security

5. Configure the Google Gemini nodes with these credentials

## Workflow Customization

### Adding New Locations

To add new default locations:

1. Modify the system message in the Lead Agent node to include new location examples
2. Update any default location lists in the workflow if applicable

### Adding New Business Types

Similarly, you can add new business types by updating the relevant parts of the system message and workflow logic.

### Adding New Tools

To add a new research tool:

1. Create a new Tool Workflow node
2. Configure it with the appropriate API/workflow
3. Add it to the Lead Agent's available tools
4. Update the system message to describe the new tool and its format requirements
