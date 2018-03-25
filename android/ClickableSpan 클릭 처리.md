# ClickableSpan 클릭 처리
ClickableSpan을 상속받은 커스텀 Span을 사용할 경우 TextView에
  
~~~java
textView.setMovementMethod(LinkMovementMethod.getInstance());
~~~
위와같이 세팅 해줘야 clickable span이 먹은 spannable text를 클릭했을 때 클릭 이벤트를 감지한다.
