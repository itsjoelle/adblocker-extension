# Ad Blocker Extension

A simple Chrome extension designed to block ads on websites by preventing requests from common ad networks such as Google Ads, DoubleClick, and Google Syndication. It uses Chrome's declarativeNetRequest API to efficiently block these requests by defining rules in a JSON format.

## Installation

**Download** or **clone** the repository to run locally:

```zsh
git clone https://github.com/itsjoelle/adblocker-extension.git
```

**Open Chrome Extensions**
`chrome://extensions/`

Enable Developer Mode by toggling the switch in the top right.

Click "Load unpacked" and select the extension's directory.

The extension will now be installed and active! 🎉

## Features

- **Blocks Google Ad Networks**  
  Blocks requests to popular Google ad-serving domains such as doubleclick.net, googleadservices.com, and googlesyndication.com.

- **Declarative Ad Blocking**  
  Utilizes Chrome's `declarativeNetRequest` API to block ads efficiently, without requiring background JavaScript execution.

- **Simple and Fast**  
  Blocks ads as soon as a page loads, ensuring an ad-free browsing experience.

## How It Works

The extension uses Chrome's **`declarativeNetRequest`** API to block specific URLs associated with ad networks. When the browser encounters a request matching a blocked pattern, the request is prevented from loading.

### Currently Blocked Ad Networks:

- **Google Ads**: googleadservices.com, googlesyndication.com, etc.
- **DoubleClick**: doubleclick.net

### How to Add More Blocked URLs

To block additional ad networks:

1. Open the `ruleset.json` file.
2. Add new rules with the pattern for the ad network you want to block (e.g., `*://*.exampleadnetwork.com/*`).
3. Reload the extension in Chrome (go to `chrome://extensions/`).

#### Example Rule

```json
{
  "id": 4,
  "priority": 1,
  "action": {
    "type": "block"
  },
  "condition": {
    "urlFilter": "*://*.exampleadnetwork.com/*"
  }
}
```

### Folder Structure

- **manifest.json**: The metadata for the Chrome extension (name, permissions, rules).
- **ruleset.json**: A JSON file where ad-blocking rules are defined.

If you're using an older approach (like manifest V2), you may include a `background.js` file for dynamic blocking.

## Contributing

Feel free to fork the repository and **submit pull requests** if you want to:

Add more ad networks to the block list.

Add new features (like a toggle to enable/disable ad blocking).

Improve performance or extend the functionality.

## License

This project is licensed under the [MIT License](https://choosealicense.com/licenses/mit/).
