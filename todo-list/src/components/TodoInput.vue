<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem"  v-on:keyup.enter="addTodoItem" placeholder="add new todo "> 
        <span class="addContainer" v-on:click="addTodoItem">
            <i class="far fa-plus addBtn" aria-hidden="true"></i>
        </span>
    </div>
</template>

<script>
export default {
    data: function(){
        return {
            newTodoItem: ""
        }
    },

    methods: {
        addTodoItem : function(){
            if(this.newTodoItem !== '') {
                //emit을 통해 이벤트를 발생시키고 인자로 this.newTodoItem을 넘김
                this.$emit('addTodoItem', this.newTodoItem);
                var obj = {completed: false, item: this.newTodoItem};
                localStorage.setItem(this.newTodoItem, JSON.stringify(obj));
                this.clearInput();
            }
        },
        clearInput: function(){
            this.newTodoItem=""; // 비워주기(초기화)
        }
    }
}
</script>

<style scoped>
input {
    max-width: 600px;
    width: 90%;
}

input:focus {
    outline: none;
}

.inputBox {
    max-width: 600px;
    width: 90%;
    margin: 0 auto;
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
}
.inputBox input {
    border-style: none;
    font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #98c1ff, #5280ff);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
  cursor: pointer;
}

.addBtn {
  color: white;
  vertical-align: middle;
}
</style>