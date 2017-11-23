# 온라인 옥션 이론
 * 정승원(영국 브리스톨대 교수)
  
### Market Design 학문
 - 시장의 제도를 모델링하고 개선
 - 제도 = 메커니즘 = 예: 옥션, 매칭, ...
 - 

## 목차
   Auction 101 (First-Price, Second-Price, English, Dutch Auctions)
   Online Advertising Auctions
   Generalized Second-Price (GSP) Auctions (Google)
   Vickrey-Clarke-Grove (VCG) Auctions (Facebook)
   Incentive Compatibility of VCG and GSP 

## 101
 * Sealed Bid 
   * First Price
   * Second Price : 전략을 고민하지 않는 = truth telling
   * VCG : 멀티 아이템의 second price
 * Dynamic (open) Bid
  * English : 미술품 경매, 높은 가격 (유사 = second price auction)
  * Dutch : 농산물 경매, 낮은 가격으로 가다가 결정, 가격 결정이 빠르다 (유사 = First price auction)
 * Best method => "Best"의 정의를 먼저 내리자.
  * Revenue maximization
    - 이상적인 가정(bidder의 표준분산 환경)하에서, 옥션의 종류와 상관없이 이익이 동일하다.
    - 실제에서는 Fist Price, bidder가 위임받은 경우라면, 그냥 책임한도 내에서 지른다.
  * Efficiency 
    - allocation(할당) 배당의 효율
  * Stability (Fairness)
    - 
  * Incentive Compatibility (Strategy-proofness)
    * 전략을 고민하지 않고 해당 가치를 지름
    
  * Individual Rationality 
    * 개별적인 연관성 = 외부효과중 하나, 경쟁사, 경쟁팀..  

## 광고시장 규모 
  * emarketer.com 에서 함 찾아보자
  * google => keyword
  * facebook => demographics + 관심사 기반 매
  
## GSP
 * 장점:
 * 단점: Incentive Compatibility 하지 않는다. => 1위 먹기 보다는 2위 먹는다. ()
 
## VCG
 * 
 * 장점: Incentive Compatibility 하다
 * 외부효과에 대한 금액도 계산, second price이다. 나 없을때 가격 (내 낙찰가 - 나 없을때 낙찰가)
 * 단점: 계산이 복잡하다.
 
 * AE: 광고효과
 * PE: 위치효과
 * AE가 좋은가 PE가 좋은가? : PE 계산이 더 쉽다.
 
## Actions with Extensidisle (외부효과에 의한 경매)
 * 