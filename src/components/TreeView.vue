
<template>
  <md-card>
    <md-card-content>
      <div class="tree">
        <div class="node">
          <div class="column">Head</div>
          <div class="column">Head</div>
          <div class="column">Head</div>
          <div class="column">Head</div>
          <div class="column end">Head</div>
          <div class="children">
            <template v-for="(tree, i) in trees">
              <tree-node :node="tree" :key="i" :level="1"></tree-node>
            </template>
          </div>
        </div>
      </div>
    </md-card-content>
  </md-card>
</template>

<script>
import TreeNode from "./TreeNode.vue";
export default {
  components: {
    TreeNode,
  },
  data() {
    return {
      trees: [
        {
          name: "Node 1",
          children: [
            {
              name: "Node 1.1",
              children: [
                {
                  name: "Node 1.1.1",
                  children: [{ name: "Node 1.1.1" }],
                },
                {
                  name: "Node 1.1.1",
                  children: [],
                },
                {
                  name: "Node 1.1.1",
                  children: [],
                },
                {
                  name: "Node 1.1.1",
                  children: [],
                },
              ],
            },
          ],
        },
        {
          name: "Node 1",
          children: [
            {
              name: "Node 1.1",
              children: [
                {
                  name: "Node 1.1.1",
                  children: [{ name: "Node 1.1.1" }],
                },
              ],
            },
          ],
        },
        {
          name: "Node 1",
          children: [
            {
              name: "Node 1.1",
              children: [
                {
                  name: "Node 1.1.1",
                  children: [{ name: "Node 1.1.1" }],
                },
              ],
            },
          ],
        },
        {
          name: "Node 1",
          children: [
            {
              name: "Node 1.1",
              children: [
                {
                  name: "Node 1.1.1",
                  children: [{ name: "Node 1.1.1" }],
                },
              ],
            },
          ],
        },
      ],
    };
  },
};
</script>

<style scoped>
.tree {
  display: grid;
  gap: 10px;
}

.node {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}

.column {
  padding: 5px;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  display: flex;
  align-items: center;
}
.end {
  display: flex;
  justify-content: end;
}
.children {
  grid-column: 1 / span 5;
  margin-top: 10px;
}
.node > .column:last-child {
  justify-self: end; /* Aligning the last column to the right */
}
</style>