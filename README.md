# YoutubeSummarAI

Generate YouTube summaries using latest AI tech and services

## Description

YoutubeSummarAI is an advanced tool that leverages cutting-edge AI technology to automatically generate concise summaries of YouTube videos. This project aims to save time for users by providing quick, accurate summaries of video content, making it easier to decide whether to watch a full video or get the main points quickly.

## Features

- Extract speech from YouTube videos using local speech recognition via Whisper or use YoutubeToText API
- Generate summaries using local AI models or popular AI services
- Chrome extension for seamless integration with YouTube 
- Support for multiple source languages (summaries currently only support English)
- Customizable summary length and style (planned feature)

## Project Structure

- `YoutubeSummarAI/`: Main project directory
  - `backend/`: Backend directory
  - `extension/`: Chrome extension directory

## Installation

### Backend Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/YoutubeSummarAI.git
   ```
2. Navigate to the project directory:
   ```bash
   cd YoutubeSummarAI/backend
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Set up environment variables:
   - Create a `.env` file in the `backend` directory
   - Add necessary API keys  (refer to `YoutubeSummarAI\backend\.env.example`)
   - TODO: Make backend models configurable via file (currently hardcoded Llama 3.1 setup, you can put the llama 3.1 GGUF model file in the `backend` directory)
   - Backend can be either run with ad-hoc `python main.py` or installed as windows service with `python main.py install` and uninstalled with `python main.py remove`

*note: if you are using the `python main.py install` option, you will need to run the command prompt with admin privileges*

### Chrome Extension Setup

1. Open Google Chrome/Brave/Edge/etc. and navigate to `chrome://extensions/`
2. Enable "Developer mode" in the top right corner
3. Click "Load unpacked" and select the `extension` directory from the project
4. You can review and change options by clicking on the YoutubeSummarAI extension icon in the Chrome toolbar

## Usage

1. Open a YouTube video in Google Chrome
2. Click on the YoutubeSummarAI extension icon
3. Select desired summary options (if available)
4. Click "Generate Summary" to get a concise summary of the video content

## Options page

The extension's options page allows users to customize various settings:

1. Backend URL: This setting specifies the server address for video transcription and processing. By default, it's set to a local server (e.g., http://localhost:5000). You may need to adjust this URL based on your specific setup. To troubleshoot connection issues, check the service log file located at:
   C:\ProgramData\YouTubeTranscriptionService\youtube_transcription_service.log

2. Transcription Method:
   - Choose between YouTube API or different Whisper models for transcribing video content.
   - Options include YouTube API, Whisper (Base), Whisper (Base English), Whisper (Tiny), etc.

3. Process Locally:
   - Toggle between processing summaries locally or using an external AI provider.
   - Options: Yes or No

4. AI Provider (when not processing locally):
   - Select from various AI providers for summary generation.
   - Options are dynamically populated based on available providers.

5. Provider-specific settings:
   - Each AI provider has its own set of configurable options:
     - URL: The endpoint for the AI service
     - Input Selector: CSS selector for the input field
     - Button Selector: CSS selector for the submit button
     - Confirm Button Selector: CSS selector for any confirmation button (if applicable)
     - Result Selector: CSS selector for the generated summary

*note: The selectors are subject to change as the UI of the providers change. You can find the correct selectors by inspecting the elements in the page.*

These options can be accessed and modified through the extension's options page, which can be reached by right-clicking the extension icon and selecting "Options" or through the Chrome extensions management page.

## Technologies Used

- Python 3.10+
  - Speech recognition libraries for text extraction
  - Natural Language Processing (NLP) libraries for summarization
- JavaScript (ES6+) for Chrome extension
- AI Models:
  - Meta-Llama-3.1-8B-Instruct for local summary generation
  - OpenAI Whisper for Youtube video to text transcription
- Chrome Extension APIs

## Development

- Backend: The Python backend handles video processing, text extraction, and summary generation.
- Frontend: The Chrome extension provides the user interface and communicates with the backend.

To contribute to the development:
1. Fork the repository
2. Create a new branch for your feature
3. Implement your changes
4. Submit a pull request with a detailed description of your modifications

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgements
- https://github.com/jdepoix/youtube-transcript-api for the Youtube transcript API
- https://github.com/openai/whisper for the Whisper models
- https://github.com/ggerganov/llama.cpp for the local inference capabilites
- Contributors and open-source projects that made this possible

## Roadmap

- Make backend models and setup configurable via parameters
- Add customizable summary lengths and styles
- Integrate with more video platforms/sources

## Contact

For questions, suggestions, or collaborations, please open an issue on this repository or contact the maintainers directly.
