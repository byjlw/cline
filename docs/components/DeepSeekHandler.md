# DeepSeekHandler

The `DeepSeekHandler` component is responsible for handling communication with the DeepSeek API, providing an interface for sending requests and receiving responses. It implements the `ApiHandler` interface and provides the following key functionalities:

1. **API Request Handling**
   - Sends requests to the DeepSeek API for text generation or other tasks.
   - Supports streaming responses from the API.
   - Handles context caching and usage reporting for input tokens, output tokens, cache reads, and cache writes.

2. **Model Information**
   - Provides information about the configured DeepSeek model, including its ID and default settings.

The `DeepSeekHandler` class interacts with the OpenAI library to communicate with the DeepSeek API, as DeepSeek uses a compatible API interface.

## Key Methods

### `createMessage(systemPrompt: string, messages: Anthropic.Messages.MessageParam[])`
Sends a request to the DeepSeek API for text generation, using the provided system prompt and conversation history.

### `getModel()`
Returns an object containing the configured DeepSeek model ID and its default settings (e.g., max tokens, support for computer use).

## Workflows

1. **API Request Handling**
   - The `createMessage` method is called with the system prompt and conversation history.
   - The `DeepSeekHandler` converts the input messages to the OpenAI format.
   - A request is sent to the DeepSeek API using the `chat.completions.create` method.
   - The API response is streamed back, and the `DeepSeekHandler` yields the generated text and usage information as it becomes available.
   - The `DeepSeekHandler` handles context caching and reports usage for input tokens, output tokens, cache reads, and cache writes.

2. **Model Information Retrieval**
   - The `getModel` method is called to retrieve information about the configured DeepSeek model.
   - The `DeepSeekHandler` checks if the configured model ID is valid and returns an object containing the model ID and its default settings.

For more detailed information on the implementation and interactions with other components, please refer to the respective source code files and documentation comments.
