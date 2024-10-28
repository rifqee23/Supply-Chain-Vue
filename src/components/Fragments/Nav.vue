<script setup>
import { ref } from "vue";
import Button from "../Elements/Button.vue";
const isOpen = ref(false);
const isOpenMenu = ref(false);

const toogleMenu = () => {
  isOpen.value = !isOpen.value;
};

const subMenu = () => {
  isOpenMenu.value = !isOpenMenu.value;
};

const emit = defineEmits(["navigate"]);

const navigateTo = (page) => {
  emit("navigate", page);
};
</script>

<template>
  <nav class="bg-green-700 border-b border-green-500">
    <Button class="absolute left-2 top-5 md:hidden z-30" @click="toogleMenu">
      <i class="pi pi-align-justify text-2xl"></i>
    </Button>

    <div class="mx-auto max-w-7xl px-2 md:mx-0">
      <div class="relative flex h-16 items-center justify-between z-20">
        <div
          class="flex flex-1 items-center justify-center md:justify-start md:flex-auto"
        >
          <div class="flex justify-center flex-shrink-0 items-center md:pl-4">
            <h3 class="text-xl text-white">Supply Chain</h3>
          </div>
        </div>
      </div>
      <div>
        <div
          :class="{
            'hidden md:block': !isOpen,
            'absolute top-0 left-0 right-0 bottom-0 bg-white z-10 md:right-auto md:': true,
          }"
        >
          <ul class="flex flex-col justify-center mt-20 gap-y-2 text-gray">
            <li
              class="text-center px-2 hover:bg-orange-300 hover:cursor-pointer"
              @click="navigateTo('home')"
            >
              Home
            </li>
            <li
              class="text-center px-2 hover:bg-orange-300 hover:cursor-pointer"
              @click="subMenu"
            >
              Master Data
            </li>
            <ul :class="{ hidden: !isOpenMenu }">
              <li
                class="text-sm text-center px-2 hover:bg-orange-300 hover:cursor-pointer"
                @click="navigateTo('item')"
              >
                Data Barang
              </li>
              <li
                class="text-sm text-center px-2 hover:bg-orange-300 hover:cursor-pointer"
                @click="navigateTo('supplier')"
              >
                Data Supplier
              </li>
              <li
                class="text-sm text-center px-2 hover:bg-orange-300 hover:cursor-pointer"
                @click="navigateTo('stackholder')"
              >
                Data Stackholder
              </li>
            </ul>
            <li
              class="text-center px-2 hover:bg-orange-300 hover:cursor-pointer"
            >
              Rak Penyimpanan
            </li>
            <li
              class="text-center px-2 hover:bg-orange-300 hover:cursor-pointer"
            >
              Transaksi
            </li>
            <li
              class="text-center px-2 hover:bg-orange-300 hover:cursor-pointer"
            >
              Laporan
            </li>
          </ul>
        </div>
      </div>
    </div>
  </nav>
</template>
