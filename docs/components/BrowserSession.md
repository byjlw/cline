# BrowserSession

The `BrowserSession` component is responsible for managing a browser instance and providing browser automation capabilities within the Visual Studio Code environment. It provides the following key functionalities:

1. **Browser Launching**
   - Launches a new browser instance with specified configurations (e.g., user agent, viewport, headless mode).
   - Ensures the availability of the required Chromium executable.

2. **Browser Navigation**
   - Navigates the browser to a specified URL.
   - Waits for the page to fully load and stabilize.

3. **Browser Actions**
   - Performs actions on the browser, such as clicking, typing, scrolling, and capturing screenshots.
   - Handles network activity and page navigation resulting from actions.

4. **Browser Cleanup**
   - Closes the browser instance and cleans up resources.

The `BrowserSession` class interacts with the Puppeteer library to control the browser instance and perform various automation tasks.

## Key Methods

### `launchBrowser()`
Launches a new browser instance with the specified configurations.

### `closeBrowser()`
Closes the current browser instance and cleans up resources.

### `navigateToUrl(url: string)`
Navigates the browser to the specified URL and waits for the page to fully load.

### `click(coordinate: string)`
Performs a click action on the specified coordinates within the browser window.

### `type(text: string)`
Types the specified text into the focused element in the browser.

### `scrollDown()` and `scrollUp()`
Scrolls the browser window down or up, respectively.

### `doAction(action: (page: Page) => Promise<void>)`
Executes a provided action on the browser page, capturing console logs, errors, and screenshots.

## Workflows

1. **Browser Launching**
   - The `launchBrowser` method is called to launch a new browser instance.
   - The required Chromium executable is ensured to be available.
   - The browser is launched with the specified configurations (e.g., user agent, viewport, headless mode).

2. **Browser Navigation**
   - The `navigateToUrl` method is called with the desired URL.
   - The browser navigates to the specified URL and waits for the page to fully load and stabilize.
   - A screenshot and console logs are captured and returned as part of the `BrowserActionResult`.

3. **Browser Actions**
   - Methods like `click`, `type`, `scrollDown`, and `scrollUp` are called with the desired action parameters.
   - The `doAction` method is used to execute the action on the browser page.
   - Console logs, errors, and screenshots are captured during the action execution.
   - The `BrowserActionResult` is returned, containing the action result, console logs, current URL, and mouse position.

4. **Browser Cleanup**
   - The `closeBrowser` method is called to close the current browser instance.
   - Resources associated with the browser instance are cleaned up.

For more detailed information on the implementation and interactions with other components, please refer to the respective source code files and documentation comments.
