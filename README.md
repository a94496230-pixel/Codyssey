# 🖥️ 개발 환경 세팅 미션

## 📌 프로젝트 개요
터미널, Docker, Git, GitHub를 직접 실습하고
개발 환경 세팅 전 과정을 기록하는 미션입니다.

---

## 💻 실행 환경

| 항목 | 내용 |
|------|------|
| OS | Windows 11 |
| 쉘/터미널 | WSL/Linux, Git Bash (VS Code 내장) |
| Git 버전 | 2.56.0.windows.4 |
| Docker 버전 | 추후 추가 예정 |

---

## ✅ 수행 항목 체크리스트

### 터미널 조작
- [x] 현재 위치 확인 (`pwd`)
- [x] 목록 확인 숨김 파일 포함 (`ls -a`)
- [x] 디렉토리 이동 (`cd`)
- [x] 디렉토리/파일 생성 (`mkdir`, `touch`)
- [x] 파일 내용 확인 (`cat`)
- [x] 파일 복사 (`cp`)
- [x] 파일 이동/이름변경 (`mv`)
- [x] 파일 삭제 (`rm`)

### 파일 권한
- [x] 권한 확인 (`ls -l`)
- [x] 권한 변경 (`chmod`)

### Docker 설치 및 기본점검
- [x] Docker 버전 확인 (`docker --version`)
- [x] Docker 데몬 동작 확인 (`docker info`)

### Docker 기본 운영 명령 수행
- [x] hello-world 컨테이너 실행 (`docker run hello-world`)
- [x] 이미지 목록 확인 (`docker images`)
- [x] 실행 중 컨테이너 확인 (`docker ps`)
- [x] 전체 컨테이너 확인 (`docker ps -a`)
- [x] 컨테이너 로그 확인 (`docker logs`)
- [ ] 컨테이너 리소스 확인 (`docker stats`)

### Ubuntu 컨테이너 실습
- [x] Ubuntu 컨테이너 실행 (`docker run -it ubuntu bash`)
- [x] 컨테이너 내부에서 간단 명령 수행 (`ls`, `echo`, `exit`)
- [x] 실행 중 컨테이너에 접속 (`docker exec -it`)
- [ ] 백그라운드 컨테이너 실행 (`docker run -dit`)
- [ ] 이름 붙여 실행 (`docker run --name`)
- [ ] "attach"와 "exec" 차이 간단 정리

### 컨테이너 관리 (중지 / 재시작 / 삭제)
- [ ] 컨테이너 중지 (`docker stop`)
- [ ] 컨테이너 재시작 (`docker start`)
- [ ] 컨테이너 삭제 (`docker rm`)
- [ ] 이미지 삭제 (`docker rmi`)
> 💡 **stop ↔ start**, **rm ↔ rmi** 짝으로 기억하기

### Dockerfile / 커스텀 이미지
- [ ] Dockerfile 작성
- [ ] 커스텀 이미지 빌드 (`docker build`)
- [ ] 컨테이너 실행 성공
- [ ] 이미지 층(layer) 확인 (`docker history`)

### 포트 매핑
- [ ] 포트 매핑 실행 (`-p host:container`)
- [ ] 브라우저 접속 화면(주소창 포함) 첨부

### 바인드 마운트 / 볼륨
- [ ] 바인드 마운트 실행 + 호스트 변경 전/후 비교
- [ ] 볼륨 생성/연결/검증 (`docker volume`)
- [ ] 컨테이너 삭제 전/후 데이터 유지 확인 ⭐

### Git / GitHub
- [x] Git 설치 확인
- [x] 사용자 정보 등록
- [x] 레포지토리 클론
- [x] add / commit / push
- [ ] branch 생성 및 관리
- [ ] git config --list 결과 기록
- [ ] VSCode ↔ GitHub 연동 증거

---

## 🔍 검증 방법 및 결과

### 터미널 조작
> 🖥️ 수행 환경: Git Bash (Windows, VS Code 내장)

1. 현재 위치 확인 (`pwd`)
```bash
$ pwd
/c/Codyssey-Campus/codyssey
```

2. 목록 확인 숨김 파일 포함 (`ls -a`)
```bash
$ ls -a
./  ../  .git/  Hello.txt  practice/  README.md
```

3. 디렉토리 이동 (`cd`)
```bash
$ cd .. # .. 은 상위폴더로 이동
```
```bash
$ pwd 
/c/Codyssey-Campus/
```
```bash
$ cd - # - 는 이전 위치로 되돌아가기
/c/Codyssey-Campus/codyssey
```

4. 디렉토리/파일 생성 (`mkdir`, `touch`)
```bash
$ mkdir TEST # TEST 폴더 생성
$ touch TEST.txt # TEST.txt 파일 생성
```
```bash
$ ls -a
./  ../  .git/  Hello.txt  practice/  README.md  TEST/  TEST.txt
```

5. 파일 내용 확인 (`cat`)
```bash 
$ echo "TEST" > test.txt # echo명령어로 test.txt 파일에 "TEST"입력
```
```bash
$ cat test.txt # 입력한 "TEST" 내용 확인
TEST
```

6. 파일 복사 (`cp`)
```bash
$ cp TEST.txt TEST-사본.txt 
```
```bash
$ ls -a
./  ../  .git/  Hello.txt  practice/  README.md  TEST/  TEST.txt  TEST-사본.txt
```

7. 파일 이동/이름변경 (`mv`)
```bash
$ mv TEST-사본.txt TEST-변경.txt # 사본을 변경으로 파일 이름 변경
```
```bash
$ mv TEST-변경.txt TEST/ # 변경 파일을 TEST 폴더로 이동
```
```bash
$ ls -a # 변경 파일이 TEST파일로 이동되었는지 확인1
./  ../  .git/  Hello.txt  practice/  README.md  TEST/  TEST.txt
```
```bash
$ cd TEST
```
```bash
$ pwd
/c/Codyssey-Campus/codyssey/TEST
```
```bash
$ ls -a # 변경 파일이 TEST파일로 이동되었는지 확인2
./  ../  TEST-변경.txt
```

8. 파일 삭제 (`rm`)
```bash
$ rm -r TEST TEST.txt # -r은 디렉토리를 삭제하기 위한 명령어. 파일은 -r 없이도 삭제 가능
```
```bash
$ ls -a
./  ../  .git/  Hello.txt  practice/  README.md
```

### 파일 권한
> 🐧 수행 환경: WSL/Linux
> 💡 Git Bash(Windows)에서는 chmod가 실제 파일시스템에 정확히 반영되지 않아,
> 권한 실습은 WSL 환경에서 수행했습니다. (→ 트러블슈팅 참고)

1. 권한 확인 (`ls -l`)
```bash
$ pwd # 현재 위치 확인
/home/xoalsrla226230/Codyssey-Campus/Codyssey/권한연습
```
```bash
$ ls -l # -l이 권한을 확인하는 명령어(권한은 소유자,그룹,나머지 순서로 표시)
total 4
drwxr-xr-x 2 xoalsrla226230 xoalsrla226230 4096 Nov  3 14:05 권한연습-하위 # d는 디렉토리 r읽기 w쓰기 x실행
-rw-r--r-- 1 xoalsrla226230 xoalsrla226230    0 Nov  3 14:05 권한연습.txt # 초기 권한 644 상태
```

2. 권한 변경 (`chmod`) 
> 권한 숫자는 `소유자(owner) / 그룹(group) / 기타 사용자(others)` 순서로 표시됩니다.  
> 각 숫자는 `읽기 r = 4`, `쓰기 w = 2`, `실행 x = 1`을 더해서 계산합니다.
```bash
$ chmod 744 권한연습.txt # 소유자 실행권한 추가 rw-(6)에서 rwx(7)로 변경 (4+2+1=7)
$ ls -l # 권한 확인
total 4
drwxr-xr-x 2 xoalsrla226230 xoalsrla226230 4096 Nov  3 14:05 권한연습-하위
-rwxr--r-- 1 xoalsrla226230 xoalsrla226230    0 Nov  3 14:05 권한연습.txt # rw-가 rwx로 변경됨
```
```bash
$ chmod 764 권한연습.txt # 그룹에 쓰기권한 추가 r--(4)에서 rw-(6)으로 변경 (4+2=6)
$ ls -l
total 4
drwxr-xr-x 2 xoalsrla226230 xoalsrla226230 4096 Nov  3 14:05 권한연습-하위
-rwxrw-r-- 1 xoalsrla226230 xoalsrla226230    0 Nov  3 14:05 권한연습.txt # r--였던 그룹권한이 rw-로 변경
```
```bash
$ chmod 777 권한연습.txt # 모든 사용자에게 모든 권한 부여. 7(4+2+1=7)
$ ls -l
total 4
drwxr-xr-x 2 xoalsrla226230 xoalsrla226230 4096 Nov  3 14:05 권한연습-하위
-rwxrwxrwx 1 xoalsrla226230 xoalsrla226230    0 Nov  3 14:05 권한연습.txt # 모두 rwx상태
```
```bash
$ chmod 770 권한연습.txt # 나와 그룹을 제외한 모든 권한 제거 0(권한 없음)
$ ls -l
total 4
drwxr-xr-x 2 xoalsrla226230 xoalsrla226230 4096 Nov  3 14:05 권한연습-하위
-rwxrwx--- 1 xoalsrla226230 xoalsrla226230    0 Nov  3 14:05 권한연습.txt # 기타 사용자 ---상태
```
```bash
$ chmod 644 권한연습.txt # 초기 권한상태로 복구
$ ls -l
total 4
drwxr-xr-x 2 xoalsrla226230 xoalsrla226230 4096 Nov  3 14:05 권한연습-하위
-rw-r--r-- 1 xoalsrla226230 xoalsrla226230    0 Nov  3 14:05 권한연습.txt # 초기 644로 복구
```
```bash
$ chmod 700 권한연습-하위 # 755(초기권한)→700, 그룹·기타 권한 전체 제거 (비밀 폴더)
$ ls -l
total 4
drwx------ 2 xoalsrla226230 xoalsrla226230 4096 Nov  3 14:05 권한연습-하위
-rw-r--r-- 1 xoalsrla226230 xoalsrla226230    0 Nov  3 14:05 권한연습.txt
```

### Docker 설치 및 기본점검

1. Docker 버전 확인 (`docker --version`)
```bash
$ docker --version
Docker version 29.9.3, build 5457199
```

2. Docker 데몬 동작 확인 (`docker info`)
```bash
$ docker info
Client: Docker Engine - Community # docker의 명령을 입력하는 클라이언츠(CLI) 정보
 Version:    29.9.3
 Context:    default
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.38.1
    Path:     /usr/libexec/docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v5.7.0
    Path:     /usr/libexec/docker/cli-plugins/docker-compose

Server: # 실제 컨테이너를 돌리는 daemon의 정보
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 29.9.3
 Storage Driver: overlayfs
  driver-type: io.containerd.snapshotter.v1
 Logging Driver: json-file
 Cgroup Driver: systemd
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: b7a25261e029d68978bbf290df0a62fc819b3c51
 runc version: v1.5.2-0-g29dd3dc2
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.18.54.1-microsoft-standard-WSL2
 Operating System: Ubuntu 22.04.5 LTS
 OSType: linux
 Architecture: x86_64
 CPUs: 24
 Total Memory: 15.25GiB
 Name: GNIA-C202-A04
 ID: fd6bc33e-cf90-4269-a8dd-4a38cf4860e9
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 Experimental: false
 Insecure Registries:
  127.0.0.0/8
  ::1/128
 Live Restore Enabled: false
 Firewall Backend: iptables
  EnableUserlandProxy: true
  UserlandProxyPath: /usr/bin/docker-proxy
  ```

### Docker 기본 운영 명령 수행

1. hello-world 컨테이너 실행 (`docker run hello-world`)
```bash
$ docker run hello-world
Unable to find image 'hello-world:latest' locally # local에서 hello-world를 찾을 수 없음
latest: Pulling from library/hello-world # 인터넷에서 가져옴
4f55086f7dd0: Pull complete 
d5e71e642bf5: Download complete 
Digest: sha256:c567b231f65614688711a75f31518a064258a51d442117a3e771a3a8fdba78ef
Status: Downloaded newer image for hello-world:latest

Hello from Docker! # 결과
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps: # 과정 메시지
 1. The Docker client contacted the Docker daemon. # CLI가 daemon(server)에게 요청
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal. # daemon이 CLI에게 결과를 돌려줌

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
 ```
> 입문 교육용 이미지인 hello-world에서 여러 안내 메시지가 출력됨.


2. 이미지 목록 확인 (`docker images`)
```bash
$ docker images
                                                                                                     i Info →   U  In Use
IMAGE                ID             DISK USAGE   CONTENT SIZE   EXTRA
hello-world:latest   c567b231f656       25.9kB         9.49kB    U   
```
> 이름 : 뒤는 태그. 지정하지 않으면 자동으로 latest, ID는 고유식별ID, U는 in use 사용 중.

3. 실행 중 컨테이너 확인 (`docker ps`)
```bash
$ docker ps # 실행중인 컨테이너 없음
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

4. 전체 컨테이너 확인 (`docker ps -a`)
```bash
$ docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                      PORTS     NAMES
61344da3d406   hello-world   "/hello"   21 minutes ago   Exited (0) 21 minutes ago             laughing_driscoll
```
> 이미지와 컨테이너 분리해서 알아야함. 이미지는 In Use 상태, 컨테이너는 Exited(0)되어 running이 아니기 때문에 ps에는 보이지 않고 ps -a로 확인 가능.
> 사용 중, 실행 중의 구분이 모호했으나 이미지와 컨테이너의 차이였음.
> hello-world는 docker가 제대로 설치되고 작동되는 지 확인하는 테스트용 이미지이기 때문에 임의로 exit하지 않아도 "Hello form Docker!"라는 메시지 출력 후 자동으로 종료됨. 그래서 내가 끄지 않았는데도 ps로 확인 할 수 없었음.

5. 컨테이너 로그 확인 (`docker logs`)
```bash
$ docker logs 61344 # 컨테이너의 고유ID 앞부분 만으로 출력가능. 이전에 출력됐던 log가 출력됨.

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with: # Ubuntu 컨테이너 추천. 교육용이라 출력되는 듯
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
 ```

6. 컨테이너 리소스 확인 (`docker stats`)
```bash
$ docker ps # 리소스 확인 전 ps로 현재 실행중인 컨테이너 확인
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
636354721ff5   ubuntu    "/bin/bash"   15 minutes ago   Up 15 minutes             naughty_hoover
835f8e82e7a4   ubuntu    "/bin/bash"   27 minutes ago   Up 19 minutes             focused_lumiere
```
```bash
$ docker stats # 결과값
CONTAINER ID   NAME              CPU %     MEM USAGE / LIMIT     MEM %     NET I/O         BLOCK I/O   PIDS
636354721ff5   naughty_hoover    0.00%     1.125MiB / 15.25GiB   0.01%     1.05kB / 126B   0B / 0B     1
835f8e82e7a4   focused_lumiere   0.00%     948KiB / 15.25GiB     0.01%     1.46kB / 126B   0B / 0B     1
```


### Ubuntu 컨테이너 실습

1. Ubuntu 컨테이너 실행 (`docker run -it ubuntu bash`)
```bash
$ docker run -it ubuntu bash
Unable to find image 'ubuntu:latest' locally # hello-world와 마찬가지고 local에 없어서 인터넷에서 다운로드.
latest: Pulling from library/ubuntu
f3f25b84a7d7: Pull complete 
edafa32f5d9e: Pull complete 
21594acc2d8b: Download complete 
Digest: sha256:6a06111c3b0a8600feadb270aec771dc239bf407b25625f93f44ab00e11f4d3c
Status: Downloaded newer image for ubuntu:latest
root@79389cf69868:/#
```

2. 컨테이너 내부에서 간단 명령 수행 (`ls`, `echo`, `exit`)
```bash
ls
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
```
```bash
/# mkdir study # study 폴더 생성
/# ls # 생성 확인
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  study  sys  tmp  usr  var
/# cd study # study 폴더로 이동
/study# pwd # 현재 위치
/study
/study# touch memo.txt # memo.txt 생성
/study# ls # 생성 확인
memo.txt
/study# echo "Docker study" > memo.txt # Docker study라는 내용 memo.txt에 입력
/study# cat memo.txt
Docker study # 입력된 내용 확인
```
```bash 
/study# exit # Ubuntu 컨테이너 종료
exit
$ docker ps -a # 컨테이너에서 나와 내 컴퓨터로 프롬프트가 바뀐 상태에서 컨테이너 확인 명령(docker ps -a)
CONTAINER ID   IMAGE         COMMAND    CREATED             STATUS                           PORTS     NAMES
138cba0d7b9e   ubuntu        "bash"     32 minutes ago      Exited (0) 6 seconds ago                   optimistic_mcnulty
79389cf69868   ubuntu        "bash"     About an hour ago   Exited (127) About an hour ago             eager_kepler
61344da3d406   hello-world   "/hello"   2 hours ago         Exited (0) 2 hours ago                     laughing_driscoll
```
> 6초 전에 종료된 ubuntu 컨테이너가 방금 exit한 컨테이너.

3. 실행 중 컨테이너에 접속 (`docker exec -it`)
```bash
$ docker exec -it 138cba0d7b9e bash
```

4. 백그라운드 컨테이너 실행 (`docker run -dit`)
```bash
$ docker run -dit ubuntu # 기존 실행했던 -it에 -d가 추가됨. -d(detached):백그라운드 실행, -i(interactive):입력, -t(tty):터미널 화면
636354721ff5c5358e374016aaafafadf6a534f4f279b7563cdca7a0b82a1319
```
```bash
$ docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED          STATUS          PORTS     NAMES
636354721ff5   ubuntu    "/bin/bash"   11 seconds ago   Up 11 seconds             naughty_hoover # 백그라운드로 실행한 컨테이너
835f8e82e7a4   ubuntu    "/bin/bash"   12 minutes ago   Up 4 minutes              focused_lumiere
```

5. 이름 붙여 실행 (`docker run --name`)
```bash
$ docker run --name TEST ubuntu # TEST라는 이름을 가진 컨테이너를 ubuntu이미지로 실행함
```
```bash
$ docker ps -a # 실행했지만 -it나 -dit 가 포함되지 않아 실행 후 바로 Exited 된 상태.
CONTAINER ID   IMAGE         COMMAND       CREATED          STATUS                        PORTS     NAMES
35621fb2791e   ubuntu        "/bin/bash"   8 seconds ago    Exited (0) 7 seconds ago                TEST
636354721ff5   ubuntu        "/bin/bash"   10 minutes ago   Up 10 minutes                           naughty_hoover
835f8e82e7a4   ubuntu        "/bin/bash"   22 minutes ago   Up 15 minutes                           focused_lumiere
138cba0d7b9e   ubuntu        "bash"        2 hours ago      Exited (137) 20 minutes ago             optimistic_mcnulty
79389cf69868   ubuntu        "bash"        3 hours ago      Exited (127) 3 hours ago                eager_kepler
61344da3d406   hello-world   "/hello"      4 hours ago      Exited (0) 4 hours ago                  laughing_driscoll
```

6. "attach"와 "exec" 차이 간단 정리





### 컨테이너 관리 (중지 / 재시작 / 삭제)

1. 컨테이너 중지(`docker stop`)
```bash 
$ docker stop 138cba0d7b9e
138cba0d7b9e
```
```bash
$ docker ps -a # `ps -a`로 컨테이너 상태 확인. STATUS Exited 확인.
CONTAINER ID   IMAGE         COMMAND       CREATED         STATUS                        PORTS     NAMES
835f8e82e7a4   ubuntu        "/bin/bash"   3 minutes ago   Exited (137) 35 seconds ago             focused_lumiere
138cba0d7b9e   ubuntu        "bash"        2 hours ago     Exited (137) 14 seconds ago             optimistic_mcnulty
79389cf69868   ubuntu        "bash"        3 hours ago     Exited (127) 2 hours ago                eager_kepler
```

2. 컨테이너 재시작 (`docker start`)
```bash
$ docker start 835f8e82e7a4
835f8e82e7a4
```
```bash
$ docker ps # 'ps'로 확인. STATUS UP 확인.
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
835f8e82e7a4   ubuntu    "/bin/bash"   7 minutes ago   Up 7 seconds             focused_lumiere
```

3. 컨테이너 삭제 (`docker re`)
```bash
$ docker ps -a # 삭제 전 전체 컨테이너 확인
CONTAINER ID   IMAGE         COMMAND       CREATED          STATUS                        PORTS     NAMES
35621fb2791e   ubuntu        "/bin/bash"   8 minutes ago    Exited (0) 8 minutes ago                TEST
636354721ff5   ubuntu        "/bin/bash"   18 minutes ago   Exited (137) 19 seconds ago             naughty_hoover
835f8e82e7a4   ubuntu        "/bin/bash"   31 minutes ago   Up 23 minutes                           focused_lumiere
138cba0d7b9e   ubuntu        "bash"        2 hours ago      Exited (137) 28 minutes ago             optimistic_mcnulty
79389cf69868   ubuntu        "bash"        3 hours ago      Exited (127) 3 hours ago                eager_kepler
61344da3d406   hello-world   "/hello"      4 hours ago      Exited (0) 4 hours ago                  laughing_driscoll
```
```bash
$ docker rm 35621fb2791e # ID가 35621fb2791e인 TEST이름의 컨테이너 삭제 명령
35621fb2791e
```
```bash
$ docker ps -a # 삭제된게 확인됨.
CONTAINER ID   IMAGE         COMMAND       CREATED          STATUS                            PORTS     NAMES
636354721ff5   ubuntu        "/bin/bash"   19 minutes ago   Exited (137) About a minute ago             naughty_hoover
835f8e82e7a4   ubuntu        "/bin/bash"   32 minutes ago   Up 24 minutes                               focused_lumiere
138cba0d7b9e   ubuntu        "bash"        2 hours ago      Exited (137) 29 minutes ago                 optimistic_mcnulty
79389cf69868   ubuntu        "bash"        3 hours ago      Exited (127) 3 hours ago                    eager_kepler
61344da3d406   hello-world   "/hello"      4 hours ago      Exited (0) 4 hours ago                      laughing_driscoll
```

4. 이미지 삭제 (`docker rmi`)
```bash
$ docker images
                                                                                                                                                                          i Info →   U  In Use
IMAGE                ID             DISK USAGE   CONTENT SIZE   EXTRA
hello-world:latest   c567b231f656       25.9kB         9.49kB    U   
ubuntu:latest        6a06111c3b0a        163MB         45.9MB    U   
```
```bash
$ docker rmi c567b231f656
Error response from daemon: conflict: unable to delete c567b231f656 (must be forced) - image is being used by stopped container 61344da3d406
```
> 삭제가 되지 않음. 트러블슈팅 참고.
```bash
$ docker ps -a # 삭제하려던 이미지인 헬로월드 컨테이너 확인
CONTAINER ID   IMAGE         COMMAND       CREATED          STATUS                            PORTS     NAMES
636354721ff5   ubuntu        "/bin/bash"   19 minutes ago   Exited (137) About a minute ago             naughty_hoover
835f8e82e7a4   ubuntu        "/bin/bash"   32 minutes ago   Up 24 minutes                               focused_lumiere
138cba0d7b9e   ubuntu        "bash"        2 hours ago      Exited (137) 29 minutes ago                 optimistic_mcnulty
79389cf69868   ubuntu        "bash"        3 hours ago      Exited (127) 3 hours ago                    eager_kepler
61344da3d406   hello-world   "/hello"      4 hours ago      Exited (0) 4 hours ago                      laughing_driscoll
```
```bash
$ docker rm 61344da3d406 # 헬로월드 컨테이너 삭제
61344da3d406
```
```bash
$ docker rmi c567b231f656 # 헬로월드 이미지 삭제
Untagged: hello-world:latest
Deleted: sha256:c567b231f65614688711a75f31518a064258a51d442117a3e771a3a8fdba78ef
```
```bash
$ docker images # 헬로월드 이미지 삭제 확인
                                                                                                                                                                          i Info →   U  In Use
IMAGE           ID             DISK USAGE   CONTENT SIZE   EXTRA
ubuntu:latest   6a06111c3b0a        163MB         45.9MB    U   
```











## 🧩 트러블슈팅
### 1. Git Bash에서 chmod가 반영되지 않음
- **문제**: Git Bash(Windows)에서 `chmod 744`를 실행해도 `ls -l` 권한 표기가 바뀌지 않음
- **원인 가설**: Windows 파일시스템(NTFS)은 리눅스식 rwx 권한 모델을 그대로 지원하지 않음
- **확인**: 동일 명령을 WSL/Linux 환경에서 실행 → 권한이 정상 반영됨
- **해결/대안**: 권한 실습은 WSL 환경에서 수행하기로 결정

### 2. Docker에서 Image를 삭제하려고 했으나 오류 발생
- **문제**: Docker에서 `docker rmi ID`를 실행해도 삭제되지 않음.
- **원인 가설**: 해당 Image로 실행했던 컨테이너가 남아있어서 명령을 수행하지 못함
- **확인**: 컨테이너를 목록을 확인, 삭제를 원하는 이미지의 컨테이너를 삭제 후 다시 Image삭제 시도
- **해결/대안**: *rm ↔ rmi*을 짝을 지어 학습. 컨테이너의 큰 틀을 담당하는 이미지는 만들어진 컨테이너가 있으면 삭제가 되지 않음을 학습.