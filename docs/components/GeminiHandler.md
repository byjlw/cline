# GeminiHandler

The `GeminiHandler` component is responsible for handling communication with the Google Gemini API, providing an interface for sending requests and receiving responses. It implements the `ApiHandler` interface and provides the following key functionalities:

1. **API Request Handling**
   - Sends requests to the Google Gemini API for text generation or other tasks.
   - Supports streaming responses from the API.

2. **Model Information**
   - Provides information about the configured Gemini model, including its ID and default settings.

The `GeminiHandler` class interacts with the Google Generative AI library to communicate with the Google Gemini API.

## Key Methods

### `createMessage(systemPrompt: string, messages: Anthropic.Messages.MessageParam[])`
Sends a request to the Google Gemini API for text generation, using the provided system prompt and conversation history.

### `getModel()`
Returns an object containing the configured Gemini model ID and its default settings (e.g., max tokens, support for computer use).

## Workflows

1. **API Request Handling**
   - The `createMessage` method is called with the system prompt and conversation history.
   - The `GeminiHandler` converts the input messages to the Gemini format.
   - A request is sent to the Google Gemini API using the `generateContentStream` method.
   - The API response is streamed back, and the `GeminiHandler` yields the generated text and usage information as it becomes available.

2. **Model Information Retrieval**
   - The `getModel` method is called to retrieve information about the configured Gemini model.
   - The `GeminiHandler` checks if the configured model ID is valid and returns an object containing the model ID and its default settings.

For more detailed information on the implementation and interactions with other components, please refer to the respective source code files and documentation comments.
