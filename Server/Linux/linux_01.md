

### 터미널에서 시스템 종료 명령

```shell
$ poweroff
$ shutdown -P now
$ halt -p
$ init 0

$ shutdown -P +10 // 10분 후에 종료(power off)
$ shutdown -r 22:00 // 오후 10시에 재부팅(reboot)
$ shutdown -c // 예약된 shutdown 명령을 취소(cancel)
$ shutdown -k +15 // 현재 접속한 사용자에게 15분 후에 종료된다는 메시지를 보내지만, 실제로 종료하지는 않음
```

- 표식이 # 이면 root 사용자, $ 이면 일반 사용자



### 시스템 재부팅

```shell
$ shutdown -r now
$ reboot
$ init 6
```

