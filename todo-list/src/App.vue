<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodoItem="addOneItem"></TodoInput>
    <TodoList
      v-bind:propsdata="todoItems"
      v-on:removeOneItem="removeTodo"
    ></TodoList>

    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from "./components/TodoHeader.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";
import TodoFooter from "./components/TodoFooter.vue";

export default {
  name: "App",
  components: {
    TodoHeader: TodoHeader,
    TodoInput: TodoInput,
    TodoList: TodoList,
    TodoFooter: TodoFooter,
  },

// 데이터 속성이 변경될 때 화면을 재렌더링하여 변경된 데이터 반영
  data: function () {
    return {
      todoItems: [],
      showModal: false,
      itemToDelete: null,
    };
  },

  methods: {
    addOneItem: function (todoItem) {
      //input 컴포넌트에서 이벤트를 발생시키면 addTodoItem 과 함께 todoItem 도 딸려서 올라온다.
      //이걸 활용해서 객체를 만들고 localStorage 에 넣어준다.
      //그리고 나서 App.vue 의 data() 영역에 있는 todoItems 에도 push 를 하게 되면 바로바로 화면이 갱신이 된다.
      var obj = { completed: false, item: todoItem };
      localStorage.setItem(todoItem, JSON.stringify(obj));
      this.todoItems.push(obj);
    },

  
    clearAll(){
      localStorage.clear();
      this.todoItems = [];
    }
  },

  created: function () {
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++) {
        if (localStorage.key(i) !== "loglevel:webpack-dev-server") {
          //완료버튼 토글을 위해 JSON 형식으로 localStorage에 저장해둔걸 꺼내서 todoItems에 넣음
          //이렇게 하면 {"completed":false, "item": aaa} 이게 나오게 되고
          //이걸 JSON.parse 하면 다시 객체 형식으로 todoItems에 push 됨
          this.todoItems.push(
            JSON.parse(localStorage.getItem(localStorage.key(i)))
          );
        }
      }
    }
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Itim&display=swap");

html,
body {
  font-family: "Itim", cursive;
}

#app {
  font-family: "Itim", cursive;
}

body {
  text-align: center;
  background-color: #f6f6f6;
}

input {
  border-style: groove;
  width: 200px;
}

/* 모달 스타일 */
.modal {
  position: fixed;
  z-index: 9999;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  background-color: white;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
  width: 300px;
}

button {
  margin-top: 10px;
  padding: 5px 10px;
  cursor: pointer;
  margin-left: 10px;
}


</style>
