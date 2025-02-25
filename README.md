<h1>Fullstack Service Networking Season.2 <br />HyperCorn & Starlette RESTful API Program</h1>	

Server : Python (HyperCorn ASGI Server + Starlette Application)

Client : Web Browser (PyScript : Python in HTML, Pico.css)

Networking : HTTP/1.1, HTTP/2, HTTP/3 

Packaging : Poetry (추가 패키지: hypercorn, aioquic, h3, starlette, pyscript)

<br />
<br />

<h2>Overall Architecture</h2>	

![WSGI/ASGI Architecture.](https://derlin.github.io/introduction-to-fastapi-and-celery/assets/01-wsgi.excalidraw.png)

(출처: https://derlin.github.io/introduction-to-fastapi-and-celery/02-fastapi/)

<br />
<br />

<h2>실행 방법</h2>		

> NOTE<br />
>> macOS & Linux : 제한 사항 없음<br />
>> MS Windows : <br />
>>> Server : WSL2 사용을 권장함<br />
>>> Client : <br />
>>>> HTTP/1.1 & HTTP/2 : Windows에서 Chrome 브라우저(chrome.exe)를 실행후, WSL2의 서버로 접속함<br />
>>>> HTTP/3 : WSL2에서 Chrome 브라우저 실행후, WSL2의 서버로 접속함<br />
>>>>> Chrome 브라우저를 WSL2에 설치하고 실행하는 방법은 다음을 참조함<br />
>>>>> https://learn.microsoft.com/ko-kr/windows/wsl/tutorials/gui-apps

프로젝트를 다운로드 함

폴더안에서 poetry shell를 실행함<br />
> poetry shell

폴더안에서 필요한 패키지를 설치함<br />
> poetry install

src/server.py를 실행함<br />

> HTTP/1.1
>> poetry run hypercorn server_app:run

> HTTP/2
>> poetry run hypercorn --certfile cert/localhost.crt --keyfile cert/localhost.key --bind localhost:8000 server_app:run

> HTTP/2 & HTTP/3
>> poetry run hypercorn --quic-bind localhost:4433 --certfile cert/localhost.crt --keyfile cert/localhost.key --bind localhost:8000 server_app:run

Chrome browser로 서버에 접속함<br />

> HTTP/1.1
>> http://127.0.0.1:8000/

> HTTP/2
>> https://127.0.0.1:8000/

> HTTP/3
>> Chrome browser를 HTTP/3 모드로 강제 실햄함<br />

>>> macOS 경우:
>>>> sudo /Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --enable-quic --allow-insecure-localhost --origin-to-force-quic-on=127.0.0.1:4433 --ignore-certificate-errors-spki-list="Vy/mwFlqWXlxva7JH2xXR0bShco74LOb7xG1dFlZlrA=" <br /><br />
>>>> https://127.0.0.1:4433/ 

>>> Linux 경우:
>>>> google-chrome --enable-quic --allow-insecure-localhost --origin-to-force-quic-on=127.0.0.1:4433 --ignore-certificate-errors-spki-list="Vy/mwFlqWXlxva7JH2xXR0bShco74LOb7xG1dFlZlrA=" <br /><br />
>>>> https://127.0.0.1:4433/ 

화면 위쪽의 “Please wait, program is starting …” 문구가 다음처럼 바뀌기를 기다림<br />
Please fills key/value and executes menu :

CREATE 동작을 위하여,<br />
CREATE 버튼 왼쪽의 Key와 Value에 각각 apple과 1000을 입력하고, CREATE 버튼을 클릭함<br />
CREATE 결과를 웹브라우저 화면과 서버 출력 화면에서 확인함

READ 동작을 위하여,<br />
READ 버튼 왼쪽의 Key에 apple을 입력하고, READ 버튼을 클릭함<br />
READ 결과를 웹브라우저 화면과 서버 출력 화면에서 확인함

UPDATE 동작을 위하여,<br />
UPDATE 버튼 왼쪽의 Key와 Value에 각각 apple과 2000을 입력하고, UPDATE 버튼을 클릭함<br />
UPDATE 결과를 웹브라우저 화면과 서버 출력 화면에서 확인함

DELETE 동작을 위하여,<br />
DELETE 버튼 왼쪽의 Key에 apple을 입력하고, DELETE 버튼을 클릭함<br />
DELETE 결과를 웹브라우저 화면과 서버 출력 화면에서 확인함

서버 종료를 위하여 ctrl-c 키보드 입력을 수행함

Client를 실행하기 위해서, 실행한 Python http.server를 ctrl-c 키보드 입력으로 종료함

Poetry 실행을 중지함<br />
> exit

<br />
<br />

<h2>실행 화면</h2>	

<img src="/screen/client-http1-create.png" width="1000"/>
<img src="/screen/client-http1-read.png" width="1000"/>
<img src="/screen/client-http1-update.png" width="1000"/>
<img src="/screen/client-http1-delete.png" width="1000"/>
<img src="/screen/server-http1.png" width="1000"/>

<img src="/screen/client-http2-create.png" width="1000"/>
<img src="/screen/client-http2-read.png" width="1000"/>
<img src="/screen/client-http2-update.png" width="1000"/>
<img src="/screen/client-http2-delete.png" width="1000"/>
<img src="/screen/server-http2.png" width="1000"/>

<img src="/screen/client-http3-create.png" width="1000"/>
<img src="/screen/client-http3-read.png" width="1000"/>
<img src="/screen/client-http3-update.png" width="1000"/>
<img src="/screen/client-http3-delete.png" width="1000"/>
<img src="/screen/server-http2-3.png" width="1000"/>
