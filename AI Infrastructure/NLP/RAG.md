# LLM 캐시
- LLM 캐시를 사용하면, 캐시 요청을 통해 이전에 동일하거나 유사한 요청이 있었는지 확인
	- 있었다면 LLM 캐시에 저장된 답변을 전달
	- 없다면 LLM에 프롬프트를 전달해 새롭게 텍스트를 생성해서 LLM 오케스트레이션 도구로 전달
- 크게 두 가지 방식 
	1. 일치 캐시: 요청이 완전히 일치하는 경우, 저장된 응답을 반환
		1. 문자열 그대로 동일한지 판단하기 때문에 파이썬의 딕셔너리 같은 자료구조에 프롬프트와 그에 대한 응답을 저장하고 새로운 요청이 들어왔을 때 딕셔너리의 키에 동일한 프롬프트가 있는지 확인하는 방식으로 구현할 수 있음.
	2. 유사도 검색 캐시: 이전에 '유사'한 요청이 있었는지 확인해야하기 때문에 문자열을 그대로 비교하는 것이 아니라 문자열을 임베딩 모델을 통해 변환한 임베딩 벡터를 비교함
		1. 요청을 임베딩 모델로 임베딩 벡터로 변환, 벡터 데이터베이스에 유사한 요청이 있었는지 검색
		2. 유사한 검색이 있다면 저장된 텍스트를 반환
		3. 없으면 LLM으로 새롭게 텍스트를 생성해 응답하면서 벡터 데이터베이스에 요청의 임베딩 벡터와 생성 결과를 저장
	![[유사검색캐시.jpeg | 500]]

# 데이터 검증
> 예를 들어, 정치적인 내용과 관련된 텍스트를 임베딩 벡터로 만들고 요청의 임베딩이 정치 임베딩과 유사한 경우 답변을 피하도록 만들 수 있음
> LLM과 임베딩 유사도를 기반으로 사용자의 요청을 거부하도록 LLM 애플리케이션을 보호

# 검색 성능 높이기
- 바이 인코더와 교차 인코더를 결합해 사용

