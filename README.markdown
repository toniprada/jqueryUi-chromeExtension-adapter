# JQuery UI on Chrome extensions

If you have tried to use JQuery UI on a Chrome extension, you'll have notice that image links aren't handled properly.
The reason for this behaviour is due to the content scripts being executed on the webpage context, so Chrome takes the webpage URL as root for the paths and not the extension folder (as we want to).

The way to fix it is to overload some css rules than contains images with the base64 data of this images.

This file has been developed to work with JQueryUI 1.8.20 but should work with newer versions too.

## How to use it

Just put it on your CSS folder and link it on your manifest file **after the original JQueryUI CSS file**. Remember, we want to rewrite some of its CSS rules. Example:

```json
{
  "name": "Example",
  "version": "1.0.0",
  "manifest_version": 2,
  ...
  "content_scripts": [
    {
      "matches": ["<all_urls>"],
      "css": ["css/smoothness/jquery-ui-1.8.20.css", "css/smoothness/jqueryui-1.8.20-chrome-extension.css"],
      ...
    }
  ],
  ...
}
```

## License

GPLv3(http://gplv3.fsf.org/)

