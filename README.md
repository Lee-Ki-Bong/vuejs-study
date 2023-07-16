# Setup

### vscode 확장 설치

- vetur
- HTML CSS Support
- Vue 3 Snippets

#

### vue 버전 확인

```
vue --version
```

#

### vue 프로젝트 생성

```
vue create vuedongsan
Vue CLI v5.0.8
? Please pick a preset: Default ([Vue 3] babel, eslint)
? Pick the package manager to use when installing dependencies: Yarn
```

#

# 프로젝트 관리 명령어

### Project setup

```
yarn install
npm install

```

### 개발 모드에서 컴파일 및 핫 리로딩

```
yarn serve
npm run serve

```

### 프로덕션용 컴파일 및 최소화

```
yarn build
npm run build
```

### 코드 스타일 검사 및 파일 수정

```
yarn lint
npm run lint
```

#

# 데이터 바인딩

### 기본

- src/App.vue

```javascript

<script>
export default {
  name: 'App',
  data() {
    // 데이터 보관람부터 있어야함.
    return {
      price1: 60,
      price2: 70,
    };
  },
  components: {},
};
</script>
```

- 이렇게 바인딩 할 수 있다.

```javascript
<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <div>
    <h4>원룸</h4>
    <p>{{ price1 }} 만원</p>
  </div>
  <div>
    <h4>XX 원룸</h4>
    <p>{{ price2 }} 만원</p>
  </div>
</template>
```

#

### 반복문을 이용한 바인딩

```javascript
<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <div v-for="(product, idx) in products" :key="idx" :id="idx">
    <h4>{{ product.name }}원룸</h4>
    <p>{{ product.price }} 만원</p>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      products: [
        {
          name: '역삼동원룸',
          price: 50,
        },
        {
          name: '천호동원룸',
          price: 60,
        },
        {
          name: '마포구원룸',
          price: 70,
        },
      ],
    };
  },
  components: {},
};
</script>
```

#

# 이벤트 핸들러

### 클릭 이벤트

```javascript
<button v-on:click="<이벤트함수>">허위매물신고</button>
```

```javascript
<button @click="<이벤트함수>">허위매물신고</button>
```

- 이처럼 해당 값을 변경하여 html 변경없이 값만 랜더링이 가능.

```javascript
    <button v-on:click="product.report_count += 1">허위매물신고</button>
    <span>신고수: {{ product.report_count }}</span>
```

#

# 함수

```javascript
<script>
export default {
  name: 'App',
  data() {
    return {};
  },
  methods: {}, // 이곳에서 정의한다.
  components: {},
};
</script>
```

- 사용예제

```javascript
  methods: {
    countUp(product) {
      product.report_count += 1;
    },
  },

  <button v-on:click="countUp(product)">허위매물신고</button>
```

- 함수내에서의 this

```javascript
  data() {
    return {
      // 이곳을 가리킨다.
    };
  },
```

#

# 동적인 UI

- UI 현재상태 데이터 저장
- 데이터에 따라 UI가 어떻게 보일지 작성

### 모달창

```javascript

  // data
  modal: {
    is_open: false,
  },

  // template
  <div class="black-bg" v-if="modal.is_open" @click="modalClose()">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
    </div>
  </div>

  // function
  modalOpen() {
    this.modal.is_open = true;
  },
  modalClose() {
    this.modal.is_open = false;
  },
```
