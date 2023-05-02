![header](https://capsule-render.vercel.app/api?type=waving&color=F49303&height=300&section=header&text=Amazent&fontSize=80&animation=fadeIn&fontAlignY=36&descSize=25&desc=Prediction%20of%20positive%20and%20negative%20Amazon%20user%20reviews&descAlignY=53&fontColor=FFFFFF)

# Amazent <a href="https://www.amazon.com/" target="_blank"><img src="https://img.shields.io/badge/Amazon-F49303?style=for-the badge&logo=Amazon&logoColor=white">
MobileBert를 활용하여 Amazon 사용자 리뷰에서 나타나는 감성을 긍부정으로 예측


## 1. 개요

   * ### 문제정의
 
     현재 우리는 인터넷을 통해 언제 어디서나 쉽게 상품을 구매할 수 있다. 이러한 형태의 상거래를 전자상거래(e-commerce)라고 한다.
  
     <a href="https://www.samsungpop.com/mobile/invest/poptv.do?cmd=fileDown&FileNm=uma_200626.html"><img width="750" alt="e-commerce" src="https://user-images.githubusercontent.com/130523834/235652059-dfc61816-33cc-47cd-8ff4-28ed1d4ec2d1.jpg">
       
     (출처: 삼성증권 포트폴리오전략팀<sup>[01]</sup>) 
  
     전자상거래는 글로벌 소매유통시장의 20% 이상을 차지하고 있는 주요 유통채널이다. 정보통신기술 발전과 스마트폰 보급 확산, 안전하고 편리한 결제시스템 발달 등으로 전자상거래가 크게 성장하였다. 코로나19가 확산되면서 전자상거래는 핵심적인 쇼핑 수단으로 부상했으며 외출이 제한된 소비자들이 온라인 쇼핑에 눈을 돌리면서 세계 곳곳에서 전자상거래 주문량이 급증했다.
  
     이러한 전자상거래의 발전으로 인해 고객들은 더욱 많은 제품을 쉽게 구매할 수 있게 되었지만, 제품의 질이나 신뢰성 등에 대한 불안감 역시 함께 증가하였다. 이러한 불안감을 해소하기 위해 고객들은 온라인으로 제품 구매 시 상품의 평점과 리뷰를 주로 참고하고 있다. 이에 따라 사용자들은 상품에 대한 자신의 경험을 리뷰로 남겨 다른 고객들에게 도움을 주며, 이는 전자상거래 업체들이 구매 후기 시스템을 운영하고 활용하는 데 큰 역할을 하고 있다.
       <hr>
  
       
     <a href="https://www.insiderintelligence.com/content/top-10-us-companies-ranked-by-ecommerce-sales"><img width="700" alt="eMarket" src="https://user-images.githubusercontent.com/130523834/235666591-65b6fb37-0b9b-432d-b1c1-972568790948.png">
       
     (출처: Market share of leading retail e-commerce companies in the United States<sup>[02]</sup>)
  
     위 그래프는 미국 내 주요 소매 전자상거래 업체의 시장 점유율을 나타낸 그래프이며 eMarketer의 자료에 의하면 Amazon이 시장의 37.8%를 차지하면서 가장 높은 시장 점유율을 보여주는 것으로 나타났다. 실제, 2위인 Walmart와 6.3%와 3위인 Apple의 3.9%와는 엄청난 격차를 보여줄 뿐 아니라 2위에서 15위까지 14개 기업의 시장 점유율을 다 합쳐도 아마존의 시장 점유율에 미치지 못하는 모습을 보여준다.
       
     Amazon은 세계적인 규모를 가진 전자상거래 업체로서, 수많은 제품과 대량의 리뷰 데이터를 보유하고 있다. 이러한 Amazon 리뷰 데이터를 분석하여 제품의 평판을 파악하고, 고객들이 원하는 제품을 더욱 정확하게 추천해주는 것은 아마존뿐만 아니라 온라인 판매 업체에게 매우 중요한 과제이다.
  
  <hr>
  
  
   * ### Amazon(전자상거래, 인터넷 유통 업체) 플랫폼에서의 리뷰가 갖는 영향
   
     전자상거래는 고객들이 상품을 선택하고 구매하는데 있어서 중요한 역할을 하며 이에 따라 온라인 판매 업체들은 높은 평점과 긍정적인 리뷰를 얻기 위해 노력하고 있다. 또한 전자상거래 업체들은 고객들의 구매 경험을 개선하기 위해 더욱 발전된 시스템과 기술을 도입하고 있다.
      
     웹을 통한 전자상거래와 정보 공유가 활발해짐에 따라 상품에 대한 리뷰 문서가 기하급수적으로 증가하였는데, 사용자들은 상품을 구매한 사이트뿐만 아니라 트위터, 블로그, 페이스북과 같은 소셜 미디어를 통해 자연스럽게 의견을 공유하고 상품 구매에 실제적인 도움을 받는다. 
    
     상품에 대한 주요 의견을 효과적인 정보의 형태로 전달하는 것이 실제 구매에 영향을 주기 때문에, Amazon은 상품 자체의 정보뿐만 아니라 상품에 대한 리뷰를 효과적으로 전달하는 것에 높은 비중을 두고 있다.
     구체적으로 상품 자체의 만족도 점수와 세부 특징별 점수를 구매자로부터 입력 받고 이들 점수를 종합하여 제공하며, 구매 예정자들이 유용하다고 평가한 리뷰나 상품 특징을 강조하여 표시한다. 
       
     이번 프로젝트에서는 Amazon 리뷰 데이터를 수집하고 분석하여 플랫폼의 장단점과 개선점을 파악하는 것을 목표로 하며, 이를 위해 Kaggle에서 제공하는 Amazon 리뷰 데이터셋을 이용하여 리뷰의 긍정 혹은 부정을 예측하는 인공지능 모델을 개발하려고 한다. 

  <hr>
       
    
## 2. 데이터

   * ### 데이터 출처
      
      이번 프로젝트에서는 Kaggle에서 제공하는 [Amazon Reviews](https://www.kaggle.com/datasets/kritanjalijain/amazon-reviews) 데이터셋을 사용하였다.
      
   * ### 데이터 소개
     
      이 데이터 세트는 Amazon 고객 리뷰, 별점, 리뷰 날짜, 제품 종류 및 피드백과 같은 다양한 Amazon Alexa 제품에 대한 데이터를 포함하고 있다. 
      
      tsv 파일이었던 데이터셋을 보기 쉽게 xlxs 형식의 파일로 전환하였다.
      
      ![image](https://user-images.githubusercontent.com/130523834/232951823-d88dd0da-576c-49e7-8959-6cc858a9710d.png)

       
   ### 입력 - 모델링 - 출력
       
       
   <hr>
       
   # References
[01] https://www.samsungpop.com/mobile/invest/poptv.do?cmd=fileDown&FileNm=uma_200626.html
[02] https://www.statista.com/statistics/274255/market-share-of-the-leading-retailers-in-us-e-commerce/
[03] 

   
   
   
