# Lead Generation and Research Assistant Agent

An AI-powered assistant for lead generation and research, integrated with Telegram for voice and text interactions, with Google Gemini for transcription and chat capabilities.

## Features

- Voice and text input processing
- Lead scraping based on location, business type, and job titles
- LinkedIn research capabilities
- Memory management for conversation context
- Error handling and user-friendly responses

## Workflow Diagram

```mermaid
flowchart TD
    %% Define styles
    classDef start fill:#f9f,stroke:#333,stroke-width:2px;
    classDef process fill:#ffc,stroke:#333,stroke-width:2px;
    classDef decision fill:#cfc,stroke:#333,stroke-width:2px;
    classDef end fill:#bbf,stroke:#333,stroke-width:2px;
    classDef component fill:#fcf,stroke:#333,stroke-width:1px;

    %% Define all nodes with descriptions
    A[Telegram Trigger\nReceives messages from Telegram]:::start
    B{"Voice or Text\nSwitch node"}:::decision
    C[Download File\nDownloads voice message file]:::process
    D[Transcribe a recording\nUses Google Gemini to transcribe]:::process
    E{"Check for noise\nDetects if transcription needs cleaning"}:::decision
    F[Clean transcription\nRemoves timestamps and annotations]:::process
    G[Text\nHandles text messages directly]:::process
    H["Lead Agent\nMain AI agent that processes requests"]:::process
    I[Simple Memory\nStores conversation context]:::component
    J[Google Gemini Chat Model\nProvides AI responses]:::component
    K[leadScraping Tool\nScrapes leads based on criteria]:::component
    L[leadResearch Tool\nResearched LinkedIn profiles]:::component
    M[Response\nSends back successful responses]:::end
    N[Error Response\nHandles error cases]:::end

    %% Voice path
    A --> B
    B -->|Voice| C
    C --> D
    D --> E
    E -->|Needs Cleaning| F
    E -->|Clean| H
    F --> H

    %% Text path
    B -->|Text| G
    G --> H

    %% Lead Agent components
    subgraph LeadAgentComponents["Lead Agent Components"]
        direction TB
        H -- ai_memory --> I
        H -- ai_languageModel --> J
        H -- ai_tool --> K
        H -- ai_tool --> L
    end

    %% Response paths
    H --> M
    H --> N

    %% Add a legend
    legend
      |<b>Legend</b>|
      |Start: Telegram input|
      |Decision: Switch/routers|
      |Process: Main workflow steps|
      |Component: Agent subsystems|
      |End: Output nodes|
    end
```

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
