# OpenAiNativeHandler

The `OpenAiNativeHandler` component is responsible for handling communication with the OpenAI API, providing an interface for sending requests and receiving responses. It implements the `ApiHandler` interface and provides the following key functionalities:

1. **API Request Handling**
   - Sends requests to the OpenAI API for text generation or other tasks.
   - Supports streaming responses from the API (except for specific models like o1, o1-preview, and o1-mini).

2. **Model Information**
   - Provides information about the configured OpenAI model, including its ID and default settings.

The `OpenAiNativeHandler` class interacts with the OpenAI library to communicate with the OpenAI API.

## Key Methods

### `createMessage(systemPrompt: string, messages: Anthropic.Messages.MessageParam[])`
Sends a request to the OpenAI API for text generation, using the provided system prompt and conversation history.

### `getModel()`
Returns an object containing the configured OpenAI model ID and its default settings (e.g., max tokens, support for computer use).

## Workflows

1. **API Request Handling**
   - The `createMessage` method is called with the system prompt and conversation history.
   - The `OpenAiNativeHandler` converts the input messages to the OpenAI format.
   - For models like o1, o1-preview, and o1-mini, a non-streaming request is sent using the `chat.completions.create` method, and the response is yielded directly.
   - For other models, a streaming request is sent to the OpenAI API using the `chat.completions.create` method with the `stream` option.
   - The API response is streamed back, and the `OpenAiNativeHandler` yields the generated text and usage information as it becomes available.

2. **Model Information Retrieval**
   - The `getModel` method is called to retrieve information about the configured OpenAI model.
   - The `OpenAiNativeHandler` checks if the configured model ID is valid and returns an object containing the model ID and its default settings.

For more detailed information on the implementation and interactions with other components, please refer to the respective source code files and documentation comments.
