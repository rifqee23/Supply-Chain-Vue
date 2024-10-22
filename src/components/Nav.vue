<script setup></script>

<template>
  <nav class="bg-green-700 border-b border-green-500">
    <button class="absolute left-2 top-5 md:hidden z-30">
      <i class="pi pi-align-justify text-2xl"></i>
    </button>
    <div class="mx-auto max-w-7xl px-2">
      <div class="relative flex h-16 items-center justify-between z-20">
        <div class="flex flex-1 items-center justify-center md:justify-start">
          <div class="flex flex-shrink-0 items-center">
            <h3>Supply Chain</h3>
          </div>
        </div>
      </div>
      <div>
        <div class="absolute top-0 left-0 right-0 bottom-0 bg-white z-10">
          <ul class="flex flex-col justify-center mt-20 gap-y-2 text-gray">
            <li
              class="text-center px-2 hover:bg-orange-300 hover:cursor-pointer"
            >
              Home
            </li>
            <li
              class="text-center px-2 hover:bg-orange-300 hover:cursor-pointer"
            >
              Master Data
            </li>
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
