# SQL 스터디
* 광고 업무와 SQL을 익히기 위한 스터디

## Setup
 * SQLGateway () download
 * kwdad 계정 신청
 * ngela 계정 신청
  
 

## 광고서비스 데이터베이스 (kwd_ad db)
* 광고서비스 데이터베이스 = Oracle, KWDAD

* naming convention 
  * 테이블명은 tb_ + 엔티티명 
  * PK는 엔티티명 + _id (예외인 경우 있음) 

* 광고주 엔티티

 이름 | 테이블명 | FK |  비고 
 ----|--------|-----|----
  사용자  | tb_user | | 네이버 login_id 가 주로 사용된다. 
  광고주 | tb_customer | user_id | 광고주 정보 | 
  광고주속성 | tb_customer_attr | customer_id| 광고주 추가 속성  | 



* 광고 정보

 이름 | 테이블명 | FK |  비고 
 ----|--------|-----|----
  사업채널 | tb_ncc_business_channel | customer_id, reference_key| 광고를 통해 연결할 목적지
  캠페인 | tb_ncc_campaign | customer_id |  캠페인타입(광고상품), 캠페인기간
  광고그룹 | tb_ncc_adgroup | ncc_campaign_id, (pc, mobile)_channel_id | 전략, 집행단위 
  광고|  tb_ncc_ad | ncc_adgroup_id, reference_key | 메인소재, 
  키워드타겟팅 |tb_ncc_keyword  | ncc_adgroup_id / 노출할 키워드, 입찰가
  광고 확장소재 | tb_ncc_ad_extension | (pc, mobile)_channel_id | 부소재

* reference_key 는 반정규화한 중복정보를 가르키기 위한 컬럼

* 키워드 관련 테이블
 
 
  이름 | 테이블명 | UK | FK | 비고
  ----|--------|-----|----|----
 관리키워드 | tb_managed_keyword | keyword | - | 
 광고키워드  | tb_keyword | keyword_id | - | deprecated
 추천검색어-대표키워드 | tb_keyword_rep  | - | - |  
 추천검색어-확장키워드 | tb_keyword_rep_relation | - | - | 
 

## nbig 테이블
 * hive를 사용한 지표데이터
 * 

### Data Layer
 * Log => lumbers => Primitive => Stat, DW
 * RDB => meta 
 * StreamSet => his 
 
## 실습  
 
### 1일차 : select 사용
 * SqlGateway 광고테이블 질의 
 * nBig 지표 테이블 질의 
 * where 조건으로 특정 key만 가져오기
 * where 조건으로 기간 한정 


### 2일차 : fk를 활용한 join
  * 로그인 아이디 () 를 사용하여 광고주 구매 키워드를 알아내라
  
### 3일차 : 집합함수
 * nBig 지표테이블 간 조인 (기간: 일주일, 평균, 합계)
 * nBig 메타 + 지표 테이블 조인 (1번에 메타의 속성값 붙이기)
 * 키워드 지표 테이블 + 광고 지표 테이블 조인 (차원이 다른 테이블간 조인)
 
 
### 4일차:  join
 * inner join, left join, full outer join 해보기
 * anti pattern
 * nbig에서 그래프 그려보기
 * 튜닝
  
### 5일차: 실례 (몇개 가져오자.)
 * 
 * 
 * 