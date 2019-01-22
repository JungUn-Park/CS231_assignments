*구글 클라우드 개발환경 만들기*

0. 구글 클라우드 인스턴스를 시작한다.

1. 아래의 코드를 모두 따라친다.
```
1) sudo apt-get update && sudo apt-get install wget
2) wget http://cs231n.github.io/assignments/2018/spring1718_assignment1.zip
3) sudo apt-get install unzip
4) unzip spring1718_assignment1.zip
5) cd assignment1
6) ./setup_googlecloud.sh
```

2. 미니콘다를 설치한다.
```
1) wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
2) bash Miniconda3-latest-Linux-x86_64.sh
3) 계속해서 설치 프로그램이 뭘 물어보면 yes라고만 하면 됨. 
4) 이제 구글 클라우드 인스턴스를 껐다 켜면 conda command가 활성화된다.
``` 

3. conda를 이용해 필요한 프로그램을 깔아 놓는다.
```
conda install tensorflow
conda install pytorch
conda install keras
conda install matplotlib
conda install sklearn
등등
```

4. 외부 ip 설정하기 (google cloud tutorial에 설명되어 있는 그대로 하면 됨)

5. Firewall rule 설정하기 (google cloud tutorial에 설명되어 있는 그대로 하면 됨)

6. Jupyter notebook 실행환경 구성하기
```
0) 앞의 모든 것들이 이미 완료되어 있어야 함.
1) 홈에서 jupyter notebook --generate-config
2) config파일이 만들어지면, 어떤 경로에 만들어졌는지 바로 위에 뜨는데, 그 경로는 보통 home/<유저네임: 저의 경우엔 jungjaehoon>/.jupyter/ 이다.
3) vim jupyter_notebook_config.py
4) 파일이 열리면 i를 눌러서 커서를 맨 앞에 둔 다음 아래의 코드를 친다.
c = get_config()
c.NotebookApp.ip = '0.0.0.0' 
c.NotebookApp.open_browser = False
c.NotebookApp.port = 7000
5) esc를 누르고 :wq! 를 치면 그 파일의 변경사항이 저장된다.
```

7. jupyter notebook 런칭하기
```
1) cd ..  를 침으로써 home으로 이동한다. 
2) jupyter-notebook --no-browser --port=7000
3) http://<external-ip>:7000 을 자신이 사용하는 브라우저에 쳐서 접속이 되는지 확인한다. 만약 안 된다면 인스턴스를 한 번 종료했다가 켜보는 것도 방법이다.
4) 거기서 암호를 설정하려면 token을 넣으라는 말이 나온다. token을 확인하는 방법은 아래의 코드를 home에서 쳐보는 것이다.
jupyter notebook list
5) 그러면 Currently running servers:
http://0.0.0.0:7000/?token=어쩌구 저쩌구가 나오는 것을 확인할 수 있다. 여기에 있는 토큰을 복사해서 암호를 만들면 다음번부터 jupyter-notebook --no-browser --port=7000 치고, 웹 브라우저에 http://<자기 external ip>:7000치고, 암호 넣으면 사용할 수 있다!
```

8. 구글 클라우드 인스턴스를 종료한다.
