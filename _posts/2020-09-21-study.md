---
layout: post
title: "Sep 21th Journal Club"
author: "Soomin Cho (soominc3@illinois.edu)"
---

    Themes: Visually Grounded Language Models, Image-Grounded Conversation, Empathy Expressed In Text 

Presenters: YK (Yoon Kyung Lee), IJ (Inju Lee), HY (Hoyoung Maeng) <br>

-----------------

## Topic 1: Transformer, Visually Grounded Language Models [YK]

선정 이유: VQA의 핵심 모델이 될 grounded language model에 대한 최신 논문 리뷰를 위해 선정하였다. <br>

내용 요약: 유명한 NLP관련 오픈소스 기업인 허깅페이스(HuggingFace)에서 배포한 Transformer모델에 기반이 된 논문이다. UNC Chapel Hill 팀에서 발표했으며, 기존의 VQA에 특화된 Visually Grounded Language 모델을 소개했다. 이 논문에서 소개한 모델은 기존의 연구에서 Vision 따로, Language 따로 다뤘던 Pretraining에 Crossmodality Model (CM) 을 추가했다. CM의 역할은 VQA같은 시각 자료 기반 질의 응답 과제를 수행할때, Language Model을 통해 인식한 질문이 Vision Model을 통해 인식한 사진에 있는 object에 대해 묻는지를 확인한다. 맞을 경우 (‘yes’) 응답을 위한 다음 encoder model을 처리한다. 이로써 Groundedness 성능을 더 높이는 효과를 보였다. <br>

장단점 및 의의: 장점은 코드가 공개되어 직접 사용해볼 수 있다는 점이다. Microsoft & Allen AI에서 배포했던 OSCAR에 비하면 실험 과제가 적은 편이다 <br>

비고<br>
실제 테스트할 수 있는 코드를 배포했다<br>
[Colab](https://colab.research.google.com/drive/18TyuMfZYlgQ_nXo-tr8LCnzUaoX0KS-h?usp=sharing#scrollTo=D8J5XQql82um). 우리가 직접 원하는 이미지 (url)를 넣으면 object detection을 수행한 후에 question을 받는다.성능은 VQA와 GQA(Manning) 모델을 비교해볼 수 있다. 몇개 시험해본 결과, 간단한 질문(e.g., is the person woman or man?)은 다 정확도가 높은데, 문장 길이가 길거나 추론을 요하는 복잡한 질문(e.g., why is she sitting on a chair instead of a sofa?)은 성능이 현저히 떨어진다.

<br>

    Tan, H., & Bansal, M. (2019). Lxmert: Learning cross-modality encoder representations from transformers. arXiv preprint arXiv:1908.07490.

<br>

## Topic 2: Image-Grounded Conversation [IL]

선정이유: 이미지를 기반으로 이루어지는 대화는 어떤 특징이 있고, 이런 대화를 이용한 연구는 어떤 방식으로 이루어지고 있는지 알아보고 싶어 선정하였다. <br>

내용요약 <br> 
본 연구는 Image-Grounded Conversation(IGC) 라는 새로운 task를 소개하고 있다. IGC task는 Image captioning, VQA, Visual Dialog(VisDial) 등의 기존 vision & language task들과는 달리 이미지가 하나의 context로서 다루어진 natural conversation이고 이미지에 explicitly 드러나지 않은 정보도 다루고 있기 때문에 implicit commonsense reasoning을 필요로 한다. <br>
저자들은 모델이 주어진 image 및 text context에서 사람들의 참여를 이끌어낼 수 있는 질문과 대답을 만들어낼 수 있도록 하기 위해 deep neural generation and retrieval approach를 사용하였다. 이후 모델이 만들어낸 질문과 대답에 대한 평가를 실시한 결과, multimodal context (image+text)를 encode한 모델이 더 좋은 quality를 가진 질문과 대답을 출력해내는 것으로 나타났다. <br>

단점: 모델이 만들어낸 질문과 대답의 quality를 평가하였는데, 그 quality의 객관적인 기준이 무엇인지에 대한 내용이 논문에 나와 있지 않아 아쉽다. <br>

의의: Image-Grounded Conversation이라는 새로운 task를 소개하였다. 

<br>

    Mostafazadeh, N., Brockett, C., Dolan, B., Galley, M., Gao, J., Spithourakis, G. P., & Vanderwende, L. (2017). Image-grounded conversations: Multimodal context for natural question and response generation. arXiv preprint arXiv:1701.08251.

<br>

## Topic 3: Empathy Expressed In Text (HM)

선정 이유: 공감에 대한 연구를 찾아보는 과정에서, 현재 활발히 연구되고 있는 텍스트 분석 분야에서는 어떻게 진행되고 있는지 살펴보기 위해 선정하였다. <br>

내용 요약 <br>
공감은 보통 서로 마주보거나 대화할때, 즉 동시다발적으로 교류가 이루어질때 발생한다. 따라서 텍스트 기반으로 메시지를 주고 받아보면 시간 차이가 생기고 동시에는 교류가 이루어지지 않는다. 이로 인하여 실제 공감을 통한 정신 건강 치료가 필요한 사람들은 시간차로 적절한 피드백을 받지 못하는 경우가 발생하는데, 이때 텍스트 분석을 통해 공감할 수 있는 기법이 있다면 도움이 될 것이라고 생각한다. 실제로 논문의 저자는 3가지 empathy communication mechanisms을 선정하였고 각각 Emotional Reactions, Interpretations, Explorations(이하, ‘EPITOME’)의 구성으로 이루어져있다. 그리고 다른 텍스트 분석 기법(회기분석, RNN, HRED, BERT, DialoGPT, RoBERTa) 와 저자가 고안한 방법이랑 비교를 했을때, 성능이 좋음을 수치적으로 볼 수 있었다. <br>

장점: 텍스트 분석을 위한 최신 논문들이 참고문헌으로 사용되어, 트렌디한 느낌을 받을 수 있었다. 또한, 실제 딥러닝 모델링을 통해 다른 분석기법과 비교한 결과가 흥미로웠다. <br>

단점: 그러나 수치적 결론에 대해서는 충분한 설명이 되어 있었지만, 실제 텍스트 예시를 통한 결과 설명이 없어서 직관적으로 이해하기는 다소 어려움이 있었다.<br>

의의: 여러 NLP 기법들이 적용되어 실시된 텍스트 분석 결과가 있어 신뢰성이 있는 논문이라고 생각한다.

<br>

    Sharma, A., Miner, A., Atkins, D. and Althoff, T. (2020). A Computational Approach To Understanding Empathy Expressed In Text-Based Mental Health Support. arXiv preprint arXiv:2009.08441.(EMNLP 2020)
