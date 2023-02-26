# Fluent Python: pp 745 - 750

Sequential Example:

- 用了`httpx` 包发请求
    - `resp=httpx.get(url, timeout=6.1, follow_redirects=True)`
        - 默认值 `follow_redirects` 是False，这里设成true更灵活一点，比如之后图片换了位置

`concurrent.futures` Example:

- 主要用的就是`ThreadPoolExecutor`

    - ```python
        with figures.ThreadPoolExecutor() as executor:
        		res = executor.map(download_one, sorted(cc_list))
        ```

- `ThreadPoolExecutor` 其实有一个参数max_worker ，它的默认值是`None` => 会自动生成 `max_workers=min(32, os.cpu_count()+4)`

