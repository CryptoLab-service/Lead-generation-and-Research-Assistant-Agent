# Troubleshooting Guide

## Common Issues and Solutions

### Issue: "No prompt specified" error

**Possible Causes:**
1. The text cleaning node failed to process the input
2. The input structure doesn't match what the workflow expects
3. The connection between nodes is broken

**Solutions:**
1. Verify all nodes are properly connected in this order: Input → Set node → Lead Agent node
2. Check that input data has the expected structure (content.parts[0].text)
3. Test with mock data to isolate whether the issue is with the input format or node connections

### Issue: Voice messages not being transcribed

**Possible Causes:**
1. Missing Google Gemini API credentials
2. Audio format not supported
3. Network issues preventing API call

**Solutions:**
1. Verify your Google Gemini API credentials are correct and have sufficient quota
2. Check that the audio file is in a supported format (typically MP3 or WAV)
3. Test with a known good audio file to verify the transcription service works

### Issue: Lead scraping fails

**Possible Causes:**
1. Invalid search parameters (incorrect format)
2. Google Sheets permissions issue
3. API quota exceeded

**Solutions:**
1. Verify the search query format (spaces replaced with '+')
   - Example: "san francisco" should be "san+francisco"
2. Check Google Sheets permissions:
   - Ensure the service account has edit access to the sheet
   - Verify the sheet ID in your workflow is correct
3. Monitor your API usage against quotas:
   - Check your Google Cloud Console for usage metrics
   - Consider adding rate limiting if you're approaching limits

## Advanced Troubleshooting

### Debugging Node Connections

If nodes aren't executing in the expected order:

1. Go to the n8n UI and view your workflow
2. Verify the connections between nodes are properly configured
3. Use the "Execute Node" feature to test individual nodes

### Log Analysis

To diagnose issues:

1. Check the execution logs in n8n
2. Look for error messages or warnings
3. Pay attention to timestamps to understand the workflow execution order

### Common Fixes

1. **For authentication errors**:
   - Double-check all API keys
   - Regenerate keys if needed
   - Ensure IP restrictions aren't blocking requests

2. **For performance issues**:
   - Add delay nodes if APIs are being rate limited
   - Optimize node execution order
   - Consider breaking large workflows into smaller sub-workflows
