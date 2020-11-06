- vue3通过`getCurrentInstance`来获取当前组件实列，从而获取`$route`等信息

```
import { reactive, onMounted, computed, getCurrentInstance  } from 'vue'
// import { useRoute } from "vue-router";
export default {
    name: 'Main',
    setup() {
        const { ctx } = getCurrentInstance();
        const state = reactive({
            count: 0,
            key: computed(() => { return ctx.$root.$route.path})
        })

         onMounted(() => {
         console.log('mounted!')
            // console.log(this.$router);
        })

        function getRouter() {
            console.log(ctx.$root.$route)   //获取路由对象信息
        }
        return {
            state,
            getRouter
        }
    },

```
