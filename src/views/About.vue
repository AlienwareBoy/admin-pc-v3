<template>
  <div>{{name}}</div>
</template>

<script lang='ts'>
import { reactive, toRefs, onBeforeMount, onMounted, onUnmounted } from "vue";
let timer: number = 1;
interface DataProps {
  name: number;
}
export default {
  name: "sdf",
  setup() {
    const data: DataProps = reactive({
      name: 123,
    });
    onBeforeMount(() => {
      console.log("2.组件挂载页面之前执行----onBeforeMount");
    });
    onMounted(() => {
      console.log("3.-组件挂载到页面之后执行-------onMounted");
    });
    onUnmounted(() => {
      console.log(new Date().getTime() - timer);
    });
    const refData = toRefs(data);
    return {
      ...refData,
    };
  },
};
</script>
<style scoped>
</style>