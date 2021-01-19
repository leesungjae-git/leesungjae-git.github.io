---
title: 2021-01-19_docker
category: Deep Learning
order: 2
---

# Docker란 무엇인가?  
[출처](https://89douner.tistory.com/96?category=878197) : https://89douner.tistory.com/96?category=878197  

### 1. pytorch 컨테이너 만들기  
1) docker image 찾기 - pytorch와 관련된 image 검색  
'''
docker search pytorch
'''  

2) docker image 다운로드  
'''
docker pull pytorch/pytorch
'''  

3) image 확인  
'''
docker images
'''  

4) container 만들기  
'''
docker run -itd --name pytorch -v /home/myadress:/root/share -p 8888:8888 --restart=always pytorch/pytorch
'''  

- -v명령어 : myaddress(local folder)를 docker의 /root/share 폴더와 연결해준다.  
- -p : local의 8888포트를 docker의 8888포트와 연결해준다.  
- --restart=always : docker가 재실행될 때 docker 자동 run.  

5) container 실행  
'''
docker exec -it pytorch bash
'''  

### 2. jupyter notebook 설치 및 실행  
1) jupyter 설치  
'''
conda install jupyter
'''  

2) jupyter 실행  
'''
jupyter notebook --ip=0.0.0.0 --port=8888 --allow-root
'''  
* jupyter notebook base dir : root/share  


