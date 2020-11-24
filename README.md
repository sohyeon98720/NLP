# NLP - 시대,장르별 추천 가사생성
### 자연어처리 과목 팀프로젝트(2020.09~진행중)
-------


### 일정

 - [x] 데이터 수집 (~10.22)
 - [x] 전처리 (~11.12)
 - [x] 모델학습 (~11.23)
 - [x] 검증 및 테스트 (~11.25)

-------
### description

다음과 같이 **'시대','장르','키워드'를 입력**하면 해당 시대와 장르에 맞춘 **추천 가사를 생성**해주는 모델 <br>
`'2011-2019',''발라드','사랑'` -> `사랑하지 않아 다른 이유는 ...`
 - 시대는 `1990-2000`,`2001-2010`,`2011-2019`로 분류하였음
 - 장르는 `R_B_Soul`, `댄스`, `랩_힙합`, `록_메탈`, `발라드`, `인디음악`, `포크_블루스`로 분류하였음

--------


### 데이터 수집
|년도|가수|제목|남녀|장르|최고순위|작사가|작곡가|소속사|가사|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|20170324|아이유|밤편지|female|발라드|52|아이유|아이유|카카오M|이 밤 그날의 반딧불을...|

*수집한 데이터 예시. 여기서 **필요한 column(년도, 장르, 제목, 가사)만 추출**하여 사용하였음.* <br>
 - 제목 컬럼은 데이터확인을 위해 제거하지 않음
 - 실제로 학습에 쓰이는 컬럼은 **가사**뿐임
<!--
- 총 수집한 데이터의 갯수: <br>
- 전처리 후 데이터의 갯수: 
  - 전처리는 ~
-->
-----------
### 데이터 전처리
|전처리 과정|예시|
|:---:|:---:|
|1. '년도'컬럼의 필요한 부분만 추출| `20170324` -> `2017`|
|n. 필요한 column만 추출|`년도,가수,제목,남녀,장르,최고순위,작사가,작곡가,소속사,가사` -> `년도,장르,제목,가사`|

----------

### generator

`code`

----------

### output sample
`사진`

----------
### reference
https://github.com/gyunggyung/KoGPT2-FineTuning <br>
<!--
https://github.com/KMJJ1/hiphop <br>
https://hellya.tistory.com/96 <br>
https://github.com/jx2lee/lyric-generator
>
