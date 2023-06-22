---
layout: post
title: Python | Crawling timeoutException 에러 발생시
date: 2020-06-03 11:58:47 +09:00
modified: 
category: [posts, errors]
tags: [crawling]
image: "/assets/img/python_logo.png"
cover: ""
---

### 크롤링 시 timeoutException 뜨는 경우

- **requests 사용 시**<br>
    설정
    ```python
    ##### timeout error handling
    import backoff
    import os
    REQUESTS_MAX_RETRIES = int(os.getenv("REQUESTS_MAX_RETRIES", 100))

    class ServerError(requests.exceptions.HTTPError):
        pass

    # Re-usable decorator with exponential wait.
    retry_timeout = backoff.on_exception(
        wait_gen=backoff.expo,
        exception=(
            ServerError,
            requests.exceptions.Timeout,
            requests.exceptions.ConnectionError
        ),
        max_tries=REQUESTS_MAX_RETRIES,
    )
    ```

    사용 
    ```python
    @retry_timeout
    def getAddressTX(walletAddress):
        pass
    ```


- **selenium 사용 시**
    ```python
    try:
        self.driver.get(Url)
    except TimeoutException as ex:
        print(ex.Message)
        self.driver.navigate().refresh()
    ```