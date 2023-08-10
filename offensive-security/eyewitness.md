---
description: >-
  With EyeWitness, you can easily take snapshots of web pages, gather server
  header information, and detect default login credentials if they are present.
  It's a great documenting and reporting tool.
---

# Eyewitness

### Commands Table

#### General Commands

| Usage                                   | Command      |
| --------------------------------------- | ------------ |
| Read URLs from file                     | -f           |
| Single URL                              | --single     |
| HTTP Screenshot using Selenium          | --web        |
| Timeout to wait between each screenshot | --timeout    |
| User agent                              | --user-agent |
| Report directory                        | -d           |

#### Example

```
eyewitness --single https://example.com -d ~/target/
```

```
eyewitness -f urls.txt --timeout 30 -d ~/target/
```
