# TerminalManager

The `TerminalManager` component is responsible for managing terminal instances, executing commands, and handling terminal output within the Visual Studio Code environment. It provides the following key functionalities:

1. **Terminal Creation and Reuse**
   - Creates new terminal instances when needed.
   - Reuses existing terminals if available, considering their current working directory and busy state.

2. **Command Execution**
   - Executes commands in terminals, returning a `TerminalProcess` object.
   - Supports real-time output handling and background execution.

3. **Output Management**
   - Retrieves unretrieved output from ongoing or completed commands.
   - Handles shell integration events for improved output handling.

4. **Terminal Lifecycle Management**
   - Tracks active terminals and their associated processes.
   - Disposes of terminals and processes when no longer needed.

The `TerminalManager` works in conjunction with the `TerminalProcess` and `TerminalRegistry` classes to provide a comprehensive terminal management solution.

## Key Components

### TerminalProcess
- Extends `EventEmitter` and implements `Promise`.
- Emits 'line' events with output while the promise is pending.
- Allows continuing execution in the background or waiting for completion.
- Handles shell integration events for improved output handling.

### TerminalRegistry
- Manages a pool of terminal instances.
- Provides methods for creating, retrieving, and removing terminals.

## Key Methods

### `runCommand(terminalInfo: TerminalInfo, command: string)`
Executes a command in the specified terminal, returning a `TerminalProcess` object.

### `getOrCreateTerminal(cwd: string)`
Retrieves an available terminal with the specified working directory or creates a new one if none is available.

### `getTerminals(busy: boolean)`
Returns a list of terminals that are either busy or not busy.

### `getUnretrievedOutput(terminalId: number)`
Retrieves the unretrieved output from a specific terminal.

### `isProcessHot(terminalId: number)`
Checks if a process associated with a terminal is still actively running.

### `disposeAll()`
Disposes of all terminals and associated resources.

## Workflows

1. **Command Execution**
   - The `runCommand` method is called with a `TerminalInfo` object and the command to execute.
   - If shell integration is available, the command is executed immediately; otherwise, it waits for shell integration to activate.
   - A `TerminalProcess` object is created and returned, allowing real-time output handling or background execution.

2. **Terminal Management**
   - The `getOrCreateTerminal` method is called with the desired working directory.
   - The `TerminalManager` first attempts to find an available terminal with the specified working directory.
   - If no matching terminal is found, it tries to reuse any available terminal by navigating to the desired directory.
   - If all terminals are busy, a new terminal instance is created.

3. **Output Retrieval**
   - The `getUnretrievedOutput` method is called with a terminal ID.
   - The `TerminalManager` retrieves the unretrieved output from the associated `TerminalProcess`.

4. **Cleanup**
   - The `disposeAll` method is called to clean up resources.
   - All terminals and associated processes are disposed of, and event listeners are removed.

For more detailed information on the implementation and interactions with other components, please refer to the respective source code files and documentation comments.
