# VsCodeLmHandler

The `VsCodeLmHandler` component is responsible for handling communication with the Visual Studio Code Language Model API, providing an interface for sending requests and receiving responses. It implements the `ApiHandler` and `SingleCompletionHandler` interfaces and provides the following key functionalities:

1. **API Request Handling**
   - Sends requests to the Visual Studio Code Language Model API for text generation or other tasks.
   - Supports streaming responses from the API.
   - Handles tool calls and tool results from the API.

2. **Model Information**
   - Provides information about the configured Visual Studio Code Language Model, including its ID and default settings.

3. **Prompt Completion**
   - Provides a method to complete a given prompt using the Visual Studio Code Language Model API.

The `VsCodeLmHandler` class interacts with the Visual Studio Code Language Model API to communicate with the configured language model.

## Key Methods

### `createMessage(systemPrompt: string, messages: Anthropic.Messages.MessageParam[])`
Sends a request to the Visual Studio Code Language Model API for text generation, using the provided system prompt and conversation history.

### `getModel()`
Returns an object containing the configured Visual Studio Code Language Model ID and its default settings (e.g., max tokens, support for computer use).

### `completePrompt(prompt: string)`
Completes the given prompt using the Visual Studio Code Language Model API and returns the generated text.

## Workflows

1. **API Request Handling**
   - The `createMessage` method is called with the system prompt and conversation history.
   - The `VsCodeLmHandler` converts the input messages to the Visual Studio Code Language Model format.
   - A request is sent to the Visual Studio Code Language Model API using the `sendRequest` method.
   - The API response is streamed back, and the `VsCodeLmHandler` yields the generated text, tool calls, and usage information as it becomes available.
   - The `VsCodeLmHandler` handles tool calls and tool results from the API.

2. **Model Information Retrieval**
   - The `getModel` method is called to retrieve information about the configured Visual Studio Code Language Model.
   - The `VsCodeLmHandler` constructs the model ID and default settings based on the available information from the API.

3. **Prompt Completion**
   - The `completePrompt` method is called with the prompt to be completed.
   - The `VsCodeLmHandler` sends a request to the Visual Studio Code Language Model API using the `sendRequest` method with the provided prompt.
   - The generated text is accumulated and returned as the completion result.

For more detailed information on the implementation and interactions with other components, please refer to the respective source code files and documentation comments.
