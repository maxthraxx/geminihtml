Single HTML file to interface with google's gemini models including the latest gemini pro 2.5. 
SImply open the page in a web browser, enter your key, select a model, and begin chatting.

This should work on any operating system with a modern web browser.
Contributions are welcome, the initial version was written by gemini pro 2.5 03-35.

Go to relases, download gemini.zip, open it, and open gemini.html in a web browser.

# GeminiHTML - User Documentation

## 1. Introduction

GeminiHTML is a web-based interface that allows you to interact with Google's Generative AI models (like the Gemini family) directly from your browser. You can have text-based conversations, configure model parameters, upload files (for multimodal models), and view the formatted responses, including syntax-highlighted code blocks.

## 2. Getting Started: API Key

1.  **Obtain an API Key:** You need a Google AI Studio API key to use this application. You can get one from the [Google AI Studio website](https://aistudio.google.com/app/apikey).
2.  **Enter the API Key:** Paste your API key into the "API Key" input field at the top of the page.
3.  **Model Loading:** Once a valid API key is entered, the application will automatically try to fetch the list of available Gemini models compatible with the API key and populate the "Select Model" dropdown.
4.  **(Optional) Remember Key:** Check the "Remember Key" box if you want the browser to store your API key in its Local Storage for future sessions.
    *   **⚠️ Security Warning:** Storing API keys in browser storage is convenient but insecure, especially on shared computers. Use this feature with caution. If unchecked, the key will be forgotten when you close the browser tab/window.

## 3. Interface Overview

The application is divided into several sections:

1.  **Header:**
    *   **Title:** "Gemini HTML".
    *   **Theme Switcher:** A button (showing "Dark" or "Light") to toggle between light and dark modes.

2.  **API Key & Model Selection:**
    *   **API Key Input:** Where you enter your Google AI Studio API key.
    *   **Remember Key Checkbox:** Option to save the key locally.
    *   **Model Select Dropdown:** Choose the specific Gemini model you want to interact with. This is enabled only after a valid API key is entered and models are loaded. Models suitable for file uploads (multimodal) are usually indicated (e.g., "Gemini 1.5 Pro (Multimodal)").

3.  **Configuration Options (Collapsible):**
    *   Click "Configuration Options" to expand/collapse advanced settings.
    *   **Temperature (0-1):** Controls randomness. Lower values (e.g., 0.2) make the output more deterministic and focused. Higher values (e.g., 0.9) make it more creative and diverse. Default: 0.7.
    *   **Max Output Tokens:** The maximum number of tokens (words/subwords) the model should generate in its response. Default: 8192.
    *   **Top P (0-1):** Nucleus sampling parameter. The model considers only the tokens whose cumulative probability mass exceeds this threshold. Default: 0.95.
    *   **Top K (integer):** The model considers only the top 'K' most likely tokens at each step. Default: 40.

4.  **Conversation History:**
    *   The main area where the chat interaction appears.
    *   User messages are shown in bubbles aligned to the right.
    *   Model responses are shown in bubbles aligned to the left.
    *   Initially shows "Conversation will appear here...".

5.  **Status Bar:**
    *   Located below the chat history.
    *   Displays status messages like "Loading available models...", "Processing request...", "Response received.", error messages (red), or warnings (yellow).
    *   Shows a spinning loader icon during API calls.
    *   May display token usage information after a successful response.

6.  **Input Area:**
    *   **Your Message Textarea:** Type your prompts/messages here. Press `Ctrl+Enter` (or `Cmd+Enter` on Mac) as a shortcut to send the message.
    *   **Upload File Button:** Click this to select a file (image, PDF, audio, video, text) from your device.
        *   The selected file's name will appear next to the button (e.g., "Selected: my_image.jpg").
        *   The file data will be sent along *with your next text message* to the model.
        *   **Note:** File uploads are only effectively processed by multimodal models (like Gemini 1.5 Pro). Using files with text-only models may lead to errors or unexpected behavior.
    *   **Send Button:** Click to send your current message (and any selected file) to the Gemini API. Disabled while processing or if the API key/model is missing.
    *   **Clear Chat Button:** Clears the conversation history, the prompt input, and any selected file.

7.  **Footer:**
    *   Provides a link to the Google Gemini API documentation.
    *   Displays the name of the currently selected model (e.g., "Using model: Gemini 1.5 Pro (Multimodal)").

## 4. Core Functionality

1.  **Sending a Message:**
    *   Ensure you have entered a valid API Key and selected a Model.
    *   Type your message into the "Your Message" textarea.
    *   Click the "Send" button or press `Ctrl+Enter`/`Cmd+Enter`.
    *   Your message appears in the chat history (right-aligned).
    *   The status bar shows "Processing request...".
    *   The model's response appears below your message (left-aligned).

2.  **Using File Uploads:**
    *   Select a multimodal model (e.g., "Gemini 1.5 Pro or later").
    *   Click the "Upload File" button and choose a supported file.
    *   The filename appears next to the button.
    *   Type a related prompt in the "Your Message" textarea (e.g., "Describe this image", "Summarize this document"). The text prompt is often necessary to give context to the file.
    *   Click "Send".
    *   Your message bubble will include the text and an indication of the uploaded file (e.g., "📎 File Uploaded: image.png (image/png)").
    *   The model will process both the text and the file content to generate a response.

3.  **Clearing the Conversation:**
    *   Click the "Clear Chat" button to remove all messages from the display and reset the input fields. This does *not* delete history on the backend (if any logging occurs there), only in the browser session.

## 5. Features

*   **Light/Dark Mode:** Switch themes using the button in the header for comfortable viewing. The preference is saved locally.
*   **Markdown Rendering:** Model responses are rendered using Markdown, supporting:
    *   Headings (`#`, `##`, etc.)
    *   Lists (bulleted and numbered)
    *   Bold and Italic text
    *   Blockquotes
    *   Inline code (`like this`)
    *   Code blocks (see below)
*   **Syntax Highlighting:** Code blocks within the model's response are automatically detected and syntax-highlighted for readability.
*   **Copy Code Button:** A "Copy" button appears at the top-right corner when you hover over a code block in the model's response. Click it to copy the code snippet to your clipboard. The button briefly changes to "Copied!" on success.
*   **Model Selection Persistence:** The currently selected model is remembered for the session.
*   **API Key Persistence (Optional):** If "Remember Key" is checked, the key is stored for future visits.

## 6. Troubleshooting & Notes

*   **"API Key not valid" Error:** Double-check that you have correctly pasted your API key. Ensure the key is enabled in your Google AI Studio project and has the necessary permissions.
*   **"Failed to list models" / "Error loading models":** Check your internet connection and ensure the API key is valid. Sometimes, Google's services might have temporary issues.
*   **Model Dropdown Disabled:** Enter a valid API key first. If it remains disabled after entering a key, check the status bar for errors.
*   **File Upload Issues:**
    *   Ensure you have selected a multimodal model (like Gemini 1.5 Pro). Text-only models cannot process file data.
    *   Check the file size. While the UI has a basic check (e.g., 50MB), the actual API limits might differ. Large files can cause errors or timeouts.
    *   Ensure the file type is generally supported (images, PDFs, common audio/video/text formats). Exotic types might not be processed correctly.
*   **Blocked Responses:** Sometimes, the API might block a prompt or response due to safety filters or other policies. The status bar will usually indicate this (e.g., "PROMPT_BLOCKED", "Finish Reason: SAFETY").
*   **"Max Tokens" Reached:** If the model's response is cut short and the status shows "Finish Reason: MAX_TOKENS", the response exceeded the configured "Max Output Tokens" limit. You can increase this limit in the Configuration Options if needed (within the model's maximum context window).
*   **API Key Security:** Remember that storing API keys in the browser's Local Storage is not recommended for high-security environments or shared computers.
