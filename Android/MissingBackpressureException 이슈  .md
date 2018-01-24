## MissingBackpressureException 이슈    

#### What    

Crash의 대부분을 차지하던 예외였다. 원인은 Rx Android 를 발생한 것이었는데, 내용은 이러하다.  

보통 Rx android 를 사용할 경우 observeOn(AndroidSchedulers.mainThread()) 을 이용하여 UI 쓰레드에 수신된 데이터를 반영하는 로직을 짠다. 그런데 이미 UI 쓰레드에서 다른 작업을 처리하고 있어 observable 에서 보낸 데이터를 바로 처리하지 못할 경우 해당 예외가 발생한다.  

  

#### Soulution  

onBackpressureBuffer() 메소드를 추가해주면 된다. 해당 메소를 추가해주면 처리되지 못한 항목이 큐에 저장되며, 후에 순차적으로 처리된다!  

[참고글](http://kunny.github.io/community/2016/02/08/gdg_korea_android_weekly_02_1/)





