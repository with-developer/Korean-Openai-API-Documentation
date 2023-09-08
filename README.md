# Openai API를 시작하기 위한 문서(작성중)

## **1. 개요**

### **1.1 일반 소개**

OpenAI API는 자연어 및 코드의 이해와 생성에 필수적인 도구로 활용될 수 있다. 이 API는 또한 이미지의 생성 및 편집, 그리고 음성을 텍스트로 변환하는 작업에도 적용 가능하다. OpenAI는 다양한 능력과 가격 포인트를 가진 모델을 제공하며, 사용자 지정 모델을 파인 튜닝하는 기능도 제공한다.

### **1.2 자원 및 참조**

- 실험을 위한 놀이터
- API 참조 문서
- 도움말 센터
- 현재 API 상태 확인
- OpenAI 개발자 포럼
- 사용 정책

### **1.3 사용자 데이터 보호**

OpenAI는 사용자 데이터의 보호가 기본적인 임무로 취급한다. API를 통한 입력과 출력 데이터는 모델 훈련에 사용되지 않는다.

## **2. 주요 개념**

### **2.1 GPT (Generative Pre-trained Transformer)**

OpenAI의 GPT 모델은 자연어와 코드를 이해하기 위해 훈련되었다. GPT 모델은 입력에 대한 텍스트 출력을 제공하며, 이러한 입력을 "프롬프트"라고도 한다. 프롬프트 설계는 GPT 모델을 프로그래밍하는 기본적인 방법이며, 작업을 성공적으로 수행하는 방법에 대한 지침이나 예시를 제공하는 것이 일반적이다.

### **2.2 임베딩**

임베딩은 데이터 조각 (예: 텍스트)의 벡터 표현으로, 해당 데이터의 내용 및/또는 의미의 측면을 보존하는 것을 목적으로 한다. 유사한 데이터 조각은 더 가까운 임베딩을 갖는 경향이 있다. OpenAI는 텍스트 문자열을 입력으로 받아 임베딩 벡터를 출력으로 생성하는 텍스트 임베딩 모델을 제공한다.

### **2.3 토큰**

GPT 및 임베딩 모델은 '토큰'이라는 단위로 텍스트를 처리한다. 토큰은 일반적으로 발생하는 문자 시퀀스를 나타낸다. 예를 들어, 문자열 "tokenization"은 "token"과 "ization"으로 분해된다. 모델의 최대 컨텍스트 길이는 토큰의 수로 제한되며, 프롬프트와 생성된 출력을 합한 토큰의 수는 이 제한을 초과할 수 없다.

### **2.4 제한 사항**

GPT 모델의 경우, 프롬프트와 생성된 출력의 토큰 수의 합은 모델의 최대 컨텍스트 길이를 넘지 않아야 한다. 임베딩 모델에서는 출력 토큰을 생성하지 않으므로, 입력은 모델의 최대 컨텍스트 길이보다 짧아야 한다.

## 3. 라이브러리 및 프로그래밍 언어 별 OpenAI API 사용법

## 3.1 Python 라이브러리

OpenAI는 Python 라이브러리를 제공하며, 이를 설치하는 방법은 아래와 같습니다.

```bash
$ pip install openai
```

설치 후 다음과 같은 코드를 사용하여 API를 호출할 수 있습니다.

```python
import os
import openai

# 환경 변수 또는 비밀 관리 서비스에서 API 키를 로드
openai.api_key = os.getenv("OPENAI_API_KEY")

chat_completion = openai.ChatCompletion.create(model="gpt-3.5-turbo", messages=[{"role": "user", "content": "Hello world"}])
```

이 라이브러리는 명령행 유틸리티도 제공합니다.

```bash
$ openai api chat_completions.create -m gpt-3.5-turbo -g user "Hello world"
```

## 3.2 Node.js 라이브러리

Node.js에서도 OpenAI 라이브러리를 사용할 수 있습니다. 설치는 다음과 같이 실행합니다.

```bash
$ npm install openai
```

설치 후 API를 호출하는 예제 코드는 아래와 같습니다.

```jsx
import OpenAI from "openai";

const openai = new OpenAI({
    apiKey: process.env.OPENAI_API_KEY,
});

const chatCompletion = await openai.chat.completions.create({
    messages: [{ role: "user", content: "Say this is a test" }],
    model: "gpt-3.5-turbo",
});
```

## 3.3 Azure OpenAI 라이브러리

Microsoft의 Azure 팀도 OpenAI API와 호환되는 라이브러리를 유지 관리하고 있습니다.

- [.NET용 Azure OpenAI 클라이언트 라이브러리](https://github.com/Azure/azure-sdk-for-net/tree/main/sdk/openai/Azure.AI.OpenAI)
- [JavaScript용 Azure OpenAI 클라이언트 라이브러리](https://github.com/Azure/azure-sdk-for-js/tree/main/sdk/openai/openai)
- [Java용 Azure OpenAI 클라이언트 라이브러리](https://github.com/Azure/azure-sdk-for-java/tree/main/sdk/openai/azure-ai-openai)
- [Go용 Azure OpenAI 클라이언트 라이브러리](https://github.com/Azure/azure-sdk-for-go/tree/main/sdk/ai/azopenai)

## 3.4 커뮤니티 라이브러리

여러 프로그래밍 언어와 플랫폼에 대한 커뮤니티 라이브러리도 있습니다. 이들 라이브러리는 개발자 커뮤니티에 의해 구축 및 유지 관리되며, OpenAI는 이러한 프로젝트의 정확성이나 보안을 검증하지 않습니다. 따라서 이들 라이브러리는 **자신의 책임 하에 사용해야 합니다.**

### 예시

- **C# / .NET**
    - [Betalgo.OpenAI](https://github.com/betalgo/openai) by [Betalgo](https://github.com/betalgo)
    - [OpenAI-API-dotnet](https://github.com/OkGoDoIt/OpenAI-API-dotnet) by [OkGoDoIt](https://github.com/OkGoDoIt)
- **Python**
    - [chronology](https://github.com/OthersideAI/chronology) by [OthersideAI](https://www.othersideai.com/)
- **Go**
    - [go-gpt3](https://github.com/sashabaranov/go-gpt3) by [sashabaranov](https://github.com/sashabaranov)

자세한 정보 및 다른 언어에 대한 라이브러리는 OpenAI 공식 문서에서 확인할 수 있습니다.

## 모델

## 할 수 있는 것

## 문제점(개인정보나 기밀정보)

## 사용법

## 

## 파인튜닝

## 가격
