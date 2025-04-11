Single HTML file to interface with google's gemini models including the latest gemini pro 2.5. 
SImply open the page in a web browser, enter your key, select a model, and begin chatting.

This should work on any operating system with a modern web browser.
Contributions are welcome, the initial version was written by gemini pro 2.5 03-35.

Go to relases, download gemini.zip, open it, and open gemini.html in a web browser.

GeminiHTML Web Application - User Guide
Welcome to GeminiHTML!

This web application provides a simple interface to interact with Google's Gemini AI models directly from your browser. You can have text-based conversations, configure generation parameters, upload files for analysis (with compatible models), and view the responses formatted with Markdown and code highlighting.

1. Getting Started: API Key
Before you can use the application, you need to provide your Google AI Studio API Key.

Where to get a key: You can obtain an API key from Google AI Studio (you'll need a Google account).
Entering the Key:
Locate the "API Key" field at the top of the application.
Paste your API key into this field. It's a password field, so the characters will be hidden.
Remember Key:
Check the "Remember Key (Uses Local Storage)" box if you want the browser to save your API key for future sessions.
⚠️ Security Warning: Be cautious using this feature on shared or public computers, as the key is stored in your browser's local storage, which might not be secure in such environments. Uncheck the box if you don't want the key saved. The key is automatically saved/removed as you check/uncheck the box if a key is present in the input field.
Automatic Model Loading: Once you enter a valid API key, the application will automatically try to fetch the list of available Gemini models you have access to.
2. Selecting a Model
After providing a valid API key, the models available to you will load in the "Select Model" dropdown menu.

Choosing a Model: Click the dropdown and select the Gemini model you wish to interact with.
Model Compatibility:
The list shows models compatible with the generateContent method used by this app.
File Uploads: For uploading files (images, PDFs, etc.), you generally need a multimodal model. Models like gemini-1.5-pro-latest are recommended for this functionality (they will often have "(Multimodal)" appended to their name in the dropdown). Using file upload with text-only models might result in errors or unexpected behavior.
Current Model Display: The name of the currently selected model is displayed in the footer at the bottom of the page.
3. Configuration Options (Optional)
You can fine-tune the AI's responses using the settings under "Configuration Options". Click the summary text to expand/collapse these settings.

Temperature (0-1): Controls the randomness of the output.
Lower values (e.g., 0.2) make the output more focused, deterministic, and predictable.
Higher values (e.g., 0.9) make the output more creative, diverse, and sometimes less coherent.
Default: 0.7
Max Output Tokens: Sets the maximum length of the AI's response in tokens (roughly words or parts of words). This helps control response length and cost (if applicable to your API usage).
Default: 8192
Top P (0-1): An alternative sampling method to Temperature. The model considers only the most probable tokens whose cumulative probability exceeds the topP value. Higher values mean more tokens are considered.
Default: 0.95
Top K (integer): Another sampling method. The model considers only the topK most probable tokens at each step.
Default: 40
You generally don't need to change these unless you have specific requirements for the AI's output style or length.

4. The Conversation Interface
This is the main area where you interact with the AI.

Conversation History: This area displays the ongoing chat.
Your messages appear in blue bubbles aligned to the right (User).
The AI's responses appear in grey/themed bubbles aligned to the left (Model).
Initially, it shows "Conversation will appear here...".
Your Message Input:
Type your message or question for the AI in the text area labeled "Your Message".
Shortcut: Press Ctrl+Enter (or Cmd+Enter on Mac) while typing in the message box to send the message without clicking the button.
Status Area: Located below the conversation history, this area displays important information:
Loading available models...: Shows when fetching models after key entry.
Processing request... (with a spinner): Appears after you send a message while waiting for the AI's response.
Response received. Finish Reason: ...: Indicates a successful response and why the AI stopped generating (e.g., STOP for normal completion, MAX_TOKENS if truncated).
Warning: ...: Shows non-critical issues (e.g., using a potentially incompatible model for files, response blocked for safety/recitation).
Error: ...: Displays errors (e.g., invalid API key, network issues, request blocked).
5. Sending Messages
Type your message in the "Your Message" text area.
Click the "Send" button or use the Ctrl+Enter / Cmd+Enter shortcut.
Your message will appear in the Conversation History, and the Status Area will show "Processing request...".
Once the AI responds, its message will appear below yours in the history.
6. Uploading Files (Multimodal Interaction)
You can upload files (like images, PDFs, audio, video, text files) to be processed by a compatible multimodal model along with your text prompt.

Select a File:
Click the "Upload File" button (with the upload icon). This will open your device's file browser.
Choose the file you want to upload. The application accepts common image, PDF, audio, video, and text formats (image/*, application/pdf, audio/*, video/*, text/*).
There's a client-side size check (around 20MB) before processing, but the API itself may have stricter limits depending on the model and file type.
File Selection Display: Once you select a file, its name will appear next to the "Upload File" button (e.g., Selected: my_image.jpg). If there's an issue reading the file, an error will show in the Status Area.
Sending the File:
The selected file is sent along with your next message when you click the "Send" button.
You can optionally add text in the "Your Message" box to provide context or ask questions about the file (e.g., "Describe this image" or "Summarize this document").
You can also send just the file by leaving the message box empty and clicking "Send".
After Sending:
Your user bubble in the chat history will show your text (if any) and an indication that a file was sent (e.g., 📎 File Uploaded: my_image.jpg (image/jpeg)).
The file selection is cleared automatically after you click "Send". If you want to ask another question about the same file, you need to upload it again.
Model Choice: Remember to select a model capable of handling files (like gemini-1.5-pro-latest) for this feature to work correctly.
7. Reading AI Responses
Formatting: The AI's responses are rendered using Markdown. This means you'll see formatting like:
Headings (#, ##)
Bold (**text**) and Italic (*text*) text
Bullet points (* or -) and numbered lists (1.)
Blockquotes (>)
Inline code (code)
Code Blocks: Code snippets provided by the AI are displayed in formatted blocks with syntax highlighting based on the detected language.
Copy Code Button: A "Copy" button appears at the top-right corner when you hover over a code block. Click it to easily copy the code snippet to your clipboard. The button will briefly change to "Copied!" on success or "Error" if copying fails.
8. Other Features
Theme Switcher: Click the Moon (🌙) / Sun (☀️) icon in the top-right corner to toggle between Light and Dark themes. Your preference is saved in your browser.
Clear Chat: Click the "Clear Chat" button to remove all messages from the Conversation History and reset the conversation state. This also clears any selected file.
9. Troubleshooting
"API Key not valid..." Error: Double-check that you have copied and pasted your API key correctly. Ensure the key is enabled in your Google AI Studio project.
"Failed to list models..." or "Error loading models..." Error: Check your internet connection and ensure your API key is correct and has permissions.
"No compatible models found..." Status: Your API key might be valid but might not have access to models supporting the generateContent method.
"Please select a valid model." Error: You need to choose a model from the dropdown before sending a message. This usually happens if the models haven't loaded yet or if you haven't selected one after they loaded.
"Message or file upload is required." Error: You must either type text in the message box or select a file to upload before clicking "Send".
File Upload Issues: Ensure you're using a multimodal model (like Gemini 1.5 Pro or above). Check the file size; very large files might fail. The API might not support the specific format or content of your file.
Blocked Responses (Finish Reason: SAFETY or PROMPT_BLOCKED): Your prompt or the AI's generated response might have triggered Google's safety filters. Try rephrasing your message.
