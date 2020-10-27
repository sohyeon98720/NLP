# NLP - 시대,장르별 추천 가사생성
### 자연어처리 과목 팀프로젝트(2020.09~진행중)
-------


### 일정

 - [x] 데이터 수집 (~10.22)
 - [x] 전처리
 - [ ] 모델학습
 - [ ] 검증 및 테스트

-------
### description

다음과 같이 '시대','장르'를 입력하면 해당 시대와 장르에 맞춘 추천 가사를 생성해주는 모델 <br>
`'2019',''발라드` -> 

--------


### data structure
|년도|가수|제목|남녀|장르|최고순위|작사가|작곡가|소속사|가사|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|20170324|아이유|밤편지|female|발라드|52|아이유|아이유|EDAM엔터테인먼트|이 밤 그날의 반딧불을...|

*수집한 데이터 예시. 여기서 **필요한 column(년도, 장르, 가사)만 추출**하여 사용하였음.*

----------

### generator

`code`

----------

### output sample

-----------

### reference
https://github.com/KMJJ1/hiphop
