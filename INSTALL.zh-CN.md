# 安装 JEV News

从[发布页面](https://github.com/sheng0325/jev-news/releases/latest)下载
`jev-news-v1.0.0.zip`，解压后，在终端进入 `jev-news-v1.0.0` 文件夹。

需要 macOS 或 Linux，以及 Python 3.12。程序使用 POSIX 文件锁，暂不支持
Windows。下载包包含采用 MIT 许可的 Python 源代码。

```sh
python3.12 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
.venv/bin/python news_server.py
```

打开 <http://127.0.0.1:8000>。保持终端运行，按 Ctrl+C 停止。
如果端口被占用，运行 `news_server.py --port 8001`，再打开 8001 端口。
程序只监听本机，不是已部署的公共网站。

## 配置分析

```sh
cp -n jev_secrets.example.json jev_secrets.json
cp -n llm_secrets.example.json llm_secrets.json
chmod 600 jev_secrets.json llm_secrets.json
```

在 `TYPESAFE_API_KEY` 填入自己的 JEV / TypeSafe 密钥，在 `DEEPSEEK_API_KEY`
填入自己的 DeepSeek 密钥，保留 JSON 的引号。模板中的密钥为空，复制命令不会
覆盖已有文件。真实配置文件请留在本机。

点击 **Collect RSS** 保存新闻，再通过 **Analyze date batches (paid)**
分析马来西亚时间过去日期的新闻。分析可能产生 API 费用；启动程序不会自动
采集或分析。查看已有新闻不需要密钥。

新闻和分析结果保存在本机 `data/` 文件夹。启动分析时，相关报道文本会发送至
JEV / TypeSafe 和 DeepSeek。模型输出可能出错或带有偏见，请通过原文链接核查。

## 验证下载

发布附件中的 `SHA256SUMS.txt` 可用于核对 ZIP：

```sh
shasum -a 256 -c SHA256SUMS.txt
```

在解压后的项目文件夹运行离线检查：

```sh
.venv/bin/python -m unittest -v
```

联网 API 测试默认跳过。保持 `NEWS_ANALYSIS_LIVE_TESTS` 未设置，避免启用付费测试。
