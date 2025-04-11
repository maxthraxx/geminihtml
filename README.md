Single HTML file to interface with google's gemini models including the latest gemini pro 2.5. 
SImply open the page in a web browser, enter your key, select a model, and begin chatting.

This should work on any operating system with a modern web browser.
Contributions are welcome, the initial version was written by gemini pro 2.5 03-35.

# Key features : streaming chat, code blocks that you can copy or download, light and dark themes, chat history, source code highlighting, and file uploads.

Go to relases, download gemini.zip, open it, and open gemini.html in a web browser.

# GeminiHTML - User Guide

Welcome to GeminiHTML! This guide explains how to use this web interface to interact with Google's Gemini AI models.

**What is GeminiHTML?**
GeminiHTML is a self-contained web application that runs entirely in your browser. It allows you to chat with Google Gemini models, upload files for analysis (with compatible models), configure generation parameters, and view the conversation history. It requires your own Google AI Studio API Key to function.

---

## 1. Getting Started

1.  **Open the App:** Open the `GeminiHTML.html` file in your web browser (like Chrome, Firefox, Edge, Safari).
2.  **Enter API Key:**
    *   Locate the **API Key** field at the top.
    *   Enter your **Google AI Studio API Key**. Get one from [ai.google.dev](https://ai.google.dev/).
    *   **(Optional)** Check **Remember Key** to save the key in your browser's local storage for future use. *Use with caution, especially on shared computers.*
3.  **Select Model:**
    *   Once a valid API key is entered, the **Select Model** dropdown will automatically load available Gemini models compatible with this app.
    *   Choose a model. Models marked `(Multimodal)` or `1.5 Pro` are recommended if you plan to upload files. The currently selected model is shown in the footer.

---

## 2. Core Features

*   **Sending Messages:**
    *   Type your message or prompt into the **Your Message** text area at the bottom.
    *   Click the **Send** button or press `Ctrl+Enter` (or `Cmd+Enter` on Mac).

*   **Uploading Files (for Multimodal Models):**
    *   Click the **Upload File** button.
    *   Select an image, PDF, audio, video, or text file from your device.
    *   The selected filename will appear next to the button (e.g., `Selected: my_image.jpg`).
    *   You can optionally add text in the **Your Message** box to provide context or ask questions about the file.
    *   Click **Send**. The file data will be sent along with your text (if any) to the selected model.
    *   *Note:* File uploads work best with models like `gemini-1.5-pro-latest`. Performance with other models may vary or fail.

*   **Viewing Conversation:**
    *   Your messages appear as blue bubbles (`user-bubble`) on the right.
    *   The AI's responses appear as grey bubbles (`model-bubble`) on the left.
    *   Responses are streamed in real-time. A blinking cursor (`▌`) indicates the model is generating.
    *   Model responses are formatted using Markdown (headings, lists, bold, italics, etc.).

*   **Interacting with Code Blocks:**
    *   If the model provides code, it will appear in a formatted block.
    *   Hover over the top-right corner of the code block to reveal buttons:
        *   **Copy:** Click to copy the code to your clipboard.
        *   **Save:** Click to download the code block as a file (e.g., `code_block.py`).

*   **Configuration Options:**
    *   Click on **Configuration Options** to expand the settings panel.
    *   Adjust parameters to influence the model's output:
        *   **Temperature:** Controls randomness (0 = deterministic, 1 = max randomness).
        *   **Max Output Tokens:** Limits the length of the model's response.
        *   **Top P / Top K:** Advanced sampling parameters (usually leave at defaults unless you know what they do).

*   **Theme Switching:**
    *   Click the **Dark** / **Light** button in the top-right header to toggle the interface theme.

*   **Clearing the Chat:**
    *   Click the **Clear Chat** button to remove the entire conversation history from the screen and memory.

---

## 3. Status & Errors

*   The area below the chat history (`#status`) displays information:
    *   **Loading indicators:** Show when models are loading or a response is generating.
    *   **Success messages:** Confirm actions like model loading or response completion (including token usage).
    *   **Warnings (Yellow):** Indicate potential issues (e.g., response cut off by `MAX_TOKENS`, safety blocks, using non-multimodal model with files).
    *   **Errors (Red):** Show critical problems (e.g., Invalid API Key, network errors, file read errors, blocked prompts). Check the message for details.

---

## 4. Important Notes

*   **Local Execution:** This app runs entirely in *your* browser. Your API key and conversation data are *not* sent to any server other than the official Google AI API endpoint.
*   **API Key Security:** Be mindful when using the "Remember Key" feature, as the key is stored unencrypted in your browser's local storage.
*   **File Limits:** While the app has a ~50MB example limit for reading files, the actual limits depend on the specific Gemini model and the API itself. Large files may take time to process or exceed API limits.
*   **Troubleshooting:** If you encounter issues:
    *   Check the **Status** area for error messages.
    *   Verify your **API Key** is correct and has permissions.
    *   Open your browser's **Developer Console** (usually F12) to look for more detailed error messages.

---

*Thank you for using GeminiHTML!*
