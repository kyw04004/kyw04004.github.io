---
title: 스프링에서 테스트 코드 작성하기 - BDDMockito
categories:
- Spring
excerpt: "BDDMockito에 대한 포스팅입니다."
feature_text: |
  ## Spring 테스트 코드
  BDDMockito
feature_image: "https://picsum.photos/2560/600?image=733"
image: "https://picsum.photos/2560/600?image=733"


---

### Mockito란?
- Mock 객체를 쉽게 만들고 관리하고 검증할 수 있는 방법을 <br> 제공해주는 프레임워크 중 하나.
	+ Mock이라는 것은 가짜를 의미.
- Spring boot에서 가장 많이 사용되는 테스트 프레임워크.
- Stub이라는 기술을 주로 사용하여 검증.
	+ Stub이란 메소드의 결과를 미리 지정하는 것.
- 데이터베이스를 사용하지 않는 단위 테스트.
- 통합 테스트보다 가볍고 빠름. 의존하지 않음.
- BDDMockito란 Mockito를 상속받은 메서드 이름만 다른 프레임워크.
	+ BDD할 때 Mockito의 메서드명이 가독성을 해쳐서 사용.
	+ BDD란 행위 주도 개발. 즉, 시나리오를 기반으로 테스트하는 패턴.

<br>

### 사용법
- class 위에 @ExtendWith(MockitoExtension.class) 애노테이션 사용
- @Mock 애노테이션을 사용해서 Mock 객체를 만들어줌.
- Given : 메서드의 예상값을 지정해둔다. Stub.
	+ given사용. ex) given(메서드).willReturn(예상값);
- When : 예상값을 사용해본다.
- Then : 예상한 결과가 맞게 나오는지 확인한다.
	+ Assertions.assertThat 사용.
	+ then 사용.

<br>

### 사용 예시
```java
@ExtendWith(MockitoExtension.class)
public class UserServiceTest {

    //Mock 객체 만들기
    @Mock UserService userService;

    @DisplayName("회원정보 조회")
    @Test
    void getUser() {
        
        //given
        
        //값 세팅
        UserDto userDto = new UserDto(1L,null,null,null,null,null);
        
        //예상값 지정
        given(userService.getUser(1L)).willReturn(userDto);

        
        //when
        
        //예상한 메서드 사용하기.
        UserDto user2 = userService.getUser(1L);

        
        //then
        
        //user2와 userDto가 같은지.
        Assertions.assertThat(user2).isEqualTo(userDto);
        //메서드가 한번 사용되었는지.
        then(userService).should(times(1)).getUser(1L);
        
    }
```

<br>

### 레퍼런스

[https://velog.io/@lxxjn0/Mockito%EC%99%80-BDDMockito%EB%8A%94-%EB%AD%90%EA%B0%80-%EB%8B%A4%EB%A5%BC%EA%B9%8C](https://velog.io/@lxxjn0/Mockito%EC%99%80-BDDMockito%EB%8A%94-%EB%AD%90%EA%B0%80-%EB%8B%A4%EB%A5%BC%EA%B9%8C)
[https://beststar-1.tistory.com/31](https://beststar-1.tistory.com/31)

