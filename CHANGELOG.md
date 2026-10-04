# v1.0.0 — First public release

JEV News helps readers separate reported facts, attributed claims and political
packaging, while keeping the original article links available for checking.

- Collect news from four Malaysian RSS sources.
- Classify political relevance and assess reading value with JEV.
- Extract core information and explain packaging language with DeepSeek.
- Review saved news in a local browser interface, with source and date filters.
- Reuse completed analysis checkpoints and retain uncertain political reporting.

Download `jev-news-v1.0.0.zip` and follow [Installation](INSTALL.md)
or [中文安装说明](INSTALL.zh-CN.md). Python 3.12 on macOS or Linux is required;
Windows is not supported yet. This release contains MIT-licensed Python source.
Analysis requires your own API keys and can incur charges. Model output is not
independent fact verification and can contain errors or bias.

The package excludes credentials, collected articles, development logs and Git
history. API-key templates are blank. The server listens on localhost and does
not expose configuration files or the project directory as downloads.

Validation: 136 offline regression tests completed successfully; 4 optional
paid API tests were skipped. The extracted package passed the same offline suite in a fresh environment,
installation, local HTTP startup and private-file isolation checks.
A dependency audit on 4 October 2026 found no known vulnerabilities in the
seven resolved runtime packages.
