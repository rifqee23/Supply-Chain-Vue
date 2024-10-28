<script setup>
import { ref } from "vue";

import Nav from "./components/Fragments/Nav.vue";
import SupplierComponent from "./components/Fragments/SupplierList.vue";
import Home from "./components/Fragments/Home.vue";
import Item from "./components/Fragments/ItemList.vue";
import Stackholder from "./components/Fragments/StackholderList.vue";
import SupplierForm from "./components/Fragments/SupplierForm.vue";

const currentPage = ref("home");

const handleNavigation = (page) => {
  currentPage.value = page;
};
</script>

<template>
  <Nav @navigate="handleNavigation" />
  <div>
    <Home v-if="currentPage === 'home'" />
    <SupplierComponent v-if="currentPage === 'supplier'" />
    <Item v-if="currentPage === 'item'" />
    <Stackholder v-if="currentPage === 'stackholder'" />
  </div>
</template>
