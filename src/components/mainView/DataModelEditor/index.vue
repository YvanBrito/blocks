<template>
  <div class="middle">
    <div class="tabs">
      <Tab
        v-for="(dm, index) in dataModels"
        :dataModel="dm"
        :index="index"
        :key="index"
      />
      <button class="btn addModel" @click.prevent="addDataModel()" />
    </div>
    <Table />
  </div>
</template>

<script>
import { mapGetters, mapMutations } from "vuex";

import Table from "./Table";
import Tab from "./Tab";

export default {
  name: "DataModelEditor",
  components: {
    Table,
    Tab,
  },
  mounted() {
    this.addDataModel();
  },
  computed: {
    ...mapGetters(["dataModels"]),
    dataModelID() {
      return this.dataModels.map((dm) => dm.ID);
    },
  },
  methods: {
    ...mapMutations(["addDataModel"]),
  },
};
</script>

<style src="./style.scss" lang="scss" scoped />
