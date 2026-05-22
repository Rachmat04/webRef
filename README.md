# webRef

A tool designed to generate templated references for use on Wikipedia, simplifying the process of citing sources within articles. This gadget streamlines the creation of common reference formats, enhancing efficiency for Wikipedia editors.

## 🌟 Key Features & Benefits

*   **Templated References:** Automatically generates references in standard Wikipedia citation templates, ensuring consistency and correctness.
*   **Wikipedia Integration:** Specifically built to function within the Wikipedia environment, likely as a user script or gadget.
*   **Efficiency:** Reduces the manual effort involved in formatting citations, allowing editors to focus more on content.
*   **Client-Side:** Runs directly in your browser, providing immediate reference generation without server-side interaction.

## 🚀 Installation & Setup Instructions

This tool is designed as a client-side JavaScript gadget for Wikipedia. To install `webRef`, you typically add it to your personal JavaScript file on Wikipedia (e.g., `common.js` or `vector.js`).

**Prerequisites:**

*   An active Wikipedia account.
*   Familiarity with editing your personal JavaScript pages on Wikipedia.

**Installation Steps:**

1.  **Navigate to your personal JavaScript page on Wikipedia:**
    *   For most users, this is `Special:MyPage/common.js`. If you use a specific skin like Vector, you might also have `Special:MyPage/vector.js`.

2.  **Add the `webRef` script:**
    Copy and paste the following lines into your `common.js` (or equivalent) page. This will load both the main `webRef` script and its setup/configuration script.

    ```javascript
    // Load webRef main script
    mw.loader.load('//en.wikipedia.org/w/index.php?title=User:Rachmat04/webRef.js&action=raw&ctype=text/javascript', 'text/javascript');

    // Load webRefSetup script (essential for configuration and UI)
    // Note: The original webRefSetup is located at en.wikipedia.org/wiki/User:V111P/js/webRefSetup.js
    // You might need to adjust this URL if you have a local copy or a different setup script.
    mw.loader.load('//en.wikipedia.org/w/index.php?title=User:V111P/js/webRefSetup.js&action=raw&ctype=text/javascript', 'text/javascript');
    ```

    *   **Important Note:** The provided `webRef.js` file relies on `webRefSetup.js` from `User:V111P` on English Wikipedia. Ensure this URL is accessible and the script is compatible with your local Wikipedia project. If you plan to host your own `webRefSetup.js`, update the second `mw.loader.load` line accordingly.

3.  **Save your JavaScript page.**

4.  **Bypass your browser's cache** to ensure the new script loads.
    *   **Firefox / Chrome:** Ctrl-Shift-R (Windows, Linux) or Cmd-Shift-R (macOS)
    *   **Internet Explorer:** Ctrl-F5
    *   **Safari:** Cmd-R

After these steps, `webRef` should be active and available for use on Wikipedia pages.

## 💻 Usage Examples

`webRef` works by providing a function, `window.webRef.getRef`, which is likely called by the `webRefSetup.js` script to present a user interface or generate references based on user input.

While `webRef.js` itself doesn't expose a direct user interface, it provides the core logic. The typical usage flow, mediated by `webRefSetup.js`, might involve:

1.  **Clicking a button or gadget link** in the Wikipedia editing toolbar or sidebar.
2.  **Filling out a form** with details like the source URL, title, author, publication date, etc.
3.  **Generating the templated reference** which is then automatically inserted into the edit box.

For advanced users or developers, you might interact with the core function directly (though this is typically handled by `webRefSetup`):

```javascript
// Example of how webRef.getRef might be called internally
// This is illustrative and depends on how webRefSetup.js utilizes it.
(function() {
    'use strict';
    // Assume input parameters for reference generation
    var refParameters = {
        url: 'https://example.com/article',
        title: 'An Example Article',
        author: 'John Doe',
        publisher: 'Example Publishing',
        date: '2023-10-27'
        // ... other parameters
    };

    if (window.webRef && typeof window.webRef.getRef === 'function') {
        var generatedReference = window.webRef.getRef(refParameters);
        console.log('Generated Reference:', generatedReference);
        // This `generatedReference` would then be inserted into the Wikipedia edit summary.
    } else {
        console.warn('webRef.getRef is not available.');
    }
})();
```

## ⚙️ Configuration Options

Configuration for `webRef` is primarily handled by the `webRefSetup.js` script. This external script is responsible for:

*   Defining the user interface elements (buttons, forms).
*   Setting default values or options for reference generation.
*   Specifying which templates to use (e.g., `{{cite web}}`, `{{cite news}}`).
*   Potentially customising output formats.

Users who wish to modify the behavior or appearance of `webRef` should look into the source code of `webRefSetup.js` or create their own customized version. The `window.webRef` object is used for communication, so it might accept initial configuration via its properties.

## 🤝 Contributing Guidelines

We welcome contributions to `webRef`! If you have suggestions for improvements, bug fixes, or new features, please follow these guidelines:

1.  **Fork the repository:** Start by forking the `webRef` repository to your GitHub account.
2.  **Create a new branch:** For each new feature or bug fix, create a new branch from `main` (e.g., `feature/add-new-template`, `fix/bug-in-parsing`).
3.  **Make your changes:** Implement your changes in the new branch.
4.  **Test your changes:** Ensure your modifications do not introduce new issues and work as expected within the Wikipedia environment.
5.  **Submit a Pull Request (PR):**
    *   Provide a clear and concise description of your changes.
    *   Reference any relevant issues.
    *   Ensure your code adheres to JavaScript best practices and is well-commented.

For reporting bugs or suggesting features, please open an issue in the GitHub repository.

## 📄 License

The license for this project has **not been specified**.
Until a license is explicitly stated, all rights are reserved by the copyright holder, Rachmat04.

## 🙏 Acknowledgments

This project is inspired by and directly uses code from:

*   **User:V111P/js/WebRef** on English Wikipedia, which serves as the original source for the core functionality and the associated `webRefSetup.js` script.
