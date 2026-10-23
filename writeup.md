
## The core problem:
The CORS policy of mcp-chrome can be bypassed. It checks with `pattern instanceof RegExp ? pattern.test(origin) : origin.startsWith(pattern)`, and constant is defined by `CORS_ORIGIN: [/^chrome-extension:\/\//, /^moz-extension:\/\//, 'http://127.0.0.1'] as const`.

In this case, anything starting with `http://127.0.0.1` will bypass the filter. For example, you can register a A-DNS record pointing to `http://127.0.0.1.test.malicious.example.com`, and the CORS validation can be bypassed.

## How I discovered it in the beginning:

I'm not trying to actually find a BUG ... ehhh ...

It all starts with one question: What is the CORS policy of this extension?

In this case, I asked Claude: "Where can I find the CORS handling code?"

And after I found the code, I just saw that `origin.startsWith(pattern)`, so I go checked `CORS_ORIGIN` and I felt I won a lottery.

## How it could become RCE:

Then, I tried to connect to the bridge, while it didn't work. There are two reasons:
* Chrome's depense-in-depth: `Local Network Access Checks`
  * Goto `chrome://flags` and disable `Local Network Access Checks`
* Another BUG in the extension
