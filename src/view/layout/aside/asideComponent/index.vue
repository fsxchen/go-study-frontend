<template>
  <component :is="menuComponent" :routerInfo="routerInfo">
    <template v-if="routerInfo.children.length">
      <AsideComponent :key="item.name" :routerInfo="item" v-for="item in routerInfo.children" />
    </template>
  </component>
</template>

<script>
import MenuItem from './menuItem'
import AsyncSubmenu from './asyncSubmenu'

export default {
  name: 'AsideComponent',
  computed:{
      menuComponent(){
          if(this.routerInfo.children.length){
              return 'AsyncSubmenu'
          }else{
              return 'MenuItem'
          }
      }
  },
  props: {
    routerInfo: {
      default: function() {
        return null
      },
      type: Object
    }
  },
  components: {
    MenuItem,
    AsyncSubmenu
  }
}
</script>
<style lang="scss">
</style>