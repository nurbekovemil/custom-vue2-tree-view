<template>
  <div class="node">
    <div class="column cursor">
      <div
        :style="{ marginLeft: level >= 2 ? 10 * level + 'px' : 0 + 'px' }"
        @click="toggle"
      >
        <template v-if="expanded">
          <md-icon>arrow_drop_down</md-icon>
        </template>
        <template v-else>
          <md-icon>arrow_right</md-icon>
        </template>
        {{ node.name }}
      </div>
    </div>
    <div class="column">Column 2</div>
    <div class="column">Column 3</div>
    <div class="column">Column 4</div>
    <div class="column end">Column 5</div>
    <div v-show="expanded" class="children">
      <tree-node
        v-for="child in node.children"
        :key="child.id"
        :node="child"
        :level="level + 1"
      ></tree-node>
    </div>
  </div>
</template>

<script>
export default {
  name: "TreeNode",
  props: ["node", "level"],
  data() {
    return {
      expanded: false,
    };
  },
  methods: {
    toggle() {
      this.expanded = !this.expanded;
    },
  },
};
</script>

<style scoped>
.node {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  /* grid-template-columns: repeat(4, 1fr) auto; Four columns with equal width and the last column taking remaining space */
  background-color: #ffffff;
}
.node:nth-child(odd) {
  background-color: #f9f9f9;
}
.column {
  padding: 5px;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  display: flex;
  align-items: center;
}
.cursor {
  cursor: pointer;
}
.end {
  display: flex;
  justify-content: end;
}

.column.label {
  padding-right: 10px;
}

.column.label.root {
  background-color: lightblue;
}

.children {
  grid-column: 1 / span 5;
  margin-top: 10px;
}

.node > .column:last-child {
  justify-self: end;
}
</style>