# Submitting Translations

If you have questions following these steps, please open an issue: https://github.com/TurboWarp/translations/issues

## Requirements

 * You must be fluent in both English and another language. Taking one year of a language class in high school does not make you fluent.
 * Machine translations (Google Translate, DeepL, etc.) are not allowed.

## Writing translations

First, make a fork of this repository. You can complete every step here directly from the GitHub website. You don't need to clone the repository if you don't want to.

Then, go into the `languages` folder and find the file for your language. See [languages.md](languages.md) to figure out which file to open.

Translations are stored in JSON files that contain entries like this:

```json
"tw.menuBar.code": {
    "defaultMessage": "Source Code",
    "description": "Text for source code link in the Help menu",
    "message": null
},
```

`tw.menuBar.code` is the message ID. This is used internally. Do not change this.

`defaultMessage` is the English translation of the message for you to reference. Do not change this.

`description` describes more about the message, where it's displayed, the context, etc. Do not change this.

`message` is the translated message. This is what you should change. `null` means that this message has not been translated into this language and the default message will be used instead (except for languages like Español Latinoamericano where it will first check Español before defaulting to English). Write the translated message here as a JSON string. For example, this is how "Turbo Mode" would be translated into Spanish:

```json
"gui.turboMode.active": {
    "defaultMessage": "Turbo Mode",
    "description": "Label indicating turbo mode is active",
    "message": "Modo Turbo"
},
```

Remember, this file is JSON. That means that strings need to have "quotes around them" and that you may need to escape certain special characters (although you probably won't have to do any escaping)

Commit your changes and submit a pull request to this repository.

## Special syntax

Sometimes messages can contain variables, for example:

```json
"tw.framerateIndicator": {
    "defaultMessage": "{framerate} FPS",
    "description": "Label indicating project framerate",
    "message": null
},
```

`{framerate}` is a variable that will be replaced with something else. In this case, `{framerate}` will become a number like `60`. Make sure your translated message contains the same variable. Do not translate the name of the variable.

It's also possible that the variable is replaced with another translation, for example:

```json
"tw.footer.host": {
    "defaultMessage": "Hosting for TurboWarp is provided by {fosshost}.",
    "description": "Host credit",
    "message": null
},
"tw.footer.host.fosshost": {
    "defaultMessage": "fosshost.org",
    "description": "Link to fosshost.org",
    "message": null
},
```

When this happens, the variable's translation is usually directly below the primary message. In this case, `{fosshost}` will be replaced with the translation of `tw.footer.host.fosshost`. This generally only happens when a translation contains a link, for example.
