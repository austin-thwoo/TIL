
###ANACONDA 명령어 List
conda activate : 아나콘다 on!!!
conda deactivater : 아나콘다down!!!
conda config --set auto_activate_base False : 아나콘다 자동 설정 OFF
onda env list : 가상환경 목록 보기
conda create -n <가상환경이름> python=<버젼> : 가상환경 생성 ex) conda create -n TestEnv python=3.7
conda env remove -n <가상환경이름> : 가상환경 삭제
conda activate <가상환경이름> : 가상환경 실행
conda deactivate : 가상환경 종료
conda list : 현재 가상환경에서 설치되어있는 패키지 보기
conda install <패키지 이름> : 현재 가상환경에서 패키지 설치
ex1) conda install numpy
ex2) conda install numpy pandas
ex3) conda install tensorflow-gpu==1.13.1
conda uninstall <패키지 이름> : 현재 가상환경에서 패키지 삭제
 
conda create --name <복사하여 생성할 가상환경명> --clone <복사할 가상환경명> :
ex) conda create --name NewProject --clone OldProject : OldProject를 복사하여 NewProject로 생성함
conda env create --file <yml파일명.yml or yaml> : yml/yaml로 가상환경 생성
ex) conda env create --file environment.yml
conda env update --file <yml파일명.yml or yaml> --prune : yml 덮어쓰기 (activate상태에서 사용가능)
ex) conda env update --file environment.yml --prune
conda env create -f <yml파일명.yaml or yaml> , conda env export > <yml파일명.yml> : 현재 가상환경의 yml 생성
ex) conda env create -f environment.yml
ex) conda env export > environment.yaml
 
python --version : 파이썬 버전 확인
 
nvidia-smi : 드라이버 정보 표시 (+ CUDA 버전 표시)



###error
>>> import tensorflow as tf
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ModuleNotFoundError: No module named 'tensorflow'
해결
[https://magoker.tistory.com/114 ]
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/apple/tensorflow_macos/master/scripts/download_and_install.sh)"

tensorflow
https://pasus.tistory.com/218