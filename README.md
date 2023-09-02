## 인스턴스 등록

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

## 인스턴스 생성

- 생성자 함수 객체 생성

        funtion Person(name, job){
         this.name = name;
         this.job = job;
        }}
        
        var p = new Person('josh', 'developer');
        
        p 콘솔
        
        Object { name: "josh", job: "developer" }
        job: "developer"
        name: "josh"
      
      
        function Vue(){
        this.logText = function(){
          console.log('hello');
        }}
      
        var vm = new Vue();
      
        vm.logText();
        로그 hello

- 인스턴스 속성 등록

      var vm = new Vue({
      el: '#app',
      data: {
        message: 'hi'
      },
      methods: {
    
      },
      created: function() {
    
      }});

## 뷰 컴포넌트

- 재사용성 : 컴포넌트 기반으로 코드의 반복을 줄여 빠르게 화면을 제작, 컴포넌트간의 관계도 생김

  기본 컴포넌트를 생성하면 - root(부모 컴포넌트)가 생성됨

  - 전역 컴포넌트(하위 컴포넌트)로 등록
    
      <!-- #app인스턴스 -->
      <div id="app">
        <app-header></app-header>
        <app-content></app-content>
      </div>
  
        //전역 컴포넌트 등록
        Vue.component('app-header', {
          //마크업
          template: '<h1>Header</h1>'
        });
        Vue.component('app-content', {
          template: '<div>Content</div>'
        });
    
        //부모컴포넌트 root
        new Vue({
          el: '#app',
        });

  - 지역 컴포넌트
