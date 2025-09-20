We’ll build a server that exposes two tools: get_alerts and get_forecast. Then we’ll connect the server to an MCP host (in this case, Claude for Desktop):
Core MCP Concepts
MCP servers can provide three main types of capabilities:
Resources: File-like data that can be read by clients (like API responses or file contents)
Tools: Functions that can be called by the LLM (with user approval)
Prompts: Pre-written templates that help users accomplish specific tasks

Prerequisite knowledge
This quickstart assumes you have familiarity with:
Python
LLMs like Claude
​
Logging in MCP Servers
When implementing MCP servers, be careful about how you handle logging:
For STDIO-based servers: Never write to standard output (stdout). This includes:
print() statements in Python
console.log() in JavaScript
fmt.Println() in Go
Similar stdout functions in other languages
Writing to stdout will corrupt the JSON-RPC messages and break your server.
For HTTP-based servers: Standard output logging is fine since it doesn’t interfere with HTTP responses.
​
Best Practices
Use a logging library that writes to stderr or files.
