# Stream

Java에서 사용하는 Stream은 원본 데이터를 수정하지 않고, 필터링하고 가공하여 원하는 결과를 얻을 수 있도록 해줍니다. 람다를 사용할 수 있고, 내부 반복을 사용하여 간단한 코드를 작성할 수 있습니다. 요소들의 매핑, 필터링, 정렬을 하는 중간 연산 메소드와 가공한 스트림을 가지고 원하는 결과물로 만들어 내도록 하는 최종 연산 메소드로 구성되어 있습니다.

<br>

____

<br>

+ 스트림은 자바8부터 추가된 컬렉션의 저장 요소를 하나씩 참조해서 람다식으로 처리할 수 있도록 해주는 반복자입니다.

```java
데이터소스객체집합.stream().중개연산().최종연산();

return new ProfileReviewResponse(reviews.stream().map( //중간 연산 ex) map(), filter()
                review -> ProfileReviewDto.builder()
                        .id(review.getId())
                        .nickname(review.getWriter().getNickname())
                        .grade(review.getGrade())
                        .comment(review.getComment())
                        .createdAt(review.getCreatedAt())
                        .build()
        ).collect(Collectors.toList())); //최종 연산
```

+ 중간 연산 메소드는 리턴 타입이 스트림이므로, 계속해서 다른 스트림 메소드를 연결해 사용할 수 있다.
+ 최종 연산 메소드는 리턴타입이 스트림이 아니며, 메소드 체이닝을 끝내는 역할을 한다.
+ 최종 연산이 실행되어야 중간 연산도 처리되기 때문에, 중간 연산들만으로 구성된 메소드체인은 실행되지 않는다.

> 메소드 체이닝 : OOP(객체 지향 프로그래밍)에서 여러 메소드를 이어서 호출하는 문법이다. 메소드가 객체를 반환하여 여러 메소드를 순차적으로 선언할 수 있도록 한다.