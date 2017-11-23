# R입문
* 역사: S 사용프로그램 이후 오픈소스로 개발된 R 응답형 콘솔, 

## 기본 문법
* 세미콜론( ; ) 으로 개행 사칙연산
* 변수 선언 & 값 할당 ( = , <- ), <- , < - 조심해라 변수 제거: rm()
* rm (list=ls()) # 모든 변수 삭제 변수 조회: ls()
* 벡터 생성: c()

```sql

a = c(1,2,3)
s = c("1", 2, 3) # 2, 3 도 캐릭터가 된다. 왜? 벡터는 같은 타입이므로
명칭의 유래: .. objects to be concatenated , 출처 mode() : 값의 타입 조회
mode(s) : [1] "character"
b = TRUE; mode(b) : [1] "logical" 지정어: NA, TRUE, FALSE, ...

```

## R의 데이터 타입
                            
타입 | 설명 | 예제
-----|------|---------
Factor | 범주형자료 | factor()
Vectors | 동질타입 | c(1,2,3)
matrix | 동질타입, 벡터*차원 | dim(2,3) # 2* 3의 배열
array | 동질타입, 3차원 벡터 | facotr(요인)
list | 이질적 자료 | list(x,y,z), foreach()

## data frame  
 * data.frame(), $를 사용하여 변수 추출
 * 자료입출력
 * c() : 벡터 scan()
 * what 아규먼트로 타입 지정할수 있다. 없으면 숫자형 v3 = scan(what = "") # 문
    
  *  자형
  * 옵션: file="filepath"
  * edit(객체) : 편집기를 수행시키는 함수, 객체
  * read.table() : 파일을 읽는 명령어 행렬
  * 옵션 : read.table("filepath"", sep=",") read.csv() : 콤마 파일 읽기
  * write.table(데이터프레임, "filepath")
  * 옵션: sep, row.names=F, quote=F
  * write.csv()
  * sink("filepath") # 먼저 setwd() 자료를 저장함 cat("")

## R컴퓨팅 2교시 자료조작

* 자료생성
  * rep: Replicate Elements of Vectors and Lists, 사용법: rep(x, times = 1, length.out = NA, each = 1)
  * seq: Sequence Generation, 사용법: seq(from = 1, to = 1, by = ((to - from)/(length.out - 1)),
  * rev: 거꾸로 벡터자료 함수
  * []: 원소 엑세스
* 함수들    
  * replace()
  * append()
  * sort() : 오름차순으로 자료 정렬
  * order() : 오름차순에 의한 자료 위치 출력
  * rank() : 순위함수, 동점처리할때는 중간값 1위 5개가 있으면 3찍힘.


```sql
datenew = data.frame()
datenew = edit(datenew)
                 emkbq = read.table("~/Downloads/weekend_emkbq.txt")
na.stringᄂ="miss") # miss스트링을 NA로
 emkbq$V1 # 열을 모두 출력
 emkbq$V1[0] # $열[0]행
 emkbq = read.table("~/Downloads/weekend_emkbq.txt", header = TRUE)
 emkbq = read.table("~/Downloads/weekend_emkbq.txt", header = TRUE,
         

     >v1=11:20#c() 제외 가능
 > v1
 [1] 11 12 13 14 15 16 17 18 19 20
 >v1[2]#2번째 자료 조회
 [1] 12
 > v1[2:5] # 2~5번 조회
 [1] 12 13 14 15
 > v1[c(1,3,5)] # 1,3,5번째 조회
 [1] 11 13 15
 > v1[-3] # 3제외하고 조회
 [1] 11 12 14 15 16 17 18 19 20
 > replace(v1, 2, 0) # 2번째를 0으로 바꿔라
 [1]11 01314151617181920
 > append(v1, 2) # 2를 추가해라. 끝에 삽입됨
 [1]11121314151617181920 2
 > append(v1, 2, 0) # 2를 0번째 다음에 넣어라, append(x, values, after =
 length(x))
 [1] 211121314151617181920
 > sort(v1, decreasing = T)
 [1] 20 19 18 17 16 15 14 13 12 11
 > x = c(rep(1,3), seq(1,5,2), rev(seq(1,5,length=3)))
 > order(x) # 소팅한 위치 출력
 [1] 1 2 3 4 9 5 8 6 7
 > sort(x) # 소팅한 값 출력
 [1] 1 1 1 1 1 3 3 5 5
 > rank(x)
 [1] 3.0 3.0 3.0 3.0 6.5 8.5 8.5 6.5 3.0
```


##  행렬(matrix) 함수
  * matrix() : 자료생성 rbind() : 열 추가
  * cbind() : 행 추가
  * dim() : 행과 열의 수 출력
  * dim(x)
  * dim(x) <- value
  * 행렬의 계산: % * % : %로 quote 한다.
  * apply(x, 행렬, 함수) : 함수 적용, MARGIN=1 행방향, MARGIN=2 열방향; apply(X, MARGIN, FUN, ...)
  *s weep(x, 행렬, 함수) : 함수를 각각 적용해준다; sweep(x, MARGIN, STATS, FUN = "-", check.margin = TRUE, ...)
  
  
  ```sql
> m1 = matrix(1:9, nrow=3) # 열방향으로 자료를 생성함
> m1
[,1] [,2] [,3]
[1,] 1 4 7
[2,] 2 5 8
[3,] 3 6 9
> m2 = matrix(1:9, nrow=3, byrow = T) #행방향으로 자료 생성 > m2
     [,1] [,2] [,3]
[1,]    1    2    3
[2,]    4    5    6
[3,]    7    8    9
> rbind(m2, 10:12)
     [,1] [,2] [,3]
[1,]    1    2    3
[2,]    4    5    6
[3,]    7    8    9
[4,]   10   11   12
> cbind(m2, 10:12)
     [,1] [,2] [,3] [,4]
[1,]    1    2    3   10
[2,]    4    5    6   11
[3,]    7    8    9   12
> dim(m2)
[1] 3 3
> dim(m2)
[1] 3 3
>x=1:12#x 벡터 생성
> dim(x) # 매트릭스가 아니므로, 차원 출력 불가? NULL
> dim(x) = c(3,4) # x를 매트릭스로 변환
>x
     [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
[2,]    2    5    8   11
[3,]    3    6    9   12
> x[2,3]
[1] 8
> x[c(2,3), c(3,1)]
     [,1] [,2]
[1,]    8    2
[2,]    9    3
> x[1,]
[1] 1 4 7 10
> x[,3]
[1] 7 8 9
> x[,3] > 8 # 3열에서 8보다 큰수 iteration을 돌면서 논리값 출력
[1] FALSE FALSE TRUE
> x[x[,3] > 8, 3] # 3열에서 3번째행(8번째가 True이므로) 출력, 일단, 위 조건의 논리값에 해당 하는 팩터에 따라 출력 유무 결정됨
> [1] 9
> x[x[,3] > 8, 2] # 2열에서 3번째행 출력
                                                      
    [1] 6
 >x
 [,1] [,2] [,3] [,4]
 [1,] 1 4 7 10
 [2,] 2 5 8 11
 [3,] 3 6 9 12
 > sweep(x, 2, c(1,4, 7, 10)) # 열방향으로 1,4,7, 10을 각각 빼준다.
 [,1] [,2] [,3] [,4]
 [1,] 0 0 0 0
 [2,] 1 1 1 1
 [3,] 2 2 2 2
 > sweep(x, 1, c(1,2, 3)) # 행방향으로 1,2,3d을 각각 빼준다.
 [,1] [,2] [,3] [,4]
 [1,] 0 3 6 9
 [2,] 0 3 6 9
 [3,] 0 3 6 9
 > sweep(x, 1, c(1,2, 3), "+")
 [,1] [,2] [,3] [,4]
 [1,] 2 5 8 11
 [2,] 4 71013
 [3,] 6 91215
```


## 배열(Array) 함수
 * array(): 3차원임, 행렬X행렬의 개수 ; array(data = NA, dim = length(data), dimnames = NULL)
 * [] : 행, 렬, 번째 행렬 ; ex a1[1,10,3] 3번째 행렬의 1행10열
  * dim(x) = c(2,2,3) ; x는 12개의 백터였는데, 2x2 3개로 어레이로 변환
```sql

> a1 = array(1:15, c(2,2,3)) #배열 생성, 1번째 자료, 2x2행렬 3개
,,2
,,3
 > a1
 ,,1
 [,1] [,2]
[1,] 1 3
[2,] 2 4
[,1] [,2]
[1,] 5 7
[2,] 6 8
[,1] [,2]
[1,] 9 11
[2,] 10 12
> a1[2,1,3] # 3번째 행렬의 2, 1 값
 [1] 10
 > x = 1:12
 > dim(x) = c(2, 2, 3)
 >x
 ,,1
 [,1] [,2]
[1,] 1 3
[2,] 2 4
,,2
,,3
[2,] 10 12
[,1] [,2]
[1,] 5 7
[2,] 6 8
[,1] [,2]
[1,] 9 11
 
```   
