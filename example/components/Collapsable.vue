<template>
  <ComponentExample link="Collapsable">
    <VueNestable
    expandable
    v-model="nestableItems">

      <VueNestableHandle
      slot-scope="{ item }" :item="item">
        <i class="fas fa-user" />


      <a @click="toggleExpansion(item)" v-if="item.children && item.children.length > 0">
        <slot name="expandable-trigger" :v-bind="item.expanded">
            <i :class="`${item.expanded ? 'fas fa-caret-up' : 'fas fa-caret-down'}`"></i>
        </slot>
      </a>

      {{ item.text }} <br>

      </VueNestableHandle>
    </VueNestable>
  </ComponentExample>
</template>

<script>
import ComponentExample from "./ComponentExample.vue";

export default {
  components: {
    ComponentExample
  },

  data() {
    return {
      nestableItems: [
        {
          id: 1,
          text:'Parent',
          expanded: false,
          children: [
            {
              id: 2,
              text:'First child',
              children: [],
              expanded: false,
            },
            {
              id: 3,
              text:'First child with children',
              expanded: false,
              children: [
                {
                  id: 4,
                  text:'First child',
                  children: [],
                  expanded: false,
                },
              ],
            },
          ],
        },
      ]
    };
  },
  methods: {
    toggleExpansion(item) {
      item.expanded = !item.expanded;
    }
  }
};
</script>

<style scoped>
</style>
