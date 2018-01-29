# Locale 값 이슈  
### what  
디바이스에서 현재 사용하고 있는 Language 정보를 가져오기 위해 Locale 값을 이용할 때가 있다.  
그때 보통 일반적인 솔루션이  
~~~java
Locale.getDefault()
~~~
다음과 같이 default 메소드를 이용하는 것이다.  
  
하지만 이 방법은 한가지 문제가 존재하는데, 이렇게 가져온 Locale 값은 해당 app 이 켜졌을 때 static 하게 저장되는 값이라는 것이다. 즉, app 이 이미 구동되고 있는 상태에서 Language가 변경됐을 경우 위와 같은 방법으로 얻은 Locale 을 이용하게 되면 원하는 Language 값을 값을 얻지 못할 수 있다.  
  
  
### Soulution
~~~java
Locale current = contextgetResources().getConfiguration().locale;
~~~
위 방법을 사용하면 중간에 Language 가 변경되었더라도 값을 올바르게 가져오게된다.  
[StackOverflow](https://stackoverflow.com/questions/14389349/android-get-current-locale-not-default)
