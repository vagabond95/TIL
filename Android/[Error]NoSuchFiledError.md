## NoSuchFiledError


여러 모듈의 코드를 합칠 때 resource의 id 중복될 경우에 발생하는 Error<br>
중복되는 id가 있을 때 id 하나를 지워버려서 결국 인식을 못하게 되어 발생하게 됨. 런타임에 발생하므로 주의할필요가 있음. <br>
**Solution**
id 가 중복되어 발생하는 오류이므로, id 를 유니크하게 지으면 ok. 
id resource 에 대한 컨벤션도 정해놓고 작성하는 것이 좋음. 해당 모듈을 나타낼 수 있는 prefix 를 id 앞에 달아주면 왠만해서는 예방할 수 있을 것
<br>
[stackOverflow](https://stackoverflow.com/questions/16204667/nosuchfielderror-on-findviewbyid)