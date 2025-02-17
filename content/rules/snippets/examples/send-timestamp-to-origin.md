---
type: example
summary: Convert timestamp to hexadecimal format and send it as a custom header to the origin.
goal:
  - Manage headers
operation:
  - Request modification
product:
  - Snippets
pcx_content_type: example
title: Send timestamp to origin as a custom header
layout: example
---

```js
export default {
    async fetch(request) {
        // Get the current timestamp
        const timestamp = Date.now();

        // Convert the timestamp to hexadecimal format
        const hexTimestamp = timestamp.toString(16);

        // Clone the request and add the custom header
        const modifiedRequest = new Request(request, {
            headers: new Headers(request.headers)
        });
        modifiedRequest.headers.set("X-Hex-Timestamp", hexTimestamp);

        // Log the custom header for debugging
        console.log(`X-Hex-Timestamp: ${hexTimestamp}`);

        // Pass the modified request to the origin
        const response = await fetch(modifiedRequest);

        return response;
    },
};
```