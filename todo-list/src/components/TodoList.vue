<template>
  <div>
    <ul>
      <li
        v-for="(todoItem, index) in propsdata"
        v-bind:key="index"
        class="shadow"
      >
        <!-- v-bind:class="{xxxx}" 속성을 통해서 특정한 값에 따라서 css 를 적용 할 수 있다 -->
        <i
          class="checkBtn fas fa-check"
          v-bind:class="{ checkBtnCompleted: todoItem.completed }"
          v-on:click="toggleComplete(todoItem, index)"
        ></i>
        <span v-bind:class="{ textCompleted: todoItem.completed }">{{
          todoItem.item
        }}</span>
        <span class="removeBtn" v-on:click="removeTodo">
          <i class="fas fa-trash-alt"></i>
        </span>
      </li>
    </ul>
    
  </div>
</template>

<script>
export default {
  props: [
    'propsdata'
  ],
  
  methods: {


    removeTodo: function (todoItem, index) {
      localStorage.removeItem(todoItem);
      this.$emit('removeOneItem', todoItem, index);
    },
     toggleComplete : function(todoItem){
        todoItem.completed = !todoItem.completed;
        
        //로컬 스토리지 데이터 갱신
        localStorage.removeItem(todoItem.item);
        localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
     }
  },

 
};
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0;
  margin-top: 0;
  text-align: left;
  max-width: 600px;
}

li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  background: white;
  border-radius: 5px;
  width: 90%;
  margin: 10px auto;
}

li > span:nth-child(1) {
  padding: 0 0.9rem;
}

.checkBtn {
  line-height: 50px;
  color: #62acde;
  margin-right: 5px;
  padding: 0 10px;
}
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}
.removeBtn {
  margin-left: auto;
  padding-right: 20px;
  color: #f75f5f;
  cursor: pointer;
}


</style>
