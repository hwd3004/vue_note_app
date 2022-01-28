import { reactive } from '@vue/reactivity';
<template>
  <div class="memo">
    <div class="act">
      <button class="btn btn-primary" @click="add()">+ 추가</button>
    </div>
    <ul>
      <li v-for="d in state.data" :key="d.id" @click="edit(d.id)">
        {{ d.content }}
      </li>
    </ul>
  </div>
</template>


<script>
import { reactive } from "@vue/reactivity";
import axios from "axios";

export default {
  // script 입력하고 ctrl + 스페이스 한 다음 2번쩨
  setup() {
    // 상태관리와 리렌더링
    const state = reactive({
      // data: ["메모 1", "메모 2", "메모 3", "메모 4", "메모 5"],
      data: [],
    });

    const add = () => {
      // state.data.push("추가된 메모");

      const content = prompt("내용 입력 : ");

      axios.post("/api/memos", { content }).then((res) => {
        console.log(`post result : ${res.data}`);
        state.data = res.data;
      });
    };

    const edit = (id) => {
      const content = prompt("내용 수정 : ", state.data[id]);
      console.log(content);

      axios.put(`/api/memos/${id}`, { content }).then((res) => {
        state.data = res.data;
      });
    };

    axios.get("/api/memos").then((res) => {
      console.log(`get result : ${res.data}`);
      state.data = res.data;
    });

    return { state, add, edit };
  },
};
</script>

<style lang="scss" scoped>
.memo {
  .act {
    padding: 10px 10px 5px 5px;
    text-align: right;
  }
  ul {
    list-style: none;
    padding: 15px;
    margin: 0;

    li {
      padding: 15px;
      margin: 10px 0;
      border: 1px solid #eee;
    }
  }
}
</style>