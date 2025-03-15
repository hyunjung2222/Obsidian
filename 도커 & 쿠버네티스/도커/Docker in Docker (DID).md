Docker Container 안에 Docker를 설치하고 사용하기

Container 내부에 Docker CLI를 설치한 후, 이미 호스트에 설치된 docker.sock 에 접근하는 방식으로 호스트의 Docker daemon으로 Docker build 작업을 수행할 수 있음

# DID 사용하는 방법
- Docker 명령어 실행이 필요한 컨테이너를 실행할 때 아래 옵션을 추가하기
- Container가 실행되는 기존 docker run 명령어에 위와 같이 호스트의 docker.sock 파일 경로를 container 내부의 동일한 경로에 복사하는 -v 옵션을 추가
- 추가로 해당 container 내부에 docker CLI를 설치하면, container 내 터미널 환경에서 docker 명령어를 바로 수행할 수 있게 됨
```bash
docker run -v /var/run/docker.sock:/var/run/docker.sock.....
```

## DID 보안 문제
- container 내부의 Docker CLI가 호스트에 설치된 Docker demon을 사용함
- -> container 안으로 접근만 할 수 있다면 호스트의 Docker demon을 제한없이 사용할 수 있음
- 이를 외부에서 악용하면 심각한 보안 이슈가 발생할 수 있음
- [배포한 컨테이너 보안 높이기](https://maily.so/newslettertodevops/posts/edb58667)
