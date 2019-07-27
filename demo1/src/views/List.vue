<template>
<div>
    <div>List</div>
    <div>
        <ul>
            <li v-for="(item, index) in pageList" :key="index">
                {{item.title}} - {{item.content}}
            </li>
        </ul>
    </div>
</div>

</template>
<script>
import store from '@/store'
export default {
    name: 'List',
    store,
    computed: {
         pageList() {
             return store.state.lists
         }
    }
}
</script>