# AnthropicHandler

The `AnthropicHandler` component is responsible for handling communication with the Anthropic API, providing an interface for sending requests and receiving responses. It implements the `ApiHandler` interface and provides the following key functionalities:

1. **API Request Handling**
   - Sends requests to the Anthropic API for text generation or other tasks.
   - Supports streaming responses from the API.
   - Handles prompt caching for specific Anthropic models.

2. **Model Information**
   - Provides information about the configured Anthropic model, including its ID and default settings.

The `AnthropicHandler` class interacts with the Anthropic SDK to communicate with the Anthropic API.

## Key Methods

### `createMessage(systemPrompt: string, messages: Anthropic.Messages.MessageParam[])`
Sends a request to the Anthropic API for text generation, using the provided system prompt and conversation history.

### `getModel()`
Returns an object containing the configured Anthropic model ID and its default settings (e.g., max tokens, support for computer use).

## Workflows

1. **API Request Handling**
   - The `createMessage` method is called with the system prompt and conversation history.
   - The `AnthropicHandler` determines the appropriate API endpoint based on the configured model ID.
   - For models supporting prompt caching, the handler sets cache control headers and marks specific messages as ephemeral.
   - A request is sent to the Anthropic API using the appropriate endpoint (e.g., `messages.create` or `beta.promptCaching.messages.create`).
   - The API response is streamed back, and the `AnthropicHandler` yields the generated text and usage information as it becomes available.

2. **Model Information Retrieval**
   - The `getModel` method is called to retrieve information about the configured Anthropic model.
   - The `AnthropicHandler` checks if the configured model ID is valid and returns an object containing the model ID and its default settings.

For more detailed information on the implementation and interactions with other components, please refer to the respective source code files and documentation comments.
