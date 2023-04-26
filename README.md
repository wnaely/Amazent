<div align="center">

![header](https://capsule-render.vercel.app/api?type=waving&color=F49303&height=300&section=header&text=Amazent&fontSize=80&animation=fadeIn&fontAlignY=38&descSize=25&desc=Prediction%20of%20positive%20and%20negative%20Amazon%20user%20reviews&descAlignY=55&descAlign=62)
</div>

# Amazent <a href="https://www.amazon.com/" target="_blank"><img src="https://img.shields.io/badge/Amazon-F49303?style=for-the badge&logo=Amazon&logoColor=white">
MobileBert를 활용하여 Amazon 사용자 리뷰에서 나타나는 감성을 긍부정으로 예측


## 1. 개요

   * ### Alexa에 대해서
   
      Amazon Alexa는 Amazon에서 개발한 음성 인식 가상 비서이다. 이 기술은 사용자의 음성 명령을 이해하고 처리하여 다양한 작업을 수행한다.
   
      Alexa는 자연어 처리(NLP), 음성 인식 기술 등의 인공지능 기술을 활용하여 일정 관리, 홈 제어 등 다양한 기능을 제공하며 의료 서비스나 항공편 예약과 같은 다양한 분야에서 활용되고 있다.
   
      Alexa의 API 서비스는 "Alexa Skills Kit"이라는 이름으로 제공되며, 이를 활용하여 개발자는 Alexa의 기능을 확장하거나 자신의 스킬을 개발할 수 있다.
   
      Alexa는 사용자의 음성 명령을 처리하기 위해 녹음 데이터를 수집함으로 Amazon은 사용자의 보안과 개인 정보 보호를 위해 다양한 보안 및 개인 정보 보호 정책을 시행하고 있다. <hr>
      

   * ### 문제정의
   
      음성 인식 기술은 많은 분야에서 매우 빠르게 발전하고 있으며, 사회나 산업적으로도 큰 영향을 미치고 있다. 또한 이러한 기술의 발전으로 우리의 삶은 더욱 편리하고 효율적으로 바뀌고 있다.
      
      이번 프로젝트에서는 Alexa를 사용하는 사람들의 의견을 수집하고 분석하여 제품의 장단점과 개선점을 파악하는 것을 목표로 하며, 이를 위해 Kaggle에서 제공하는 Amazon Alexa 리뷰 데이터셋을 이용하여 리뷰의 긍정 혹은 부정을 예측하는 인공지능 모델을 개발하려고 한다. <hr>
      

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
   
   
   
