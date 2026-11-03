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
- [x] 현재 위치 확인 (pwd)
- [x] 목록 확인 숨김 파일 포함 (ls -a)
- [x] 디렉토리 이동 (cd)
- [x] 디렉토리/파일 생성 (mkdir, touch)
- [x] 파일 복사 (cp)
- [x] 파일 이동/이름변경 (mv)
- [x] 파일 삭제 (rm)
- [ ] 파일 내용 확인 (cat)

### 파일 권한
- [x] 권한 확인 (ls -l)
- [x] 권한 변경 (chmod)

### Docker 설치 및 기본점검
- [ ] Docker 버전 확인 (docker --version)
- [ ] Docker 데몬 동작 확인 (docker info)

### Docker 기본 운영 명령 수행
- [ ] hello-world 컨테이너 실행 (docker run hello-world)
- [ ] 이미지 목록 확인 (docker images)
- [ ] 실행 중 컨테이너 확인 (docker ps)
- [ ] 전체 컨테이너 확인 (docker ps -a)
- [ ] 컨테이너 로그 확인 (docker logs)
- [ ] 컨테이너 리소스 확인 (docker stats)
- [ ] 컨테이너 중지 (docker stop)
- [ ] 컨테이너 삭제 (docker rm)

### Ubuntu 컨테이너 실습
- [ ] Ubuntu 컨테이너 실행 (docker run -it ubuntu bash)
- [ ] 컨테이너 내부에서 간단 명령 수행 (ls, echo, exit)
- [ ] 백그라운드 컨테이너 실행 (docker run -dit)
- [ ] 실행 중 컨테이너에 접속 (docker exec -it)
- [ ] "attach"와 "exec" 차이 간단 정리

### Dockerfile / 커스텀 이미지
- [ ] Dockerfile 작성
- [ ] 커스텀 이미지 빌드
- [ ] 컨테이너 실행 성공

### 포트 매핑
- [ ] 포트 매핑 실행 (-p host:container)
- [ ] 브라우저 접속 화면(주소창 포함) 첨부

### 바인드 마운트 / 볼륨
- [ ] 바인드 마운트 실행 + 호스트 변경 전/후 비교
- [ ] 볼륨 생성/연결/검증
- [ ] 컨테이너 삭제 전/후 데이터 유지 확인

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

1. 현재 위치 확인 (pwd)
```bash
$ pwd
/c/Codyssey-Campus/codyssey
```

2. 목록 확인 숨김 파일 포함 (ls -a)
```bash
$ ls -a
./  ../  .git/  Hello.txt  practice/  README.md
```

3. 디렉토리 이동 (cd)
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

4. 디렉토리/파일 생성 (mkdir, touch)
```bash
$ mkdir TEST # TEST 폴더 생성
$ touch TEST.txt # TEST.txt 파일 생성
```
```bash
$ ls -a
./  ../  .git/  Hello.txt  practice/  README.md  TEST/  TEST.txt
```

5. 파일 복사 (cp)
```bash
$ cp TEST.txt TEST-사본.txt 
```
```bash
$ ls -a
./  ../  .git/  Hello.txt  practice/  README.md  TEST/  TEST.txt  TEST-사본.txt
```

6. 파일 이동/이름변경 (mv)
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

7. 파일 삭제 (rm)
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

1. 권한 확인 (ls -l)
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

2. 권한 변경 (chmod) 
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




## 🧩 트러블슈팅
### 1. Git Bash에서 chmod가 반영되지 않음
- **문제**: Git Bash(Windows)에서 `chmod 744`를 실행해도 `ls -l` 권한 표기가 바뀌지 않음
- **원인 가설**: Windows 파일시스템(NTFS)은 리눅스식 rwx 권한 모델을 그대로 지원하지 않음
- **확인**: 동일 명령을 WSL/Linux 환경에서 실행 → 권한이 정상 반영됨
- **해결/대안**: 권한 실습은 WSL 환경에서 수행하기로 결정