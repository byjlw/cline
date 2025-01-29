# OpenRouterHandler

The `OpenRouterHandler` component is responsible for handling communication with the OpenRouter API, providing an interface for sending requests and receiving responses. It implements the `ApiHandler` interface and provides the following key functionalities:

1. **API Request Handling**
   - Sends requests to the OpenRouter API for text generation or other tasks.
   - Supports streaming responses from the API.
   - Handles prompt caching for specific Anthropic models.
   - Retrieves generation details and usage information after the initial streaming response.

2. **Model Information**
   - Provides information about the configured model, including its ID and default settings.

The `OpenRouterHandler` class interacts with the OpenAI library to communicate with the OpenRouter API, as OpenRouter uses a compatible API interface.

## Key Methods

### `createMessage(systemPrompt: string, messages: Anthropic.Messages.MessageParam[])`
Sends a request to the OpenRouter API for text generation, using the provided system prompt and conversation history.

### `getModel()`
Returns an object containing the configured model ID and its default settings (e.g., max tokens, support for computer use).

## Workflows

1. **API Request Handling**
   - The `createMessage` method is called with the system prompt and conversation history.
   - The `OpenRouterHandler` converts the input messages to the OpenAI format.
   - For specific Anthropic models, the handler sets cache control headers and marks messages as ephemeral for prompt caching.
   - A streaming request is sent to the OpenRouter API using the `chat.completions.create` method.
   - The API response is streamed back, and the `OpenRouterHandler` yields the generated text as it becomes available.
   - After the initial streaming response, the `OpenRouterHandler` retrieves generation details and usage information from the OpenRouter API.

2. **Model Information Retrieval**
   - The `getModel` method is called to retrieve information about the configured model.
   - The `OpenRouterHandler` checks if a custom model ID and settings are provided, and returns an object containing the model ID and its default settings.

For more detailed information on the implementation and interactions with other components, please refer to the respective source code files and documentation comments.
