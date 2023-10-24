# Spring Boot를 이용하여 Api 호출할 때 double encoding Problem


# 사건의 발단

"[https://api.odsay.com/v1/api/searchPubTransPathT?lang=0&output=json&SX=127.0368&SY=37.50066001&EX=127.0339528&EY=37.50732819&OPT=0&apiKey=](https://api.odsay.com/v1/api/searchPubTransPathT?lang=0&output=json&SX=127.0368&SY=37.50066001&EX=127.0339528&EY=37.50732819&OPT=0&apiKey=fIjyUAGsU4ya8+K+3lTfAafT8TQL/F/QVrSR25LvePI)fIjyUAGsU4ya8%2BK%2B3lTfAafT8TQL%2FF%2FQVrSR25LvePI”

로 올바르게 api 호출을 보내고 있었으나 제대로 응답이 오지 않는 문제가 발생

![Untitled](Spring%20Boot%E1%84%85%E1%85%B3%E1%86%AF%20%E1%84%8B%E1%85%B5%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%84%8B%E1%85%A7%20Api%20%E1%84%92%E1%85%A9%E1%84%8E%E1%85%AE%E1%86%AF%E1%84%92%E1%85%A1%E1%86%AF%20%E1%84%84%E1%85%A2%20double%20en%20951d0a39c8b24738bfd25d272e618835/Untitled.png)

문의 결과 이러한 답변을 받음

갖가지 경우의 수를 따지며 호출을 시도할 때도 안돼서 결국 String 형식으로 아예 url을 전달하고 있었기에 인코딩 에러가 발생하는게 이해가 되지 않았다. 그래서 Spring 자체의 이슈인가 싶어 검색을 한 결과…

# 전개

[RestTemplate 사용시 URL 인코딩 이슈](https://lng1982.tistory.com/341)

[[Spring] RestTemplate + UriComponentBuilder 사용시 double url encoding 을 조심하자](https://velog.io/@dailylifecoding/becareful-for-Spring-RestTemplate-UriComponentBuilder-double-url-encoding)

[Spring restTemplate UrlEncoding](https://taes-k.github.io/2019/11/15/spring-resttemplate-url-encoding/)

UriComponentBuilder, RestTemplate 모두 자체적으로 내부 인코딩을 거치는 과정이 있었다. 특히 RestTeamplate의 경우 url 인자로 String 타입을 전달하면 강제로 인코딩을 시켜버리는데, https:// 로 보내버려도 : 나 // 같은 문자가 아예 다른 % 어쩌고로 인코딩이 되어버려 제대로 된 url이 전달되지않았다!!!! 이런...(UriComponentBuilder의 경우 어떤 조건에서 인코딩을 시키는 지는 제대로 확인하지 못했지만, 내부적으로 인코딩을 거치는 과정이 있는 건 확실하다)

# 해결

인코딩을 어떤 조건에서 거치는 지 확실하지 않은 UriComponentBuilder는 제외하고, RestTemplate으로 요청을 보내기로 결정했다. url 값을 String으로 보낼 때 문제가 발생하기 때문에 String 값을 uri로 변경하여 인자를 넘기기로 했다.

```java
String apiUrl = "대충문자열"

URI urur = URI.create(apiUrl);

String response1 = restTemplate.getForObject(urur, String.class);

DONE!
```

URI 클래스의 create 메소드를 이용하여 URI 객체를 생성하고 전달하여 응답을 잘 받아왔다.

이걸로 이틀날림 수구링
