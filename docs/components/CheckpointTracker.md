# CheckpointTracker

The `CheckpointTracker` component is responsible for managing checkpoints and tracking workspace file changes within the Visual Studio Code environment. It provides the following key functionalities:

1. **Checkpoint Creation**
   - Creates a shadow Git repository to track workspace file changes.
   - Initializes the shadow Git repository with appropriate configurations and exclusions.
   - Commits changes to the shadow Git repository, creating checkpoints.

2. **Workspace Restoration**
   - Resets the workspace to a specific checkpoint by resetting the shadow Git repository to the corresponding commit.
   - Handles untracked files, staged changes, and merge conflicts during restoration.

3. **Diff Generation**
   - Generates diffs between checkpoints or between a checkpoint and the current workspace state.
   - Provides the before and after content of changed files.

4. **Workspace Validation**
   - Ensures that checkpoints are only used within the original workspace directory.
   - Prevents the use of checkpoints in certain system directories (e.g., Desktop, Documents, Downloads).

The `CheckpointTracker` class interacts with the simple-git library to manage the shadow Git repository and perform checkpoint-related operations.

## Key Methods

### `create(taskId: string, provider?: ClineProvider)`
Creates a new `CheckpointTracker` instance for the specified task ID and provider.

### `initShadowGit()`
Initializes the shadow Git repository, configuring it with the appropriate settings and exclusions.

### `commit()`
Commits the current workspace changes to the shadow Git repository, creating a new checkpoint.

### `resetHead(commitHash: string)`
Resets the workspace to the specified commit hash, effectively restoring the workspace to the corresponding checkpoint.

### `getDiffSet(lhsHash?: string, rhsHash?: string)`
Generates a diff set between two commit hashes or between a commit hash and the current workspace state.

### `getShadowGitConfigWorkTree()`
Retrieves the configured working tree directory for the shadow Git repository.

## Workflows

1. **Checkpoint Creation**
   - The `create` method is called with the task ID and provider to create a new `CheckpointTracker` instance.
   - The `initShadowGit` method is called to initialize the shadow Git repository.
   - The `commit` method is called to create a new checkpoint, committing the current workspace changes.

2. **Workspace Restoration**
   - The `resetHead` method is called with the desired commit hash.
   - The `CheckpointTracker` resets the workspace to the specified commit, handling untracked files, staged changes, and merge conflicts.

3. **Diff Generation**
   - The `getDiffSet` method is called with the desired commit hashes or the current workspace state.
   - The `CheckpointTracker` generates a diff set, including the before and after content of changed files.

4. **Workspace Validation**
   - During the creation of a new `CheckpointTracker` instance, the `getWorkingDirectory` method is called to validate the workspace directory.
   - If the workspace directory is not valid (e.g., Desktop, Documents, Downloads), an error is thrown, preventing the use of checkpoints.

For more detailed information on the implementation and interactions with other components, please refer to the respective source code files and documentation comments.
