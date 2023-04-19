

### 터미널에서 시스템 종료 명령

```shell
$ poweroff
$ shutdown -P now
$ halt -p
$ init 0

$ shutdown -P +10 	// 10분 후에 종료(power off)
$ shutdown -r 22:00 // 오후 10시에 재부팅(reboot)
$ shutdown -c 		// 예약된 shutdown 명령을 취소(cancel)
$ shutdown -k +15 	// 현재 접속한 사용자에게 15분 후에 종료된다는 메시지를 보내지만, 실제로 종료하지는 않음
```

- 표식이 # 이면 root 사용자, $ 이면 일반 사용자



### 시스템 재부팅

```shell
$ shutdown -r now
$ reboot
$ init 6
```



## 리눅스 기본 명령

#### ls

> List. 해당 디렉터리에 있는 파일의 목록을 나열하는 명령

```shell
$ ls	// 현재 디렉터리의 파일 목록을 표시
$ ls /etc/sysconfig		// /etc/sysconfig 디렉터리의 목록을 표시
$ ls -a		// 현재 디렉터리의 목록(숨김 파일 포함)을 표시
$ ls -l		// 현재 디렉터리의 목록을 자세히 표시
$ ls *.cfg	// 확장자가 cfg인 목록을 표시
$ ls -l /etc/sysconfig/a*	// /etc/sysconfig 디렉터리 중 앞 글자가 'a'인 것의 목록을 자세히 표시
```

#### cd

> Change Directory. 디렉터리를 이동하는 명령

```shell
$ cd		// 현재 사용자의 홈 디렉터리로 이동, 만약 현재 사용자가 root면 '/root' 디렉터리로 이동
$ cd ~rocky // rocky 사용자의 홈 디렉터리로 이동
$ cd .. 	// 바로 상위의 디렉터리로 이동
$ cd /etc/sysconfig 	// /etc/sysconfig 디렉터리로 이동(절대 경로)
$ cd ../etc/sysconfig 	// 상대 경로로 이동. 현재 디렉터리의 상위로 이동한 후 다시 /etc/sysconfig 로 이동
```

#### pwd

> Print Working Directory. 현재 디렉터리의 전체 경로를 화면에 표시

```shell
$ pwd // 현재 작업 중인 디렉터리의 경로를 출력
```

#### rm

> ReMove. 파일이나 디렉터리를 삭제

- 파일이나 디렉터리를 삭제할 권한이 있어야 해당 명령을 실행할 수 있다.

```shell
$ rm abc.txt	// 해당 파일을 삭제(내부적으로 'rm -i'로 연결됨)
$ rm -i abc.txt	// 삭제 시 정말 삭제할 지 확인하는 메시지를 표시
$ rm -f abc.txt	// 삭제 시 확인하지 않고 바로 삭제(f는 Force의 약자)
$ rm -r abc		// 해당 디렉터리를 삭제(r은 Recursive의 약자)
$ rm -rf abc	// r옵션과 f옵션을 합친 것, abc 디렉터리와 그 아래에 있는 하위 디렉터리를 강제로 전부 삭제
```

#### cp

> CoPy. 파일이나 디렉터리를 복사

- 새로 복사한 파일은 복사한 사용자의 소유가 된다.
- 명령을 실행하는 사용자는 해당 파일의 읽기 권한이 필요하다.

```shell
$ cp abc.txt cba.txt	// abc.txt를 cba.txt라는 이름으로 바꿔서 복사
$ cp -r abc cda			// 디렉터리 복사
```

#### touch

> 크기가 0인 새 파일을 생성하거나 생성된 파일이 존재한다면 파일의 최종 수정 시간을 변경

```shell
$ touch abc.txt // 파일이 없는 경우 abc.txt 라는 빈 파일을 생성하고, abc.txt 파일이 있는 경우 최종 수정 시간을 현재 시간으로 변경
```

#### mv

> MoVe. 파일이나 디렉터리의 이름을 변경하거나 다른 디렉터리로 옮길 때 사용

```shell
$ mv abc.txt /etc/sysconfig // abc.txt을 /etc/sysconfig/ 디렉터리로 이동
$ mv aaa bbb ccc ddd	// aaa, bbb, ccc 파일을 /ddd 디렉터리로 이동
$ mv abc.txt www.txt	// abc.txt의 이름을 www.txt로 변경해서 이동
```

#### mkdir

> Make DIRectory. 새로운 디렉터리를 생성

- 생성된 디렉터리는 명령을 실행한 사용자의 소유가 된다.

```shell
$ mkdir abc				// 현재 디렉터리 아래에 /abc 이름의 디렉터리 생성
$ mkdir -p /def/fgh		// /def/fgh 디렉터리를 생성(p는 Parents 약자)
```

#### rmdir

> ReMove DIRectory. 디렉터리를 삭제

- 해당 디렉터리의 삭제 권한이 있어야 하고, 디렉터리는 비어 있어야 한다.
- 파일이 있는 디렉터리를 삭제하려면 **rm -r** 명령을 실행

```shell
$ rmdir abc 	// /abc 디렉터리를 삭제
```

#### cat

> conCATenate. 파일 내용을 화면에 출력

- 여러 파일을 나열하면 파일을 연결해서 출력

```shell
$ cat a.txt		// a.txt 파일의 내용을 화면에 출력
```

#### head, tail

> 텍스트 형식으로 작성된 파일의 앞 10행 또는 마지막 10행만 화면에 출력

```shell
$ head anaconda-ks.cfg		// 해당 파일의 앞 10행을 화면에 출력
$ head -3 anaconda-ks.cfg	// 앞 3행만 화면에 출력 
$ tail -5 anaconda-ks.cfg	// 마지막 5행만 화면에 출력
```

#### more

> 텍스트 형식으로 작성된 파일을 페이지 단위로 화면에 출력

- *space* 를 누르면 다음 페이지로 이동하며, *B* 를 누르면 앞페이지로 이동, *Q* 를 누르면 명령을 종료한다.

```shell
$ more anaconda-ks.cfg
$ more +30 anaconda-ks.cfg // 30행부터 출력
```

#### less

> more 명령과 용도가 비슷하지만 기능이 더 확장

- **more** 에서 사용하는 키와 더불어 화살표 키나 *PageUp*, *PageDown* 도 사용할 수 있다.

```shell
$ less anaconda-ks.cfg
$ less +30 anaconda-ks.cfg	// 30행부터 출력
```

#### file

> 파일의 종류를 표시

```shell
$ file anaconda-ks.cfg	// 텍스트 파일이므로 아스키 파일(ASCII)로 표시
$ file /dev/sr0
```

#### clear

> 현재 사용 중인 터미널 화면을 깨끗하게 지움

```shell
$ clear
```

#### 
