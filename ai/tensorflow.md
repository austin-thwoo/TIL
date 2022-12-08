#### 1. Anaconda 설치하기 (M1을 지원하기 시작함)
 
#### 2. 가상환경 (이름을 tf 로 함) 만들기
conda create -n __austin__(가상환경이름) anaconda
 
####3. 가상환경으로 이동 후, 텐서플로 설치 전에 pip 부터 업그레이드
conda activate __austin__(가상환경이름) ==> 가상환경 이동
pip install --upgrade pip
 
####4. 가상환경에서 텐서플로 설치
 
conda install -c apple tensorflow-deps
pip install tensorflow-macos
pip install tensorflow-metal
 
#### 4. 에러 나오면 numpy, scipy 업그레이드 (이 부분이 중요)
 
pip install numpy –-upgrade
pip install scipy --upgrade
 
####5. 설치 확인
 
$ Python
.>>> import tensorflow as tf
 .>>> tf.__version__
'2.10.0'
 
#### 6. Gym, Mujoco 설치
 
pip install pygame
conda install -c conda-forge box2d-py
pip install gym==0.24.1
pip install mujoco==2.2.0
gym==0.25.1, 0.23.1 에서는 Mujoco 오류 발생. OpenAI Gym은 0.23.1에서 잘 실행됨.
 
7. 기타 필요한 패키지 설치
 
pip install opencv-python
pip install tensorflow_probability
 