# Install JEV News

Download `jev-news-v0.1.0.zip` from the
[release page](https://github.com/sheng0325/jev-news/releases/latest), then
extract it and open a terminal in the `jev-news-v0.1.0` folder.

Requires Python 3.12 on macOS or Linux. Windows is not supported yet because
the pipeline uses POSIX file locking. The download contains Python source
code under the MIT license.

```sh
python3.12 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
.venv/bin/python news_server.py
```

Open <http://127.0.0.1:8000>. Keep the terminal running; use Ctrl+C to stop.
If the port is occupied, run `news_server.py --port 8001` and open port 8001.
The server listens only on your computer. It is not a hosted public service.

## Configure analysis

```sh
cp -n jev_secrets.example.json jev_secrets.json
cp -n llm_secrets.example.json llm_secrets.json
chmod 600 jev_secrets.json llm_secrets.json
```

Enter your own JEV / TypeSafe key in `TYPESAFE_API_KEY` and your DeepSeek key in
`DEEPSEEK_API_KEY`. Keep the quotation marks. The templates have blank keys;
the copy commands preserve existing files. Keep the real files private.

Use **Collect RSS** to save news, then **Analyze date batches (paid)** to
process saved articles from past dates in Malaysia time. API analysis can
incur charges. No collection or analysis runs automatically when the server
starts. Saved news can be viewed without API keys.

Articles and analysis results stay in the local `data/` folder. Selected
article text is sent to JEV / TypeSafe and DeepSeek when you start analysis.
Model output can contain errors or bias; follow the original article links
to check claims.

## Verify the download

The release includes `SHA256SUMS.txt` for checking the ZIP:

```sh
shasum -a 256 -c SHA256SUMS.txt
```

Run the included offline checks from the extracted project folder:

```sh
.venv/bin/python -m unittest -v
```

Live API tests are skipped by default. Keep `NEWS_ANALYSIS_LIVE_TESTS` unset
to avoid enabling paid tests.
