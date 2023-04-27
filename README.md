![header](https://capsule-render.vercel.app/api?type=waving&color=F49303&height=300&section=header&text=Amazent&fontSize=80&animation=fadeIn&fontAlignY=38&descSize=25&desc=Prediction%20of%20positive%20and%20negative%20Amazon%20user%20reviews&descAlignY=55&fontColor=FFFFFF)

# Amazent <a href="https://www.amazon.com/" target="_blank"><img src="https://img.shields.io/badge/Amazon-F49303?style=for-the badge&logo=Amazon&logoColor=white">
MobileBert를 활용하여 Amazon 사용자 리뷰에서 나타나는 감성을 긍부정으로 예측


## 1. 개요

   * ### 문제정의
   
      아마존(전자상거래, 인터넷 유통 업체) 플랫폼에서의 리뷰가 갖는 영향
      
      전자 상 거래를 우리는 자주 사용하고 있다
      언제 어디서나 인터넷으로 물건을 살 수 있다
      하지만 그중에 평점은 중요한 역할을 하고 있다
      그러므로 리뷰시스템이 잘 잡혀있고 
      잘 활용이 되며 유용하게 쓰여지고 있다.
      
      아마존 리뷰로 그런것들을 분석해보려고 한다.
      
   
      음성 인식 기술은 많은 분야에서 매우 빠르게 발전하고 있으며, 사회나 산업적으로도 큰 영향을 미치고 있다. 또한 이러한 기술의 발전으로 우리의 삶은 더욱 편리하고 효율적으로 바뀌고 있다.
      
      이번 프로젝트에서는 Alexa를 사용하는 사람들의 의견을 수집하고 분석하여 제품의 장단점과 개선점을 파악하는 것을 목표로 하며, 이를 위해 Kaggle에서 제공하는 Amazon Alexa 리뷰 데이터셋을 이용하여 리뷰의 긍정 혹은 부정을 예측하는 인공지능 모델을 개발하려고 한다. <hr>
      
      가상비서 점유율 그래프
      비중을 차지하고 있고 시장을 이만큼 차지하고 있다.
      스마트 시장이 커지고 있는 상황에서 아마존 알렉사 리뷰를 분석하는 것을 
      통해서 리뷰에 대한 긍부정을 분석하려고 한다.
      
      아마존의 플랫폼으로써의 가치
      이런 점이 구매에 끼치는 영향

      

   * ### Amazon Alexa 사용자 리뷰의 영향력
   
      Amazon Alexa 사용자 리뷰는 Alexa를 사용한 사용자들의 경험과 평가를 담고 있는 정보이다. 이러한 리뷰들은 다른 소비자들이 제품을 구매하기 전에 제품에 대한 정보와 평가를 확인할 수 있는 유용한 참고 자료가 된다. 
      
      Amazon Alexa 리뷰는 제품 개발과 개선에도 큰 도움이 된다. 제품에 대한 피드백을 제공하고, 문제점이나 개선사항을 전달함으로써 제품 개발자들은 소비자들의 요구에 더욱 부합하는 제품을 개발할 수 있다. 또한 기업이 제품 마케팅 전략을 수립하는 데에도 활용되는데 제품의 장점이나 단점을 파악하고, 이를 고려하여 마케팅 전략을 수립함으로써 기업은 더욱 효과적인 제품 홍보와 판매를 할 수 있다.
      
      따라서 Amazon Alexa 사용자 리뷰는 소비자들과 기업 간의 소통을 원활하게 하고, 제품의 품질과 개발을 더욱 효율적이게 해주는 중요한 역할을 한다.
      
      
    
## 2. 데이터

   * ### 데이터 출처
      
      이번 프로젝트에서는 Kaggle에서 제공하는 [Amazon Reviews](https://www.kaggle.com/datasets/kritanjalijain/amazon-reviews) 데이터셋을 사용하였다.
      
   * ### 데이터 소개
     
      이 데이터 세트는 Amazon 고객 리뷰, 별점, 리뷰 날짜, 제품 종류 및 피드백과 같은 다양한 Amazon Alexa 제품에 대한 데이터를 포함하고 있다. 
      
      tsv 파일이었던 데이터셋을 보기 쉽게 xlxs 형식의 파일로 전환하였다.
      
      ![image](https://user-images.githubusercontent.com/130523834/232951823-d88dd0da-576c-49e7-8959-6cc858a9710d.png)

       
   ### 입력 - 모델링 - 출력
   
   
   
