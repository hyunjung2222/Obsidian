#spring #http #ObjectMapper

# url 내용 확인하기
1. 터미널 창에서 아래와 같이 입력하면
`http -v https://open.er-api.com/v6/latest/USD 

2. 아래와 같은 출력 결과가 나옴
3. body 에 들어있는 것이 어떠한 형식인가 content-type 에 적혀있음 (여기선 json)
```
GET /v6/latest/USD HTTP/1.1
Accept: */*
Accept-Encoding: gzip, deflate
Connection: keep-alive
Host: open.er-api.com
User-Agent: HTTPie/3.2.4

HTTP/1.1 200 OK
Accept-Ranges: bytes
Age: 2397
CF-Cache-Status: HIT
CF-RAY: 8f68b3d8da45eb7e-NRT
Cache-Control: public, max-age=3600
Connection: keep-alive
Content-Encoding: gzip
Content-Length: 1634
Content-Type: application/json
Date: Mon, 23 Dec 2024 13:29:47 GMT
Last-Modified: Mon, 23 Dec 2024 12:35:01 GMT
```
4. 아래부터 Json의 내용
5. 환율을 알고 싶으므로 rates 부분이 중요
```
{
"base_code": "USD",
"documentation": "https://www.exchangerate-api.com/docs/free",
"provider": "https://www.exchangerate-api.com",
"rates": {
	"AED": 3.6725,
	"AFN": 70.251481,
	"ALL": 94.543909,
	"AMD": 395.236674,
	"ANG": 1.79,
	"AOA": 925.391201,
	"ARS": 1025.42,

```

### url 을 호출해서 이 결과를 어떻게 가져올 것인가?
1. URL url = new URL("https://open.er-api.com/v6/latest/USD") 로 가져옴
```
	URL url = new URL("https://open.er-api.com/v6/latest/" + currency);  
	HttpURLConnection connection = (HttpURLConnection) url.openConnection();  
	BufferedReader br = new BufferedReader(new InputStreamReader(connection.getInputStream()));  
	String response = br.lines().collect(Collectors.joining());  
	// 읽어온 각 줄을 스트림으로 처리하여 모두 이어붙인 후 하나의 문자열로 반환
	br.close();
```

# Json 파일 처리
1. `implementation 'org.springframework.boot:spring-boot-starter-json'` 추가
2. `ObjectMapper`를 사용할 수 있게 됨
3. json 을 다룰 수 있는 형태의 자바 object 타입으로 바꿔서 가져옴