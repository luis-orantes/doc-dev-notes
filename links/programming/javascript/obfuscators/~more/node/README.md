
### node-obf

The node-obf library by WeAreFractal is a minimalistic JavaScript code obfuscator for Node.js that transforms a given source string into an unreadable form by mapping its characters and expressions into a convoluted chain of mathematical and string manipulations assigned to a globally defined variable (e.g., $$).
It’s installed via npm install node-obf and used by calling require('node-obf').obfuscate(globalVarName, code), producing obfuscated code that remains runnable through dynamic evaluation.
While its implementation is basic and largely unchanged since its initial release 13 years ago, it serves as a lightweight, easy-to-integrate option for developers seeking simple obfuscation—but for serious, modern-grade protection, more sophisticated and actively maintained tools are likely more effective.

https://github.com/wearefractal/node-obf
