# OpenAiHandler

The `OpenAiHandler` component is responsible for handling communication with the OpenAI API, providing an interface for sending requests and receiving responses. It implements the `ApiHandler` interface and provides the following key functionalities:

1. **API Request Handling**
   - Sends requests to the OpenAI API for text generation or other tasks.
   - Supports both the standard OpenAI API and the Azure OpenAI API.
   - Handles streaming responses from the API.

2. **Model Information**
   - Provides information about the configured OpenAI model, including its ID and default settings.

The `OpenAiHandler` class interacts with the OpenAI Node.js library to communicate with the OpenAI API.

## Key Methods

### `createMessage(systemPrompt: string, messages: Anthropic.Messages.MessageParam[])`
Sends a request to the OpenAI API for text generation, using the provided system prompt and conversation history.

### `getModel()`
Returns an object containing the configured OpenAI model ID and its default settings (e.g., context window size, support for computer use).

## Workflows

1. **API Request Handling**
   - The `createMessage` method is called with the system prompt and conversation history.
   - The `OpenAiHandler` converts the input messages to the OpenAI format.
   - A request is sent to the OpenAI API using the `chat.completions.create` method.
   - The API response is streamed back, and the `OpenAiHandler` yields the generated text and usage information as it becomes available.

2. **Model Information Retrieval**
   - The `getModel` method is called to retrieve information about the configured OpenAI model.
   - The `OpenAiHandler` returns an object containing the model ID and its default settings.

For more detailed information on the implementation and interactions with other components, please refer to the respective source code files and documentation comments.
