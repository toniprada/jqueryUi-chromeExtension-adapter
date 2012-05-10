# JQuery UI on Chrome extensions

If you have tried to use JQuery UI on a Chrome extension, you'll have notice that image links aren't handled properly.
The reason for this behaviour is due to the content scripts being executed on the webpage context, so Chrome takes the webpage URL as root for the paths and not the extension folder (as we want to).

The way to fix that is simple: rewrite the paths to link to the extension files, and that is what this CSS file does.

## How to use it

Just put it on your CSS folder and link it on your manifest file **after the original JQueryUi CSS file**. Remember, we want to rewrite some of it CSS rules. Example:

```json
{
  "name": "Example",
  "version": "1.0.0",
  ...
  "content_scripts": [
    {
      "matches": ["<all_urls>"],
      "css": [css/smoothness/jquery-ui-1.8.20.css", "css/smoothness/jquery-ui-1.8.20-chrome-extension.css"],
      ...
    }
  ],
  ...
}
```

## License

```
Copyright (c) 2012 Antonio Prada <toniprada@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```




