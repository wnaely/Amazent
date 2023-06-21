![header](https://capsule-render.vercel.app/api?type=waving&color=F49303&height=300&section=header&text=Amazent&fontSize=80&animation=fadeIn&fontAlignY=36&descSize=25&desc=Prediction%20of%20positive%20and%20negative%20Amazon%20user%20reviews&descAlignY=53&fontColor=FFFFFF)

# Amazent <a href="https://www.amazon.com/" target="_blank"><img src="https://img.shields.io/badge/Amazon-F49303?style=flat&logo=Amazon&logoColor=white">
MobileBert를 활용하여 Amazon 사용자 리뷰에서 나타나는 감성을 긍부정으로 예측


## 1. 개요

   * ### 문제정의
 
     현재 우리는 인터넷을 통해 언제 어디서나 쉽게 상품을 구매할 수 있다. 이러한 형태의 상거래를 전자상거래(e-commerce)라고 한다.
  
     <a href="https://www.samsungpop.com/mobile/invest/poptv.do?cmd=fileDown&FileNm=uma_200626.html"><img width="600" alt="e-commerce" src="https://user-images.githubusercontent.com/130523834/235652059-dfc61816-33cc-47cd-8ff4-28ed1d4ec2d1.jpg"> <br>
     (출처: 삼성증권 포트폴리오전략팀<sup>[01]</sup>) 
  
     전자상거래는 글로벌 소매유통시장의 20% 이상을 차지하고 있는 주요 유통채널이다. 정보통신기술 발전과 스마트폰 보급 확산, 안전하고 편리한 결제시스템 발달 등으로 전자상거래가 크게 성장하였다. 코로나19가 확산되면서 전자상거래는 핵심적인 쇼핑 수단으로 부상했으며 외출이 제한된 소비자들이 온라인 쇼핑에 눈을 돌리면서 세계 곳곳에서 전자상거래 주문량이 급증했다.
  
     이러한 전자상거래의 발전으로 인해 고객들은 더욱 많은 제품을 쉽게 구매할 수 있게 되었지만, 제품의 질이나 신뢰성 등에 대한 불안감 역시 함께 증가하였다. 이러한 불안감을 해소하기 위해 고객들은 온라인으로 제품 구매 시 상품의 평점과 리뷰를 주로 참고하고 있다. 이에 따라 사용자들은 상품에 대한 자신의 경험을 리뷰로 남겨 다른 고객들에게 도움을 주며, 이는 전자상거래 업체들이 구매 후기 시스템을 운영하고 활용하는 데 큰 역할을 하고 있다.
       <hr>

       
     <img width="600" alt="eMarket" src="https://github.com/wnaely/Amazent/assets/130523834/2c04ec4b-de8f-4a91-b4f3-d687980c3482"><a href="https://www.statista.com/statistics/274255/market-share-of-the-leading-retailers-in-us-e-commerce/"> <br>
     (출처: Market share of leading retail e-commerce companies in the United States<sup>[02]</sup>)

  
     위 그래프는 미국 내 주요 소매 전자상거래 업체의 시장 점유율을 나타낸 그래프이며 eMarketer의 자료에 의하면 Amazon이 시장의 37.8%를 차지하면서 가장 높은 시장 점유율을 보여주는 것으로 나타났다. 실제, 2위인 Walmart의 6.3%와 3위인 Apple의 3.9%와는 엄청난 격차를 보여줄 뿐 아니라 2위에서 15위까지 14개 기업의 시장 점유율을 다 합쳐도 아마존의 시장 점유율에 미치지 못하는 모습을 보여준다.
       
     Amazon은 세계적인 규모를 가진 전자상거래 업체로서, 수많은 제품과 대량의 리뷰 데이터를 보유하고 있다. 이러한 Amazon 리뷰 데이터를 분석하여 제품의 평판을 파악하고, 고객들이 원하는 제품을 더욱 정확하게 추천해주는 것은 아마존뿐만 아니라 온라인 판매 업체에게 매우 중요한 과제이다.
  
  <hr>
  
  
   * ### Amazon(전자상거래, 인터넷 유통 업체) 플랫폼에서의 리뷰가 갖는 영향
       
     전자상거래에서 리뷰는 고객들이 상품을 선택하고 구매하는데 있어서 중요한 역할을 하며 이에 따라 온라인 판매 업체들은 높은 평점과 긍정적인 리뷰를 얻기 위해 노력하고 있다. 또한 전자상거래 업체들은 고객들의 구매 경험을 개선하기 위해 더욱 발전된 리뷰 시스템과 기술을 도입하고 있다.
      
     웹을 통한 전자상거래와 정보 공유가 활발해짐에 따라 상품에 대한 리뷰 문서가 상당히 증가하였는데, 사용자들은 상품을 구매한 사이트와 더불어 트위터, 블로그, 페이스북과 같은 소셜 미디어를 통해 자연스럽게 의견을 공유하고 상품 구매에 실질적인 도움을 받는다. 
     
     <img width="600" alt="amazon-review-stat" src="https://github.com/wnaely/Amazent/assets/130523834/6ff096b1-478d-45f0-98b3-6eb24b9d8ded"><a href="https://www.insiderintelligence.com/articles/topics/retail-ecommerce?ecid=NL1016"> <br>
     (출처: Consumers' Trust in Online Reviews Gives Amazon an Edge<sup>[04]</sup>)

     
     2018년 Salsify의 조사 결과에 따르면 미국의 디지털 구매고객의 절반이상인 51%가 아마존을 가장 유용한 제품 정보로 신뢰한다고 나타나 있다. Amazon은 이런 유용한 리뷰 작성을 장려하기 위해 다양한 방법을 제공한다. 제품 리뷰 작성을 완료한 구매자들에게 인센티브를 제공하거나, 리뷰 작성을 요청하는 이메일을 보내는 것 등으로 이루어진다. 이러한 노력은 Amazon의 리뷰 시스템이 상품 구매 결정에 미치는 영향력을 높이는 데 큰 도움을 준다.
     
     <a href="https://www.amazon.com/Echo-4th-Gen/dp/B085HK4KL6/ref=sr_1_4?crid=39IGDKOPR5EGJ&keywords=alexa&qid=1683047928&sprefix=alexa%2Caps%2C275&sr=8-4&th=1"><img width="700" alt="review" src="https://user-images.githubusercontent.com/130523834/235738605-8519e0a4-9564-4d1c-9705-a111a768c264.png"> <br>
     (출처: Amazon.com<sup>[05]</sup>)

     
     상품에 대한 주요 의견을 효과적인 정보의 형태로 전달하는 것이 실제 구매에 영향을 주기 때문에, Amazon은 상품 자체의 정보를 제공하는 거에 나아가 상품에 대한 리뷰를 효과적으로 전달하는 것에 높은 비중을 두고 있다.
     구체적으로 상품 자체의 만족도 점수와 세부 특징별 점수를 구매자로부터 입력 받고 이들 점수를 종합하여 제공하며, 구매 예정자들이 유용하다고 평가한 리뷰나 상품 특징을 강조하여 표시한다.<sup>[03]</sup>

     Amazon의 리뷰는 구매자들이 상품을 구매하기 전에 중요한 정보를 보여주는 것뿐만 아니라, 제품 품질과 서비스에 대한 피드백을 제공하여 업체들이 제공하는 제품과 서비스의 개선을 도와준다. 이는 고객들의 구매 경험을 개선하고 더 나은 제품과 서비스를 제공하는 것으로 이어진다.

     이러한 점들을 보았을 때 전자상거래 플랫폼인 Amazon에서의 리뷰는 종합적인 면에서 매우 중요한 것을 알 수 있다.

     따라서 이번 프로젝트에서는 Amazon 리뷰 데이터를 수집하고 분석하여 플랫폼의 장단점과 개선점을 파악하는 것을 목표로 하며, 이를 위해 Kaggle에서 제공하는 Amazon 리뷰 데이터셋을 이용하여 리뷰의 긍정 혹은 부정을 예측하는 인공지능 모델을 개발하려고 한다.


  <hr>
       
    
## 2. 데이터

   * ### 원본 데이터 출처
      
      이번 프로젝트에서는 Kaggle에서 제공하는 [Amazon Reviews](https://www.kaggle.com/datasets/bharadwaj6/kindle-reviews) 데이터셋을 사용하였다.
      
   * ### 원본 데이터 소개
       
       #### [ 데이터 구성 ]
       
       |asin|helpful|ratings|reviewText|reviewTime|reviewerID|reviewerName|summary|unixReviewTime|
      |-|-|-|-|-|-|-|-|-|
      |ID of the product|helpfulness rating of the review|rating of the product|text of the review(heading)|time of the review(raw)|ID of the reviewer|name of the reviewer|summary of the review|unix timestamp| 
       
       #### [ 데이터 ]
       
      |index|asin|helpful|ratings|reviewText|reviewTime|reviewerID|reviewerName|summary|unixReviewTime|
      |-|-|-|-|-|-|-|-|-|-|
      |0|B000F83SZQ|[0, 0]|5|I enjoy vintage books and movies so I...|05 5, 2014|A1F6404F1VG29J|Avidreader|Nice vintage story|1399248000|
      |1|B000F83SZQ|[2, 2]|4|This book is a reissue of an old one; the..|01 6, 2014|AN0N05A9LIJEQ|critters|Different...|1388966400|
      |2|B000F83SZQ|[2, 2]|4|This was a fairly interesting read.  It had old...|04 4, 2014|A795DMNCJILA6|dot|Oldie|1396569600|
      |...|...|...|...|...|...|...|...|...|...|
      |982618|B00M13FNSS|[0, 0]|5|When I say this was an excellent book please...|07 23, 2014|A1BQO66R6OLCCW|Nikey|Wow!!|1406073600|
      |982619|B00M13FNSS|[2, 2]|5|This book was everything. I just hope Alexus...|07 23, 2014|A2NRGE3CSFY2TQ|Yo|Great read. hands down #5star hit|1406073600|
       
       원본 데이터는 총 982,619건으로 상당히 많은 것을 확인할 수 있다.
       데이터를 줄이기 위해 10만건이 넘는 데이터는 삭제하였고 10만건의 새로운 데이터셋을 만들었다. <br>
       
       리뷰의 분포를 확인하기 위해 평점 1점부터 5점까지의 정보를 시각화하여 그래프로 나타내 보았다. <br>
       
      
       <img width="500" alt="ratings" src="https://github.com/wnaely/Amazent/assets/130523834/4c90990d-74dc-4338-a787-f5708db13153">
       
       리뷰의 평점 분포는 1점이 3,786개로 가장 낮고 점차 늘어나 5점이 47,356개로 가장 많은 것을 보아 만족도가 높은 사용자들의 평점이 더 많은 것을 확인할 수 있다.

     <img width="500" alt="length_new" src="https://github.com/wnaely/Amazent/assets/130523834/87a4bf42-b52b-4aaa-bdd4-73da18b656e2">

     리뷰의 문장 길이는 100자와 200자 사이인 문장이 8,000개 정도로 가장 많고 200자가 넘어갈수록 점점 줄어든다.<hr>


   * ### 분석 데이터
       
       분석을 위해 평점이 4, 5인 리뷰에는 레이블 1을 평점이 1, 2인 리뷰에는 레이블 0을 부여하고 부여된 레이블은 새로 생성한 label이라는 열에 저장하였다.
      평점이 3인 리뷰 데이터와 리뷰 문장의 길이가 20자 미만인 데이터는 삭제하였고 'index', 'ratings', 'reviewText', label' 데이터로 새로운 데이터셋을 만들었다.
       
       
       |index|ratings|reviewText|label|
      |-|-|-|-|
      |1|5|I enjoy vintage books and movies so I...|1|
      |...|...|...|...|
      |86148|5|Well-crafted story and characters. All the twi...|1|
      <br>
       
       
      <img width="500" alt="plot" src="https://github.com/wnaely/Amazent/assets/130523834/57747309-4487-4133-8ae1-b6c0a7b1068d">

     데이터의 긍정적인 리뷰와 부정적인 리뷰의 비율을 확인하기 위해 레이블 0과 1의 리뷰의 갯수를 각각 구하고 n에 저장하였으며 이를 시각화 하여 막대그래프로 나타내 보았다. 긍정적인 리뷰가 부정적인 리뷰에 비해 훨씬 많은것을 확인할 수 있다. <br>
       

  * ### 데이터셋 분할 - 학습 데이터 생성

      분석의 정확도를 높이기 위해 긍정적인 리뷰와 부정적인 리뷰의 데이터를 각각 1000개씩 랜덤으로 추출하여 2000개의 학습 데이터를 만들었다.

      |index|ratings|reviewText|label|
      |-|-|-|-|
      |1|4|A great read to continue the Bride Train serie...|1|
      |2|4|good western read, with a little sci fi mixed...|1|
      |...|...|...|...|
      |1999|1|I would have easily given this book four stars...|0|
      |2000|1|I wanted to say something nice - the cover is...|0|

    <hr>


## 3. 결과

   #### [ 개발환경 ]

   <a href="https://blog.jetbrains.com/pycharm/2023/03/2022-3-3/" target="_blank"><img src="https://img.shields.io/badge/PyCharm_2022.3.3-2bc382?style=flat&logo=PyCharm&logoColor=white"/></a>
   <a href="https://www.python.org/downloads/release/python-3913/" target="_blank"><img src="https://img.shields.io/badge/Python_3.9.13-3776AB?style=flat&logo=Python&logoColor=white"/></a>
   <a href="https://blog.jetbrains.com/pycharm/2023/03/2022-3-3/" target="_blank"><img src="https://img.shields.io/badge/JupyterLab 3.3.2-F37626?style=flat&logo=Jupyter&logoColor=white"/></a>
     
   #### [ 패키지 ] 
      
   <a href="" target="_blank"><img src="https://img.shields.io/badge/TensorFlow_2.9.1-FF6F00?style=flat&logo=TensorFlow&logoColor=white"/></a>
   <a href="" target="_blank"><img src="https://img.shields.io/badge/Pytorch_1.12.1-EE4C2C?style=flat&logo=PyTorch&logoColor=white"/></a>
   <a href="" target="_blank"><img src="https://img.shields.io/badge/NumPy_1.24.3-013243?style=flat&logo=NumPy&logoColor=white"/></a>
   <a href="" target="_blank"><img src="https://img.shields.io/badge/pandas_1.4.4-150458?style=flat&logo=pandas&logoColor=white"/></a>
   <a href="" target="_blank"><img src="https://img.shields.io/badge/transformers_4.21.2-409FFF?style=flat&logoColor=white"/></a>
   <a href="" target="_blank"><img src="https://img.shields.io/badge/scikit--learn_1.2.2-F7931E?style=flat&logo=scikit-learn&logoColor=white"/></a>

  * ### MobileBERT를 사용하여 학습한 결과

     <img width="600" alt="BERT_RETRAIN_with_writer" src="https://github.com/wnaely/Amazent/assets/130523834/baa00705-e096-482c-b668-1e4a3147d227">

     <img width="750" alt="train_valid" src="https://github.com/wnaely/Amazent/assets/130523834/ad60a77b-c22c-4b08-b92e-a4088389bf04">

    각 단계의 loss와 Accuracy의 평균을 내어 나타내보면 아래와 같다. 

    |step|0|1|2|3|
    |-|-|-|-|-|
    |loss|96,990|0.37|0.2149|0.1567|
    |Accuracy|0.877|0.911|0.9167|0.9238|

    결과를 보면 학습의 첫 번째 단계에 높은 손실값과 달리 4번째 단계에서는 0.1567로 손실값이 각 학습 단계마다 감소하고 있다. 이는 모델이 학습 데이터에서 효과적으로 학습되고 있는 것을 나타내며 텐서보드를 통해 손실 값의 변화를 그래프로 시각화하여 학습 진행 상황을 보다 명확하게 확인할 수 있다.

    정확도(Accuracy)도 학습이 진행됨에 따라 증가하는 변화를 보인다. 초기에는 0.877이었지만, 4번째 단계에서는 0.9238로 성능이 향상된 것을 확인할 수 있고 리뷰의 감성을 잘 예측하고 있다는 것을 나타낸다.
    

  * ### 분석 데이터 전체에 적용한 결과값

    <img width="600" alt="BERT_TESTv2" src="https://github.com/wnaely/Amazent/assets/130523834/037fb1f4-62b3-4b82-b637-3d4f9403f009">

    최종적으로 분석 데이터에 학습 시킨 모델을 적용한 결과, 0.93의 긍부정 예측 정확도가 나왔다.

   <hr>

## 4. 마무리

#### 느낀점 등
       
   ## References
[01] https://www.samsungpop.com/mobile/invest/poptv.do?cmd=fileDown&FileNm=uma_200626.html <br>
[02] https://www.statista.com/statistics/274255/market-share-of-the-leading-retailers-in-us-e-commerce/ <br>
[03] http://www.calsec.or.kr/110429spring/paper/2-2-2.pdf <br>
[04] https://www.insiderintelligence.com/articles/topics/retail-ecommerce?ecid=NL1016 <br>
[05] https://www.amazon.com/Echo-4th-Gen/dp/B085HK4KL6/ref=sr_1_4?crid=39IGDKOPR5EGJ&keywords=alexa&qid=1683047928&sprefix=alexa%2Caps%2C275&sr=8-4&th=1

   
   
   
