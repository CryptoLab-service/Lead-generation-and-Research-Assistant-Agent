# Development Guide

## Extending the Workflow

### Adding New Tools

To add a new research tool:

1. Create a new Tool Workflow node in your n8n workflow
2. Configure it with:
   - A descriptive name
   - Clear input format requirements
   - Proper error handling

3. Add it to the Lead Agent's available tools by:
   a. Connecting its output to the Lead Agent node
   b. Updating the system message to describe when to use it

4. Update the system message to include:
   - When to use the tool
   - Expected input format
   - Example outputs

### Modifying the System Prompt

To update the agent's behavior:

1. Edit the system message in the Lead Agent node
2. Maintain the format requirements for tool usage (especially JSON formatting)
3. Test thoroughly with various input types including:
   - Short requests
   - Complex requests
   - Partial information requests

### Performance Considerations

1. **Transcription Time**:
   - The full transcription and cleaning process should ideally take less than 5 seconds
   - Consider adding loading messages for longer operations

2. **Lead Search Time**:
   - Scraping operations may take longer (aim for under 30 seconds)
   - Add progress indicators if searches take longer

3. **API Usage**:
   - Monitor your Google Gemini API usage against quotas
   - Consider caching frequent queries
   - Implement retry logic with exponential backoff for rate limits

## Testing Guidelines

### Test Cases

1. Basic text input tests:
   - Simple requests with all required information
   - Requests missing some parameters
   - Very long requests

2. Voice input tests:
   - Clear voice recordings
   - Recordings with background noise
   - Recordings with timestamps or annotations

3. Edge cases:
   - Empty inputs
   - Requests with special characters
   - Malformed requests

### Test Data

Use the mock data files provided in this repository to test different scenarios.

### Debugging Tips

1. Use n8n's execution logs extensively
2. Test nodes individually before testing the full workflow
3. For transcription issues, test with pre-recorded audio files of known quality
