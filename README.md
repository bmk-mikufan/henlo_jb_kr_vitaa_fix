이 도구는 near 앱을 vitadeploy로 대체가 불가능해 공식 메모리 없이 sd2vita만으로 커스텀 펌웨어를 설치할 수 없는 한국 모델 사용자를 위한 커스텀 henlo입니다.
## 기기에 벽돌이 일어나도 책임지지 않으며, 모든 책임은 사용자에게 있습니다.
## 백업 관련 코드는 수정하지 않았기 때문에 사용하지 마세요. 이 도구를 이용해서 실행 가능한 것은 오직 

1. 이 도구를 사용해서 다른 시스템 앱에 vdep를 설치하세요.
2. 공식 henlo를 이용해서 near를 vdep로 대체하세요. 다른 앱에 설치해도 vdep 소스를 수정하지 않는 이상, near 앱의 경로의 파일을 사용하기 때문에 필수적입니다.
3. vdep로 대체된 다른 시스템 앱을 실행하세요. 대부분의 기능이 작동하지 않겠지만, sd2vita 관련 설정은 작동할 것입니다.
4. vdep로 sd2vita를 포맷하고, 다시 공식 henlo로 sd2vita를 ux0에 마운트합니다. 기기를 재부팅하라는 메시지가 나오면 무시합니다.
5. 다시 공식 henlo로 vdep를 ux0에 설치합니다.
6. sd2vita에 설치된 vdep는 imcunlocker를 포함한 모든 기능이 작동할 것입니다. imcunlocker을 이용해 내장 메모리를 만들고, 재부팅합니다.
7. 이렇게 되면, 내장 메모리가 생기기 때문에 공식 가이드를 따라 커스텀 펌웨어 설치를 진행할 수 있습니다.


## 이 모든 방법은 제 삽질을 통해 깨달은 것입니다. 더 효율적인 방법이 있을 수도 있지만, 저는 시도해 보지 않았습니다. 
## 대체된 시스템 앱은 펌웨어 업데이트를 하면 돌아오는 것으로 보이나, 돌아오지 않을 수도 있습니다.



# henlo_jb_local
webkit-based jailbreak for Playstation Vita/TV on firmware 3.65+

Based on [SKGleba's work](https://github.com/SKGleba/henlo_jb), this allows you to run HENlo server fully locally for offline usage.

## Requirements
- PC with Python2 or Python3 installed on it
- WiFi router or WiFi dongle capable of acting as access point for Vita (2.4Ghz, AP Mode)

## Usage
1. Download [henlo_jb_local.zip](https://github.com/loomweaver/henlo_jb/releases/tag/henlo_jb_local) to your PC. 
2. Change your PC WiFi's IPv4 connection settings to Manual, set your PC's LAN IP  to 192.168.0.123, and set the gateway IP as the LAN IP of your router/WiFi dongle (usually 192.168.0.1 or something similar).
3. Unzip henlo_jb_local.zip somewhere on your PC. 
4. Open console terminal, navigate to the unzipped folder and run one of the server scripts, depending on your installed version of Python (server_python2.py for Python2 or server_python3.py for Python3). If successful, you should see the following message appear: `Starting server on 192.168.0.123:8888`
5. Connect your Vita via WiFi to your router/WiFi dongle, open http://192.168.0.123:8888 on your Vita and follow the [HENlo Vita guide](https://vita.hacks.guide/using-henlo.html) instructions as normal.

### Why 192.168.0.123? I want to use a different IP!
Repo IP that serves henkaku/VitaDeploy downloads is hardcoded within compiled payload.bin. If you want to use a different IP, you will need to:
1. Download or checkout this repo with git,
2. Change `HEN_REPO_URL` string value in `bootstrap_lite/main.c` (line 52),
3. Run `prepare_jb.sh` to recompile the `payload.bin` (you will need [Vita SDK](https://vitasdk.org/) installed for compilation),
4. Change the IP address in `server_python2.py`/`server_python3.py`.
