<script setup>
import { ref, watch } from "vue";

const props = defineProps({
  user: {
    type: Object,
    default: () => ({}),
  },
  isEdit: {
    type: Boolean,
    default: false,
  },
});

const form = ref({
  username: "",
  email: "",
  role: "",
});

watch(
  () => props.user,
  (newUser) => {
    if (props.isEdit) {
      form.value = { ...newUser };
    } else {
      form.value = {
        username: "",
        email: "",
        role: "",
      };
    }
  },
  { immediate: true }
);

const emit = defineEmits(["submit", "back"]);

const submitForm = () => {
  if (form.value.username && form.value.email && form.value.role) {
    emit("submit", form.value);
  }
};

const backToList = () => {
  emit("back");
};
</script>

<template>
  <div class="max-w-lg mx-auto p-4">
    <form @submit.prevent="submitForm">
      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2">
          Username
        </label>
        <input
          v-model="form.username"
          type="text"
          class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:outline-none focus:border-blue-500"
          required
        />
      </div>

      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2">
          Email
        </label>
        <input
          v-model="form.email"
          type="email"
          class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:outline-none focus:border-blue-500"
          required
        />
      </div>

      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2"> Role </label>
        <select
          v-model="form.role"
          class="w-full px-3 py-2 border border-gray-300 rounded-lg focus:outline-none focus:border-blue-500"
          required
        >
          <option value="">Pilih Role</option>
          <option value="supplier">Supplier</option>
          <option value="stackholder">Stackholder</option>
        </select>
      </div>

      <button
        type="submit"
        @click="submitForm"
        class="w-full bg-blue-500 text-white font-bold py-2 px-4 rounded-lg hover:bg-blue-600"
      >
        {{ isEdit ? "Edit" : "Add" }}
      </button>
      <button
        @click="backToList"
        class="bg-gray-500 text-white px-4 py-2 rounded-lg"
      >
        Back
      </button>
    </form>
  </div>
</template>
