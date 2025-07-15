# 📘 melissa_prompting
이 프로젝트는 일기 데이터를 LLM을 활용해 요약 및 벡터화하고,
사용자 질문에 대해 벡터 DB 기반으로 검색/응답하는 흐름을 구현합니다.

## ✅ 일기 내용 벡터화 관련 코드
⏰ 하루에 한 번 (사용자가 자고 있을 때) 수행하는 일괄 처리 작업입니다.
일기 내용을 그대로 벡터화하지 않고, 요약 및 청크화 → 벡터화 과정을 거칩니다.

1. summary.ipynb
일기 전체를 주제별로 요약 및 청크화합니다.

LLM을 사용하여 JSON 형태로 구조화된 요약을 생성합니다.
(현재는 text 형식으로 output을 받고 있고 프롬프트는 편하신 대로 수정하셔서 output 형식으로 변경하셔도 됩니다.)

벡터화하기 전 사전 처리 단계입니다.
→ 일기를 그대로 벡터화하지 않고, 요약 정보를 벡터화하는 구조입니다.

2. vectorize.ipynb
summary.ipynb에서 생성한 요약(청크 단위) 데이터를 벡터로 변환하고 저장합니다.

생성된 벡터는 이후 사용자 질문에 대한 검색에 활용됩니다.

## ✅ 사용자 질문 → 벡터 DB 검색 관련 코드
실시간 대화 중에 동작하는 부분입니다.

1. query.ipynb
사용자의 입력을 그대로 벡터 DB에 쿼리하면 검색 정확도가 낮을 수 있습니다.

따라서, 입력에 대해 전처리 및 임베딩 작업을 수행한 후 검색합니다.

이를 통해 사용자의 의도에 더 적합한 일기 내용을 검색할 수 있습니다.

```
🔁 전체 흐름 요약
1. 일기 입력 (User Input)
2. → summary.ipynb로 요약 + 청크화
3. → vectorize.ipynb로 벡터화 및 저장
4. → 사용자가 질문하면 query.ipynb로 전처리 + 벡터 DB 검색
5. → 적절한 응답 반환
```

---
## conda 환경 설정 방법
```
conda env list
conda create -n melissa python=3.12
conda create melissa
```

### (~21일까지) 미션
- 대화 내용 전체를 크로마 db에 넣지 말고 요약한 내용을 넣어라
- 프롬프트 깎아라 (현재는 "저번 주에도 그랬잖아" 이런 식의 하드코딩이 되어있는데 이건 좋지 않음)
- 사용자의 답변이 왔을 때 크로마 디비를 훑을지 말지 yes or no를 출력하는 llm이 필요함.

### 참고 자료
[EP01. openai 의 새로운 기능 assistant API 완벽히 이해해보기](https://www.youtube.com/watch?v=-Wne4a-8RlY&list=TLPQMjQwMTIwMjVF8yDU1ax6MQ&index=1)   
[공식문서](https://platform.openai.com/docs/assistants/overview)     

