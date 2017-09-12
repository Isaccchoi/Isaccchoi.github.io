### pyenv
프로젝트별로 **python버전**을 관리하기 위해 사용 함 


방향키 관련 이슈가 일어날 수 있기 때문에 하기 명령어로 readline 및 xz를 설치 한다
```
brew install readline xz
```

[Pyenv - Github](https://github.com/pyenv/pyenv/wiki/Common-build-problems)

pyenv global [python version]
시스템에서 사용하는 python에 대한 버전을 pyenv에서 설치한 버전으로 변경

---

### virtualenv 
프로젝트별로 Python **개발환경** *(python 패키지 설치 환경)*을 관리하기 위해 사용 함


---


### pyenv-virtualenv
pyenv 제작자가 pyenv 사용시 virtualenv 사용이 편리하도록 만듬

pyenv에서 python 버전 다운로드 이후 
```
pyenv virtualenv [python version] [virtualenv name]
```
을 입력 하여 새로운 virtualenv를 만든다

그다음 작업하길 원하는 디렉토리에 들어가 ```pyenv local [virtualenv name] ```을 입력하여 해당 디렉토리에서 pyenv-virtualenv를 적용한다 


---


