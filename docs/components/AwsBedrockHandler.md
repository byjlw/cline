# AwsBedrockHandler

The `AwsBedrockHandler` component is responsible for handling communication with the Anthropic Bedrock API hosted on AWS, providing an interface for sending requests and receiving responses. It implements the `ApiHandler` interface and provides the following key functionalities:

1. **API Request Handling**
   - Sends requests to the Anthropic Bedrock API on AWS for text generation or other tasks.
   - Supports streaming responses from the API.
   - Handles cross-region inference if configured.

2. **Model Information**
   - Provides information about the configured Bedrock model, including its ID and default settings.

The `AwsBedrockHandler` class interacts with the Anthropic Bedrock SDK to communicate with the Anthropic Bedrock API on AWS.

## Key Methods

### `createMessage(systemPrompt: string, messages: Anthropic.Messages.MessageParam[])`
Sends a request to the Anthropic Bedrock API on AWS for text generation, using the provided system prompt and conversation history.

### `getModel()`
Returns an object containing the configured Bedrock model ID and its default settings (e.g., max tokens, support for computer use).

## Workflows

1. **API Request Handling**
   - The `createMessage` method is called with the system prompt and conversation history.
   - The `AwsBedrockHandler` determines the appropriate model ID based on the configured settings and cross-region inference support.
   - A request is sent to the Anthropic Bedrock API on AWS using the `messages.create` method.
   - The API response is streamed back, and the `AwsBedrockHandler` yields the generated text and usage information as it becomes available.

2. **Model Information Retrieval**
   - The `getModel` method is called to retrieve information about the configured Bedrock model.
   - The `AwsBedrockHandler` checks if the configured model ID is valid and returns an object containing the model ID and its default settings.

For more detailed information on the implementation and interactions with other components, please refer to the respective source code files and documentation comments.
