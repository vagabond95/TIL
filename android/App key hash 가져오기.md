# App Key hash 가져오기
외부 SDK를 이용하다보면 App 키해시 를 요구하는 상황을 빈번히 맞이한다. 키해시는 해당 app을 구별할 수 있는 고유의 값으로써 debug 키해시, release 키해시로 나뉜다.  
  
key hash 를 구하는 방법은  
1. 커맨드에서 keytool 을 이용  
2. 소스코드를 이용  

2가지로 나뉜다.  
리서치를  해보면 keytool 의 경우 사용자의 세팅환경에 따라 값이 달라질 수 있어 권장하지 않는다. 본인 역시 keytool 을 이용하여 가져온 key hash 값의 경우 올바르게 인식하지 못하는 문제를 겪었다. 따라서 소스코드에서 얻는 방법만 명시하고자 한다.  
  
~~~java
private void getAppKeyHash() {
    try {
      PackageInfo info = getPackageManager().getPackageInfo(getPackageName(), PackageManager.GET_SIGNATURES);
      for (Signature signature : info.signatures) {
        MessageDigest md;
        md = MessageDigest.getInstance("SHA");
        md.update(signature.toByteArray());
        String key = new String(Base64.encode(md.digest(), 0));
        Logger.e("package name : " + getPackageName());
        Logger.e("Hash key : " + key);
      }
    } catch (Exception e) {
      // TODO Auto-generated catch block
      Log.e("name not found", e.toString());
    }
  }
~~~  
위 코드를 통해 디버그 빌드를 할 경우 디버그 키해시, 릴리즈 빌드를 할 경우 릴리즈 키해시 값을 얻을 수 있다.

**사용시 참고사항**  
1. 실수를 방지하기 위해 Package name 을 하드코딩 하지말고 getPackageName() 메소드를 이용할 것.
2. 배포하기전에 릴리즈 키해시를 등록해둘 것. (개발할 때 미리 디버그, 릴리즈 키해시 모두 등록해두면 좋다.)
