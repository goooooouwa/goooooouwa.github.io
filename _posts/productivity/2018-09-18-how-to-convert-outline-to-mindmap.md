---
title: How to convert outline text to mindmap
category: productivity
tags: outline freemind mindmap
published: true
---

## Requirements:
- [text-to-freemind](https://github.com/wbolster/text-to-freemind)
- Python 2.x

## Setup
1. clone text-to-freemind project
2. prepare a tab-indented UTF-8 text file, use file extension `.txt.mm`. (If you're using space for indentation, use your text editor to replace them with tab (`\t` in Regex))

## How to use
```bash
cd text-to-freemind
python2 ./text-to-freemind path/to/input.txt.mm > output.mm
```

now you can use Freemind or other mindmap tool's "Import from Freemind" option to open the output mindmap file.