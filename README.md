# melissa_prompting
2025년 겨울방학 프로젝트 Melissa

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
