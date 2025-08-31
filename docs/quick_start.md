# Quick Start Guide

## 1. Prerequisites

Before you begin, ensure you have:

1. An n8n instance (self-hosted or cloud)
2. A Telegram account and a new bot created via BotFather
3. Google Cloud account with PaLM API access
4. Google Sheets account for storing leads
5. Node.js installed (if running n8n locally)

## 2. Installation Steps

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/lead-generation-assistant.git
   cd lead-generation-assistant
   ```
2. Import the workflow:
a. In your n8n dashboard, go to Workflows
b. Click "Import from file"
c. Upload the workflow JSON file from the /workflows directory

3. Configure credentials:
* Telegram API token
* Google Gemini API key
* Google Sheets access credentials

## 3. Testing the Workflow
1. Start with text messages to verify basic functionality:
   * Send a text message to your Telegram bot with a lead request
   * Verify you receive a proper response

2. Test voice messages to ensure transcription works correctly:
   * Send a voice message to your bot
   * Verify the transcription and response

3. Try various request combinations:
   * Different locations
   * Various business types
   * Multiple job titles

## 4. Common First Issues
1. Authentication errors:
   * Double-check your API keys in n8n's credential management
   * Ensure your Telegram bot token is correct

2. Transcription issues:
   * Verify your Google Gemini API access
   * Test with a known good audio file

3. Lead scraping failures:
   * Check your Google Sheets permissions
   * Verify the sheet ID in your workflow
   * Ensure your API quotas aren't exhausted

## 5. Customization
To customize the system for your needs:
1. Edit the system prompt in the Lead Agent node to match your requirements
2. Add or modify the tools available to the agent
3. Adjust the response formatting in the Response node
4. Customize default locations or business types in the system message

---

## Implementation Notes

1. **Workflow Import**: The workflow JSON file contains the complete configuration of your lead generation assistant. Import this into n8n to get started.

2. **Credential Security**: Never commit your actual API keys or credentials to version control. Use environment variables or n8n's credential management system.

3. **Testing**: The mock data files provide different scenarios to test your workflow:
   - Regular text inputs
   - Voice inputs with noise annotations
   - Error cases

4. **Customization**: The documentation guides you through common customizations like adding new locations or business types.
