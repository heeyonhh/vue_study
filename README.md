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

        new Vue({
          el: '#app',
          components: {
            'app-footer': {
              template: '<footer>Footer</footer>'
            }}});

        태그 등록

    실무에서 구현할때는 대부분 지역 컴포넌트로 등록

    전역 컴포넌트는 : 플러그, 라이브러리 형태

## 인스턴스와 컴포넌트의 관계

인스턴스를 또 생성하면 지역 컴포넌트는 또 등록해야함 / 전역 컴포넌트는 등록할 필요 없음

## 컴포넌트 통신 방식

데이터는 각각 관리 공유하려면 상위 > 하위 컴포넌트 : props로 전달(데이터를 내려줌) / 하위 > 상위 컴포넌트 : 이벤트를 올려줌

컴포넌트 간의 데이터 전달은 서비스를 구현하다보면 관계 추적하기가 어려움

- 흐름이 통일되어있어야함 아래 방향 '데이터 프롭스' 위 방향 '이벤트 에밋'

## Props

        <div id="app">
        <app-header v-bind:propsdata="message"></app-header>
        <app-content v-bind:propsdata="num"></app-content>
        </div>
        
        var appHeader = {
          // template : '<h1>header</h1>',
          template : '<h1>{{propsdata}}</h1>',
          props: ['propsdata']
        }
        var appContent = {
          template : '<h1>{{propsdata}}</h1>',
          props: ['propsdata']
        }
        
        new Vue({
          el: '#app',
          components: {
            'app-header': appHeader,
            'app-content': appContent
          },
          data: {
            message: 'hi props',
            num: 10
          }
        })

## Emit
