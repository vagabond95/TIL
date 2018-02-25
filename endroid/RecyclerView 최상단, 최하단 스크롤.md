## Recycler View 최하단, 최상단 스크롤 이벤트 감지  
Recycler View 를 이용하다보면 최상단, 최상단으로 스크롤을 했을 때 이벤트를 처리해줄 일이 종종 있다. 일반적인 해결책으로는 position 값을 통해 가장 마지막에 있는 아이템이 그려졌을 경우 이벤트처리를 해주곤 한다. 해당 방법의 문제는 마지막 아이템이 보이기 시작한 때부터 이벤트가 발동된다는 것. 즉, 정확히 최하단에 스크롤이 갔을 때 발동되는 것이 아니기 때문에 원하지 않는 결과가 나올 수 있다.  
#### Solution  
Recycler View 에서 자체적으로 제공하는 **canScrollVertically** 메소드를 이용할 경우 위 문제를 깔끔히 해결할 수 있다. 
~~~java
if(!recylcerView.canScrollVertically(-1)) {
    // 최상단 스크롤
}
if(!recyclerView.canScrollVertically(1)) {
    // 최하단 스크롤
}
~~~  

위 코드 처럼 인자만 바꾸어 Catch 할 상태를 정하고(최상단/최하단) 내부에 해당 이벤트를 적어주면 끝.

~~~java
recyclerView.setOnScrollListener(recyclerView, state -> {
        if (!recyclerView.canScrollVertically(1)) {
            Log.i(TAG, "최상단 스크롤시 이벤트 처리!");
        } else if (!recyclerView.canScrollVertically(1)) {
            Log.i(TAG, "최하단 스크롤시 이벤트 처리!");
        } else {
            Log.i(TAG, "일반적인 스크롤 상태");
        }
    }
);
~~~

다음과 같이 구현해서 사용할 수 있다.