# Lead Generation and Research Assistant Agent

An AI-powered assistant for lead generation and research, integrated with Telegram for voice and text interactions, with Google Gemini for transcription and chat capabilities.

## Features

- Voice and text input processing
- Lead scraping based on location, business type, and job titles
- LinkedIn research capabilities
- Memory management for conversation context
- Error handling and user-friendly responses

---
```mermaid
flowchart TD
  A --> B
  B -->|🎙️ Voice| C
  B -->|✍️ Text| G
  C --> D
  D --> E
  E -->|✅ Needs Cleaning| F
  E -->|🚫 Clean| H
  F --> H
  G --> H
  %% Lead Agent components
  subgraph 🧩 Components
    H -- 🧠 memory --> I
    H -- 🤖 model --> J
    H -- 🔎 tool --> K
    H -- 🔗 tool --> L
  end
  %% Output paths
  H --> M
  H --> N
```
---

# 🧩 Workflow Details

This workflow is designed to handle Telegram-based input and process both voice and text messages using AI-powered tools. It includes modular components for transcription, cleaning, lead generation, and error handling.

---

## 🔹 Input Handling

- **Telegram Trigger**: Receives incoming messages from Telegram.
- **Voice or Text Switch Node**: Determines whether the message is a voice or text input and routes accordingly.

---

## 🔊 Voice Processing Path

- **Download File Node**: Downloads the voice message file.
- **Transcribe a Recording Node**: Uses Google Gemini to transcribe the audio.
- **Check for Noise Node**: Detects whether the transcription contains noise or formatting issues.
- **Clean Transcription Node**: Removes timestamps, annotations, and other noise from the transcription.
- **Lead Agent**: Receives the cleaned text and processes the request.

---

## 💬 Text Processing Path

- **Text Node**: Directly forwards text messages to the Lead Agent for processing.

---

## 🧠 Lead Agent

The Lead Agent is the core AI component responsible for understanding and responding to user requests.

### Integrated Components:

- **Google Gemini Chat Model**: Generates intelligent responses.
- **Simple Memory Node**: Maintains conversation context for continuity.
- **leadScraping Tool**: Scrapes leads based on user-defined criteria.
- **leadResearch Tool**: Researches LinkedIn profiles for enriched lead data.

---

## 📤 Output Handling

- **Response Node**: Sends successful responses back to the user.
- **Error Response Node**: Handles and returns error messages when something goes wrong.

---

## 🌟 Key Features

- **Multi-modal Input**: Seamlessly supports both voice and text messages.
- **Automatic Transcription**: Converts voice messages into readable text.
- **Text Cleaning**: Removes unnecessary formatting and noise from transcriptions.
- **Modular Design**: Each component is isolated for easy updates and maintenance.
- **Error Handling**: Dedicated error path ensures graceful failure management.
- **Memory Support**: Maintains context across interactions for smarter responses.

---

## 🛠️ Customization Points

- Modify the **Clean Transcription Node** to adjust how noise and formatting are removed.
- Add new tools to the **Lead Agent** by connecting additional nodes.
- Customize the **system prompt** in the Lead Agent to change its behavior or personality.
- Adjust formatting logic in the **Response** and **Error Response** nodes to suit your output style.

---

## System Requirements

- n8n workflow automation tool
- Telegram API credentials
- Google Gemini (PaLM) API credentials
- Access to Google Sheets for lead storage

## Setup Instructions

### Prerequisites

1. Install n8n (either self-hosted or cloud version)
2. Set up Telegram bot:
   - Create a new bot with BotFather
   - Get your Telegram API credentials
3. Get Google Gemini API access

### Installation

1. Clone this repository
2. Import the workflow JSON file into your n8n instance
3. Configure credentials for Telegram and Google Gemini APIs

### Configuration

1. **Telegram API**:
   - Create a Telegram bot via BotFather
   - Get your API token and set it in the Telegram nodes

2. **Google Gemini API**:
   - Set up your Google Cloud account with PaLM API access
   - Configure the API credentials in the Google Gemini nodes

### Importing the Workflow

1. In your n8n dashboard, go to Workflows
2. Click "Import from file"
3. Upload the workflow JSON file
4. Set up your connections and credentials

## Workflow Components

### Key Nodes

1. **Telegram Trigger**: Receives messages from Telegram
2. **Voice/Text Switch**: Routes messages based on type
3. **Transcription Service**: Converts voice messages to text using Google Gemini
4. **Text Cleaner**: Removes timestamps and annotations from transcriptions
5. **Lead Agent**: Main AI agent that processes requests
6. **Response Handler**: Sends back responses via Telegram

### Error Handling

The workflow includes error response paths for:
- Missing prompts
- Failed API calls
- Unexpected input formats

## Usage Examples

### Basic Interaction

1. User sends text message: "Find me CEOs of tech companies in New York"
2. System responds with clarifying questions if needed
3. System performs search and returns results

### Voice Interaction

1. User sends voice message with the same request
2. System transcribes the audio
3. Processes the request as above

## Troubleshooting

Common issues and solutions:

1. **"No prompt specified" error**:
   - Ensure the text cleaner node is properly connected
   - Verify that the cleaned_text field is being created

2. **API credential errors**:
   - Double-check your API keys
   - Ensure proper permissions are set

3. **Workflow execution failures**:
   - Check node connections
   - Verify that all required input data is present

## Development

To modify or extend this workflow:

1. Fork the repository
2. Make your changes to the workflow JSON file
3. Test thoroughly with different input types
4. Submit a pull request with your improvements

## License

MIT License - see LICENSE file for details
