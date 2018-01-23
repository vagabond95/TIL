## NoSuchFiledError

**What**  
하나의 프로젝트에 여러 모듈의 코드를 합칠 때 resource의 id 중복될 경우에 발생할 수 있는 Error 이다.  
프로젝트에 중복되는 id가 있을 경우 그중 하나를 자동으로 지워버려서 기존의 코드가 resource id 를 인식하지 못하는 상황이 발생하는 것. 런타임에 발생하므로 까다로울 수 있음!!  
 
**Solution**  
id 가 중복되어 발생하는 오류이므로, id 를 유니크하게 지으면 ok. 해당 모듈을 특징지을 수 있는 prefix 를 id 앞에 달아주면 왠만해서는 예방할 수 있음.  
당연한 얘기이지만 개발 시 id resource 에 대한 컨벤션을 정해놓고 작성하는 것이 좋다. 
ex) ch_desk_message_text
<br>
[stackOverflow](https://stackoverflow.com/questions/16204667/nosuchfielderror-on-findviewbyid)
