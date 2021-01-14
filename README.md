# NLP - 실습정리 / 팀프로젝트(시대,장르별 추천 가사생성)
### 자연어처리 팀프로젝트(2020.09~2020.11)
-------


### 일정

 - [x] 데이터 수집 (~10.22)
 - [x] 전처리 (~11.12)
 - [x] 모델학습 (~11.23)
 - [x] 검증 및 테스트 (~11.25)

-------
### 주제

다음과 같이 **'시대','장르','키워드'를 입력**하면 해당 시대와 장르에 맞춘 **추천 가사를 생성**해주는 모델 <br>
-> 뉴트로 마케팅에 이용
`'2011-2019',''발라드','사랑'` -> `사랑하지 않아 다른 이유는 ...`
 - 시대는 `1990-2000`,`2001-2010`,`2011-2019`로 분류하였음
 - 장르는 `R_B_Soul`, `댄스`, `랩_힙합`, `록_메탈`, `발라드`, `인디음악`, `포크_블루스`로 분류하였음

--------


### 데이터 수집
|년도|가수|제목|남녀|장르|최고순위|작사가|작곡가|소속사|가사|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|20170324|아이유|밤편지|female|발라드|52|아이유|아이유|카카오M|이 밤 그날의 반딧불을...|

*수집한 데이터 예시. 여기서 **필요한 column만 추출**하여 사용하였음.* <br>

-----------
### 데이터 전처리
|전처리 과정|예시 or 비고|
|:---:|:---:|
|1. '년도'컬럼의 필요한 부분만 추출후 년도별 데이터 분리| `20170324` -> `2017`|
|2. 2020년도 데이터 삭제|2020년도 노래는 뉴트로 마케팅이라는 프로젝트의 목적에 부합하지 않음|
|3. 년도, 장르, 가사가 비어있는 행 삭제|`df=df[df[가사] != None]`|
|4. 가사가 중복되는 remix곡 외 다수 삭제|inst, remix, mix, ment, ver 이 해당|
|5. 공백, 괄호 및 멤버별 가사파트 삭제|정규표현식 활용|
|6. 필요한 column만 추출|`년도,가수,제목,남녀,장르,최고순위,작사가,작곡가,소속사,가사` -> `년도,장르,제목,가사`|
|7. 장르별 데이터 분리 및 주제에 맞지 않는 장르 제거|`랩/힙합, 중국음악, 인디음악, 키즈, 재즈, 국내드라마, R&B/Soul, 만화, 국내영화, 발라드, 댄스, 록/메탈, 포크/블루스, 국외드라마, 애시드/퓨전/팝, POP, 애니메이션/웹툰, 성인가요, 게임, 일렉트로니카, 월드뮤직, J-POP` -> `랩/힙합, 인디음악, R&B/Soul, 댄스, 록/메탈, 포크/블루스`|
|8. 년도, 장르별 데이터 저장|-|

----------

### 학습

```sh
python main.py --epoch=200 --data_file_path=dataset/2010-2019_댄스.tsv --save_path=./checkpoint/ --load_path=./checkpoint/~~~.tar batch_size=1
```
+더 많은 파라미터 조정에 대해서는 참고자료 이용

-------

### 가사생성

```sh
python generator.py --temperature=1.0 --load_path='./checkpoint/~~~.tar' --tmp_sent='사랑'
```
+더 많은 파라미터 조정에 대해서는 참고자료 이용

----------

### 기술시연

`2011-2019` + `댄스` 데이터로 학습후 `temperature=1.0` `tmp_sent='사랑'`으로 생성한 문장 예시
<img src="https://user-images.githubusercontent.com/47767202/103736445-9d724d00-5033-11eb-9120-6b650c421fa9.png">

----------
### 참고자료
https://github.com/gyunggyung/KoGPT2-FineTuning <br>
<!--
https://github.com/KMJJ1/hiphop <br>
https://hellya.tistory.com/96 <br>
https://github.com/jx2lee/lyric-generator
>
