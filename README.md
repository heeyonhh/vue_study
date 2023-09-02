# 인스턴스 등록

 + vue cdn 스크립트
 <div id="app>
  //엘리먼트 등록으로 뷰 사용 시작
 </div>
 <script>
   var vm = new Vue({
     el: '#app'
     data: {
       message: 'hi'
     }
   });
 </script>

-> vm 콘솔 : 뷰에서 제공하는 api & 속성

# 인스턴스 생성

- 생성자 함수 객체 생성

  funtion Person(name, job){
   this.name = name;
   this.job = job;
  }
  
  var p = new Person('josh', 'developer');
  
  -> p 콘솔
  
  Object { name: "josh", job: "developer" }
  job: "developer"
  name: "josh"


