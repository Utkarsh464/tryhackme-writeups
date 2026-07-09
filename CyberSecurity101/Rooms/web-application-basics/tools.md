# Web Application Basics - Tools

## Browser Developer Tools
Modern web browsers include powerful developer tools that are essential for web security testing. Access them by pressing F12 or right-clicking and selecting Inspect. The Network tab shows every HTTP request made by the page, including timing, headers, and response bodies. You can filter by request type, search within requests, and replay requests. The Console tab displays JavaScript errors and allows execution of arbitrary code. The Sources/Debugger tab enables step-through debugging of JavaScript. The Application tab shows cookies, local storage, session storage, and cached data. These tools are invaluable for understanding how a web application communicates with its server and for identifying potential vulnerabilities.

## curl
curl is a command-line tool for transferring data using various protocols, including HTTP and HTTPS. It is widely used for testing web applications from the terminal because it gives fine-grained control over every aspect of an HTTP request. With curl, you can set custom headers, send different HTTP methods, include cookies, follow redirects, upload files, and inspect response headers. curl is available on Linux, macOS, and Windows, making it a universal tool for web testing. Common use cases include testing API endpoints, verifying authentication mechanisms, and automating web requests in scripts.

## netcat (nc)
Netcat is a networking utility for reading from and writing to network connections using TCP or UDP. While not a dedicated HTTP tool, it can be used to craft raw HTTP requests by manually typing the request line, headers, and body. This is useful for understanding the exact format of HTTP messages and for testing servers that may not handle malformed requests correctly. Netcat can also be used to set up simple listeners for receiving HTTP requests during testing.

## Wget
wget is a free utility for non-interactive download of files from the web. It supports HTTP, HTTPS, and FTP protocols and is useful for recursively downloading websites, resuming interrupted downloads, and mirroring web content. While less flexible than curl for testing, wget excels at bulk downloads and website mirroring.

## Postman (Alternative)
Postman is a graphical API client that simplifies testing HTTP APIs. It provides a user-friendly interface for constructing requests, organizing them into collections, and viewing responses. Postman supports environment variables, authentication helpers, and automated testing scripts. While not covered directly in this room, it is a popular alternative to curl for developers and testers who prefer a GUI.
