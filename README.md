# 지하철 유동인구 분석 웹사이트


# 개요


서울시 지하철 유동인구 데이터를 활용하여 지하철 유동인구 분석 웹사이트 구현
- [일별 데이터](https://data.seoul.go.kr/dataList/OA-12914/S/1/datasetView.do)
- [시간대별 데이터](https://data.seoul.go.kr/dataList/OA-12252/S/1/datasetView.do)

위 두 데이터를 활용하여 지하철 유동인구를 분석 및 시각화


## 기대효과
- 지하철 유동인구 분석을 통해 지하철 유동인구에 따른 상권 분석
- 출퇴근 시간에 유동인구가 많은 지하철역을 인지하여, 인프라 개선 

## 시연

https://user-images.githubusercontent.com/43350428/236599476-24bc3b55-5cfb-4952-aead-6fdbc110ead6.mp4




## 팀 구성
|    | 이동수 | 최민수 | 박주미 | 전성현 | 명우성 |
| :---: | :---: | :---: | :---: | :---: |:---: |
| 역할 | PM <br> 백엔드 | 크롤러 자동화 <br> 백엔드 | 프론트엔드 <br> 백엔드 | DB 구축 <br> 데이터 적재 | 데이터 분석 <br> 시각화 |
|GitHub| [@TonysHub](https://github.com/TonysHub) | [@usiohc](https://github.com/usiohc) | [@swanim](https://github.com/swanim) | [@Jeon-peng](https://github.com/Jeon-peng) | [@LameloBally](https://github.com/LameloBally)


# Tech

| 분야  | Tools  |  
| ---- | ---- |
| 프론트엔드 | <img src="https://img.shields.io/badge/html-F05132?style=for-the-badge&logo=html5&logoColor=black"> <img src="https://img.shields.io/badge/css-61DAFB?style=for-the-badge&logo=css3&logoColor=black"> | 
| 백엔드 | <img src="https://img.shields.io/badge/Django-173B0B?style=for-the-badge&logo=django&logoColor=white"> |
| 데이터베이스 | <img src="https://img.shields.io/badge/sqlite-4479A1?style=for-the-badge&logo=sqlite&logoColor=white">  |
| 크롤링 | <img src="https://img.shields.io/badge/-selenium-%43B02A?style=for-the-badge&logo=selenium&logoColor=white">
| 분석 & 시각화 | <img src="https://img.shields.io/badge/Plotly-%233F4F75.svg?style=for-the-badge&logo=plotly&logoColor=white">
| 코드 관리 |  <img src="https://img.shields.io/badge/github-181717?style=for-the-badge&logo=github&logoColor=white"> |

## Database

## 구조

![Screenshot 2023-05-06 at 1 19 24 PM](https://user-images.githubusercontent.com/43350428/236599483-acad43a9-97ee-40cc-926c-f5143bf107ea.png)


### index
![Screenshot 2023-05-06 at 1 22 33 PM](https://user-images.githubusercontent.com/43350428/236599564-62595650-8baf-4e9e-b83c-6c37a55cae72.png)

 
### line_details
![Screenshot 2023-05-06 at 1 22 50 PM](https://user-images.githubusercontent.com/43350428/236599577-7dc44a34-cc91-49dd-bd9c-62f5e0f10dd6.png)


### station_details
![Screenshot 2023-05-06 at 1 23 07 PM](https://user-images.githubusercontent.com/43350428/236599584-0dfb2b00-4c4c-4567-ab27-8c5773d6dc99.png)


### Database ERD
![image](https://user-images.githubusercontent.com/70497132/236601348-b0760061-341a-40ed-849a-698d55bee7fc.png)


<br><br><br>

# Setting up Python version to 3.10.0

Check if you have pyenv installed
```
$ pyenv --version
```


## Setup
#### Getting pyenv

**Skip this step if you already have pyenv**

```
$ update brew
$ brew install pyenv
$ open ~/.zshrc
```

Add the following lines to ~/.zshrc or ~/.zprofile for zsh.
For bash, add to ~/.bash_profile or ~/.profile

```
export PYENV_ROOT="$HOME/.pyenv"
command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
```
#### Clone project
Move to your project DIR
```
$ git clone https://github.com/TonysHub/subway.git
```



#### Install Python version


At your home DIR,
```
$ pyenv install 3.10.0
```
Open project DIR
```
$ pyenv shell 3.10.0

# check python version at this point
$ python3 --version
>>> Python 3.10.0
```

#### Setup venv
At your project DIR (~/subway)
```
$ python3 -m venv venv
$ source venv/bin/activate
$ pip3 install -r requirements.txt
```

Now our setup is good to go :)

# Project Git Convention
## What to do before you start coding
Open your local directory
```
$ git pull
```
if there's a conflict, try
```
$ git stash
$ git pull
$ git stash pop
```
if there's still a conflict, try
```
$ git reset --hard
$ git pull
```
Check which branch you are on
```
$ git branch
```
If you are not on the branch you want to be on, try
```
$ git checkout <branch_name>
```
If you want to create a new branch, try
```
$ git checkout -b <branch_name>
```

## What to do after you finish coding
Check which files you have changed
```
$ git status
```
Add the files you want to commit
```
$ git add <file_name>
```
Commit the files
```
$ git commit -m "<commit_message>"
```
Push the files to your branch
```
$ git push origin <branch_name>
```
If you want to merge your branch to the main branch, go to github and create a pull request :)

## Branch naming convention
Branch name should be in lower case and separated by underscore. Your initials at the beginning, and select from [feature, bugfix, refactor, etc] for the middle part. The last part should be the feature name.

Ex. 
```
git branch -b lds_feature_datascrapping
```

## Commit message convention
commit_message should be concise and imply what you have done. If you are fixing a bug, start with "fix: ", if you are adding a feature, start with "add: ", etc.

Ex.
```
git commit -m "fix: fix bug in datascrapping"
```

# Database Setup

1. migrations 폴더에 있는 __init__.py 제외 모든 파일 삭제
2. db.sqlite3 삭제
-> 데이터베이스가 기존것과 중복으로 오류가 날 수 있기 때문에 삭제 후 사용하시는 것을 추천
`$ python manage.py makemigrations`
`$ python manage.py migrate`

## 데이터베이스 확인하기

`$ python manage.py dbshell`
`>>> .table`
sql 사용하여 각 테이블 확인하기


## crontab 사용법

requirements.txt 실행

작업 등록
`$ python manage.py crontab add`

작업 등록 확인
`$ python manage.py crontab show`

작업 삭제
`$ python3 manage.py crontab remove`

등록한 작업 id값으로 그냥 실행 (id 값은 show했을때 나오는 id값)
`$ python3 manage.py crontab run <hash_id>`
