# GraphRAG: Neo4j DB와 LangChain 결합을 통한 질의응답 구현하기

> **GraphRAG** 프로젝트는 Neo4j 데이터베이스와 LangChain을 결합하여 질의응답(Question & Answer)을 수행하기 위한 데모/실습 예제입니다.  
> No4j에서 제공하는 영화화 데이터셋을 이용해 Neo4j에 데이터를 적재하고, LangChain을 통해 자연어 질의로부터 Cypher 쿼리를 자동 생성하고, 결과를 요약/응답하는 방식을 시연합니다.
> Neo4j에서 기본으로 제공하는 데이터 셋을 통해 DB를 만들고 실행

---

## 목차

1. [프로젝트 개요](#프로젝트-개요)  
2. [시스템 아키텍처](#시스템-아키텍처)  
3. [구성 요소](#구성-요소)  
4. [실행 화면](#실행-화면)  

---

## 프로젝트 개요

- **목표**  
  - 대규모 언어 모델(LLM) 기반으로 자연어 질의를 받아 **Neo4j** DB에 질의하고, 사용자에게 답을 반환  
  - **LangChain** 라이브러리를 사용하여 자연어를 Cypher 쿼리로 변환하고, 쿼리 결과를 가독성 좋은 형태로 응답

- **핵심 아이디어**  
  1. **LangChain**의 PromptTemplate / GraphCypherQAChain 활용  
  2. **Neo4j**에서 그래프형 데이터 저장 및 탐색  
  3. 자연어 질의 → Cypher 쿼리 생성 → DB 조회 → 결과 요약/응답

---

## 시스템 아키텍처

아래 다이어그램은 전체 프로세스를 나타냅니다.

![image](https://github.com/user-attachments/assets/8dec9d19-d80d-4a84-96c4-b2111de00240)

1. **사용자 질의** (예: “Who played in Top Gun?”)  
2. **LangChain** → Cypher 쿼리 생성  
3. **Neo4j** → 쿼리 실행 후 결과 반환  
4. **LangChain** → 응답 포맷팅 및 사용자에게 전달

---

## 구성 요소

1. **Neo4j Database**  
   - 영화, 배우, 감독 등 그래프 데이터가 저장됨

2. **LangChain**  
   - PromptTemplate / GraphCypherQAChain 사용  
   - 자연어 질의를 Cypher로 변환하여 Neo4j 질의  
   - 결과를 받아 사용자 친화적인 답변 작성

3. **OpenAI API** (또는 기타 LLM API)  
   - ChatOpenAI 등의 모델 사용  
   - 문맥 이해, 질의 변환, 결과 요약

---

## 실행 화면

### 1) Neo4j 데이터베이스 내용

Neo4j DB에 데이터가 적재된 모습입니다.  
![image](https://github.com/user-attachments/assets/b1b7741b-bbfa-41db-81d5-a817a2483230)


### 2) VSCode 콘솔 실행 결과

LangChain이 Cypher 쿼리를 생성·실행하고 결과를 반환하는 모습입니다.  
![image](https://github.com/user-attachments/assets/4686814d-0ca1-42c9-b326-e880d1d1bf76)


### 3) Neo4j Desktop에서 동일 쿼리문 조회 결과

Neo4j Browser(또는 Desktop)에서 동일한 쿼리 결과를 직접 확인한 화면입니다.  
![image](https://github.com/user-attachments/assets/61d404cb-de48-46a4-8129-c6507eea7b13)



참고 블로그 --> https://uoahvu.tistory.com/entry/GraphRAG-Neo4j-DB%EC%99%80-LangChain-%EA%B2%B0%ED%95%A9%EC%9D%84-%ED%86%B5%ED%95%9C-%EC%A7%88%EC%9D%98%EC%9D%91%EB%8B%B5-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0-Kaggle-CSV-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%A0%81%EC%9A%A9%ED%95%98%EA%B8%B0#GraphRAG%20%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0-1
